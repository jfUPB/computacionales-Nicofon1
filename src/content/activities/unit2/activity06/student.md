
1. **¿Qué hace esto `int *pvar;`?**
   - Este es un **declarador de puntero**. Declara una variable llamada `pvar` que es un puntero a un entero. Es decir, `pvar` puede almacenar la dirección de memoria de una variable de tipo `int`, pero no está inicializado con ninguna dirección de memoria en este momento.

2. **¿Qué hace esto `*pvar = var;`?**
   - Este es un **operador de desreferenciación**. El `*pvar` hace referencia al valor almacenado en la dirección de memoria a la que apunta `pvar`. La instrucción `*pvar = var;` asigna el valor de `var` a la variable que está en la dirección de memoria contenida en `pvar`. En otras palabras, modifica el valor de la variable a la que `pvar` apunta, no el puntero mismo.

3. **¿Qué hace esto `var2 = *pvar;`?**
   - Esto es una **asignación de valor**. Aquí, el valor que está almacenado en la dirección de memoria a la que apunta `pvar` (usando `*pvar`) se asigna a `var2`. Es decir, el valor apuntado por `pvar` se copia a la variable `var2`. No se está modificando el puntero, solo el valor al que apunta.

4. **¿Qué hace esto `pvar = &var3;`?**
   - Esto es una **asignación de dirección de memoria**. El operador `&` obtiene la dirección de memoria de `var3`. Entonces, `pvar = &var3;` hace que `pvar` apunte a `var3`. Es decir, ahora `pvar` contendrá la dirección de memoria de `var3`, y podrás acceder al valor de `var3` a través de `*pvar`.

