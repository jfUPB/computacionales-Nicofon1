``` asm
@60 
D=A 
@9 
D=D+A 
@6 
M=D 
@0 
0;JMP 
```



### **Tabla del ciclo Fetch-Decode-Execute**  

| Ciclo | PC (Contador de Programa) | Instrucción | Decodificación | Ejecución y cambios en registros/memoria |
|-------|---------------------------|-------------|---------------|--------------------------------------|
| 1     | 0                         | `@60`       | A = 60       | Se carga el valor `60` en el registro `A`. |
| 2     | 1                         | `D=A`       | D = A        | Se copia el valor de `A (60)` en `D`. Ahora `D = 60`. |
| 3     | 2                         | `@9`        | A = 9        | Se carga el valor `9` en el registro `A`. |
| 4     | 3                         | `D=D+A`     | D = D + A    | Se suma `D (60) + A (9)`, resultando en `D = 69`. |
| 5     | 4                         | `@6`        | A = 6        | Se carga el valor `6` en el registro `A`. |
| 6     | 5                         | `M=D`       | M[A] = D     | Se almacena el valor `D (69)` en la memoria en la dirección `6`, es decir, `M[6] = 69`. |
| 7     | 6                         | `@0`        | A = 0        | Se carga el valor `0` en el registro `A`. |
| 8     | 7                         | `0;JMP`     | Salto incondicional | El `PC` se actualiza a `0`, reiniciando el programa. |

