# 📖 Critica: A user-centric evaluation framework for recommender systems.
 
### 📚Introducción:


Hasta la época cercana al paper (~2010), la mayoría de los estudios en sistemas recomendadores se habían basado en la idea de que un mejor sistema recomendador era el que perfeccionaba méticas como *Accuracy*, *Precision*, *nDCG*, etc. Sin embargo, el uso y perduración en el tiempo de estos sistemas está fuertemente ligado a la percepción que los usuarios tienen de este, la cual no siempre está bien promovida por mejores *accuracies*. En este sentido, este artículo explora y profundiza la idea de hacer evaluaciones en base a la **_Experiencia del usuario_**, lo cual, si bien lleva a hacer una evaluación más cualitativa del funcionamiento del recomendador, generar estadísticas importantes y que deben ser analizadas a la hora de implementar un Sistema Recomendador. 

### 🧾 ResQue:

Con esto en mente, los autores presentan un *framework* basado en un cuestionario (**ResQue**) para someter a evaluación y medir, desde la subjetividad de los usuarios, la satisfacción que tienen sobre un sistema recomendador.

 El esquema que proponen se divide en 4 *construcs* principales: **_User Perceived Qualities_**, **_User Beliefs_**, **_User Attitudes_** y **_Behavioral Intentions_**. A su vez, cada uno de estos *constructs* tiene subdivisiones que finalmente conforman 13 componentes distintos del esquema.

 ❌ Creo que la principal crítica que se le puede hacer a la publicación es el hecho de que, si bien presentan el esquema, no hay ningun resultados de su aplicación (hay resultados de esquemas similares en el pasado). Esto es un problema, ya que, sobre todo al necesitar directamente interacción con usuarios, la puesta en marcha del método puede generar problemáticas no vistas en la formulación teórica.

## 📈 Contrucs:

En este apartado se analizará cada uno de los componentes principales presentados en el *framwork*:

1. **Perceived System Qualities:** Referido al funcionamiento como tal del sistema recomendador, **busca cuantificar las métricas que generalmente se estudian de manera *offline*** (*accuracy*, *diverse*, *context compatible*, etc), desde la experiencia e interacción con el usuario. Además, se incluye la evaluación de la interfaz que se le expone al usuario (cómo se exponen las recomendaciones).

    ✅ Creo que este primer apartado logra bien su objetivo ya que presenta ideas que no se han estudiado hasta ahora, como *relative accuracy*, respecto a recomendaciones de amigos. Además, creo que varias de las métricas como *Novelty* y *Diversity* son mucho más significativas si son evaluadas desde el punto de vista del usuario (que es lo que se hace en este apartado).

    ❌ Como punto en contra, creo que alguna de las preguntas que se plantean pueden ser algo ambiguas (lo que puede suponer respuestas no tan representativas):

    ><ul>
    ><li>The items recommeded to me are attractive. </li>
    ><li>I enjoyed the items recommended to me.</li>
    ></ul>

2. **User Beliefs:** Esta más orientado a cómo se siente el usuario al ser recomendado/usar el Sistema (se explica como algo más del momento). En este sentido, se evalúan la idea de *Ease of Use* (la habilidad del usuario para resolver tareas de buena manera), *Perceived Usefulness* (la sensación del usuario sobre si usar el sistema mejoró su rendimiento) y *Control and Trasparency* (si el usuario siente control sobre sus recomendaciones y si estas se pueden explicar de buena manera).

    ✅ Creo que este apartado es bastante bueno y significativo, en el sentido que explora ideas significativas del uso de un sistema recomendador. Por ejemplo, ellos dicen que 
    
    > (...) perceived ease of use may be more appropiate than using the objective task completion time (...)
    
    Lo cual presenta una buena ventaja comparativa y diferenciación respecto a otros esquemas estudiados (me gusta porque lo presenta como una actividad más real). En este sentido, creo que las decisiones tomadas en este apartado están bien justificadas y pueden un impacto positivo y significativo en la implementación de estos modelos de testeo.

3. **User Attitudes:** Es similar al concepto de *Beliefs*, pero, según el paper, estos perduran más en el usuario. Se ven métricas de *Overall Satisfaction*, *Confidence Inspiring* y *Trust*.

4. **Behavioral Intentions:** Orientado a si el sistema es capaz de influenciar al usuario para usar o recomendar el sistema en un futuro.

    ❌ Siento que estos dos últimos puntos se analizan con poca profundidad en el *paper*, siendo que, creo, están bastante relacionados y tienen gran relevancia en la perduración y éxito de un sistema recomendador. Sobre todo para estos puntos creo que hubiera sido fundamental ver resultados experimentales, ya que, por ejemplo, un usuario puede hablar sobre recomendar la aplicación en el momento que se le pregunta, pero no llegar realmente a hacerlo (creo que esto se mezcla un poco con la psicología en este tipo de estudios). En este sentido, creo que fácilmente estos dos aparatados pueden caer al ser analizados con resultados reales.

### 📕 Simplified Model:

En la última sección del paper se propone un modelo simplificado de este esquema, en base a la idea de que estas ```60 preguntas``` pueden ser complejas de aplicar en una evaluación normal.

❌ Creo que si bien hay un punto en el número de preguntas que se aplican, siento que sin una experimentación real es muy complicado efectivamente decir si este modelo simplificado obtiene buenos resultados (o incluso el modelo que proponen). En este sentido, creo que lo correcto hubiera sido hacer una comparativa con resultados sobre la inferencia que se puede hacer desde ambos modelos.

## 💻 Conclusiones:

Creo que este *paper* sienta bases importantes para la medición de la experiencia del usuario de un sistema recomendador. Este es un elemento bastante significativo en la implementación de muchas aplicaciones de uso comercial (también de no comerciales) donde la interacción con el usuario debe ser la mejor posible y donde, en pos de captar la atención de usuarios, métricas como *perceived ease of use* pueden tomar relevacia frente a métricas tradionales de *accuracy*.

## 🖇 Bibliografía Revisada: