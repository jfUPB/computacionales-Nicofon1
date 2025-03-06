```c++
#include <iostream>

using namespace std;

// Función que modifica el parámetro pasado por valor
void modificarPorValor(int a,int b) {
    int t = b;
    b = a;
    a = t;

}

// Función que modifica el parámetro pasado por referencia
void modificarPorReferencia(int& a, int& b) {
    int t = b;
    b = a;
    a = t;
}

// Función que modifica el parámetro utilizando punteros
void modificarPorPuntero(int* a, int* b) {
    int t = *b;
    *b = *a;
    *a = t;
}

int main() {
    int a = 1;
    int b = 2;


    cout << "Valor inicial de a (paso por valor): " << a << endl;
    cout << "Valor inicial de b (paso por referencia): " << b << endl;


    cout << "\nLlamando a modificarPorValor(a)..." << "valor de a : " << a << endl;
    modificarPorValor(a,b);
    cout << "Después de modificarPorValor, valor de b: " << b << "  valor de a : " << a << endl;
     a = 1;
     b = 2;
    cout << "\nLlamando a modificarPorReferencia(b)..." << endl;
    modificarPorReferencia(a,b);
    cout << "Después de modificarPorReferencia, valor de b: " << b << "  valor de a : " << a << endl;
     a = 1;
     b = 2;
    cout << "\nLlamando a modificarPorPuntero(&c)..." << endl;
    modificarPorPuntero(&a, &b);
    cout << "Después de modificarPorReferencia, valor de b: " << b << "  valor de a : " << a << endl;


    return 0;
}
```
