# Comparación de Rendimiento

## Qué he hecho

He jugado partidas de los dos bots contra RandomBot para ver si el reordenamiento de movimientos con Prolog mejora algo.

## Pruebas

Primero lancé TacticalAlphaBetaBot contra RandomBot:

```
python3 main.py --player1 TacticalAlphaBetaBot --player2 RandomBot
```

El bot ganó en 11 movimientos y tardó unos 85 segundos. Las estadísticas que salieron fueron:

TacticalAlphaBetaBot Search Statistics:
==================================================
Total moves made: 11
Total nodes visited: 39315
Total pruning events: 1705
Average nodes per move: 3574.1
Average pruning per move: 155.0
Pruning rate: 4.34%
==================================================

Y estos fueron los resultados de la partida:
Result: 1-0 (Ganó TacticalAlphaBetaBot)
Total moves: 21
Game duration: 85.0 seconds
hite time left: 117.0s
Black time left: 200.0s
Game exported to: last_game.pgn

```
python3 main.py --player1 HeuristicAlphaBetaBot --player2 RandomBot
```

Este también ganó pero mucho más rápido, en unos 8 segundos.

## Hallazgos

TacticalAlphaBetaBot tarda bastante más. Creo que es porque cada vez que tiene que evaluar un movimiento, tiene que preguntarle a Prolog si hay algún patrón táctico (fork, pin, skewer...) y esa comunicación entre Python y Prolog tiene su coste.


## Conclusión

El bot funciona y detecta los patrones, pero Prolog lo ralentiza. Contra un rival que juegue bien se notaría más la mejora, pero contra el RandomBot no se nota tanto.
