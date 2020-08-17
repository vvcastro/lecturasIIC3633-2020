# 📖 Critica: Item-based collaborative filtering recommendation algorithms...

### 📚Contexto:
Los algoritmos que utilizan _Collaborative Filtering (CF)_ son métodos de recomendación que se basan en buscar similitudes entres usuarios o _items_ y, a partir de estas, generar recomendaciones. Estos algoritmos se pueden dividir en _memory-based methods_ y _model-base methods_, entre los primeros se encuentran los _user-based_ e _item-based_ (según [2]) que serán los principales puntos de discusión en el artículo.

Si bien algoritmos que emplean _CF_ y, específicamente, _user-based CF_ son los algoritmos más populares y utilizados en la práctica (en los años del paper), la expansión de las aplicaciones _web_ y los millones de nuevos datos que estas generan ha revelado problemas específicos en estos cuando se habla de **escalabilidad** o la **distribución datos**.

### 🧾 Item-Based CF:
Ante estas problemáticas, los autores proponen un esquema _item-based CF_ que ataca ambos problemas y que, según los experimentos realizados, resulta en un menor tiempo de computo y mejores rendimientos. A continuación se discutirán los aspectos relevantes de su propuesta:

La cualidad que me parece destacable del esquema es la idea de poder calcular similitudes con anterioridad y, a partir de estas, hacer **_prunning_** para disminuir la carga posterior del procesamiento. Y que, si bien en el paper se propone un método que termina con _top-k_ vecinos:

> For each item _j_ we compute the _k_ most similar items, where _k_ << _n_ and record these item numbers and their similarities with _j_

Existen otras técnicas interesantes, como la que se muestra en [1], donde que se hace _prunning_ dejando _items_ que tengan un mínimo de ```m``` evaluciones de usuarios en común.

Esta lógica es la clave de **escalabilidad** presentada en el paper, pues al agregar nuevos usuarios se puede asumir que la similitud entre _items_ tiene variaciones pequeñas o incluso despreciables. Además, esta misma es capaz de atacar el problema de reducción de rendimiento  en los casos donde la **distribución de datos** es pobre (ie: usuarios nuevos que no tienen muchos _ratings_), pues el recomendador se basará en los _items_ en los que sí se han hecho evaluaciones, lo que en definitiva mejorará la predicción para estos usuarios.

### 💻 Experimentación:
El experimento que se realiza en el paper se basa en un _dataset_ de evaluación de películas con 43.000 usuarios y más de 3.500 películas, de los cuales se seleccionó al azar para obtener exactamente ```100.000 ratings```. Estos datos definieron un **sparcity level** de 0.9369 el cuál no se varió en ningún experimento.

Para mí este es el primer punto en contra en sus experimentos, pues creo que sería necesario hacer un análisis de sensibilidad sobre esta variable (_sparcity level_), pues tampoco hay una justificación para esta elección (como por ejemplo, que estos sean los valores observados en las aplicaciones comerciales). En vez de esto se elige variar la porción de datos en _training/testings sets_, lo cuál no parece tener un significado teórico muy profundo.

A partir de este _dataset_ se elige la métrica **_MAE_** para la comparación de rendimientos de diferentes esquemas. Creo que si bien esta es una buena métrica para determinar la **precisión de las predicciones**, en un sistema recomendador se debería evaluar algo más que eso (no evalua la **calidad**). En mis lecturas me topé con el término **_serendipity_** que lo aplico a la idea de que este esquema no le ofrece al usuario una recomendación a la cual ella/él no pueda acceder (ie: haciendo una búsqueda rápida de un director que le guste), es decir, se podría argumentar sobre si estás predicciones son realmente valiosas para el usuario o si simplemente son predicciones "seguras" (yo creo que son las segunda).

### 📥 Palabras Finales:
Creo que si bien el método presentado en el paper es eficiente para el caso estudiado (considerando la métrica _MAE_), esto está fuertemente sujeto al _dataset_ utilizado. En [2] se hace una referencia importante a que es la relación ```usuarios/items``` la que genera mayor impacto en cuanto al rendimiento de métodos _user-based_ vs _item_based_, siendo el método propuesto en el paper mejor en los casos de donde existen muchos más usuarios que productos.




## 🖇 Referencias:

1. Schafer, J. B., Frankowski, D., Herlocker, J., & Sen, S. (2007). Collaborative filtering recommender systems. In The adaptive web (pp. 291-324).

2. Ricci, F., Rockach L., Shapira B. (2010). A Comprehensive Survey of Neighborhood-Based Recommendation Methods. Recommender Systems Handbook (pp. 37-76).
