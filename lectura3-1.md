# 📖 Critica: Performance of recommender algorithms on Top-N recommendation tasks

### 📚Contexto:
Como ya lo hemos discutido con anterioridad, la gran parte de los sistemas recomendadores de uso comercial se basan en entregar una lista de los *top-N items* que, se supone, deberían ser de gran interés para el usuario. Y, si bien este _output_ de los modelos es justamente lo que se está buscando, **la forma en la que se evalúan** estos modelos, para determinar "el mejor", no es la mejor. Esto pasa porque se ocupa una métrica que, si bien es importante para predicciones individuales, no se integra de forma correcta a la hora de buscar estas predicciones "grupales".

Así, este paper busca someter a un análisis más riguroso a los prinicipales modelos que se utilizan hoy comercialmente. Para esto, se propone utilizar dos métricas como "más significativas" en la tarea de _top-N_: **_precision_ y _recall_**. Además, propone variaciones a estos modelos con el objetivo de mejorar su rendimiento en esta tarea:

### 🧾 Esquema de Testeo y comentarios:

Como este paper se basa en hacer un análisis experimental de los modelos, lo primero que hace es definir la metodología con la que testearon sus experimentos. De los _datasets_ que ellos utilizarán obtendrán dos _subsets_; el _set_ _M_ de entrenamiento y el _set_ _T_, de training. La principal peculiaridad de su división es que este último va a contemplar **solo _ratings_ de cinco estrellas**, de un _subset_ llamado _probe set_. Además, proponen una división en el set de _testing_ a partir de la popularidad y porcentaje de _ratings_ de los _items.

❌ Sobre la construcción del conjunto _T_ a partir de solo _ratings_ de 5 estrellas, los autores dicen lo siguiente:

> (...) we can reasonably state that _T_ contains items relevant to the respective users.

Para mi, acá existe un error, ya que usen que la relevancia de un _item_ viene solo por la nota máxima asociada a los pares ```(user, item)```, lo cual puede ser cuestionable por dos motivos:
 
1. No hay una justificación de, por ejemplo, porqué un _item_ con _ranking_ 4 no puede caer en la categoría de relevante para un usuario.
2. El punto más importante, no considera los **sesgos específicos de cada usuario** en sus evaluacones. Acá entra el clásico ejemplo del usuario que no suele dar ratings altos.

Esto claramente genera un problema en su metodología, ya que, posiblemente, dejan fuera del análisis a un gran grupo de usuarios/items (algo así como un problema de  _Coverage_).


✅ Por otra parte, creo que la idea de dividir y, en realidad, testear los distintos algoritmos considerando o no lo _items_ más populares es tremendo. Creo que este análisis es importante, ya que en trabajos como [1], se ha mostrado que la mayoría de lso algoritmos de filtrado colaborativo tienen una componente social que, en definitiva, inserta un _bias_ hacia los _items_ más populares. En estte sentido, creo que es interesante poder ver este análisis en los distintos tipos de algoritmos. 

### 📈 Modelos y variaciones

En el paper se discuten dos tipos de algoritmos  **"bases": _item-based CF_ y _SVD_**. Desde ambos se discuten distintas variaciones a estos, como la métrica de similitud en _item-based CF_ y la forma de obtener las predicciones desde los modelos (recordar que ahora solo nos interesa el _ranking_). Por otra parte, se busca analizar los modelos de _SVD_ ya testeados en los _datasets_ que presentan buenos rendimientos en cuanto a _RSME_.

🥑 En esta parte no tengo mucho que agregar, me parece que cubren bien todos los modelos tradicionales. Me hubiera parecido interesante incluir en el análisis como un modelo _user-based_ se comportaba a la hora de predecir particularmente _rankings_ (ya que en este caso nos estamos desprendiendo de las métricas tradicionales).

La última propuesta que hace el paper es la de **utilizar _PureSVD_**. Esto es "algo nuevo", ya que este algoritmo no trabaja bien con datos _sparse_ y, gracias a la contrucción que los autores hicieron del problema, (los autores dicen que) la pérdida de información debido a setear los valores nulos en 0 es nula. De acá, que el método tradicional de _SVD_ puede ser utilizado en el _dataset_ contruido (además de necesitar poco poder de cómputo).

❌ En este punto creo que tienen un problema, ya que si bien ellos mencionan que:

> In terms of predictive power, the choice of zero is not very important, and we have received similar results with higher imputed values.

Estos resultados no se encuentran públicados en el _paper_. Por otro lado, creo que si bien para estos _datasets_ este esquema puedo no resultar en grandes implicancias, no sabemos si en otros _datasets_ el esquema de _PureSVD_ se mantendrá consistente. Realmente, me hubiera gustado de ver un poco de experimentación al respecto, por ejemplo, incluyendo comparaciones con métodos que tratan de "llenar" estas casillas vacías, como se hace en otros esquemas de _SVD_.


### 📕 Conclusión:

Creo que el paper me sirvió para cerrar de buena forma mis ideas de acuerdo a las principales métricas que se ocupan en sistemas recomendadores (en lecturas pasadas me he interesado bastante en el tema). Hablando un poco más de los resultados que ellos obtuvieron, **me sorprende bastante como su _PureSVD_** fue capaz de superar al resto de los modelos en sus experimentos. En definitiva, creo que fue un buen paper, simple de seguir, pero que tiene la idea potente de que los modelos y las formas de evaluarlos no siempre se han construido a favor de las tareas con los que se ocupan hoy en día.


## 🖇 Referencias:

1. Celma, O. and Cano, P. 2008. From hits to niches? or how popular artists can bias music recommendation and discovery. In Proceedings of the 2nd KDD Workshop on Large-Scale Recommender Systems and the Netflix Prize Competition (NETFLIX '08). Association for Computing Machinery, New York, NY, USA, Article 5, 1–8.

1. Anna B. (2016). Recommender Systems - It's Not All About the Accuracy. Recuperado de [Medium](https://gab41.lab41.org/recommender-systems-its-not-all-about-the-accuracy-562c7dceeaff).
