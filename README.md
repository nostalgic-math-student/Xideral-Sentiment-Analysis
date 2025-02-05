# Xideral-Sentiment-Analysis

#### Josue Rojas Noble

## Idea

Realizamos un proceso ETL desde la tabla de DynamoDB "Peliculas_S3D2_xideral" realizada en una tarea anterior.

El objetivo de la práctica es realizar un análisis de sentimiento de los títulos más repetidos en la tabla presente.

Para cumplir esto, la idea principal es realizar un análisis de NLP (Natural Language Processing) clásico mediante un proceso de vectorización de palabras y un modelo de palabras de **gensim**. El propósito es simple, comparar numéricamente la similaridad de las palabras en los títulos con multiples palabras en un espacio geométrico, argumentando que las palabras más cercanas a conceptos negativos (matar, muerte, oscuridad, venganza, etc) que a conceptos positivos (amor, felicidad, sorpresa, maravilloso, etc) dice que el titulo es más perteneciente a un concepto oscuro que a uno feliz, por lo que se asigna la categoría "Terror / Suspenso " si es más negativo que positivo, pero si es más positivo se asigna a " Comedia / Aventura ". Si no son distintos, significa que es una pelicula con igual de oscuridad que positiva así que de momento es una pelicula "Drama".
Otro factor es la categoría de la película, pues una película más adulta hace mas notorios los conceptos oscuros que los positivos, mientras que una película más infantil tiene conceptos más positivos que negativos por lo que se hace un ajuste de pesos al cálculo de los puntajes para determinar la categoría.

Resultado:
<img width="251" alt="image" src="https://github.com/user-attachments/assets/5c3bc145-3ae0-45a4-b797-48be5b2a77e4" />

Posteriormente, se guarda la tabla de nuevo en una tabla DynamoDB llamada "josue_analysis_movies" con la columna de categoría seguida de el valor de puntaje ganador. 
Esto nos dice que tan positiva o negativa es una película.
