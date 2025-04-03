**1. ¿Qué es el direccionamiento directo? ¿Cómo se usa en el lenguaje ensamblador Hack?**

El direccionamiento directo es un modo de acceso a la memoria en el que una instrucción hace referencia a una dirección específica dentro de la RAM. En el lenguaje ensamblador Hack, esto se logra utilizando la instrucción @n, donde n es una dirección de memoria.


**2. ¿Qué significa M=D en lenguaje ensamblador Hack? ¿Y D=M?**

M=D: Guarda el valor del registro D en la dirección de memoria apuntada por A.
Ejemplo: Si D=25 y A=6, entonces M=D almacena 25 en RAM[6].

D=M: Carga en D el valor almacenado en la dirección de memoria apuntada por A.
Ejemplo: Si RAM[3] = 42 y A=3, entonces D=M deja D=42


**3.Concepto de "puntero" en el contexto de la memoria**
Un puntero es una variable que almacena la dirección de otra ubicación en memoria, permitiendo el acceso indirecto a datos. En Hack, esto se logra usando el registro A como un puntero para acceder a M.

```
@100  
D=A    // D = 100 (dirección de memoria)
@10    
M=D    // Almacena 100 en RAM[10] (puntero)
@10    
A=M    // A apunta a la dirección almacenada en RAM[10] (100)
D=M    // Carga el valor almacenado en RAM[100] en D
```
