# β-VAE sobre Fashion-MNIST

Entrenamiento de un autoencoder variacional (β-VAE) con capas densas sobre Fashion-MNIST para ver cómo afecta el parámetro β a la calidad de las reconstrucciones. β controla el peso de la divergencia KL: con valores bajos el modelo prioriza reconstruir bien las imágenes, y con valores altos prioriza un espacio latente más ordenado.

## Qué se hace

- Encoder y decoder densos (784 → 150 → 100 → espacio latente de 10 dimensiones) y capa de muestreo con el truco de reparametrización.
- Entrenamiento con seis valores de β: 0, 0,5, 1, 2, 6 y 11.
- Evaluación de las reconstrucciones con SSIM, que tiene en cuenta luminosidad, contraste y estructura.
- Comparación de optimizadores (Nadam, Adam y RMSprop) y búsqueda del learning rate.

## Resultados

| β | SSIM medio |
|---|---|
| 0 | 0,598 |
| 0,5 | 0,547 |
| 1 | 0,518 |
| 2 | 0,477 |
| 6 | 0,395 |
| 11 | 0,279 |

Cuanto mayor es β, peor es la reconstrucción. El mejor resultado es con β = 0 (equivale a un autoencoder clásico), aunque su espacio latente está menos ordenado, así que para generar imágenes nuevas convendría un β mayor.

Nadam y Adam dan resultados casi iguales (0,598 y 0,593) y RMSprop queda por debajo (0,534). Subir el learning rate a 0,01 empeoró el resultado, así que el valor por defecto era el adecuado.

Incluso el mejor modelo se queda en un SSIM de 0,6, lo que indica que un autoencoder con capas densas tiene un límite claro con este tipo de imágenes. Una arquitectura convolucional probablemente daría mejores reconstrucciones.
