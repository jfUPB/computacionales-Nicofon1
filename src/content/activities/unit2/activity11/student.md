
**Principales conceptos aprendidos:**

* **Traducción de control de flujo:** `if/else` y bucles (`while`/`for`) a comparaciones y saltos en ensamblador.
* **Punteros:** Variables que almacenan direcciones de memoria (`&`), acceso al valor apuntado (`*`).
* **Manipulación de memoria:** Acceso y modificación directa de contenido en direcciones de memoria.
* **Arreglos:** Bloques contiguos en memoria, acceso por dirección base + offset.
* **Funciones:** Llamadas (saltos) y retornos en ensamblador.
* **Relación alto/bajo nivel:** Conceptos de alto nivel tienen representación de bajo nivel.

**Ejemplos de la unidad:**

* **`while` a ensamblador:**
    ````asm
    (LOOP)
    @i
    D=M
    @100
    D=D-A
    @END
    D;JGT
    @sum
    M=D+M
    @i
    M=M+1
    @LOOP
    0;JMP
    (END)
    ````
* **Escritura por puntero (`*p = 20;`):**
    ````asm
    @17     // Dirección de 'p'
    A=M      // A = dirección de 'a'
    @20
    D=A
    M=D      // Valor en dirección apuntada por 'p' ('a') es 20
    ````
* **Lectura por puntero (`b = *p;`):**
    ````asm
    @18     // Dirección de 'p'
    A=M      // A = dirección de 'a'
    D=M      // Valor en dirección apuntada por 'p' ('a')
    @17     // Dirección de 'b'
    M=D      // 'b' ahora tiene el valor apuntado por 'p'
    ````
* **Arreglos:** Manipulación de bloques contiguos (Actividad 07).
* **Funciones:** Saltos para llamadas y retornos (Actividad 10).
