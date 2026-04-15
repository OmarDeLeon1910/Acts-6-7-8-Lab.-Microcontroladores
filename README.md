# Emulador de Mouse y Teclado Bluetooth (HID) con ESP32 (Equipo 10 Laboratorio Microcontroladores)

Este proyecto consiste en la creación de un dispositivo periférico inalámbrico utilizando un **ESP32**. El sistema emula un protocolo HID (Human Interface Device), permitiendo controlar una computadora o celular (pasar diapositivas, controlar música o mover el cursor) mediante hardware externo.

---

Representación Gráfica

# Act. 6: Diagrama Pictórico
Este diagrama muestra la conexión física real de los componentes.
![Diagrama Pictórico](./imagenes/pictorico.jpg)
*Descripción: Conexión de los pulsadores y el joystick a los pines GPIO del ESP32 en una protoboard.*

# Act. 7: Diagrama de Bloques
Visualización de alto nivel del funcionamiento del sistema.
![Diagrama de Bloques](./imagenes/bloques.jpg)
*Descripción: Flujo desde la entrada de datos (Sensores/Botones) -> Procesamiento (ESP32) -> Salida (Bluetooth HID).*

# Act. 8: Diagrama Esquemático
Representación técnica y simbólica del circuito electrónico.
![Diagrama Esquemático](./imagenes/esquemático.jpg)
*Descripción: Circuito detallado indicando resistencias pull-down de $10k\Omega$ y conexiones a tierra.*

---

# ¿Cómo funciona internamente?

El proyecto utiliza la pila de protocolos Bluetooth del ESP32 para anunciarse como un dispositivo de entrada estándar. 

**Arquitectura General:**
* **Capa de Hardware:** Pulsadores de colores para funciones digitales y un Joystick para el movimiento de los ejes $X$ e $Y$.
* **Capa de Firmware:** Programado en C++/Arduino, utiliza librerías de emulación HID que traducen los voltajes de los pines en paquetes de datos Bluetooth.
* **Alimentación:** Diseñado para ser portátil mediante una batería LiPo de $3.7V$.

**Tecnologías usadas:**
* **Microcontrolador:** ESP32 (WROOM-32).
* **Entradas:** Joystick analógico y botones táctiles.
* **Protocolo:** Bluetooth Low Energy (BLE) / HID.

---

# Instalación y Uso

# Requisitos
1.  **Hardware:** ESP32, 3 pulsadores, 1 joystick, resistencias de $10k\Omega$, cables.
2.  **Software:** Arduino IDE con el paquete de placas ESP32 instalado.

# Pasos para ponerlo en marcha
1.  Debemos de clonar este repositorio creado por nosotros: `git clone https://github.com/OmarDeLeon1910/Acts-6-7-8-Lab.Microcontroladores.git`
2.  Hay que conectar los componentes según el **Diagrama Esquemático**.
3.  Cargar el código de la carpeta `/codigo` a tu ESP32.
4.  Debemos emparejar el dispositivo vía Bluetooth con el nombre "ESP32 Mouse BT".


# Resumen Técnico
* **Pines Clave:** GPIO 13, 15, 2 (Configurados con resistencias Pull-down).
* **Interfaz:** Bluetooth HID.
* **Componente Principal:** Joystick para navegación de cursor.
