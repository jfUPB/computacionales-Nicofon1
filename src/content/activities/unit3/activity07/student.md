![image](https://github.com/user-attachments/assets/97ae7232-c825-44ba-b211-dfc17abd7086)


1. Valores en la memoria:

    +  En hexadecimal, 0a es 10 en decimal.

    +  En hexadecimal, 14 es 20 en decimal.

    +  Observación: Los bytes se almacenan en orden little-endian, donde el byte de menor peso va primero.

2. Diferencia entre constructor y destructor en C++:

    +  Constructor: Se utiliza para inicializar un objeto cuando se crea. Define cómo se inicializan sus datos miembro.

    +  Destructor: Se llama automáticamente cuando el objeto se destruye. Se utiliza para liberar recursos o realizar acciones de limpieza.

3. Diferencia entre objeto y clase en C++:

    + Una clase en C++ es una plantilla que define el diseño de un objeto.

    + Un objeto es una instancia concreta de esa clase en tiempo de ejecución, con sus datos específicos.

4. Diferencia entre Punto en C++ y C#:

    + En C++, Punto p(10, 20); crea un objeto en el stack.

    + En C#, Punto p = new Punto(10, 20); crea un objeto en el heap y p es una referencia a ese objeto.

5. ¿Qué es p en C++ y qué es p en C#?:

    + En C++, p es un objeto en el stack.

    + En C#, p es una referencia a un objeto en el heap.

6. Parte de memoria donde se almacena p:

    + En C++, p se almacena en el stack.

    + En C#, p (la referencia) se almacena en el stack, pero el objeto real se aloja en el heap.


7. ¿Qué es un objeto en C++ según lo observado?:

    + Un objeto en C++ es una instancia concreta de una clase que tiene sus propios datos (en este caso, las coordenadas x e y del punto) y métodos para manipular esos datos.
