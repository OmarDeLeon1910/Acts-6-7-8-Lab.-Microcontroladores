
# Información del Proyecto
# Autores: 
## -[2061110] - Erick Alejandro Francisco Baltazar
## -[2057902] - Omar Santiago De León Salinas
## -[2056820] - Walter Giovani Benavente Tapia
# Nombre del Proyecto: Emulador de Mouse y Teclado Bluetooth (HID) con ESP32 (Equipo 10 Laboratorio Microcontroladores)

Este proyecto consiste en el diseño, desarrollo e implementación de un dispositivo periférico inalámbrico basado en el microcontrolador **ESP32**, capaz de actuar como un dispositivo de interfaz humana (HID por sus siglas en inglés). 
El objetivo principal es emular las funciones de un ratón y un teclado convencional utilizando componentes electrónicos externos, permitiendo que el usuario controle computadoras, tabletas o teléfonos inteligentes mediante el protocolo Bluetooth Low Energy (BLE). Al configurarse como un dispositivo HID, el sistema es reconocido automáticamente por cualquier sistema operativo moderno sin la necesidad de instalar controladores adicionales, lo que garantiza una integración fluida y multiplataforma.
La arquitectura del sistema combina el uso de entradas analógicas y digitales para recrear una experiencia de navegación completa. Un joystick analógico se encarga de traducir los movimientos físicos en coordenadas cartesianas para desplazar el cursor en pantalla, mientras que una serie de pulsadores táctiles se programan para ejecutar acciones específicas como clics, desplazamientos de diapositivas o controles multimedia. Internamente, el firmware procesa los cambios de voltaje en los pines GPIO y los empaqueta en tramas de datos compatibles con los estándares de comunicación HID, ofreciendo una solución técnica versátil que demuestra las capacidades del ESP32 en el ámbito de la conectividad inalámbrica y el control de hardware.

---

# Representación Gráfica

# Act. 6: Diagrama Pictórico
Este diagrama muestra la conexión física real de los componentes.
<img width="1536" height="1024" alt="Diagrama Pictorico" src="https://github.com/user-attachments/assets/2d741794-3795-4a26-8a4d-2a879ee10a10" />

*Descripción: Conexión de los pulsadores y el joystick a los pines GPIO del ESP32 en una protoboard, el cual funciona como el plano de montaje físico que traduce la teoría a la realidad de la protoboard. En este apartado se documenta la disposición espacial de los componentes, mostrando cómo el ESP32 interactúa físicamente con el joystick y los pulsadores de colores a través de conexiones directas y puentes de voltaje. Es una pieza fundamental para la replicabilidad del hardware, ya que permite identificar a simple vista la organización de los cables de datos, las líneas de alimentación de $3.3V$ y los puntos de retorno a tierra común.* 

# Act. 7: Diagrama de Bloques

<img width="1023" height="355" alt="Diagrama de Bloques" src="https://github.com/user-attachments/assets/5733e63f-9be8-498b-8942-b3c1a4d8b6ed" />

*Descripción: Flujo desde la entrada de datos (Sensores/Botones) -> Procesamiento (ESP32) -> Salida (Bluetooth HID), el diagrama representa la arquitectura lógica y el flujo de información del sistema sin entrar en detalles de cableado. Este resumen gráfico describe la secuencia operativa donde los periféricos de entrada capturan estímulos mecánicos que el microcontrolador procesa mediante sus conversores analógico-digitales para finalmente transmitir paquetes de datos bajo el protocolo Bluetooth HID. Esta etapa es crucial para entender la jerarquía del sistema, dividiendo el proyecto en módulos de adquisición de señales, procesamiento central y comunicación inalámbrica de salida.*

# Act. 8: Diagrama Esquemático
Representación técnica y simbólica del circuito electrónico.

<img width="552" height="306" alt="Diagrama Esquematico" src="https://github.com/user-attachments/assets/1ab6e1da-a60a-4d7f-bc35-cce8c62191df" />

*Descripción: Circuito detallado indicando resistencias pull-down de $10k\Omega$ y conexiones a tierra, el cual constituye la documentación técnica formal utilizando simbología electrónica universal. En esta actividad se detalla la ingeniería eléctrica del dispositivo, especificando la función crítica de las resistencias de $10k\Omega$ en configuración Pull-down que aseguran la estabilidad de los pines GPIO frente al ruido eléctrico. Este diagrama es la referencia definitiva para el análisis de nodos, validando que todas las señales analógicas del joystick y digitales de los botones cuenten con las referencias de voltaje y tierra necesarias para un funcionamiento preciso y seguro del emulador.*

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
