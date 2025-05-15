**¿Cómo se crea la lista enlazada?**


En el archivo ofApp.h, se declara la lista así:

```
std::list<glm::vec2> snake;
```
Esto crea una lista enlazada (doblemente enlazada, en realidad, según la implementación estándar de C++) llamada snake, donde cada elemento representa una posición 2D con la clase glm::vec2.


**¿Cómo se añaden los primeros nodos a la lista?**


En el método setup():

```
for (int i = 0; i < 20; i++) {
    snake.emplace_back(ofGetWidth() / 2, ofGetHeight() / 2);
}
```

Este bucle añade 20 nodos en el centro de la pantalla. Se usa emplace_back() para agregar un nuevo nodo al final de la lista.


**¿Cómo se añaden nodos adicionales a la lista?**
Dentro del método keyPressed():

```
else if (key == 'a') {
    snake.emplace_back(ofRandomWidth(), ofRandomHeight());
}
```
Cuando presionas la tecla 'a', se añade un nuevo nodo con una posición aleatoria dentro de la ventana.



**¿Cómo se eliminan nodos de la lista?**
También en keyPressed():
```
else if (key == 'r') {
    if (!snake.empty()) {
        snake.pop_back();
    }
}
```
Cuando presionas la tecla 'r', se elimina el último nodo de la lista (si no está vacía), usando pop_back().

**¿Cómo se limpia la lista?**

Otra opción del método keyPressed():
```
if (key == 'c') {
    snake.clear();
}
```
Con la tecla 'c', se eliminan todos los elementos de la lista con el método clear().

**¿Cómo se verifica si la lista está vacía?**
Usando:

if (!snake.empty())


El método empty() retorna true si la lista no tiene elementos. Aquí se usa una condición para evitar intentar eliminar un nodo si no hay ninguno.




