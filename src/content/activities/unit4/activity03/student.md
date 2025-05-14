```
#pragma once
#include "ofMain.h"

// Nodo de la cola
struct Node {
    float x, y;
    float radius;
    ofColor color;
    float opacity;
    Node* next;

    Node(float _x, float _y, float _radius, ofColor _color, float _opacity)
        : x(_x), y(_y), radius(_radius), color(_color), opacity(_opacity), next(nullptr) {
    }
};

// Implementación manual de una cola (FIFO)
class BrushQueue {
public:
    Node* front;
    Node* rear;
    int size;
    int maxSize;

    BrushQueue(int _maxSize);
    ~BrushQueue();

    void enqueue(float x, float y, float radius, ofColor color, float opacity);
    void dequeue();
    void clear();
    bool isEmpty();
    ofColor color = ofColor::fromHex(1, 1);
};


// Constructor
BrushQueue::BrushQueue(int _maxSize) : front(nullptr), rear(nullptr), size(0), maxSize(_maxSize) {}

// Destructor
BrushQueue::~BrushQueue() {
    clear();
}

// Implementa aquí `enqueue()`
void BrushQueue::enqueue(float x, float y, float radius, ofColor color, float opacity) {
    // TODO: crear un nuevo nodo y agregarlo al final de la cola.
    // Si la cola supera `maxSize`, eliminar el nodo más antiguo con `dequeue()`.
    Node* newNode = new Node(x, y, radius, color, opacity);
    if (size == 0) {
        front = rear = newNode;
        size++;
    }
    else {
        rear->next = newNode;
        rear = newNode;
        if (size > maxSize)
            dequeue();
        else
            size++;
    }
        

}

// Implementa aquí `dequeue()`
void BrushQueue::dequeue() {
    // TODO: eliminar el nodo más antiguo si la cola no está vacía.
    if (front == nullptr)
        return;

    Node* temp = front;
    front = front->next;
    delete temp;

}

// Implementa aquí `clear()`
void BrushQueue::clear() {
    // TODO: eliminar todos los nodos de la cola.
    Node* temp = front;
    while (temp->next != NULL) {
        Node* garb = temp;
        temp = garb->next;
        delete garb;
    }
    delete temp;
    front = rear = nullptr;
    size = 0;
}

// Implementa aquí `isEmpty()`
bool BrushQueue::isEmpty() {
    // TODO: retornar si la cola está vacía.
    if (size == 0)
        return true;
    else
        return false;
}


class ofApp : public ofBaseApp {
public:
    BrushQueue strokes; // Cola de trazos
    float backgroundHue = 0;

    ofApp() : strokes(50) {} // Tamaño máximo de la cola

    void setup();
    void update();
    void draw();
    void keyPressed(int key);
};
```

```
#pragma once
#include "ofMain.h"

// Nodo de la cola
struct Node {
    float x, y;
    float radius;
    ofColor color;
    float opacity;
    Node* next;

    Node(float _x, float _y, float _radius, ofColor _color, float _opacity)
        : x(_x), y(_y), radius(_radius), color(_color), opacity(_opacity), next(nullptr) {
    }
};

// Implementación manual de una cola (FIFO)
class BrushQueue {
public:
    Node* front;
    Node* rear;
    int size;
    int maxSize;

    BrushQueue(int _maxSize);
    ~BrushQueue();

    void enqueue(float x, float y, float radius, ofColor color, float opacity);
    void dequeue();
    void clear();
    bool isEmpty();
    ofColor color = ofColor::fromHex(1, 1);
};


// Constructor
BrushQueue::BrushQueue(int _maxSize) : front(nullptr), rear(nullptr), size(0), maxSize(_maxSize) {}

// Destructor
BrushQueue::~BrushQueue() {
    clear();
}

// Implementa aquí `enqueue()`
void BrushQueue::enqueue(float x, float y, float radius, ofColor color, float opacity) {
    // TODO: crear un nuevo nodo y agregarlo al final de la cola.
    // Si la cola supera `maxSize`, eliminar el nodo más antiguo con `dequeue()`.
    Node* newNode = new Node(x, y, radius, color, opacity);
    if (size == 0) {
        front = rear = newNode;
        size++;
    }
    else {
        rear->next = newNode;
        rear = newNode;
        if (size > maxSize)
            dequeue();
        else
            size++;
    }
        

}

// Implementa aquí `dequeue()`
void BrushQueue::dequeue() {
    // TODO: eliminar el nodo más antiguo si la cola no está vacía.
    if (front == nullptr)
        return;

    Node* temp = front;
    front = front->next;
    delete temp;

}

// Implementa aquí `clear()`
void BrushQueue::clear() {
    // TODO: eliminar todos los nodos de la cola.
    Node* temp = front;
    while (temp->next != NULL) {
        Node* garb = temp;
        temp = garb->next;
        delete garb;
    }
    delete temp;
    front = rear = nullptr;
    size = 0;
}

// Implementa aquí `isEmpty()`
bool BrushQueue::isEmpty() {
    // TODO: retornar si la cola está vacía.
    if (size == 0)
        return true;
    else
        return false;
}


class ofApp : public ofBaseApp {
public:
    BrushQueue strokes; // Cola de trazos
    float backgroundHue = 0;

    ofApp() : strokes(50) {} // Tamaño máximo de la cola

    void setup();
    void update();
    void draw();
    void keyPressed(int key);
};
```
![image](https://github.com/user-attachments/assets/f2d50a7c-c2e7-454b-bf36-a995969b1823)
![image](https://github.com/user-attachments/assets/85391f12-9602-4c1b-abb9-dafaba6907bc)

#### 3. Uso del depurador

Puse breakpoints en `enqueue`, `dequeue` y `clear`. En `enqueue` vi que `front` y `rear` se actualizan bien. En `dequeue` vi que el primero se elimina. En `clear` se borran todos los nodos. Usé la ventana de variables locales para ver los punteros. Todo parecía funcionar.



#### 4. Pruebas realizadas

- **Inserción:** Llamé a `enqueue()`, el nodo apareció.  
- **Límite FIFO:** Metí 51 nodos, el primero se fue.  
- **Clear:** Presioné ‘c’, se vació todo.  
- **Cambio de tamaño:** Presioné ‘a’, pasó de 50 a 100.  
- **Cola vacía:** Llamé a `dequeue()` con la cola vacía, no se crasheó. 
