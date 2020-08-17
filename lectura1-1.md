# 📖 Critica: Item-based collaborative filtering recommendation algorithms...

### 📚Contexto:
Los algoritmos que utilizan _Collaborative Filtering (CF)_ son métodos de recomendación que se basan en buscar similitudes entres usuarios o _items_ y, a partir de estas generar recomendaciones. Estos algoritmos se pueden dividir en _memory-based methods_ y _model-base methods_, entre los primeros se encuentran los _user-based_ e _item-based_ que serán los principales puntos de discusión en el artículo.

Si bien algoritmos que emplean _CF_ y, específicamente, _user-based CF_ son los algoritmos más populares y utilizados en la práctica (en los años del paper), la expansión de las aplicaciones _web_ y los millones de nuevos datos que estas generan ha revelado problemas específicos en estos cuando se habla de **escalabilidad** o la **distribución datos**.

### 🧾 Item-Based CF:
Ante estas problemáticas, los autores proponen un esquema _item-based CF_ que ataca ambos problemas y que, según los experimentos realizados, resulta en un menor tiempo de computo y mejores rendimientos. Se discutirá qué aspectos del esquema propuesto ayudan a mitigar o mejorar estos problemas:

La cualidad que parece más relevante en el esquema es la idea de poder calcular similitudes con anterioridad y, a partir de estas, hacer **_prunning_** para disminuir la carga posterior del procesamiento. Y, si bien en el paper se propone un método que termina con _top-k_ vecinos:

> For each item _j_ we compute the _k_ most similar items, where _k_ << _n_ and record these item numbers and their similarities with _j_

Existen otras técnicas interesantes que se podrían agregar en el árticulo, como hacer _prunning_ dejando _items_ que tengan un mínimo de _m_ evaluciones de usuarios en común.

Esta lógica es la clave de **escalabilidad** presentada en el paper, pues al agregar nuevos usuarios se puede asumir que la similitud entre _items_ tiene variaciones pequeñas o incluso despreciables. Además, esta misma es capaz de atacar el problema de reducción de rendimiento  en los casos donde la **distribución de datos** es pobre (ie: usuarios nuevos que no tienen muchos _ratings_), pues el recomendador se basará en los _items_ en los que sí se han hecho evaluaciones, lo que definitiva mejorará la predicción para estos usuarios.

### 💻 Experimentación:
El experimento que se realiza en el paper se basa en un _dataset_ de evaluación de películas con 43.000 usuarios y más de 3.500 películas, de los cuales se seleccionó al azar para obtener exactamente ```100.000 ratings```. Estos datos definieron un **sparcity level** de 0.9369 el cuál no se varió en ningún experimento.

Para mí este es el fue el primer punto en contra en sus experimentos, pues creo que sería necesario hacer un análisis de sensibilidad sobre esta variable, pues tampoco hay una justificación para esta elección (como por ejemplo, que estos sean los valores observados en las aplicaciones comerciales). En vez de esto se elige variar la porción de datos en _training/testings sets_.

A partir de este _dataset_ se elige la métrica _MAE_ para la comparación de rendimientos de diferentes esquemas. Esto genera 




## 🖇 Referencias:

1. Schafer, J. B., Frankowski, D., Herlocker, J., & Sen, S. (2007). Collaborative filtering recommender systems. In The adaptive web (pp. 291-324). Springer Berlin Heidelberg.

2. Ricci, F., Rockach L., Shapira B. (2010). A Comprehensive Survey of Neighborhood-Based Recommendation Methods. Recommender Systems Handbook (pp. 37-76) 
