
#### Condicionales:

**Alto Nivel (C++):**
````cpp
int a = 10;
int b;
if (a > 5) {
 b = 1;
} else {
 b = 0;
}
````

**Ensamblador (Hack - Simulación):**
````asm
@10     // a = 10 (dir 20)
D=A
@20
M=D
@20     // Cargar a
D=M
@5
D=D-A   // a - 5
@ELSE_COND
D;JLE   // Si a <= 5, ir a ELSE_COND
@1      // b = 1 (dir 21)
D=A
@21
M=D
@END_COND
0;JMP
(ELSE_COND)
@0      // b = 0
D=A
@21
M=D
(END_COND)
````

#### Ciclos while:

**Alto Nivel (C++):**
````cpp
int counter = 5;
while (counter > 0) {
 counter--;
}
````

**Ensamblador (Hack - Simulación):**
````asm
@5      // counter = 5 (dir 22)
D=A
@22
M=D
(WHILE_INV)
@22     // Cargar counter
D=M
@0
D=D-A   // counter - 0
@END_WHILE_INV
D;JGE   // Si counter >= 0, salir
@22     // counter--
M=M-1
@WHILE_INV
0;JMP
(END_WHILE_INV)
````

#### Ciclos for:

**Alto Nivel (C++):**
````cpp
int sum_for_inv = 0;
for (int i = 3; i >= 1; i--) {
 sum_for_inv += i;
}
````

**Ensamblador (Hack - Simulación):**
````asm
@0      // sum_for_inv = 0 (dir 23)
D=A
@23
M=D
@3      // i = 3 (dir 24)
D=A
@24
M=D
(FOR_INV)
@24     // Cargar i
D=M
@1
D=D-A   // i - 1
@END_FOR_INV
D;JLT   // Si i < 1, salir
@24     // Cargar i
D=M
@23     // Cargar sum_for_inv
M=D+M
@24     // i--
M=M-1
@FOR_INV
0;JMP
(END_FOR_INV)
````

#### Escritura por puntero:

**Alto Nivel (C++):**
````cpp
int value = 1000;
int* ptr_value = &value;
*ptr_value = 1001;
````

**Ensamblador (Hack - Simulación):**
````asm
@1000   // value = 1000 (dir 25)
D=A
@25
M=D
@25     // ptr_value = &value (dir 26)
D=A
@26
M=D
@26     // Cargar ptr_value
A=M      // A = dirección de value
@1001
D=A
M=D      // *ptr_value = 1001
````

#### Lectura por puntero:

**Alto Nivel (C++):**
````cpp
int origin = 55;
int* ptr_origin = &origin;
int destiny = *ptr_origin;
````

**Ensamblador (Hack - Simulación):**
````asm
@55     // origin = 55 (dir 27)
D=A
@27
M=D
@27     // ptr_origin = &origin (dir 28)
D=A
@28
M=D
@28     // Cargar ptr_origin
A=M      // A = dirección de origin
D=M      // D = valor de origin
@29     // destiny = *ptr_origin
M=D
````

#### Manipulación de arreglo por puntero:

**Alto Nivel (C++):**
````cpp
int data[] = {5, 10, 15};
int* ptr_data = data;
*(ptr_data + 2) = 20; // Modifica el tercer elemento
````

**Ensamblador (Hack - Simulación - Arreglo en dir 30):**
````asm
@5      // data[0] = 5 (dir 30)
D=A
@30
M=D
@10     // data[1] = 10 (dir 31)
D=A
@31
M=D
@15     // data[2] = 15 (dir 32)
D=A
@32
M=D
@30     // ptr_data = data (dir 33)
D=A
@33
M=D
@33     // Cargar ptr_data
D=M
@2      // Offset + 2
A=D+A    // A = dirección de data[2] (30 + 2 = 32)
@20
D=A
M=D      // data[2] ahora es 20
````

#### Llamado a funciones con parámetros:

**Alto Nivel (C++):**
````cpp
int multiply_two(int x, int y) {
 return x * y;
}

int main() {
 int result = multiply_two(7, 2);
 return 0;
}
````

**Ensamblador (Hack - Simulación - Simplificado):**
````asm
// main
@7      // Primer parámetro (x)
D=A
@SP
A=M
M=D
@SP
M=M+1
@2      // Segundo parámetro (y)
D=A
@SP
A=M
M=D
@SP
M=M+1
@MULTIPLY_FUNC
0;JMP
(RETURN_MAIN_MULT_TWO)
@SP
M=M-1
A=M
D=M      // result
@END_MAIN_MULT_TWO
0;JMP
(MULTIPLY_FUNC)
@SP
M=M-1
A=M
D=M      // y
@SP
M=M-1
A=M
D=D*M    // x * y (simulado)
@SP
A=M
M=D      // Resultado en pila
@RETURN_MAIN_MULT_TWO
0;JMP
(END_MAIN_MULT_TWO)
0;JMP
````

#### Llamado a funciones con retorno:

**Alto Nivel (C++):**
````cpp
int get_five() {
 return 5;
}

int main() {
 int value_five = get_five();
 return 0;
}
````

**Ensamblador (Hack - Simulación - Simplificado):**
````asm
// main
@GET_FIVE_FUNC
0;JMP
(RETURN_MAIN_GET_FIVE)
@SP
M=M-1
A=M
D=M      // value_five = 5
@END_MAIN_GET_FIVE
0;JMP
(GET_FIVE_FUNC)
@5
D=A
@SP
A=M
M=D      // Poner 5 en la pila (valor de retorno)
@SP
M=M+1
@RETURN_MAIN_GET_FIVE
0;JMP
(END_MAIN_GET_FIVE)
0;JMP
````
