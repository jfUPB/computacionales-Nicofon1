+ ¿Qué esperas ver en memoria (hipótesis)?
  + ver una instancia de ofapp
+  ¿Qué puedes observar?
  
![image](https://github.com/user-attachments/assets/bb245529-7c9d-443d-940f-79d61e8df7b8)
 
+  ¿Qué información te proporciona el depurador?

![image](https://github.com/user-attachments/assets/ca34118d-c445-4bcf-af24-26459a661cce)
 
+ ¿Qué puedes concluir?
  + que hay un puntero llamado this que apunta a una intancia de ofapp
 
+ ¿Qué puedes observar en la memoria?

![image](https://github.com/user-attachments/assets/68988df2-cc4b-40c2-805e-e34264e29f94)

+ ¿Qué información te proporciona el depurador?

![image](https://github.com/user-attachments/assets/b2cdbc9c-a445-4e0d-b52d-0e9eca227aad)

+ ¿Qué puedes concluir?
  +  que la intaca de circular ecplocion creo q hace parte por herencia de particle, y esta sindo almasenada en enuna lista de particulas dentro de la instancia tipo ofapp
    
+ ¿Cómo se logra que el método HacerSonido se llame dos veces, una para el perro y otra para el gato?
  + Porque se usa un arreglo de tipo IAnimal, entonces se recorren los dos objetos (Perro y Gato) y cada uno tiene su propia implementación de HacerSonido, así que se ejecuta la que le toca a cada uno.

+ ¿Qué relación existe entre los métodos virtuales y el polimorfismo?
  + Sirven para que se puedan sobreescribir métodos en clases hijas. Aunque en este caso se usa una interfaz, la idea es parecida a los métodos virtuales porque el comportamiento cambia dependiendo del objeto real.

+ Al llamar HacerSonido, ¿cómo sabe esta función sobre cuál objeto debe actuar?
  + Porque aunque el tipo es IAnimal, en tiempo de ejecución se ve cuál es el tipo real del objeto (si es Perro o Gato) y se llama la versión correcta del método. Eso es lo que hace el polimorfismo.

+ ¿Qué sucede cuando se ejecuta el código tal como está?
  + Compila y corre bien. Solo se cambia el valor de publicVar porque es el único que se puede acceder directamente desde fuera de la clase.

+ ¿Qué pasa cuando se descomentan las líneas con protectedVar y privateVar?
  + Da error de compilación. El compilador no deja acceder a esas variables porque no son públicas.

+ ¿Por qué sucede esto?
  + Porque en C++ las variables privadas y protegidas no se pueden usar directamente desde fuera de la clase. Solo las públicas se pueden modificar así.

+ ¿Qué puedes concluir?
  + Que el encapsulamiento sirve para controlar quién puede acceder a qué partes de una clase. Es útil para proteger los datos y evitar que se cambien sin control.

+ ¿Qué pasa al compilar el programa con la línea que accede a obj.secret1?
  + No compila. Muestra un error diciendo que secret1 es privado y no se puede acceder desde fuera de la clase.

+ ¿Qué puedes concluir después de compilar y ejecutar este programa?
  + Que sí se puede acceder a los campos privados si se usan punteros con reinterpret_cast. O sea, el encapsulamiento se puede romper en tiempo de ejecución, aunque el compilador lo prohíba directamente.

+ ¿Qué es el encapsulamiento? ¿Por qué es importante?
  + Es una forma de proteger los datos de una clase, para que solo puedan ser usados o modificados desde adentro o con métodos específicos. Es importante porque ayuda a mantener el control sobre cómo se usan los datos y a evitar errores o mal uso desde fuera del objeto.

+ ¿Cómo se implementa la herencia en C++?
  + Usando dos puntos y el tipo de acceso. Por ejemplo: `class Hija : public Padre`. Así, la clase Hija hereda los atributos y métodos públicos y protegidos de la clase Padre. Sirve para reutilizar código sin tener que escribirlo todo otra vez.


+ ¿Qué relación existe entre los métodos virtuales y el polimorfismo?
  + Los métodos virtuales permiten que una función se comporte diferente según el tipo real del objeto, aunque se use un puntero o referencia a la clase base. Sin eso, se usaría siempre el método base. O sea, gracias a los métodos virtuales es que el polimorfismo funciona bien.

