#### Instrucciones
+ **Instrucción A:**
   se utiliza para cargar un valor de 15 bits en el registro A. Este valor puede ser un número decimal no negativo o un símbolo que se refiere a un número. Se utiliza para varios propósitos, como ingresar un valor constante, establecer una dirección de memoria o configurar una dirección de salto.


  **Binario:** 0vvv vvvv vvvv vvvv (v correspondiendo a los digitos de le valor de @ en binario)

     **Ejemplos**
  + @5: Se carga el valor 5 en el registro A.
  + @100: Se carga el valor 100 en el registro A.
  + @0: Se carga el valor 100 en el registro A. 

+ **Instrucción C:**
 permite realizar cálculos, almacenar resultados y controlar el flujo del programa mediante saltos. Se divide en tres partes:

     comp: La operación que realiza la unidad aritmético-lógica (ALU), como suma, resta, o operaciones lógicas.

     dest: Determina en qué registros se almacenará el resultado de la operación, como los registros A, D o M (Memoria[A]).

     jump: Define el comportamiento de salto, indicando qué instrucción ejecutar a continuación según el valor de la condición.
  

  **Binario:** 1 1 1 a c1 c2 c3 c4 c5 c6 d1 d2 d3 j1 j2 j3 (dest=comp;jump)
  
  
  
   **Ejemplos**
  + D = D + 1: Se incrementa el valor del registro D y se almacena el resultado en D.
  + M = M + D: Se suma el valor del registro D con el valor de memoria en la dirección A (M) y se guarda el resultado en M.
  + D;JGT: Si el valor de D es mayor que cero (positivo), se realiza un salto a la instrucción de destino especificada por la condición JGT.
