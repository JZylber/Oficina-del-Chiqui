# La oficina del Chiqui

## Objetivo

El Chiqui nos pidio analizar distintos sistemas de competencia en el fútbol. En particular, nos interesa comparar un sistema de campeonato (todos contra todos) contra un sistema de llaves por eliminación. Para esto, vamos a armar funciones que simulen cada tipo de torneo, y vamos a armar experimentos que testeen hipótesis sobre cada tipo.

## Equipos

A los equipos los vamos a modelar con un número del 0 al 100, que va representar su efectividad. A mayor número, mejor el equipo.

## Partidos

Los partidos van a ser simulados de la siguiente forma: se dividen en 4 jugadas, y en cada jugada, puede meter gol algún equipo o ninguno. La probabilidad de que ocurra cada hecho está determinada por la efectividad de ambos equipos, y la cuenta es la siguiente:

```
ProbabilidadGolA = EfectividadA * (1 - EfectividadB)
ProbabilidadGolB = EfectividadB * (1 - EfectividadA)
ProbabilidadSinGoles = 1 - ProbabilidadGolA - ProbabilidadGolB
```

No se enganchen demasiado con esto, hay una función auxiliar que lo resuelve, lo importante son como utilizar dichas probabilidades. El resultado del partido es la suma de las 4 jugadas.

## Campeonato

En un campeonato, todos los equipos juegan con todos los otros 1 sola vez. Suman 3 puntos si ganan, 1 si empatan y 0 si pierden. El campeón es quien al final de todos los partidos, tiene más puntos. Si hay dos con igual cantidad de puntos, gana el que mayor diferencia de goles (```golesMetidos - golesRecibidos```) y si perisiste el empate, quien tiene más. Hay una función auxiliar que les puede ayudar a determinar el campeón de un torneo.

## Llaves

Asumiendo que la cantidad de equipos es una potencia de 2 (4,8,16,32,etc), se realizan partidos de a pares de equipos, en donde se determina un ganador que pasa a la siguiente ronda. Esto se repite hasta llegar a un único equipo, que es el ganador. Como en cada partido no puede haber empate, se define de la siguiente manera:

1. Se simulan las 4 jugadas del partido
2. Si no hay un ganador, se va a tiempo extra que son 2 jugadas más
3. Si sigue sin haber ganador, se define por "gol de oro", es decir, se simula una jugada más hast algún equipo mete gol. 

## Experimentación

Antes de arrancar, planteense algunas hipótesis. ¿Qué esperan que pase en cada sistema? ¿Quiénes son los que ganan más seguido?
Corran los sistemas reiteradas veces, y cambien las efectividades de los equipos. Registren lo observado, y vean que ocurrió con sus hipótesis. **Tienen que registrar la experimentación**. La experimentación la deben registrar en **un archivo de texto aparte** y debe incluir, por cada experimento que hacen:
- Hipótesis de que creen que va a pasar (no hace falta que sea súper formal, alcanza con que digan que creen que va a pasar).
- Parámetros que usaron, osea, los equipos que usaron, qué sistema de torneo usaron y las veces corridas.
- Resultados obtenidos.
- Observaciones contrastadas con lo esperado. 


## Funciones auxiliares
Partes del programa que son más complejas de hacer. Por suerte, en el repositorio hay algunas funciones auxiliares que pueden (o no) usar. ¡Cada una tiene comentado arriba que hace!

## EXTRAS

Para ganar puntos extras, complejicen un poco el simulador o/y hagan otros experimentos. En este punto los dejo a ustede sugerir ideas e implementarlas. Discutan conmigo previamente que quieren hacer. Algunas ideas:
- Complejizar los datos por equipo (que no sea un único número).
- Complejizar el modelo de partidos. Por ejemplo, cambiar el sistema de jugadas con otro modelo de probabilidad.
- Complejizar el modelo del torneo. Por ejemplo, tomar en cuenta locales y visitantes.
- Probar otros sistemas de llaves (eliminación doble, variar el arranque, etc).
En todos los casos, hacer algunos experimentos extras.

## Entrega
La entrega se hace pusheando al repositorio creado por github classroom, y enviando el hash del commit en una entrega del campus.

## Evaluación
Se va a evaluar por código funcional y legible para otras personas. **Hay reentrega**. En la reentrega pueden corregir y agregar extras. Va a haber una instancia de feedback antes de la reentrega (más adelante más detalles sobre esto).
La nota está compuesta por:
- 1-5 puntos: Código de simuladores
- 5-7 puntos: Experimentación: código y conclusiones
- 7-10 puntos: Extras