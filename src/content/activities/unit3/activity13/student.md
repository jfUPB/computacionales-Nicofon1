**Código Fuente del Programa:**

```cpp
#include <iostream>
#include <string>

using namespace std;

class Personaje {
public:
    string nombre;
    int nivel;
    float energia;
    static int numPersonajes;

    Personaje(string _nombre, int _nivel) : nombre(_nombre), nivel(_nivel), energia(100.0f) {
        numPersonajes++;
        cout << "¡" << nombre << " ha sido creado! (Nivel " << nivel << ")" << endl;
    }

    ~Personaje() {
        cout << nombre << " ha sido destruido. (Energía restante: " << energia << ")" << endl;
        numPersonajes--;
    }

    void atacar(Personaje& objetivo) {
        cout << nombre << " ataca a " << objetivo.nombre << "!" << endl;
        objetivo.recibirDanio(20.0f);
    }

    void recibirDanio(float danio) {
        energia -= danio;
        if (energia < 0) energia = 0;
        cout << nombre << " recibe " << danio << " de daño. Energía: " << energia << endl;
    }

    void subirNivel(int incrementoNivel = 1) {
        nivel += incrementoNivel;
        cout << nombre << " sube al nivel " << nivel << "!" << endl;
    }

    static void mostrarNumPersonajes() {
        cout << "Número total de personajes: " << numPersonajes << endl;
    }
};

int Personaje::numPersonajes = 0;

int main() {
    Personaje heroe("Héroe", 1);
    Personaje enemigo("Enemigo", 5);
    Personaje* jefeFinal = new Personaje("Jefe Final", 10);
    Personaje& refHeroe = heroe;

    heroe.atacar(enemigo);
    enemigo.atacar(heroe);
    heroe.subirNivel();
    jefeFinal->atacar(heroe);
    refHeroe.subirNivel(3);

    Personaje::mostrarNumPersonajes();

    delete jefeFinal;

    return 0;
}
```

Explicación de Conceptos Aplicados:

* Clases y Objetos: `Personaje` es la clase; `heroe`, `enemigo`, `jefeFinal` son objetos.
* Paso de Parámetros: `atacar()` usa referencia; `subirNivel()` usa valor (con valor por defecto).
* Constructores y Destructores: Constructor inicializa, destructor "limpia" (simula limpieza).
* Métodos y Atributos: `nombre`, `nivel`, `energia` son atributos; `atacar()`, `recibirDanio()`, `subirNivel()` son métodos.
* Objetos en Stack y Heap: `heroe`, `enemigo` en stack; `jefeFinal` en heap (con `new` y `delete`).
* Punteros y Referencias: `jefeFinal` es puntero (acceso con `->`); `refHeroe` es referencia.
* Variables Estáticas: `numPersonajes` cuenta personajes; `mostrarNumPersonajes()` es método estático.
* Depuración: Usé breakpoints para ver valores y flujo del programa.

Análisis de la Memoria:

* Código: Direcciones de funciones.
* Datos/BSS: `Personaje::numPersonajes`.
* Stack: `heroe`, `enemigo`, `refHeroe` (la referencia).
* Heap: Objeto apuntado por `jefeFinal`.
