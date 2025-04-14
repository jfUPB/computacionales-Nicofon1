1. ¿Qué ocurre después de llamar a la función cambiarNombre? ¿Por qué aparece el mensaje Destructor: Punto cambiado(70, 80) destruido.?
+ Se imprime: Destructor: Punto cambiado(70, 80) destruido.
+  Porque p es una copia por valor de original. Se crea un objeto nuevo dentro de la función, se le cambia el nombre, y al terminar la función… se destruye. Por eso aparece el mensaje del destructor.
2. ¿Por qué original sigue existiendo luego de llamar cambiarNombre?
+ Porque nunca se modificó el objeto original, solo se modificó la copia p. Al terminar la función, esa copia muere, pero original sigue igual.
3. ¿En qué parte del mapa de memoria se encuentra original y en qué parte se encuentra p? ¿Son el mismo objeto? 
+ original: está en el stack (pila) de main.
+ p: está en el stack de la función cambiarNombre.
+ NO son el mismo objeto. Son dos instancias distintas con el mismo contenido (al principio).
4. ¿Qué ocurre ahora? ¿Por qué?
+ Ahora sí se cambia el nombre de original y NO aparece destructor adicional.
+ Porque:
  + p no es una copia, es un alias de original.
  + Cualquier cambio sobre p afecta directamente a original.
  + No se crea ni destruye un nuevo objeto.
4. ¿Qué ocurre ahora? ¿Por qué?
+ Igual que con referencia: el nombre de original se cambia correctamente.
+ ¿Por qué?
  + Se pasa la dirección de memoria de original.
  + Se trabaja directamente sobre el objeto apuntado.
  + Tampoco hay copia ni destructor adicional.
 
| Forma de paso     | ¿Se crea copia? | ¿Afecta al original? | ¿Aparece destructor extra? |
|-------------------|------------------|------------------------|-----------------------------|
| Por valor         |   Si            |   No                 |   Si                        |
| Por referencia    |   No            |   Si                 |   No                        |
| Por puntero       |   No            |   Si                 |   No                        |
