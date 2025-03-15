- Carga el programa en el simulador y ejecuta paso a paso cada instrucción. Trata de predecir el resultado de la instrucción antes de ejecutarla.

  `@i` llegara a 101 y `@sum` a 5050

- ¿En qué direcciones de memoria se implementan las variables i, sum?
  

  `@i` → 16

  `@sum` → 17


- Basado en esta experiencia, ¿Cuál es la diferencia entre la dirección de una variable y su contenido?

  La direccion es donde se gurada y el contenido es lo que guarda.

- Explica cómo se implementa la condición i <= 100

```asm
   @i
   D=M
   @100
   D=D-A
   @END
   D;JGT
   ```
