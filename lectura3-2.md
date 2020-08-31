# 📖 Critica: Evaluating Recommender Systems, Recommender Systems Handbook

### 📚Contexto:
Esta lectura fue un poco distinta al resto ya que pertenecia a un libro y, por lo tanto, no estaba escrito con la idea de revelar nuevos hallazgos o indicar experimentación realizadas.

Dicho esto, el capítulo se centra en las distintas metodologías y métricas que se tienen para evaluar los sistemas recomendadores actuales (~2010). Para esto los autores señalan dos principales ejes en los cuales se centra su contenidos: **_Experimental Settings_** y **_Recommender System Properties_**:

### 🧪 Experimental Settings:

Esta sección explora las principales métodologías y herramientas estadísticas que se pueden utilizar a la hora de hacer experimentos con sistemas recomendadores. En primera instancia, se definen tres esquemas que permiten evaluar características de estos sistemas: **_Offline Experiments_**, **_User Studies_** y **_Online Evaluation_**.

1. **_Offline Experiments_**: Todos los papers que hemos analizado hasta ahora siguen este tipo de evaluación. En esta sección me gustó la idea de que incluir los _timestamps_ en la formulación del _dataset_ y el testeo sobre este. Para mi esto fue interesante, pues, si bien casi todos los papers que he visto siguen este método, pocas veces se ocupa se utilizan todas las ideas que se proponen (en cuanto a la simulación del comportamiento de los usuarios) .

2. **_User Studies_**: Este punto se basa en utilizar grupos de usuarios para testear distintos recomendadores y, como las distintas formas de conseguirlos puede introducir _bias_ en nuestro experimento. Para mi, esta sección me resultó sumamente interesante, ya que permitía hacer un puente con temas relacionados a la psicología de los usuarios.

3. **_Online Evaluation_**: Básicamente, es la idea de hacer experimentación y evaluación "en  vivo". Acá el usuario utiliza la plataforma real donde el sistema se va a implementar. Si bien esto tiene el beneficio de que el usuario no se da cuenta que se está ocupando para el experimento (lo cual sirve para disminuir _bias_), el hecho de estar "probando" recomendadores pueden disminuir el uso de la página.

✅ Un tema que me gustó y descubrí en esta lectura, es que estos métodos no son excluyentes y muchas veces para implementar un sistema recomendador es necesario pasar por todos estos pasos antes de poder tomar decisiones.

❌ Creo que, siendo que acá se abordan temas desde la interdisciplina (con _marketing_ o _psicología_), hay aspectos que quizás no fueron tan bien profundizados (de todas formas, se entiende que este no era el fuerte del texto).

Finalmente, esta sección termina con los métodos estadísticos que se utilizan para determinar si un experimento fue significativo y si los resultados fueron o no concluyentes. En específico se exploran métodos de inferencia como _p value_, intervalos de confianza, etc.

✅ Para mi esto es bastante significativo, ya que si bien son _tests_ que sabía que existían, en ningún paper relacionado (de los que he leído para el ramo) he visto que han introducido este tipo de estadística para justificar los experimentos.

### 📈 Recommender System Properties

En este punto se exploran (creo) todas las métricas que hoy se utilizan para evaluar sistemas recomendadores. Y, si bien, creo que existen métricas más significativas que otras (por lo menos cuando estamos buscando mejores recomendaciones), el hecho de que **se hable de un _trade-off_** entre estas me parece relevante y algo a considerar siempre que se implementen estos sistemas.

Por otra parte, creo que es importante destacar que el texto da ejemplos de cómo estas distintas métricas pueden afectar la visión que los clientes tienen sobre el sistema. Y, si bien hay métricas como **_Privacy_** que, aún siendo dificiles de calcular desde un punto de vista de programación, deben ser consideradas como "utilidad" para los usuarios.

 Finalmente, creo que una de las métricas que más me gustó es la de _utility_, pues siento que sirve como una herramientas de generalización bastante fuerte frente a problemas reales (especialmente el hecho de poder dar utilidad negativa a resultados no deseados).

### 📕 Conclusión:

Creo que este capítulo y, especialmente, la sección de las métricas, abren el espacio para poder entender que un sistema recomendador no solo se base en mejorar predicciones. Es importante entender como cada decisión que se toma sobre la implementación que estamos haciendo puede afectar positiva o negativamente como resulta nuestro experimento o lo que el usuario está recibiendo de nosotros (la idea del _tradeoff_)

## 🖇 Bibliografía Revisada:

1. Anna B. (2016). Recommender Systems - It's Not All About the Accuracy. Recuperado de [Medium](https://gab41.lab41.org/recommender-systems-its-not-all-about-the-accuracy-562c7dceeaff).
