#### ¿Qué es una cola y cómo funciona FIFO?

Una cola es como una fila en la vida real. El primero que llega es el primero que se atiende. Eso es **FIFO**: *First In, First Out* (el primero en entrar, es el primero en salir).


####  ¿Cómo se hace `enqueue()` y `dequeue()`?

- **enqueue(x):** agrega un nuevo elemento al **final** de la cola.
  - Si la cola está vacía, ese nuevo nodo es tanto el `front` como el `rear`.
  - Si ya hay elementos, se enlaza al final (`rear->next = nuevo`) y se actualiza `rear`.

- **dequeue():** elimina el **primer** elemento de la cola (`front`).
  - Se mueve el puntero `front` al siguiente (`front = front->next`) y se borra el anterior.

#### Error común

Un error muy común es **olvidar actualizar el tamaño** o los punteros.  
Por ejemplo, en `dequeue()`, si eliminas el nodo pero no actualizas `front`, te quedas con un puntero colgando.  
También hay que tener cuidado cuando la cola queda vacía: en ese caso, pon `rear = nullptr` también.
