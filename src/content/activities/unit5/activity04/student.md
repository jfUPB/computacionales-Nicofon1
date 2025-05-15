#### 1. ¿En la actividad anterior dónde estás aplicando el concepto de encapsulamiento? ¿Por qué? Muestra en qué parte del código.

Se usa encapsulamiento porque las variables están privadas en las clases, por ejemplo `amplitude` y `frequency` en `CurvedRisingParticle`.

```cpp
private:
    float amplitude;
    float frequency;
```

Así se controla mejor el acceso a esos datos.

#### 2. ¿En la actividad anterior dónde estás aplicando el concepto de herencia? ¿Por qué? Muestra en qué parte del código.

Se aplica herencia porque `CurvedRisingParticle` y `ExpandingRisingParticle` heredan de `RisingParticle`.

```cpp
class CurvedRisingParticle : public RisingParticle
```

Esto se hace para reutilizar el código base y modificar lo necesario.

#### 3. ¿En la actividad anterior dónde estás aplicando el concepto de polimorfismo? ¿Por qué? Muestra en qué parte del código.

El polimorfismo se usa cuando se llama `update()` y `draw()` desde un puntero a `RisingParticle`, pero se ejecuta el de la subclase.

```cpp
p->update(dt);
p->draw();
```

Esto funciona porque están declaradas como `virtual` en la clase base.

#### 4. Luego de esta experiencia de aprendizaje define con tus propias palabras: ¿Qué es un objeto? ¿Qué es una clase?

Una clase es como una plantilla. Un objeto es una copia de esa plantilla que se puede usar.

#### 5. ¿Cómo se ve en memoria un objeto de una clase que hereda de otra clase?

Tiene primero los datos de la clase base y luego los de la clase hija. Todo está junto en memoria.
