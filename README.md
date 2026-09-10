# 🌡️ Módulo de Monitoreo de Penetración de Calor en Alimentos Sólidos

> Sistema IoT embebido diseñado para registrar y analizar en tiempo real la transferencia de calor en el núcleo de un alimento sólido durante su cocción en un baño de agua caliente, midiendo simultáneamente la temperatura del medio y del alimento.

---

## 📌 Tabla de Contenidos

- [Descripción General](#-descripción-general)
- [Estructura del Repositorio](#-estructura-del-repositorio)
- [Requisitos Previos](#-requisitos-previos)
- [Instalación y Configuración](#-instalación-y-configuración)
  - [1. Firmware (ESP32 / Arduino)](#1-firmware-esp32--arduino)
  - [2. Frontend Web](#2-frontend-web)
- [Uso y Funcionamiento](#-uso-y-funcionamiento)
- [Arquitectura y Tecnologías](#-arquitectura-y-tecnologías)
- [Autores](#-autores)

---

## 📋 Descripción General

Este módulo experimental permite estudiar el comportamiento térmico y la cinética de penetración del calor en alimentos sólidos sumergidos en agua caliente. 

El dispositivo utiliza dos sensores de temperatura tipo sonda (ej. DS18B20 sumergibles o termocuplas):
1. **Sensor 1 (Baño de Agua):** Mide la temperatura constante o controlada del medio de cocción.
2. **Sensor 2 (Núcleo del Alimento):** Mide la evolución de la temperatura en el centro geométrico del alimento a lo largo del tiempo.

Los datos capturados son procesados por el microcontrolador (ESP32 / Arduino) y transmitidos a un **Dashboard Web Frontend** para su visualización mediante gráficos de temperatura vs. tiempo. 

---

## 📂 Estructura del Repositorio

```text
/
├── firmware/            # Código fuente para ESP32 / Arduino
│   ├── main/            # Código principal (.ino / .cpp)
│   └── config.h         # Configuración de pines de sensores y WiFi
├── frontend/            # Dashboard web de visualización
│   ├── index.html       # Interfaz gráfica de monitoreo
│   ├── css/             # Estilos de la aplicación
│   └── js/              # Lógica de gráficos y lectura de datos
├── .gitignore           # Archivos omitidos del control de versiones
└── README.md            # Documentación general del proyecto
```
## 🛠️ Requisitos Previos
Hardware
Microcontrolador ESP32 (o Arduino con módulo de red/WiFi).

2× Sensores de temperatura sumergibles / de inserción (ej. DS18B20 con recubrimiento de acero inoxidable).

Resistencia de pull-up de 4.7kΩ (en caso de usar protocolo OneWire / DS18B20).

Fuente de alimentación o cable USB.
🛠️ Requisitos Previos
Hardware
Microcontrolador ESP32 (o Arduino con módulo de red/WiFi).

2× Sensores de temperatura sumergibles / de inserción (ej. DS18B20 con recubrimiento de acero inoxidable).

Resistencia de pull-up de 4.7kΩ (en caso de usar protocolo OneWire / DS18B20).

Fuente de alimentación o cable USB.
## ⚙️ Instalación y Configuración
1. Firmware (ESP32 / Arduino)
  1.Abre el proyecto en la carpeta firmware/ con tu IDE.

 2. Abre el archivo de configuración config.h y asigna los pines de conexión para las dos sondas de temperatura y las credenciales de red:
``` cpp
#define PIN_SENSOR_AGUA 4
#define PIN_SENSOR_NUCLEO 5

const char* SSID = "TU_RED_WIFI";
const char* PASSWORD = "TU_CONTRASEÑA";
```
 3. Conecta la tarjeta al ordenador, selecciona la placa adecuada y el puerto COM.

 4. Compila y carga el programa.

 5. Abre el Monitor Serie (115200 baudios) y copia la dirección IP que asigna la red a la tarjeta.

2. Frontend Web
 1. Navega a la carpeta frontend/.

 2. Abre el archivo de configuración o lógica JS (js/app.js o similar) e introduce la dirección IP obtenida en el paso anterior:

```JavaScript
const ESP32_IP = "[http://192.168.](http://192.168.)X.X";
```
 3. Abre index.html en tu navegador web.
## 🚀 Uso y Funcionamiento

1. Preparación:
    Coloca el primer sensor sumergido en el recipiente de agua caliente.

    Inserta la sonda del segundo sensor en el centro/núcleo del alimento sólido que se va a cocinar.

2. Inicio del Registro:

    Al encender el dispositivo y abrir la plataforma web, el sistema comenzará a registrar las lecturas simultáneas de ambos puntos.

3. Análisis:

    La interfaz web graficará en tiempo real las dos curvas de temperatura (Agua vs. Núcleo), permitiendo analizar el tiempo de retraso térmico y la             velocidad de penetración del calor.
## 🧰 Arquitectura y Tecnologías

Hardware: ESP32 / Arduino.

Sensores: Sondas de temperatura sumergibles (DS18B20 / Termocuplas).

Firmware: C++ / Wiring.

Frontend: HTML5, CSS3, JavaScript (Chart.js para graficación diferencial).

Protocolo de Comunicación: HTTP REST API / WebSockets (transmisión en tiempo real en formato JSON).
## 👨‍💻 Autores
Javiera Aldana  Proyect Owner: Coordinar el equipo, organizar tareas y plazos, supervisar avances y asegurar la integración del proyecto.

Gonzalo Ampuero Responsable científico: Transferencia de calor, variables, hipótesis, protocolo experimental y análisis de resultados.

Matias Sepulveda Software y datos: Programación, captura y almacenamiento de temperaturas, procesamiento de datos y gráficos.  

Fernando Reyes documentación: Diseño de la interfaz, facilidad de uso, guía de laboratorio, instrucciones y apoyo en pruebas con usuarios.

Benjamin Vejar Hardware e instrumentación: Sensores de temperatura, Arduino/ESP32, conexiones, montaje y calibración.
