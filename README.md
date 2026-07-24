# LegalMatch AI

Final project for the Building AI course
## Summary
## Resumen

LegalMatch AI es un sistema que recomienda al usuario el tipo de servicio legal más adecuado según su caso (laboral, civil, penal, familiar) y sugiere abogados especializados con mejor historial de éxito en casos similares, usando datos de casos previos y filtrado colaborativo.

## Antecedentes

Muchas personas no saben qué tipo de abogado necesitan ni cómo elegir uno adecuado para su caso específico, lo que genera pérdida de tiempo, dinero y a veces resultados legales desfavorables. Trabajando en el desarrollo frontend de un sistema de gestión legal, noté que los casos se clasifican manualmente y no existe ninguna sugerencia automática para el cliente ni para el estudio jurídico sobre qué abogado asignar. Este es un problema común, especialmente en países donde el acceso a información legal clara es limitado.

* Falta de orientación inicial para personas sin conocimientos legales
* Asignación manual e ineficiente de casos a abogados dentro de un estudio
* Dificultad para encontrar abogados especializados en un tipo de caso específico

## ¿Cómo se utiliza?

El cliente describe brevemente su situación (por ejemplo, "mi empleador no me pagó el finiquito") a través de un formulario web. El sistema clasifica el tipo de caso (laboral, civil, etc.) y recomienda tanto el área legal correspondiente como los abogados del estudio con más experiencia y éxito en casos similares. Los usuarios principales serían clientes que buscan asesoría legal por primera vez, y el personal administrativo del estudio jurídico que necesita asignar casos de forma más eficiente.

## Fuentes de datos y técnicas de IA

Los datos vendrían del historial de casos gestionados por el estudio jurídico (tipo de caso, abogado asignado, resultado del caso), similar a la estructura que ya manejamos en nuestro sistema actual. Para clasificar el tipo de caso a partir de la descripción del cliente, se usaría un clasificador Naive Bayes con bolsa de palabras (bag-of-words) sobre el texto ingresado. Para recomendar abogados, se aplicaría filtrado colaborativo basado en el método del vecino más cercano, comparando casos similares y su nivel de éxito.

## Desafíos

El proyecto no resuelve la necesidad de asesoría legal personalizada real — sigue siendo necesaria la intervención de un abogado humano para cualquier decisión final. Existe el riesgo de sesgo si el historial de casos no está balanceado entre tipos de casos o abogados, lo que podría generar recomendaciones injustas. También hay que considerar la confidencialidad de los datos de los clientes al entrenar el modelo.

## ¿Qué sigue?

El proyecto podría crecer incorporando un chatbot que guíe al cliente paso a paso antes de la clasificación, o integrando datos de tribunales públicos para enriquecer el modelo de predicción de éxito de un caso. Necesitaría más experiencia con NLP en español y colaboración con abogados para validar la calidad de las recomendaciones.

## Agradecimientos

* Inspirado por el curso Building AI de Reaktor y la Universidad de Helsinki
* Basado en conceptos de clasificación Naive Bayes y filtrado colaborativo estudiados en este curso
