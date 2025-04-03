+ la variable estatica no se destruye al salir de la funcion por lo queconserva su valor, mientras que la no estatica si se destruye

+ la memoria en la que se almacenaba el array ya fue liberada por lo que el ya no hay informacion a la que ingresar


Diferencias entre Heap y Stack:
Stack: La memoria se maneja sola, se asigna y libera cuando la función termina.



Heap:Tú debes asignar y liberar memoria con new y delete.

Lento: El acceso es más lento que en el stack, pero tiene más espacio.

Consecuencias de no liberar memoria con new:
Si no usas delete, la memoria sigue ocupada, lo que puede causar fugas de memoria. Esto significa que el programa usa más memoria y puede llegar a quedarse sin recursos, haciéndolo lento o inestable.
