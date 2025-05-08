+ ¿Qué pasaría si el objeto de la clase LinkedList no tuviera el puntero a head?
  + no se podria encontrar la lista
+ ¿Podrías recorrer la lista?
  + no, ya que aunq se tenga el tail, de ahi no hay referencia al resto de nodos
+ ¿Qué pasaría si no tuviera el puntero a tail?
  + sin un puntero a tail se compljisaria el pop back y puushback, pero pal resto no es estrictamente necesario
+ ¿Podrías agregar un nuevo nodo al final de la lista?
  + si pero de manera mas compleja teniendo que recorrer toda la lista
+ ¿Qué pasaría si no tuviera el entero size?
  + justo ahora no tiene una funcionalidad  concreta
+ ¿Podrías saber cuántos nodos hay en la lista?
  + no
+ ¿Por qué se necesario liberar la memoria que ocupa el objeto y además liberar la memoria de los nodos de la lista?
  + para que se mantenga alimoia la memoria y no se termine llenando
+ ¿Qué pasaría si no lo hicieras?
  + podria llenarse la memoria colapsanod el programa
+ ¿Por qué crees que en C++ es necesario liberar la memoria de los objetos?
  + pq no se cuenta con un garbage colector a diferencia de C#
+ ¿Qué hace el método setup?
  + genera una lista de 20 nodos en el centro de pantalla, y el fondo
+ ¿Qué hace el método update?
  + si la lista esta vacia sale del metoo si no inicialisa el objetivo siendo la posicion del puntero lugo recorre la lista moviendo el nodo al objetivo con un mixt y un factor de interpolacion, ademas actualiza el objetivo a la posicion del nodo actual para que sea el objetivo del proximo nodo, por ultimo cambia el fondo
+ ¿Qué hace el método draw?
  + primero actualiza el fondo, dsps recorre la lista añadiendo las lineas que lo conectan y por ultimo grafica los nodos
+ ¿Qué hace el método keyPressed?
  + realiza la lectura de teclado y llama la funcion correspondiente
