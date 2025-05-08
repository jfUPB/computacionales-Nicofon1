pStack

![image](https://github.com/user-attachments/assets/19d1eea9-c93a-4c19-ac45-a0acfe452107)

pHeap

![image](https://github.com/user-attachments/assets/b33a2e50-8a2c-4bb9-90bb-a3857ac91227)


¿Qué es pStack?

- pStack es un objeto, no un puntero.

- Se crea en el stack, por lo tanto, su memoria se gestiona automáticamente y se libera al final del main().

¿Qué es pHeap?

- pHeap es un puntero a un objeto, o sea, una referencia a un objeto creado en el heap.

- Contiene la dirección del objeto Punto(50, 60) que vive en el heap.

- Tú eres responsable de liberar su memoria con delete pHeap.

Observa en Memory1
- pHeap

![image](https://github.com/user-attachments/assets/7526b5cc-d8b0-4073-a43e-662c304191e7)

  
- &pHeap

![image](https://github.com/user-attachments/assets/5e402b37-3c97-4d09-86a6-acd5357700cc)


- pHeap es un puntero que almacena la dirección de un objeto en el heap.

- &pHeap es la dirección del puntero mismo, que vive en el stack.


- Al inspeccionar pHeap, ves el contenido del objeto.

- Al inspeccionar &pHeap, ves la dirección que contiene el puntero, es decir, el valor de pHeap almacenado byte por byte.
