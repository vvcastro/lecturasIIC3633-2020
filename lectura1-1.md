# 📖 Critica: Item-based collaborative filtering recommendation algorithms...

### 📚Contexto:
Los algoritmos que utilizan _Collaborative Filtering (CF)_ son métodos de recomendación que se basan en buscar similitudes entres usuarios o _items_ y, a partir de estas, generar recomendaciones. Estos algoritmos se pueden dividir en _memory-based methods_ y _model-base methods_, entre los primeros se encuentran los _user-based_ e _item-based_ (según [2]) que serán los principales puntos de discusión en el artículo.

Si bien algoritmos que emplean _CF_ y, específicamente, _user-based CF_ son los algoritmos más populares y utilizados en la práctica (en los años del paper), la expansión de las aplicaciones _web_ y los millones de nuevos datos que estas generan ha revelado problemas específicos en estos cuando se habla de **escalabilidad** o de **vacíos en los datos** (_sparsity_).


### 🧾 Item-Based CF:
Ante estas problemáticas, los autores proponen un esquema _item-based CF_ que ataca ambos problemas y que, según los experimentos realizados, resulta en un menor tiempo de computo y mejores rendimientos. A continuación se discutirán los aspectos relevantes de su propuesta:

La cualidad que me parece más destacable del esquema es la idea de poder calcular similitudes con anterioridad y, a partir de estas, hacer **_prunning_** para disminuir la carga posterior del procesamiento. Y que, si bien en el paper se propone un método que termina con _top-k_ vecinos:

> For each item _j_ we compute the _k_ most similar items, where _k_ << _n_ and record these item numbers and their similarities with _j_

Existen otras técnicas interesantes, como la que se muestra en [1], donde que se hace _prunning_ dejando _items_ que tengan un mínimo de ```m``` evaluciones de usuarios en común.

Esta lógica es la clave de **escalabilidad** presentada en el paper, pues al agregar nuevos usuarios se puede asumir que la similitud entre _items_ tiene variaciones pequeñas o incluso despreciables. Además, esta misma es capaz de atacar el problema de reducción de rendimiento  en los casos donde hay gran **vacíos en los datos** (ie: usuarios nuevos que no tienen muchos _ratings_), pues el recomendador se basará en los _items_ en los que sí se han hecho evaluaciones, lo que en definitiva mejorará la predicción para estos usuarios.

### 💻 Experimento:
El experimento que se realiza en el paper se basa en un _dataset_ de evaluación de películas con 43.000 usuarios y más de 3.500 películas, de los cuales se seleccionó al azar para obtener exactamente ```100.000 ratings```. Estos datos definieron un **sparsity level** de 0.9369 el cuál **no se varió** en ningún experimento.

Para mí este es el primer punto en contra en su desarrollo, pues creo que sería necesario hacer un análisis de sensibilidad sobre esta variable (_sparsity level_), ya que tampoco hay una justificación para esta elección (como por ejemplo, que estos sean los valores observados en las aplicaciones comerciales). En vez de esto se elige variar la porción de datos en _training/testings sets_, lo cuál no parece tener un significado teórico muy profundo.

A partir de este _dataset_ se elige la métrica **_MAE (Mean Absolute Error)_** para la comparación de rendimientos de diferentes esquemas. Si bien esta es una buena métrica para determinar la **precisión de las predicciones de _ratings_**, un sistema recomendador debería evaluar algo más que solo esta magnitud.\
De hecho, existe una amplia gama de métricas para la evaluación de sistemas recomendadores como **Diversity**, **Covarage**, **Serendepity** y **Novelty** definidas (de muy buena manera) en [3], las cuales (me parece) son fundamentales a la hora de hablar de qué tan bueno es un sistema recomendador en su totalidad. Por ejemplo, el problema más típico de quedar solo con _MAE_, es que las predicciones son muy similares a las _items_ que el usuario ya ha visto (y que podrían encontrar por si mismo), esto lleva a que las predicciones de nuestro sistemas sean algo "irrelevantes" para el usuario.

### 📕 Conclusión (vs _user-based CF_):
Creo que si bien el método presentado en el paper es eficiente para el caso estudiado (considerando solo la métrica de error descrita), este resultado está fuertemente sujeto al _dataset_ utilizado y el cómo este está conformado. En [2] (_User-Based vs Item-Based Recommendation) se explica como la conformación la organización del _set_ de datos afecta de forma positiva/negativa a ambos métodos. Desde esto, se dice que es el _ratio_  ```usuarios/items``` el que determina cuál método será mejor, en específico se dice que:

> (...) a small number of high-confidence neighbors is by far preferable to a large number of neighbors for wich the similarity weights are not trustable.

Es desde este _approach_ que para _databases_ con un número mayor de usuarios que de _items_ (como lo son las bases de datos comerciales), los _item-based methods_ resultan tener mejores resultados (la similitud entre _items_ es más representativa al haber más usuarios). 




## 🖇 Referencias:

1. Schafer, J. B., Frankowski, D., Herlocker, J., & Sen, S. (2007). Collaborative filtering recommender systems. In The adaptive web (pp. 291-324).

2. Ricci, F., Rockach L., Shapira B. (2010). A Comprehensive Survey of Neighborhood-Based Recommendation Methods. Recommender Systems Handbook (pp. 37-76).

3. Anna B. (2016). Recommender Systems - It's Not All About the Accuracy. Recuperado de [Medium](https://gab41.lab41.org/recommender-systems-its-not-all-about-the-accuracy-562c7dceeaff).
