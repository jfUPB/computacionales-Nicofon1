#### ¿Qué aspectos de la implementación de la cola te resultaron más fáciles? ¿Por qué?

Lo más fácil fue entender el concepto de FIFO y crear los nodos. Como ya había trabajado con estructuras similares, me resultó natural crear structs y usar punteros básicos. Además, la lógica de agregar al final y quitar del principio es intuitiva si uno lo piensa como una fila de espera.

#### ¿Qué parte te pareció más difícil o te tomó más tiempo? ¿Cómo la resolviste?

Lo más difícil fue manejar bien los punteros en los casos límite, como cuando la cola está vacía o queda con un solo nodo. Al principio no actualizaba bien el `rear` al hacer `dequeue`, y eso causaba errores. Revisé el código paso a paso con el depurador de Visual Studio hasta entender qué estaba fallando.

#### Si pudieras repetir esta actividad, ¿Qué harías diferente para mejorar tu desempeño?

Si la repitiera, empezaría probando cada función individualmente desde el inicio, con mensajes por consola o tests simples. Me habría evitado errores que descubrí muy tarde. También comentaría más el código mientras avanzo, para no perder el hilo cuando lo reviso después.

#### ¿Cómo se relaciona lo que aprendiste en esta unidad con otras áreas de la programación o de tu carrera?

Entender bien las colas ayuda en cualquier parte de programación que implique manejo de datos en orden, como simulaciones, procesamiento de eventos, o incluso redes. También sirve para optimizar tareas, como en sistemas de impresión, animaciones o buffers de audio, que son cosas que pueden aparecer en desarrollo de software o multimedia.

#### ¿Qué aprendizajes de esta unidad te servirán en futuros proyectos?

Me llevo una mejor comprensión sobre cómo manejar memoria dinámicamente con punteros y cómo estructurar datos de forma manual. Saber construir una cola desde cero me da una base sólida para implementar estructuras más complejas como árboles o grafos más adelante.
