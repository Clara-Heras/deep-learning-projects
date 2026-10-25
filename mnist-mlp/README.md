# Clasificación de dígitos MNIST con MLP

Comparación de perceptrones multicapa para clasificar los dígitos escritos a mano de MNIST, variando el número de capas ocultas, el número de neuronas y el learning rate.

## Qué se hace

- Búsqueda de un learning rate de partida aumentándolo de forma exponencial en cada batch y viendo cuándo se dispara la pérdida.
- Cuatro arquitecturas: 3 capas ocultas (64-64-32 y 128-128-64) y 4 capas ocultas (64-64-32-16 y 128-128-64-32), entrenadas con SGD, early stopping y TensorBoard.
- Reentrenamiento de las dos mejores con un learning rate más bajo (0,3 → 0,1).
- Evaluación en test con matrices de confusión.

## Resultados

| Capas ocultas | Neuronas | Learning rate | Accuracy test |
|---|---|---|---|
| 3 | 64-64-32 | 0,3 | 96,9 % |
| 3 | 128-128-64 | 0,3 | 97,0 % |
| 3 | 128-128-64 | 0,1 | 97,5 % |
| 4 | 64-64-32-16 | 0,3 | 96,5 % |
| 4 | 128-128-64-32 | 0,3 | 97,7 % |
| 4 | 128-128-64-32 | 0,1 | 97,3 % |

Los modelos con más neuronas funcionan mejor en los dos casos. Las diferencias entre configuraciones son pequeñas, y el mejor resultado es el de 4 capas con 128-128-64-32 neuronas y learning rate 0,3.
