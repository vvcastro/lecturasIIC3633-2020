# 📖 Critica: Content-Based recommendation systems
  
*Content-Based Recommendation Systems* es un capítulo del libro *The Adaptive Web* que tiene como objetivo introducir en las principales técnicas que los sistemas **_content-based_**  de recomendación utilizan (hacia la fecha de publicación). En este sentido, es un poco díficil criticar aspectos teóricos o experimentales, pues el texto no tiene este foco. De todas formas, varias criticas e ideas se puedieron extraer:

## 📚Contexto:
La principal idea detrás de los sistemas recomendadores que se basa en contenido es la de utilizar la descripción de los _items_ para hacer _matching_ con los intereses de los usuarios y, así, hacer recomendaciones personalizadas. Esta lectura se encarga de explorar (parte de) los dos problemas que se extienden de esta definición: **cómo obtener estas descripciones** y **cómo utilizarlas para hacer recomendaciones**.

Específicamente, en el primer punto los autores exploran la idea de cómo extraer _data_ desde los usuarios y, principalmente, **cómo procesar esta información** para ser utilizada. Por otra parte, para el segundo problema, se dedican a mencionar y explicar los **principales algoritmos de _machine learning_** que se ocupan para clasificar todos estos datos adquiridos (hasta la fecha de excritura del texto).

## 🤖 Unrestricted Text Fields y Text Classification:
Si bien el capítulo se centra en _content-based systems_, gran parte del texto habla sobre **Unrestricted Text Fields** o sobre **Text Classification**. El primer término se refiere a un tipo de _feedback_ que da el usuario donde este escribe en un lenguaje libre o "semi-libre", sobre un _item_ específico o sobre sí mismo. Este tipo de _input_ es bastante relevante ya que nos permite **acceder a mucha información que se encuentra en forma de texto**, como comentarios, descripciones, críticas, menús, etc.

Si bien esto nos abre la puerta a mucha información, el principal problema con esto es **cómo procesar y clasificar** estos escritos y, para lo cual, los autores nos presentan distintos métodos como el _Stemming_ y varias técnica de _Text Classification_. A continuación un breve análisis de algunos de estos métodos:

1. **Stemming**: Este método se refiere a la idea extraer el verbo _stem_ (que es algo similiar a la raíz, pero no es necesariamente lo mismo) de una palabra. Esto se hace en base a una heurística, por lo que se puede decir que es un método _ruled-based_, donde básicamente, con las reglas de escritura de un idioma podríamos ir procesando las palabras. Los principales problemas que este método tiene es el _UnderStemming_ y _OverStemming_, donde se corta muy poco o mucho de una palabra. En [1] se hace un gran análisis de todo esto y se presentan algunos algoritmos típicos del método.

2. **SVM**: Las SVM son un método de machine learning que fue el estado del arte en muchos problemas hasta el auge del _Deep Learning_, por lo que están validadas en muchos problemas de aprendizaje. En el paper donde se presentan para "Text Categorization" [2], se comparan con otros métodos que también se discuten en el texto como _Bayes_ y _Rocchio_ (el estado del arte en esa época) y llega a bastantes mejores resultados. Sobre estos resultados el autor (de [2]) señala que las _SVM_ son especialmente "*well suited*" para este tipo de problemas ya que logran representar de buena maneras las principales características que tienen los textos.

3. **RIPPER**: Es un algoritmo basado en _rule learning_ (aprender reglas lógicas desde los datos) que nació de una mejora hecha al algoritmo de **IREP** (en [3]) para que pudiera generalizar mejor, reducir errores y mejorar su escalibidad en _datasets_ de mayor tamaño. Destaco a este algoritmo porque pertenecen a una rama de _machine learning_ que realmente no había escuchado hasta que leí este paper.

✅ Para mí este eje es la parte más interesante del capítulo, ya que se habla de muchas ideas que en la actualidad han tomado relevancia. Especialmente, hay muchas ideas de _Natural Language Processing (NLP)_ que me parecen interesantes, pues son de una época no tan "avanzada" como la de ahora (que igual da cuenta de lo mucho que ha avanzado el área).

❌ Por otra parte, si bien este texto se basa en recomendadores basados en contenidos, siento que prima la importancia y centralidad que se le da a los tópicos de NLP. Si bien esto no es un problema para mí, siento que el texto si falla en discutir otras ideas de _content-based_, quizás menos "interesante", pero sumamente útiles.

❌ Si bien esto no lo puedo decir como una crítica, como bien se dijo en el texto, la mayoría de los métodos de NLP que se presentan tienen serios problemas a la hora de generalizar datos y tampoco tocan ideas de _user-bias_ en sus definiciones.

### 📕 Conclusión:
Si bien los algoritmos de _content-based_ pueden ser potentes a la hora de describir los gustos o intereses de un usuario, el método pareciera tener no muy buenos resultados prácticos. En [4], se habla de dos problemas típicos: _**Limited content analysis**_, el problema de no tener suficientes datos para describir a las entidades y _**Over-specialization**_, cuando describimos tan bien los intereses del usuario que todos los _items_ que recomendamos son muy similares entre si. Así, se llega a una conclusión general que para obtener buenas recomendaciones es necesario utilizar método híbridos.
## 🖇 Bibliografía Revisada:

1. Heidenreich, H. (2018). Stemming? Lemmatization? What?. Recuperado en [Medium](https://towardsdatascience.com/stemming-lemmatization-what-ba782b7c0bd8).

2. Joachims, T. (1998). Text Categorization with Support Vector Machines: Learning with Many Relevan Features. In: European conference on machine learning.
   
4. Cohen, W. (1995). Fast Effective Rule Induction. In: Proceedings of the Twelfth International Conference on Machine Learning, Tahoe City, CA.

5. Ricci, F., Rockach L., Shapira B. (2010). A Comprehensive Survey of Neighborhood-Based Recommendation Methods. Recommender Systems Handbook (pp. 38).