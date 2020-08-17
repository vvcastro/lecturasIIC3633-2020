# 📖 Critica: Post FunkSVD...

### 📚Contexto:
En 2006 Netflix inició el concurso de NetflixPrize el que tenía como tarea ensamblar el mejor algoritmo de _Collaborative Filtering (CF)_ para un sistema recomendador basado en los datos de la propia plataforma. El blog/post presentado cuenta el desarrollo y la lógica que siguió _Simon Funk_ para terminar en el tercer lugar de dicha competencia.

### 🧾 FunkSVD:

_Funk_ basó su propuesta en un algoritmo SVD (_Single Value Decomposition_) el cual pertenece a la rama de _model-based CF_, es decir, tiene como objetivo generalizar los datos en un modelo que contabilice "características" (en este caso _latent factors_) tanto de los usuarios como de las películas. Además, este método realiza _Matrix Factorization (MF)_, que es la idea de reducir la matriz principal de ```user/movies``` en dos matrices con dimensiones más pequeñas (con el número de usuarios/películas vs los _latent factors_).

El gran problema que generaba el _dataset_ entregado por _Netflix_ era la **sparcity** de los datos (habían muchas casillas nulas en la matriz). Lo que él hizo fue ignorar estás casillas sin datos y centrarse en aprender desde los datos que tenía. Para esto, como cualquier modelo de _machine learning_ al calculaba el error de su predicción y reajustaba estos _latent factors_ según estos errores (en otras palabras hacia un _gradient descent_). De todas formas, explora métodos para obtener información relevante sobre estas casillas nulas (determina de que se podían estimar con una distribución _Gaussiana_).

### 💻 Aspectos interesantes:
Creo que una de las propiedades más importante de su modelo es la **gran escabilidad** que alcanza (esto dado que es un _MF method_). De hecho, para los _latent factors_ definidos en su experimentación (40) el logró un factor de reducción de alrededor de x400, lo que produce un disminución en tiempo de ejecución bastante significativa.

Otro punto que me parece necesario recalcar es que su algoritmo **no se ve afectado por el problema de _local minima_** presentes en otros problemas de optimización. Esto se (puede deber) debe a que la función de pérdida que _FunkSVD_ busca minimizar es convexa lo que nos asegura poder llegar a un óptimo. De todas formas, esto trae el problema de _overfitting_ que también se describe en el post.

### 📕 Aspectos (no tan) en contra:
Si bien existe el problema de que muchas de sus decisiones no fueron justificadas ya sea matemáticamente o experimentalmente, puedo asumir que esto se debe a que el blog no es un medio científico formal. Así que, pasando esto por alto, hay un par de aspectos en lo que creo pudo haber mejorado:

1. Si bien es algo que viene desde la métrica definida por (principalmente) _Netflix_ para evaluar sus predicciones, creo que el hecho de haber **escogido solo la métrica de _MSE_ (_mean squared error_)** puede ser contraproducente porque esta (la métrica) recae directamente en lo que significan las recomendaciones que genera el algoritmo y, en este caso, lo único que se busca es minimizar este error en _rating_, lo que podría generar problemas de "sobre-especialización" hacia películas muy similares a las que el usuario ya conoce (lo que es un problema de **serendipity**).\
Este fenómeno me resulta interesante ya que cambiar la métrica de error con la que se aprende **podría** significar recomendaciones, por ejemplo, que sean muy distintas a lo que generalmente se ve, pero aún así le gusten mucho al usuario.
   
2. Otro punto importante, en el cuál este esquema decae un poco es en la **incorporación de un _bias_ por usuario**, es decir, qué pasa con los usuarios que tienden a ser "más exigentes" y dan calificaciones menores (o mayores). Este punto es abordado por la _Biased Matrix Factorization Recommendation_ en [2], donde se decide incluir el _bias_ que tiene cada usuario y película, llegando a resultados mejores que sin incluirlos.
   
3. Por último, el mismo autor señala que a la hora de tratar de **agregar información extra** (fecha) los rendimientos no se mantuvieron. Este problema se ha estudiado desde dos puntos, está la idea de cómo incluir información implícita en el modelo (de acá sale **SVD++**) y la forma en la que se puede incluir la **variable de tiempo** (dado el hecho de que, por ejemplo, las películas suelen tener un _peak_ de popularidad). Ambas temáticas son desarrolladas en [3] donde, además, bajo análisis experimental, se lográ ver mejores resultados en el **modelo ```TimeSVD++```** que incorpora la idea de SVD++ y la inclusión del tiempo en el modelo.

## 🖇 Referencias:

1. Post de [medium](https://medium.com/datadriveninvestor/how-funk-singular-value-decomposition-algorithm-work-in-recommendation-engines-36f2fbf62cac) donde se discute sobre cómo funciona FunkSVD.

2. Sun W., Zhang X., Liang W., He Z. (2015) High Dimensional Explicit Feature Biased Matrix Factorization Recommendation. In: Li XL., Cao T., Lim EP., Zhou ZH., Ho TB., Cheung D. (eds) Trends and Applications in Knowledge Discovery and Data Mining. Lecture Notes in Computer Science, vol 9441.

3. Ricci, F., Rockach L., Shapira B. (2010). Advances in collaborative filtering. Recommender Systems Handbook (pp. 83-91).