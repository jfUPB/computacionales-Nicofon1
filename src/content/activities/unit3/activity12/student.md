****Ciclo de Vida de Objetos: Stack vs. Heap****

* **Stack:**
    * Objeto vive dentro del bloque `{}` donde se declara.
    * Constructor al entrar, destructor automático al salir del bloque.
    * Gestión automática de memoria.

* **Heap:**
    * Objeto creado con `new`, vive hasta `delete`.
    * Constructor al `new`, destructor al `delete`.
    * Gestión manual de memoria.

**Análisis de la Modificación:**

* **¿Compila la segunda versión?** No, `pBloque2` tiene ámbito local al bloque.

* **¿Qué ocurre al declarar `pBloque2` fuera e inicializar dentro?** Compila y ejecuta. `pBloque` se destruye al salir de su bloque (stack). `pBloque2` (puntero en stack) apunta a objeto en heap, que persiste hasta `delete`.

* **¿Por qué `pBloque` se destruye y `pBloque2` no?** `pBloque` es objeto en stack (vida automática). `pBloque2` es puntero; el objeto apuntado en heap requiere `delete`.

* **¿`pBloque2` objeto o referencia?** Puntero (almacena dirección).

* **¿Dónde se almacena `pBloque2`?** Stack.

* **¿Dónde se almacena el objeto apuntado por `pBloque2`?** Heap.
