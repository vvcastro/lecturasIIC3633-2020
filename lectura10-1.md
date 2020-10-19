# 📖 Critica: Deep Learning based Recommender System: A Survey and New Perspectives
 
### 📚Introducción:

Este es un paper tipo *survey*, donde se hace presentan, describen y se analizan (brevemente) los principales algoritmos que podemos clasificar como *Deep Recommender Systems* (*DRS*). La idea básica detrás de este tipo de algoritmos será la de utilizar técnicas de *deep learning* para mejorar uno o varios aspectos de los sistemas tradicionales de recomendación.

Dado el tipo de *paper*, no se puede hacer una análisis profundo respecto a la experimentación o métricas propuestas, pero podemos discutir la clasificación y presentación de algoritmos que se hacen en el texto.

(Me saltaré la parte donde se describen las diferentes arquitecturas/modelos del *deep learning* ya que no está orientado a a *RS*).

## 🧾 Ventajas y Desventajas del *Deep Learning* en Recomendaciones:

Los métodos de *deep learning* han tenido un gran auge en los último ~10 años, pues han podido igual y superar a gran parte de los métodos *state-of-the-art* que se tenían hasta entonces. En este sentido, aplicar estos algoritmos y métodos a los *Sistemas Recomendadores* puede traer bastantes mejorar, pero hay que tener cuidado con ciertos aspectos de estos algoritmos:

### 📈 Ventajas:

Los autores son capaces de identificar varias ventajas en la utilización de estos algoritmos, para mi las 3 principales son:

1. **NonLinear Transformation:** Esto es algo que impacta en gran medida en el rendimiento que puede tener el sistema, pues los métodos de *Deep Learning* (una red neuronal) son *capaces de aproximar cualquier función continua*. Esto quiere decir que ahora se podrían generalizar distribuciones más complejas de datos.
   
2. **Representation Learning:** Se basa en la idea de cómo una red neuronal es capaz de aprender las características de ciertos *items*/usuarios. Esto está acompañado en gran parte de los *embeddings*, donde uno puede obtener una información propia de ciertos *items* y que, muchas veces, resulta ser bastante buena para representar características que de otra forma se tendrían que extraer a mano o hacer por *labels*.
   
3. **Sequence Modeling:** Se basa en la idea de que algunos tipos de redes neuronales son capaces de extraer de muy buena manera la información desde datos de tipos secuenciales. En este sentido, extraer información de texto (por ej) puede enriquecer bastante el proceso de recomendaciones. Creo que en este sentido, algoritmos como *Conversational Recommender Systems* (en [1] se hace un *survey* sobre estos métodos y cómo algoritmos que usan *RNN* (*LSTM*) han mejorado en gran parte este tipo de sistemas) o métodos que utilicen *written feedback* (reseñas escritas) pueden verse muy beneficiados.

✅ Personalmente siento que partir introduciendo ventajas que estos algoritmos pueden tener es una gran idea pues ayuda a formular o idear métodos propios (ideas de cómo se podría armar un recomendador dadas estas utilidades).

### 📉 Desventajas:

Por otro lado, los autores presentan las principales desventajas que estos algoritmos pueden tener a la hora de ser utilizados para sistemas recomendadores. Si bien me parece importante estas desventajas, los autores presentan argumentos que limitan un poco esta desventaja, con todo esto creo que el límite más fuerte sigue siendo la ***Explicablidad*** y ***Interpratabilidad*** de los resultados.

❌ Creo que los autores pecan un poco de justificar demasiado el advenimiento del *DL*, pues tratan de señalar que las limitaciones de este no son tales. Si bien hablan de que la interpretabilidad de los modelos no será un problema con el enfoque en *Attention*, esto es algo que ha sido un *boom* en *NLP* (como en el *paper* de *Google*, *Attention is All you Nedd* [2]), *no se presenta nada de este ámbito en recomendaciones*. En este sentido, creo que los autores se adelantan un poco a lo que puede ocurrir en el futuro de *DL*. (De todas formas, en [3] se habla de que estos métodos podrían no ser tan interpretables como se proponen)


## 📈 Incorporando *Deep Learning* en Recomendación:

Finalmente, los autores proponen un esquema para categorizar los distintos tipos de Sistemas Recomendadores que utilizan técnicas de *Deep Learning*. A continuación se hará un análisis de cada uno:

1. ***Deep Learning Based Recommendation Models***: Estos métodos son los que, básicamente, están basados únicamente en *DL*, es decir, ocupan métodos clasicos de *deep learning* para predecir *ratings* (en formato de listas). En este sentido, se podría entender a este tipo de algoritmos como "básicos", ya que creo, no aportan un conocimiento nuevo a ninguno de los dos campos.

2. **_Multilayer Perceptron based Recommendation_:** Estos tipos de algoritmos ya entran en un dinámica de incorporar ideas de *deep learning* al conocimiento previo que se tenía de problemas de recomendación. En este sentido, técnicas como *Deep Factorization Matrix* o *Neural Collaborative Filtering* llevan un paso más allá lo que ya conocíamos sobre sistemas recomendadores.

3. **_Autoencoder based Recommendation_:** A mi parecer, uno de los mejores métodos propuestos y que se puede aplicar de distintas maneras en los algoritmos de recomendación. Por una parte, está la idea de utilizarlos para aprender características de *items*, esto tiene grandes ventajas, por ejemplo en el modelo de ***AutoSVD++* o *HRDC*** los cuales mejoran tanto el rendimiendo y eficiencia (en tiempo) del tradicional modelo *SVD++*. \
⚙️ Creo que este tipo de utilización es bastante intereantes y me gustaría ver estos aplicado a modelos que quizás incluyan más *implicit data* comomo *timeSVD++*. \
Por otro lado, está la idea de *AutoRec* que trata de reconstruir (y llenar los *user vectores* e *item vectors*). Este método me parece interesante (creo que tiene una gran aproximación a lo que se podría hacer con una *GAN*) y, de hecho, es uno de los método que presenta mejor *RSME* para el dataset de *MovieLens* (en [este link](https://paperswithcode.com/sota/collaborative-filtering-on-movielens-1m)), por lo que creo, tiene un gran potencial como método a aplicar.

4. ***Convolutional Neural Networks based Recommendation**:* Otro método bastante potente (a mi parecer) y que se basa, principalmente, en aprender caracterísitcas de datos no estructurados (imágenes, texto, audio). En este sentido, creo que, como método, tiene una gran ventaja, pues abre la posibilidad a este tipo de datos.

## 💻 Conclusiones:


## 🖇 Bibliografía Revisada:

1. Jannach, D., Manzoor, A., Cai, W., Chen, L. (2020). A Survey on Conversational Recommender Systems.
   
2. Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Lukasz Kaiser, Illia Polosukhin. (2017). Attention is All you Need.

3. Sofia Serrano, Noah A. Smith. (2019). Is Attention Interpretable?
