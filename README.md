##### Introducción a Processing y arduino para el desarrollo de una interfaz interactiva #####

1. [Hola Mundo](#ejercicio-1-hola-mundo) <br>
2. [Led intermitente](#ejercicio-2-led-intermitente-blink) <br>
3. [Control Pulsador](#ejercicio-3-control-por-pulsador) <br>
4. [Led con potenciometro](#ejercicio-4-led-con-potenci%C3%B3metro) <br>


# Interfaz-II
##### Ejercicio 1 "Hola mundo" #####
```js
void setup() {
  Serial.begin(9600); // Inicia la comunicación serie a 9600 bps
  Serial.println("felices juegos del hambre y que la suerte este siempre de su lado"); // Envía "felices juegos del hambre y que la suerte este siempre de su lado" al monitor serie
}
void loop() {
  // No es necesario poner nada en el loop para este ejemplo
}
```
<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/img/Hola%20mundo.png"/>

##### Ejercicio 2 LED Intermitente (Blink) #####
```js
void setup() {  // Configuración inicial (ej: pines como entrada/salida)
  pinMode(13, OUTPUT);  // Pin 13 como salida
  pinMode(8, OUTPUT);  // Pin 8 como salida
}

void loop() {   // Se repite infinitamente
  digitalWrite(13, HIGH);  // Encender LED
  delay(150);             // Esperar 1 segundo
  
  digitalWrite(13, LOW);   // Apagar LED
  delay(300);             // Esperar 1 segundo
  
   digitalWrite(8, HIGH);  // Encender LED
  delay(250);             // Esperar 3 segundo
  
  digitalWrite(8, LOW);   // Apagar LED
  delay(300);             // Esperar 3 segund
  
}
```
<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/img/Le%20Intermitente.png"/>

##### Ejercicio 3 Control por Pulsador #####
```js
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
}
void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
  } else {
    digitalWrite(13, LOW);
  }
}
```
<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/img/Led%20Pulsador.png"/>

##### Ejercicio 4 LED con Potenciómetro #####
```js
void setup() {
  pinMode(9, OUTPUT);  // Pin PWM (símbolo ~)
}
void loop() {
  int valor = analogRead(A0);           // Leer potenciómetro (0-1023)
  int brillo = map(valor, 0, 980, 0, 255);  // Convertir a rango PWM
  analogWrite(9, brillo);               // Ajustar brillo
}
```
<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/led%20Potenciometro.png"/>

##### Ejercicio 5 Semáforo #####
```js
// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido


  delay(2000); // 2 segundos
}
```
<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/img/Sem%C3%A1foro.png"/>

##### Ejercico 6 Semáforo parpadeante #####

```js
// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
   // Verde peatones encendido
  // 5 segundos
      digitalWrite(LED_4, HIGH);  // Encender LED
  delay(2000);             // Esperar 1 segundo
  digitalWrite(LED_4, LOW);   // Apagar LED
  delay(2000);       
    digitalWrite(LED_4, HIGH);  // Encender LED
  delay(500);             // Esperar 1 segundo
  digitalWrite(LED_4, LOW);   // Apagar LED
  delay(500);             // Esperar 1 segundo
 digitalWrite(LED_4, HIGH);  // Encender LED
  delay(500);             // Esperar 1 segundo
  digitalWrite(LED_4, LOW);   // Apagar LED
  delay(500);  
   digitalWrite(LED_4, HIGH);  // Encender LED
  delay(500);             // Esperar 1 segundo
  digitalWrite(LED_4, LOW);   // Apagar LED
  delay(500);             // Esperar 1 segundo
// Esperar 1 segundo

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(2000); // 2 segundos
}

```
##### Ejercicio 7 Processing #####

```js
import processing.serial.*;

Serial myPort;
ArrayList<CircleData> circles; 

void setup() {
  size(1200, 720);
  background(0);
  
  // Ajusta el puerto según tu Arduino
  println(Serial.list());
  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<CircleData>();
}

void draw() {
  //background(0);
  
  // Dibujar todos los círculos guardados
  //fill(0, 150, 255);
  //noStroke();
  fill(0, 0, 0);
  stroke(255, 0, 0);
  for (CircleData c : circles) {
    ellipse(c.x, c.y, c.size, c.size);
  }
  
  // Leer datos de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.startsWith("BTN")) {
        // Extraer el valor del potenciómetro
        String[] parts = split(val, ',');
        if (parts.length == 2) {
          float potVal = float(parts[1]);
          float circleSize = map(potVal, 0, 1023, 10, 100); // tamaño 10-100 px
          circles.add(new CircleData(random(width), random(height), circleSize));
        }
      }
    }
  }
}

// Clase para guardar datos de cada círculo
class CircleData {
  float x, y, size;
  CircleData(float x, float y, float size) {
    this.x = x;
    this.y = y;
    this.size = size;
  }
}
```
##### Ejercicio 8 For if #####
```js
int leds[] = {2, 3, 4, 5}; // Creamos un arreglo con los pines donde van conectados los LEDs

void setup() {
  // Esta función corre solo una vez al iniciar Arduino
  for (int i = 0; i < 4; i++) {         // Recorre el arreglo desde i = 0 hasta i = 3
    pinMode(leds[i], OUTPUT);           // Configura cada pin del arreglo como salida (para controlar LEDs)
  }
}

void loop() {
  // Esta función corre en bucle infinito
  for (int i = 0; i < 4; i++) {         // Recorre los 4 LEDs, uno por uno
    if (i % 1 == 0) {                   // Si el índice es par (0, 2)...
      digitalWrite(leds[i], HIGH);      // Enciende el LED correspondiente
    } else {                            // Si el índice es impar (1, 3)...
      digitalWrite(leds[i], LOW);       // Apaga el LED correspondiente
    }
    delay(500);                         // Espera 0,5 segundos antes de pasar al siguiente
  }
```

<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/img/For.png"/>
  
##### Ejercicio 9 if else #####
```js
int valor;  // aquí guardaremos la lectura del sensor

void setup() {
  Serial.begin(9600);   // Inicia la comunicación serial
}

void loop() {
  valor = analogRead(A0);   // lee el pin analógico A0

  if (valor < 300) {
    Serial.println("Muy bajo");
  } else if (valor < 700) {
    Serial.println("Medio");
  } else {
    Serial.println("Alto");
  }

  delay(500); // medio segundo entre lecturas
}
```
<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/If%20else.png"/>

##### ejercicio n°10: botonera con sonido

```js
import processing.sound.*;

// Importamos librería para comunicación serial
import processing.serial.*;
// Importamos librería Minim para manejar audio
import ddf.minim.*;

// Declaramos el objeto serial para comunicarnos con Arduino
Serial myPort;
// Objeto principal de Minim
Minim minim;
// Array de reproductores de audio (3 pistas)
AudioPlayer[] players;
// Variable para guardar el índice de la pista que está sonando
int currentTrack = -1;  // -1 significa que no hay pista activa al inicio

void setup() {
  size(400, 200); // Ventana de 400x200 píxeles
  
  // --- Configuración del puerto serial ---
  printArray(Serial.list()); // Muestra en consola la lista de puertos disponibles
  myPort = new Serial(this, Serial.list()[0], 9600); // Abrimos el primer puerto de la lista a 9600 baudios
  
  // --- Configuración de audio ---
  minim = new Minim(this); // Inicializamos Minim
  players = new AudioPlayer[3]; // Creamos un array de 3 reproductores
  
  // Cargamos los 3 archivos de audio desde la carpeta "data"
  players[0] = minim.loadFile("campanillaB.mp3", 2048); 
  players[1] = minim.loadFile("campanillaÑ.mp3", 2048); 
  players[2] = minim.loadFile("campanillaZ.mp3", 2048); 
}

void draw() {
  background(0); // Fondo negro
  fill(255);     // Color blanco para el texto
  textSize(16);  // Tamaño del texto
  
  // Mostramos en pantalla qué botón está activo
  text("Botón actual: " + (currentTrack == -1 ? "ninguno" : currentTrack), 20, 40);
}

void serialEvent(Serial myPort) {
  // Leemos la cadena que llega desde Arduino hasta el salto de línea
  String inString = trim(myPort.readStringUntil('\n'));
  
  // Si no llega nada, salimos
  if (inString == null) return;

  // --- Si el mensaje recibido empieza con "B" significa que es un botón ---
  if (inString.startsWith("B")) {
    // Quitamos la letra "B" y separamos el mensaje en partes (ejemplo "0:0")
    String[] parts = split(inString.substring(1), ':');
    
    // Si realmente recibimos dos partes (índice y estado)
    if (parts.length == 2) {
      int buttonIndex = int(parts[0]); // Número del botón (0,1,2)
      int state = int(parts[1]);       // Estado del botón (0 = presionado, 1 = suelto)
      
      // Si el botón fue presionado (LOW = 0 en Arduino)
      if (state == 0) { 
        playTrack(buttonIndex); // Llamamos a la función para reproducir la pista correspondiente
      }
    }
  }
}

// --- Función que reproduce una pista según el botón ---
void playTrack(int index) {
  // Si ya había una pista sonando, la pausamos y la rebobinamos al inicio
  if (currentTrack != -1 && players[currentTrack].isPlaying()) {
    players[currentTrack].pause();
    players[currentTrack].rewind();
  }
  
  // Reproducimos en bucle la pista seleccionada
  players[index].loop();
```

##### Ejercicio 11 semáforo 2.0 ##### 
```js
// Definición de pines
int LED_1 = 6;  // Luz roja autos (controlada por botón)
int LED_2 = 7;  // Luz amarilla autos (automática)
int LED_3 = 8;  // Luz verde autos (automática)
int LED_4 = 9;  // Luz verde peatones (controlada por botón)
int LED_5 = 10; // Luz roja peatones (automática)

int boton1 = 2; // Botón 1
int boton2 = 4; // Botón 2

bool estadoLED_1 = false; // Estado de LED_1
bool estadoLED_4 = false; // Estado de LED_4

unsigned long tiempoAnterior = 0;
int estadoSemaforo = 0;

void setup() {
  // Configurar LEDs como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);

  // Configurar botones como entrada pull-up
  pinMode(boton1, INPUT_PULLUP);
  pinMode(boton2, INPUT_PULLUP);

  // Apagar todos los LEDs al inicio
  digitalWrite(LED_1, LOW);
  digitalWrite(LED_2, LOW);
  digitalWrite(LED_3, LOW);
  digitalWrite(LED_4, LOW);
  digitalWrite(LED_5, LOW);
}

void loop() {
  // --------------------------
  // CONTROL CON BOTONES
  // --------------------------
  if (digitalRead(boton1) == LOW) {
    delay(200); // Evita rebotes
    estadoLED_1 = !estadoLED_1;
    digitalWrite(LED_1, estadoLED_1);
    while (digitalRead(boton1) == LOW); // Espera a soltar
  }

  if (digitalRead(boton2) == LOW) {
    delay(200);
    estadoLED_4 = !estadoLED_4;
    digitalWrite(LED_4, estadoLED_4);
    while (digitalRead(boton2) == LOW);
  }

  // --------------------------
  // SECUENCIA AUTOMÁTICA DE SEMÁFORO
  // --------------------------

  unsigned long tiempoActual = millis();

  // Cambia de estado cada 3 segundos
  if (tiempoActual - tiempoAnterior >= 3000) {
    tiempoAnterior = tiempoActual;

    // Apagar todos los LEDs automáticos antes de cambiar de estado
    digitalWrite(LED_2, LOW); // Amarillo autos
    digitalWrite(LED_3, LOW); // Verde autos
    digitalWrite(LED_5, LOW); // Rojo peatones

    // Cambiar de estado
    switch (estadoSemaforo) {
      case 0:
        digitalWrite(LED_3, HIGH); // Verde autos
        digitalWrite(LED_5, HIGH); // Rojo peatones
        estadoSemaforo = 1;
        break;
      case 1:
        digitalWrite(LED_2, HIGH); // Amarillo autos
        digitalWrite(LED_5, HIGH); // Rojo peatones
        estadoSemaforo = 2;
        break;
      case 2:
        // Nada encendido, pausa breve
        estadoSemaforo = 0;
        break;
    }
  }
}

```
<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/img/Sem%C3%A1foro%202.0.png"/> 


##### Ejercicio 12 Sensor #####
```js

// Definir el pin del sensor Sharp
int sharpPin = A0;

void setup() {
  Serial.begin(9600); // Iniciar comunicación serial
}

void loop() {
  int sensorValue = analogRead(sharpPin); // Leer valor del sensor
  Serial.println(sensorValue); // Enviar valor a Processing
  delay(100); // Esperar un momento
}

```
##### Ejercicio 13 Sensor Processing #####
```js
import processing.serial.*;

Serial myPort;  // Create object from Serial class
static String val;    // Data received from the serial port
int sensorVal = 0;

void setup()
{
  background(0); 
  //fullScreen(P3D);
   size(1080, 720);
   noStroke();
  noFill();
  String portName = "COM3";// Change the number (in this case ) to match the corresponding port number connected to your Arduino. 

  myPort = new Serial(this,Serial.list()[0], 9600);
}

void draw()
{
  if ( myPort.available() > 0) {  // If data is available,
  val = myPort.readStringUntil('\n'); 
  try {
   sensorVal = Integer.valueOf(val.trim());
  }
  catch(Exception e) {
  ;
  }
  println(sensorVal); // read it and store it in vals!
  }  
 //background(0);
  // Scale the mouseX value from 0 to 640 to a range between 0 and 175
  float c = map(sensorVal, 0, width, 0, 400);
  // Scale the mouseX value from 0 to 640 to a range between 40 and 300
  float d = map(sensorVal, 0, width, 40,500);
  fill(255, c, 0);
  ellipse(width/2, height/2, d, d);   

}

```
<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/img/Sensor%20Processing.png"/> 

##### Ejercico 14 Sensor humedad ####
```js
void setup()
{
  Serial.begin(9600);// abre el puerto serial y Establece la velocidad en baudios a 9600 bps
}
void loop()
{
  int sensorValue;
  sensorValue = analogRead(0);   //conectar el sensor de humedad al pin analogo 0
  Serial.println(sensorValue); //imprime el valor a serial.
  delay(200);
}
```
##### Ejercicio 15 Promedio de imagenes ##### 
```js
Processing:

import processing.serial.*;

Serial myPort;
PImage[] imgs;
int numImages = 3;
PImage avgImg;
float mixAmount = 0;

void setup() {
  size(800, 600);
  println(Serial.list());
  
  //Cambia el índice según tu puerto (0, 1, 2, etc.)
  myPort = new Serial(this, Serial.list()[0], 9600);
  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort.bufferUntil('\n');

  // Cargar imágenes
  imgs = new PImage[numImages];
  imgs[0] = loadImage("img1.jpg");
  imgs[1] = loadImage("img2.jpg");
  imgs[2] = loadImage("img3.jpg");

  avgImg = createImage(imgs[0].width, imgs[0].height, RGB);
}

void draw() {
  // Dibujar la imagen promedio según el valor del potenciómetro
  background(0);
  calcAverage(mixAmount);
  image(avgImg, 0, 0, width, height);
  
  fill(255);
  textSize(20);
  text("Mezcla: " + nf(mixAmount, 1, 2), 20, height - 20);
}

void serialEvent(Serial p) {
  String val = p.readStringUntil('\n');
  if (val != null) {
    val = trim(val);
    float sensor = float(val);
    mixAmount = map(sensor, 0, 1023, 0, 1); // 0 a 1
  }
}

void calcAverage(float t) {
  avgImg.loadPixels();

  for (int i = 0; i < avgImg.pixels.length; i++) {
    color c1 = imgs[0].pixels[i];
    color c2 = imgs[1].pixels[i];
    color c3 = imgs[2].pixels[i];

    // Promedio ponderado según el potenciómetro
    float r = red(c1)*(1-t) + red(c2)*t*0.5 + red(c3)*t*0.5;
    float g = green(c1)*(1-t) + green(c2)*t*0.5 + green(c3)*t*0.5;
    float b = blue(c1)*(1-t) + blue(c2)*t*0.5 + blue(c3)*t*0.5;

    avgImg.pixels[i] = color(r, g, b);
  }
  avgImg.updatePixels();
}

Arduino:

void setup() {
  Serial.begin(9600);
}

void loop() {
  int potValue = analogRead(A0);
  Serial.println(potValue);
  delay(20);
}

```

<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/img/imagen%201.png"/>

<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/img/imagen%202.png"/>

<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/img/imagen%203.png"/>

<img src="https://raw.githubusercontent.com/McabreraO/Interfaz-II/refs/heads/main/img/imagen%204.png"/>




  


