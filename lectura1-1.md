# 📖 Critica: Item-based collaborative filtering recommendation algorithms...

### 📚Contexto:
Los algoritmos que utilizan _Collaborative Filtering (CF)_ son métodos de recomendación que se basan en buscar similitudes entres usuarios o _items_ y, a partir de estas generar recomendaciones. Estos algoritmos se pueden dividir en _memory-based methods_ y _model-base methods_, entre los primeros se encuentran los _user-based_ e _item-based_ que serán los principales puntos de discusión en el artículo.

Si bien algoritmos que emplean _CF_ y, específicamente, _user-based CF_ son los algoritmos más populares y utilizados en la práctica (en los años del paper), la expansión de las aplicaciones _web_ y los millones de nuevos datos que estas generan ha revelado problemas específicos en estos cuando se habla de **escalabilidad** o la **distribución datos**.

### 🧾 Item-Based CF:
Ante esta problemática, los autores proponen un esquema _item-based CF_ que ataca ambos problemas y que, según los experimentos realizados, resulta en un menor tiempo de computo y mejores rendimientos. Se discutirán aspectos de estos resultados en los siguientes apartados: 

#### 📉 Tiempo de computo:
Una de las cualidades más importantes de de los _item-based methods_ es que, como se basa en indices de similitud entre distintos _items_ y estas se pueden precomputar con anterioridad, se puede hacer _prunning_ del número de _items_ que se consideran "vecinos". El esquema propuesto en el paper hace el siguiente _prunning_:

> For each item _j_ we compute the _k_ most similar items, where _k_ << _n_ and record these item numbers and their similarities with _j_

Además, existen otras ideas interesantes que no se exploraron en el árticulo como hacer _prunning_ comparando _items_ que tengan un mínimo de _m_ _user ratings_.\
Esta propiedad del método lleva a que se pueda optar por reducir el número de comparaciones que se hacen de forma significativa lo que puede llevar a reducir drásticamente los tiempos de ejecución _online_ y en _training_.

#### 📈 Erro MAE (Rendimiento):





## 🖇 Referencias:

1. Schafer, J. B., Frankowski, D., Herlocker, J., & Sen, S. (2007). Collaborative filtering recommender systems. In The adaptive web (pp. 291-324). Springer Berlin Heidelberg.

2. Ricci, F., Rockach L., Shapira B. (2010). A Comprehensive Survey of Neighborhood-Based Recommendation Methods. Recommender Systems Handbook (pp. 37-76) 
