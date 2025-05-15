```
#pragma once
#include "ofMain.h"
#include <vector>

// -------------------------------------------------
// Clase base abstracta: Particle
// -------------------------------------------------
class Particle {
public:
    virtual ~Particle() {}
    virtual void update(float dt) = 0;
    virtual void draw() = 0;
    virtual bool isDead() const = 0;
    // Nuevo método para saber si la partícula (tipo RisingParticle) debe explotar
    virtual bool shouldExplode() const { return false; }
    // Métodos para obtener posición y color, para usarlos en explosiones
    virtual glm::vec2 getPosition() const { return glm::vec2(0, 0); }
    virtual ofColor getColor() const { return ofColor(255); }
};

// -------------------------------------------------
// RisingParticle: Partícula que nace en la parte inferior central y sube
// -------------------------------------------------
class RisingParticle : public Particle {
protected:
    glm::vec2 position;
    glm::vec2 velocity;
    ofColor color;
    float lifetime; // tiempo máximo antes de explotar
    float age;
    bool exploded;
public:
    RisingParticle(const glm::vec2& pos, const glm::vec2& vel, const ofColor& col, float life)
        : position(pos), velocity(vel), color(col), lifetime(life), age(0), exploded(false) {
    }

    void update(float dt) override {
        position += velocity * dt;
        age += dt;
        // Aumenta la desaceleración para dar sensación de recorrido largo
        velocity.y += 9.8f * dt * 8;
        // Condición de explosión: cuando la partícula alcanza aproximadamente el 15% de la altura
        float explosionThreshold = ofGetHeight() * 0.15 + ofRandom(-30, 30);
        if (position.y <= explosionThreshold || age >= lifetime) {
            exploded = true;
        }
    }

    void draw() override {
        ofSetColor(color);
        // Partícula más grande
        ofDrawCircle(position, 10);
    }

    bool isDead() const override { return exploded; }
    bool shouldExplode() const override { return exploded; }
    glm::vec2 getPosition() const override { return position; }
    ofColor getColor() const override { return color; }
};

class CurvedRisingParticle : public RisingParticle {
private:
    float amplitude;   
    float frequency;   
    float baseX;       
public:
    CurvedRisingParticle(const glm::vec2& pos, const glm::vec2& vel, const ofColor& col, float life)
        : RisingParticle(pos, vel, col, life), amplitude(ofRandom(10, 30)), frequency(ofRandom(7, 10)), baseX(pos.x) {
    }

    void update(float dt) override {
        age += dt;

        
        position.y += velocity.y * dt;

        
        position.x = baseX + amplitude * sin(age * frequency);

        
        velocity.y += 9.8f * dt * 8;

        float explosionThreshold = ofGetHeight() * 0.15 + ofRandom(-30, 30);
        if (position.y <= explosionThreshold || age >= lifetime) {
            exploded = true;
        }
    }

    void draw() override {
        ofSetColor(color);
        ofDrawCircle(position, 10);
    }
};


// -------------------------------------------------
// Clase base para explosiones: ExplosionParticle
// -------------------------------------------------
class ExplosionParticle : public Particle {
protected:
    glm::vec2 position;
    glm::vec2 velocity;
    ofColor color;
    float age;
    float lifetime;
    float size;  // tamaño de la partícula de explosión
public:
    ExplosionParticle(const glm::vec2& pos, const glm::vec2& vel, const ofColor& col, float life, float sz)
        : position(pos), velocity(vel), color(col), age(0), lifetime(life), size(sz) {
    }

    void update(float dt) override {
        position += velocity * dt;
        age += dt;
        float alpha = ofMap(age, 0, lifetime, 255, 0, true);
        color.a = alpha;
    }

    bool isDead() const override { return age >= lifetime; }
};

// -------------------------------------------------
// ExpandingRisingParticle: sube y se expande con el tiempo
// -------------------------------------------------
class ExpandingRisingParticle : public RisingParticle {
private:
    float size;
    float growthRate;
public:
    ExpandingRisingParticle(const glm::vec2& pos, const glm::vec2& vel, const ofColor& col, float life)
        : RisingParticle(pos, vel, col, life), size(5.0f), growthRate(ofRandom(8.0f, 20.0f)) {
    }

    void update(float dt) override {
        RisingParticle::update(dt);
        size += growthRate * dt;
    }

    void draw() override {
        ofSetColor(color);
        ofDrawCircle(position, size);
    }
};


// -------------------------------------------------
// CircularExplosion: Explosión en patrón circular
// -------------------------------------------------
class CircularExplosion : public ExplosionParticle {
public:
    CircularExplosion(const glm::vec2& pos, const ofColor& col)
        : ExplosionParticle(pos, glm::vec2(0, 0), col, 1.2f, ofRandom(16, 32)) {
        float angle = ofRandom(0, TWO_PI);
        float speed = ofRandom(80, 200);
        velocity = glm::vec2(cos(angle), sin(angle)) * speed;
    }

    void draw() override {
        ofSetColor(color);
        ofDrawCircle(position, size);
    }
};

// -------------------------------------------------
// RandomExplosion: Explosión con direcciones aleatorias
// -------------------------------------------------
class RandomExplosion : public ExplosionParticle {
public:
    RandomExplosion(const glm::vec2& pos, const ofColor& col)
        : ExplosionParticle(pos, glm::vec2(0, 0), col, 1.5f, ofRandom(16, 32)) {
        velocity = glm::vec2(ofRandom(-200, 200), ofRandom(-200, 200));
    }

    void draw() override {
        ofSetColor(color);
        ofDrawRectangle(position.x, position.y, size, size);
    }
};

// -------------------------------------------------
// StarExplosion: Explosión en forma de estrella
// -------------------------------------------------
class StarExplosion : public ExplosionParticle {
public:
    StarExplosion(const glm::vec2& pos, const ofColor& col)
        : ExplosionParticle(pos, glm::vec2(0, 0), col, 1.3f, ofRandom(20, 40)) {
        float angle = ofRandom(0, TWO_PI);
        float speed = ofRandom(90, 180);
        velocity = glm::vec2(cos(angle), sin(angle)) * speed;
    }

    void draw() override {
        ofSetColor(color);
        int rays = 5;
        float outerRadius = size;
        float innerRadius = size * 0.5;
        ofPushMatrix();
        ofTranslate(position);
        for (int i = 0; i < rays; i++) {
            float theta = ofMap(i, 0, rays, 0, TWO_PI);
            float xOuter = cos(theta) * outerRadius;
            float yOuter = sin(theta) * outerRadius;
            float xInner = cos(theta + PI / rays) * innerRadius;
            float yInner = sin(theta + PI / rays) * innerRadius;
            ofDrawLine(0, 0, xOuter, yOuter);
            ofDrawLine(xOuter, yOuter, xInner, yInner);
        }
        ofPopMatrix();
    }
};

// -------------------------------------------------
// SpiralExplosion: Partículas que se mueven en espiral
// -------------------------------------------------
class SpiralExplosion : public ExplosionParticle {
private:
    float angle;
    float angularVelocity;
    float radius;

public:
    SpiralExplosion(const glm::vec2& pos, const ofColor& col)
        : ExplosionParticle(pos, glm::vec2(0, 0), col, 1.5f, ofRandom(16, 32)),
        angle(ofRandom(0, TWO_PI)),
        angularVelocity(ofRandom(3.0f, 6.0f)),  // velocidad angular (radianes/segundo)
        radius(0) {
    }

    void update(float dt) override {
        age += dt;
        radius += 100 * dt;  // la partícula se aleja del centro aumentando el radio

        angle += angularVelocity * dt;  // gira en espiral

        // Calculamos la nueva posición en coordenadas polares convertidas a cartesianas
        position.x += cos(angle) * radius * dt;
        position.y += sin(angle) * radius * dt;

        float alpha = ofMap(age, 0, lifetime, 255, 0, true);
        color.a = alpha;
    }

    void draw() override {
        ofSetColor(color);
        ofDrawCircle(position, size);
    }
};


// -------------------------------------------------
// ofApp: Manejo de la escena y eventos
// -------------------------------------------------
class ofApp : public ofBaseApp {
public:
    void setup();   
    void update();
    void draw();
    void mousePressed(int x, int y, int button);
    void keyPressed(int key);

    std::vector<Particle*> particles;
    ~ofApp();

private:
    void createRisingParticle();

};
```
```
#include "ofApp.h"

// --------------------------------------------------------------
void ofApp::setup() {
    ofSetFrameRate(60);
    ofBackground(0);
}

// --------------------------------------------------------------
void ofApp::update() {

    float dt = ofGetLastFrameTime();

    // Actualiza todas las partículas
    for (int i = 0; i < particles.size(); i++) {
        particles[i]->update(dt);
    }

    // Procesa las partículas (iteración en reversa para facilitar eliminación)
    for (int i = particles.size() - 1; i >= 0; i--) {
        // Si la partícula debe explotar, generamos nuevas explosiones
        if (particles[i]->shouldExplode()) {
            int explosionType = (int)ofRandom(4); // ahora 4 tipos de explosión
            int numParticles = (int)ofRandom(20, 30);
            for (int j = 0; j < numParticles; j++) {
                if (explosionType == 0) {
                    particles.push_back(new CircularExplosion(particles[i]->getPosition(), particles[i]->getColor()));
                }
                else if (explosionType == 1) {
                    particles.push_back(new RandomExplosion(particles[i]->getPosition(), particles[i]->getColor()));
                }
                else if (explosionType == 2) {
                    particles.push_back(new StarExplosion(particles[i]->getPosition(), particles[i]->getColor()));
                }
                else {
                    particles.push_back(new SpiralExplosion(particles[i]->getPosition(), particles[i]->getColor()));
                }
            }
            delete particles[i];
            particles.erase(particles.begin() + i);
        }
        else if (particles[i]->isDead()) {
            delete particles[i];
            particles.erase(particles.begin() + i);
        }
    }
}

// --------------------------------------------------------------
void ofApp::draw() {
    for (int i = 0; i < particles.size(); i++) {
        particles[i]->draw();
    }
}

// --------------------------------------------------------------
void ofApp::createRisingParticle() {
    float minX = ofGetWidth() * 0.35;
    float maxX = ofGetWidth() * 0.65;
    float spawnX = ofRandom(minX, maxX);
    glm::vec2 pos(spawnX, ofGetHeight());

    glm::vec2 target(ofGetWidth() / 2 + ofRandom(-300, 300), ofGetHeight() * 0.10 + ofRandom(-30, 30));
    glm::vec2 direction = glm::normalize(target - pos);
    glm::vec2 vel = direction * ofRandom(250, 350);

    ofColor col;
    col.setHsb(ofRandom(255), 220, 255);
    float lifetime = ofRandom(1.5, 3.5);

    float type = ofRandom(1.0);
    if (type < 0.33f) {
        particles.push_back(new CurvedRisingParticle(pos, vel, col, lifetime));
    }
    else if (type < 0.66f) {
        particles.push_back(new ExpandingRisingParticle(pos, vel, col, lifetime));
    }
    else {
        particles.push_back(new RisingParticle(pos, vel, col, lifetime));
    }
}



// --------------------------------------------------------------
void ofApp::mousePressed(int x, int y, int button) {
    createRisingParticle();
}

// --------------------------------------------------------------
void ofApp::keyPressed(int key) {
    if (key == ' ') {
        for (int i = 0; i < 1000; i++) {
            createRisingParticle();
        }
    }
    if (key == 's') {
        ofSaveScreen("screenshot_" + ofToString(ofGetFrameNum()) + ".png");
    }
}

// --------------------------------------------------------------
ofApp::~ofApp() {
    for (int i = 0; i < particles.size(); i++) {
        delete particles[i];
    }
    particles.clear();
}
```




#### Prueba 1: Movimiento de `CurvedRisingParticle`

- **Objetivo:** Verificar movimiento vertical con oscilación horizontal senoidal.
- **Procedimiento:** Crear varias partículas de este tipo y observar su comportamiento.
- **Resultado esperado:** Movimiento curvo visible y sin errores.

#### Prueba 2: Expansión de `ExpandingRisingParticle`

- **Objetivo:** Confirmar que la partícula crece en tamaño mientras asciende.
- **Procedimiento:** Crear partículas y observar el aumento progresivo de tamaño.
- **Resultado esperado:** Partículas aumentan de tamaño correctamente.

#### Prueba 3: Creación aleatoria con `createRisingParticle()`

- **Objetivo:** Validar que se crean aleatoriamente los tres tipos de partículas.
- **Procedimiento:** Llamar muchas veces y revisar la proporción de tipos generados.
- **Resultado esperado:** Aproximadamente 33% de cada tipo.

#### Prueba 4: Explosión con patrón en espiral (SpiralExplosion)

- **Objetivo:** Verificar que la explosión genera partículas en movimiento espiral.
- **Procedimiento:** Provocar explosiones y observar el patrón de partículas.
- **Resultado esperado:** Movimiento en espiral visible y correcto.

#### Prueba 5: Eliminación correcta de partículas

- **Objetivo:** Asegurar que partículas terminan su ciclo y se eliminan sin errores.
- **Procedimiento:** Observar vida útil y limpieza de partículas.
- **Resultado esperado:** No quedan residuos ni problemas de memoria.
