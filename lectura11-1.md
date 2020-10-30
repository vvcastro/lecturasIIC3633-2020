# 📖 Critica: Deep Learning based Recommender System: A Survey and New Perspectives (2)
 
### 📚Introducción:

Este es un paper tipo *survey*, donde se hace presentan, describen y se analizan (brevemente) los principales algoritmos que podemos clasificar como *Deep Recommender Systems* (*DRS*). La idea básica detrás de este tipo de algoritmos será la de utilizar técnicas de *deep learning* para mejorar uno o varios aspectos de los sistemas tradicionales de recomendación.

La primera parte de este *paper* ya fue abordada en la lectura de la semana pasada, por lo que ahora nos centraremos en los tópicos que quedan: **_Algoritmos de DRS_** y **_Visión Futura sobre el área_**. Sobre el primer punto, los autores desarrollaron el tópico en las secciones anteriores, pero ahora ocurre un cierto "avance" en la complejidad de los algoritmos que se estudian. A continuación se detallarán lo que, en mi parecer, son los métodos más relevantes planteados por los autores: 

## 📈 Incorporando *Deep Learning* en Recomendación (2):

1. **_Recurrent Neural Networks based Recommendation_**: 
Los autores dan un foco bastante importante a las _RNN_, esto dada su utilidad para procesar datos secuenciales. En este sentido se destaca un tipo de recomendador que, hasta el momento, no habíamos estudiado: *Session-Based Recommender*, un recomendador que no tiene como tal la información de *interacciones* de un usuario, sino que se basa en la secuencia de *clicks* que hace en la aplicación (acá también incluyo el *context-aware session-based RS*).

✅ Para mi fue importante que se estudien estos tipos de sistemas, pues presentan un *approach* diferente, pero que siento podría ser acoplado en un sistema recomendador más tradicional. En [1] se presentan y comparan estos algoritmos vs otros menos complejos , si bien se llega a la conclusión de que su rendimiento es igual o incluso peor a estos más simples, creo que el estudio de estos sistemas aún puede traer beneficios a la hora de integrar algoritmos de DL híbridos o "ensambles".

1. **_Neural Attention based Recommendation_:** Para mi el punto más fuerte y, de hecho, uno en el cual los autores se centran bastante en el resto de los puntos discutidos. Como dicen los autores:
   
   > By applying attention mechanism to recommender system, one could leverage attention mechanism to filter out uninformative content and select the most representative items (...)

    Además se presentan dos esquemas generales del uso de este tipo de redes: *vanilla attention* y *co-attention*. Según se explica, aparte de la idea de "evitar información irrelevante", también se tiene el gran beneficio de poder saber a qué le presta más atención el modelo, lo que, en definitiva, presenta grandes ventajas a nivel de *explainability*.

✅ Siento que la inclusión de _attention_ es un punto bastante acertado y que, en general, es un _boom_ que he visto harto en DL (desde las pocas cosas que he visto). Si bien en [2] se presenta un esquema más que nada para NLP, entiendo que se ha desarrollado ampliamente la idea y que ahora se puede aplicar a varios problemas del área (por lo que en _RS_ es bueno que no sea un excepción).

3. **_Adversarial Network based Recommendation_**:
Por último, otro gran tema que, creo, ha tenido un *boom* importante en el último tiempo. La idea de las *GANs* para distintas tareas dentro de recomendación tiene harto sentido, pues puede ayudar con la *sparsity*, *negative samplings*, etc. El *paper* [3] presenta un análisis similar a esta lectura, pero centrado únicamente en _GANs_ y los enfoques que se le ha dado en recomendación, creo que, para mí, fue un gran punto de partida para ver temas como *seguridad* de sistemas recomendadores.

Finalmente, los autores plantean lineas de investigación y desafios en los que estos algoritmos tienen que mejorar/adaptarse. De nuevo, resaltaré los puntos que, siento, son los más relevantes en la actualidad:

## 🎹 Future Work:

1. **_Joint Representation Learning from User and Item Content Information_:** Se basa en una de las principales ventajas de _DL_ frente a métodos tradicionales: _generación automática de features_. Según los autores, este tipo de representaciones son una gran ayuda, ya que sirven para representar datos que hasta antes podían ser dificil de incluir en modelos (imágenes, texto, sonido, etc.) 

2. **_Explainable Recommendation with Deep Learning_:** Este es un tópico bastante mencionado y que hemos estudiado bastante, hemos visto como la "explicability" de un sistema recomendador pueden mejorar bastante la idea que tiene el usuario sobre el sistema o su "overall satisfaction". En este sentido, la introducción de arquitecturas como la de "attention" brinda luces bastantes positivas toda esta rama de _RS_,

3. **_The Field Needs Better, More Unified and Harder Evaluation_**: Finalmente, uno de los temas más importates (en el área acádemica al menos), creo que la idea de tener una forma de evaluación más unificada para modelos de este tipo es necesaria. Si bien entiendo que es verdad qe hay una dificultad grande dado que cada arquitectura y los inputs que recibe varian, sería necesario tener esquemas más generales a la hora de hacer evaluación en este tipo de sistemas.

## 💻 Conclusiones:

Personalmente, creo que, principalmente, la conclusión del *paper* estuvo bastante interesante. El hecho de que se presenten estas lineas de investigación futura y posibles problemáticas en la que seguir avanzando sirve para proponer entrar al mundo de _DRS_. 

## 🖇 Bibliografía Revisada:

1. Ludewig, M., Jannach, D. (2018). Evaluation of Session-based Recommendation Algorithms.
   
2. Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Lukasz Kaiser, Illia Polosukhin. (2017). Attention is All you Need.

3. Deldjoo Yashar, Di Noia Tommaso. Merra Felice. (2020). Adversarial Machine Learning in Recommender Systems: State of the art and Challenges
