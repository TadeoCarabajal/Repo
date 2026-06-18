Trabajo practico del pela naza: 
Tarea 1
Esta tarea forma parte de un repositorio Github. El repositorio contiene un proyecto BlueJ en Java para la
aplicaci ́on KGram Stories.
El proyecto KGram Stories consiste en la implementaci ́on en Java de un generador de textos basado en k-gramas:
secuencias consecutivas de k elementos (letras, palabras o cualquier tipo de token) que se extraen de un corpus.
La idea fundamental es que, al analizar las frecuencias de aparici ́on de cada posible (k + 1)-grama, es posible
predecir, dado un k-grama observado, cu ́al es el siguiente elemento m ́as probable. Esta t ́ecnica constituye la
base de muchos modelos de lenguaje estad ́ısticos y permite generar texto nuevo que imita el estilo del corpus de
entrenamiento. Con este proyecto se busca que los estudiantes apliquen dise ̃no orientado a objetos, manejo de
colecciones, abstracci ́on y pruebas unitarias, mientras construyen un sistema que utiliza k-gramas y la estrategia
de backoff para manejar secuencias no vistas.
Un k-grama es una secuencia de k elementos consecutivos. Por ejemplo, en la frase “el gato duerme”, los
2-gramas (bigramas) de palabras son [“el”, “gato”], [“gato”, “duerme”]; y las frecuencias de estos bigramas
permiten predecir que despu ́es de “el gato” lo m ́as probable es “duerme”. La t ́ecnica de backoff se utiliza
cuando un k-grama espec ́ıfico no fue visto en el entrenamiento: se “retrocede” a un (k-1)-grama (por ejemplo,
de “el gato feliz” a “gato feliz”) para intentar una predicci ́on menos espec ́ıfica pero a ́un  ́util.
KGram Stories es una implementaci ́on de un predictor (o generador) de texto usando k-gramas y backoff.
Consta de cuatro clases:
• PredictorPalabra que representa un predictor de palabras basado en k-gramas.
• LectorArchivo, que se encarga de la lectura de archivos de texto y construcci ́on, a partir del contenido
del archivo le ́ıdo, de listas de palabras.
• KGramStoriesUI, interfaz de usuario (en modo texto) de la aplicaci’on.
• ControlKGramStories, clase que implementa los comandos principales de la interfaz de usuario mediante
el uso del resto de las clases del proyecto.
La resoluci ́on de este trabajo pr ́actico consiste en implementar varios m ́etodos:
• De la clase PredictorPalabra:
– entrenar() Este m ́etodo se encarga de utilizar el corpus para construir las transiciones, b ́asicamente,
una tabla de palabras que siguen a cada k-grama del corpus, con su respectiva frecuencia.
– predecirSiguientePalabra(texto), que utiliza el modelo entrenado para predecir la palabra m ́as
probable a seguir al texto provisto. B ́asicamente, la palabra es aquella que tiene mayor frecuencia
luego del k-grama final del texto ( ́ultimas k palabras del texto).
– existePredictor(texto), que decide si las  ́ultimas k palabras del texto pertenecen a la tabla de
transiciones, es decir, fueron vistas en entrenamiento.
• De la clase ControlKGramStories:
– predecirSiguiente(texto)), que implementa el mecanismo de backoff : intenta predecir en base a
las  ́ultimas K palabras del texto (para un K elegido por el usuario), si no existe predicci ́on intenta
usando las  ́ultimas K − 1 palabras, y as ́ı sucesivamente.
Su tarea es implementar todos los m ́etodos mencionados. Pueden decidir agregar m ́etodos auxiliares
(privados), o implementar las funcionalidades requeridas dentro de los cuerpos de los m ́etodos proporcionados.