# 📖 Critica: Collaborative Filtering for Implicit Feedback Datasets

### 📚Contexto:
Si bien la mayoría de las aplicaciones de **Sistemas Recomendadores** (hasta la fecha del paper) se basan en lo que se llama _explicit feedback_ (información en forma de _like_ o _puntuaciones_), existe información extra de los usuarios que puede ser utilizada de forma favorable a la hora de hacer recomendaciones. Este paper explora esta idea implementando un _recomendador_ que solo se basa en información implícita (no) dada por el usuario, específicamente, utiliza la **información de la _frecuencia_ con la que se consume cada _item_**.


Si bien los resultados que obtienen los autores son significativos, la implementación y evaluación de estos modelos puede contener varios **sesgos** de los cuales se discutirá un poco en esta crítica.

### 🧾 Collaborative Filtering for Implicit Feedback Datasets:
El modelo propuesto por los autores sigue un esquema similar a la de los modelos de _Matrix Factorization_, donde se busca descomponer describir a los usuarios e _items_ en atribudos llamados _factors_ (_f_). La idea es que, es estimar la disposición de un usuario _u_ hacia un item _i_ y, dado que trabajan con datos implícitos, ellos utilizan dos variables para cuantificar esta dispoción: $p_{ui}$ y $c_{ui}$, las cuales denotan **preferencia** y **confianza** de este valor $p$, respectivamente. Finalmente, en el problema de optimización, ambas variables son incluidas.

### 📈 Aspectos interesantes:

Uno de los puntos que más destaco sobre cómo se hizo la formulación es como la definición del **problema de minimización** y la **variable $c_{ui}$** (especificamente, el 1 añadido) llevaron a poder precomputar una gran parte de los calculos y, con esto, reducir en gran medida la complejidad de los calculos _online_ que tiene que hacer el recomendador. Esto es fundamental a la hora de dar escabilidad a los solución propuesta. Otro plus que tiene esta definición de $c_{ui}$ es la de dar más importancia a los pares $ui$ que tienen una preferencia más alta.

Otro aspecto que me parece significativo del esquema es su **simplicidad** y que parte de un esquema ya bien estudiado. Creo que esto es importante ya que, además, como se basa en las variables $p$ y $c$, estas se pueden **manipular y variar** de forma rápida. Por ejemplo, a mi parecer, es muy importante la idea de agregar un _threshold_ para la binarización de $p$ o el hecho de poder cambiar la fórmula de $c$, ya que estos cambios pueden incidir tanto en lo que busca el modelo, como en el rendimiento de este.

Finalmente la **explicabilidad** del modelo, como se dice en el paper, es una de los factores más importantes en su solución y para los sitemas recomendadores en general.

### 📉 Aspectos negativos:

Si bien el esquema tiene cosas muy positivas, hay un par de aseveraciones e ideas que se introducen al modelo las cuales pueden varian bastante según la idea del _implementador_ (en el fondo, estoy hablando de la **introducción de _sesgos_**). Esto me parece importante, ya que en el paper **se hacen muchas "suposiciones"** sobre porqué pueden ocurrir ciertas distribuciones en los datos, la cuales pueden ser ciertas, pero no hay una fundamentación detrás de estas y no se estudia como estos puede cambiar el rendimiento del modelo.

Otro aspecto, es la idea de que $p = 1$ se defina con $r_{ui} > 0$ (esto igual está un poco ligado con el primer punto) lo cual, si bien lo mencionan como un aspecto que puede variar, **no lo hacen en su experimentación**. Esto me parece un error, ya que se pudo a ver definido el mismo modelo sobre un parámetro _threshold_ y hacer un análisis de sensiblidad sobre este. Es mi creencia que este parámetro es importante, sobre todo porque mencionan la idea de que hay mucho valores de $r_{ui}$ que no son 0 debido al _zapping_ o problemas del estilo.

Por último, creo que es algo que pudo inducir al primer punto, es el hecho de que **los datos que tienen** o que utilizan a la hora de hacer el modelo **son pobres**. Esto va al hecho de que carecen (o no utilizan) más información que la de cuánto tiempo se vio un determinado canal. Esto creo que genera problemas, sobre todo en la personalización, ya que por ejemplo, se asume que toda una familia que ve televisión se comporta como un usuario. Si bien esto es un tema que va por la contrucción del problema, es una desventaja cuando se compara con _usuarios_ en sitios o aplicaciones _webs_.

### 📕 Una conclusión:
Si bien la inclusión de _implicit data_ en los problemas de recomendación es una herramienta poderosa, parece fundamental el uso también de _explicit data_ en estos sistemas. Ya que el uso de ambos tipos de datos puede ayudar a cerrar dudas y suposiciones que de deben hacer en los modelos con solo datos ímplicitos.

## 🖇 Referencias:
