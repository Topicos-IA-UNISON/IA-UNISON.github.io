---
layout: post
title: Programación dinamica
description: Programación dinámica, un enfoque algorítmico
image: assets/images/prog-dinamica.jpg
---


## Libros de texto

[**Reinforcement Learning: An
Introduction**](http://incompleteideas.net/book/the-book-2nd.html),
[Richard S. Sutton](http://incompleteideas.net/index.html) y [Andrew
G. Barto](http://www-anw.cs.umass.edu/%7Ebarto/). Second Edition, en
borrador, MIT Press, Cambridge, MA, 2018

Está casi por salir la versión final, y puede ser que ya no se
encuentre disponible en linea el borrador casi final. ¡Hay que
apurarse a descargarlo!


Para esta parte del curso, nos enfocamos a los capítulos 3 y 5.

[**Introduction to Stochastic Dynamic
Programming**](http://www.deeplearningitalia.com/wp-content/uploads/2018/03/Introduction-to-Stochastic-Dynamic-Programming-Ross.pdf)
Sheldon Ross, Academic Press, 1983.

El capítulo 2 presenta las ideas de los mñetodos por descuento tal
como estudian el tema en Matematicas. Un punto de vista complementario
para entender la notación usual.

## Inforación adicional

1. [Demostración de optimalidad del método de iteración de políticas](http://ee266.stanford.edu/lectures/dpproof.pdf)


## Ejercicios para desarrollar

1. [Problemas sobre MDPs del curso de Sutton](https://drive.google.com/drive/folders/0B-WvrETGtkescG5sTDk2XzZkN2M)
2. [Problemas sobre DP y MC del curso de Sutton](https://drive.google.com/drive/folders/0B-WvrETGtkescG5sTDk2XzZkN2M)


## Miniproyecto de evaluación de competencias: Una veintiuna simplificada


Vamos a representar una versión simplificada del juego de la veintiuna
(o *blackjack*) como un MDP y a partir de este vamos a encontrar una
política óptima, utilizando uno de los dos algoritmos vistos en clase
(iteración de valores y/o iteración de políticas).

Para esto, vamos a tener que generar una serie de funciones y/o
librerías (la representación de un MDP, los algoritmos de iteración de
valor y/o política, y la representación del problema particular).

El juego simplificado es el siguiente:

1. Solamente es un jugador y el *Dealer*, y en cada juagada se apuesta una
   cantidad fija de dinero (se requiere una política por jugada y los juegos son
   independientes)

2. Se asume un mazo infinito (todas las cartas tienen la misma probabilidad de
   salir)

3. El jugador juega primero, y solo tiene dos jugadas posibles: `parar` y `pedir
   carta`.

4. El jugador puede pedir cartas hasta que:
   + Llegue a 21 puntos (gana automáticamente)
   + Se pase de 21 puntos (pierde automáticamente)
   + Tenga 4 cartas o más (gana automáticamente)
   + Dedica `parar`

5. El *Dealer* empieza con una sola carta y una vez que el jugador decide
   `parar`, y no haya perdido o ganado automáticamente.

6. El *Dealer* tiene que `pedir_carta` *siempre* que tenga menos de 17 puntos.

7. El *Dealer* tiene que `parar` si tiene 17 puntos o más.

8. Si el *Dealer* tiene 4 cartas, o un número mayor que el jugador (y menos que
   21) gana. De otra forma, gana el jugador.


Para resolver este problema lo vamos a hacer en varios pasos:


1. Explicar (cada uno) como harían el modelo tipo MDP para este problema específico lo que incluye:
   + La representación de los estados
   + La cardinalidad del espacio de estado
   + Los *estados resumidero* (o finales)
   + El conjunto de acciones
   + ¿Cómo se calculan las probabilidades de transición $p(s, a, s')$?
   + ¿Cómo se calculan las recompensas $r(s, a, s')$

2. Desarrollar y explicar un modelo para establecer MDPs en espacios discretos usando *Julia*
   - La [Librería POMDP](https://github.com/JuliaPOMDP/POMDPs.jl) que es la librerá de base para MDPs y POMDPs.
   - El script para [definir MDP
     discretos](https://github.com/JuliaReinforcementLearning/ReinforcementLearningEnvironmentDiscrete.jl/blob/master/src/mdp.jl)
     en la librerá de aprendizaje por refuerzo de Julia.
   - Un [proyecto](https://github.com/sawcordwell/MDPs.jl) con ideas
     de como desarrollar el modelo de MDP en *Julia*.
   - Otro [proyecto en Github](https://github.com/cpritcha/MDP) no tan interesante pero más simple de seguir.


3. Desarrollar los algoritmos:
   + Evaluación de política
   + Iteración de política y/o
   + Iteración de valores

4. Aplicarlos al problema y ver de que manera se puede visualizar y explicar la política óptima resultante.


Hacer todo esto, bien explicado en un blog, o en una libreta de *jupyter* o en la combinación de ambos.


## Ejercicios desarrollados por estudiante para su evaluación

| Estudiante | EjerciciosLibro de Sutton                                                                                                         | Juego de Black Jack                                                                                                            |
| ------     | ------                                                                                                                            | ------                                                                                                                         |
| Belen      | [Ejercicios](https://github.com/chasil7/topicosIA/blob/master/MDP/MDP_ejercicios.pdf)                                             | [Proyecto](https://github.com/chasil7/topicosIA/blob/master/MDP/MDP_Black_Jack.ipynb)                                          |
| Adrián     | [Ejercicios](https://github.com/adrianEVI/Topicos-IA/blob/master/MDP/MPD.pdf)                                                     | [Proyecto](https://github.com/adrianEVI/Topicos-IA/blob/master/MDP/MDP.ipynb)                                                  |
| Fernando   | [Ejercicios](https://github.com/fsr313/TADIA/blob/master/MDP/ejercicios.md)                                                       | [Proyecto](https://github.com/fsr313/TADIA/blob/master/MDP/iterar_valores.ipynb)                                               |
| Ivan       | [Ejercicios](https://github.com/rexemin/Topicos-IA-UNISON/blob/master/ProgramacionDinamica/Ejercicios-ProgramacionDinamica.pdf)   | [Proyecto](https://github.com/rexemin/Topicos-IA-UNISON/blob/master/ProgramacionDinamica/21)                                   |
| Ricardo    | [Ejercicios](https://github.com/RicardoHE97/TopicosIA-Unison/blob/master/ProgramacionDinamica/EjerciciosProgramacionDinamica.pdf) | [Proyecto](https://github.com/RicardoHE97/TopicosIA-Unison/blob/master/ProgramacionDinamica/MDP_BlackJack/MDP_BlackJack.ipynb) |
| Giovanni   | No encontré                                                                                                                       | No encontré                                                                                                                    |

## Dinámica de evaluación

Para esta unidad vamos a realizar una evaluación democrática en varios pasos. En
un primer paso, vamos a organizar a todos los trabajos de los compañeros en
orden, donde el 1 es el mejor trabajo y el 7 el menos bueno. Junto a la
evaluación, vamos a incluir una opción en la que se considera si el compañero
aprobó no no la evaluación. Sobre los aprobados, haremos una dinámica en clase
para asignar las calificaciones.
