![image](https://github.com/user-attachments/assets/e80a2a14-f349-41cc-9cab-3e61e607aac5)
![image](https://github.com/user-attachments/assets/0f9b95e6-1ca0-43f5-81be-5bd363debfc1)

#### 1. Clase `Particle` (abstracta)
- Define una interfaz para las partículas con métodos virtuales puros:
  - `update`
  - `draw`
  - `isDead`
- También incluye métodos opcionales:
  - `shouldExplode`
  - `getPosition`
  - `getColor`

#### 2. Clase `RisingParticle`
- Implementa `Particle`.
- Representa partículas que suben desde la parte inferior hacia arriba.
- Tiene posición, velocidad, color y tiempo de vida.
- Puede “explotar” al alcanzar cierta altura o edad.

#### 3. Clases de explosión (`ExplosionParticle`, `CircularExplosion`, `RandomExplosion`, `StarExplosion`)
- Heredan de `Particle` y representan diferentes tipos de explosión:
  - **CircularExplosion**: se mueve en patrón radial y se dibuja como círculo.
  - **RandomExplosion**: se mueve en direcciones aleatorias y se dibuja como cuadrado.
  - **StarExplosion**: se mueve en forma de estrella con rayos y se dibuja con líneas.

#### 4. Clase `ofApp`
- Hereda de `ofBaseApp` y maneja la lógica principal.
- Métodos clave: `setup`, `update`, `draw`, `mousePressed`, `keyPressed`.
- Usa un `std::vector` de punteros a `Particle` para manejar múltiples partículas.


#### `setup()`
- Establece el framerate y el fondo negro.

#### `update()`
- Actualiza todas las partículas.
- Si alguna debe explotar (`shouldExplode`), se crean nuevas partículas de explosión.
- Las partículas muertas (`isDead`) se eliminan del vector y se libera su memoria.

#### `draw()`
- Dibuja todas las partículas en pantalla.

#### `createRisingParticle()`
- Crea una partícula `RisingParticle` con dirección aleatoria hacia arriba.
- Nace desde una zona horizontal central en la parte inferior de la pantalla.

#### `mousePressed()`
- Al hacer clic, se crea una `RisingParticle`.

#### `keyPressed()`
- Presionar barra espaciadora (`' '`) crea 1000 partículas ascendentes.
- Presionar `'s'` guarda una captura de pantalla.

#### Destructor `~ofApp()`
- Libera toda la memoria de las partículas al cerrar la aplicación.


+  ¿Cómo puedes interactuar con la aplicación?
  + al orpimir s se guarda la image
  + al orpimir espacio crea 1000 particulas
  + al dar click crea una particula 
