+ Explica con tus propias palabras el propósito del patrón Observer. ¿Qué problema resuelve?
  + esta estuctura resuelve la necesidad de tener que esta constantemente revisando el estado de una variable u objeto para registrar el cambio y actuar en base a el
+ ![image](https://github.com/user-attachments/assets/84a6bdef-1b78-4291-9752-b05a2a775d39)
+ Describe paso a paso qué ocurre en el código desde que presionas la tecla ‘r’ hasta que las partículas empiezan a ser repelidas por el mouse. Menciona las clases y métodos clave involucrados en la notificación y la reacción.
  + Cuando se presiona la tecla `'r'`, se llama al método `keyPressed` en la clase `ofApp`. Como la tecla es `'r'`, se ejecuta `notify("repel")`.

  + `notify` está en la clase `Subject`, que es la clase base de `ofApp`. Ese método recorre todos los observadores (que son partículas) y les manda el evento `"repel"`.

  + Cada partícula tiene el método `onNotify`, y cuando recibe `"repel"`, cambia su estado a `RepelState` usando `setState`.

  + En cada frame, el método `update` de `ofApp` llama al método `update` de cada partícula. Como ahora tienen el estado `RepelState`, se ejecuta el método `update` de esa clase.

  + Ese método hace que la partícula se mueva alejándose del mouse. Calcula la dirección opuesta al mouse y ajusta la velocidad para que se aleje.

  + Y así es como empiezan a ser repelidas.
+ ¿Qué ventajas crees que ofrece usar el patrón Observer en esta aplicación en comparación con, por ejemplo, que ofApp::update recorriera todas las partículas y les dijera directamente que cambien su comportamiento basado en una variable global? Piensa en términos de acoplamiento y extensibilidad.
  + Usar el patrón Observer en esta aplicación ayuda a que el código esté más ordenado y fácil de manejar.

  + Por ejemplo, `ofApp` solo les avisa a las partículas que pasó algo (como "repeler"), y cada partícula sabe qué tiene que hacer con eso. Así, `ofApp` no se encarga de todos los detalles, lo cual lo hace más simple.

  + También es útil si más adelante queremos agregar otras cosas (no solo partículas) que reaccionen a esos eventos. Solo hay que hacer que escuchen al sujeto, sin tocar mucho el resto del código.

  + Si en vez de eso se usara una variable global y todo se controlara desde `ofApp`, habría que escribir más código ahí para cada cosa nueva, y eso haría que sea más complicado de mantener.



