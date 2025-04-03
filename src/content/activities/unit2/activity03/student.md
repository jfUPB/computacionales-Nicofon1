``` asm
 @1
 M=1 
 @2
 M=0 
 @1
 D=M
 @100
 D=D-A 
 @20
 D;JGT 
 @1
 D=M
 @2
 M=D+M
 @1
 M=M+1
 @6
 0;JMP
 @20
 0;JMP
```

##### **Equivalencia del `while` y el `for`**
- Ambos tienen la misma estructura: inicialización, condición de iteración y actualización de la variable `i`.
- La única diferencia es la forma en que se organizan en alto nivel, pero en ensamblador terminan siendo casi idénticos.

##### **Comparación en ensamblador**
- La versión con `for` y la de `while` generan prácticamente el mismo código.
- En ensamblador, ambas requieren:
  - Inicialización de variables (`sum = 0`, `i = 1`).
  - Un bucle (`LOOP`) con una condición de salida (`i > 100`).
  - Sumar `i` a `sum` y luego incrementar `i`.
  - Un salto condicional para repetir hasta que se cumpla la condición de salida.
- No hay diferencia real en eficiencia entre ambas versiones en ensamblador.

#####  **Conclusión**
- En ensamblador, no hay diferencia significativa entre `for` y `while`. Ambos se traducen a la misma lógica con un bucle, comparaciones y saltos.
- La elección entre `for` y `while` en lenguajes de alto nivel **es más sobre claridad y legibilidad** que sobre eficiencia.
- En **Nand2Tetris**, el compilador traduce `for` y `while` a estructuras de control equivalentes, por lo que su rendimiento es el mismo. 🚀
