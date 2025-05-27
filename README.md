# Energy - Monitoreo y control de motor via BLE

Este proyecto implementa un sistema de monitoreo de energía y control de un motor paso a paso mediante Bluetooth Low Energy (BLE), almacenamiento de datos en tarjeta SD y control de tiempo con un reloj RTC.

## 📌 Características principales

- 📡 Comunicación BLE para transmitir datos de energía y recibir comandos de control.
- ⚙️ Control de un motor paso a paso mediante un interruptor físico y comandos remotos.
- 💾 Registro periódico de datos en una tarjeta SD con marca de tiempo.

## 📦 Ejecutar código

Asegúrate de tener instalado Arduino IDE y las siguientes librerías:

- `ArduinoBLE`
- `SD`
- `RTCZero`

## 🛠️ Hardware utilizado

- Arduino Nano 33 IoT
- Módulo SD CARD 
- Motor a pasos NEMA 17
- Interruptor físico

## 🧠 Funcionamiento

### Conexión BLE
- Al iniciar, el dispositivo se anuncia como `Energy`.
- Expone un servicio BLE personalizado con dos características:
  - `sensorConsu` (notificación del voltaje leído).
  - `switchCharacteristic` (control de dirección del motor).

### Motor
- Si el valor recibido por BLE es `> 0` y el interruptor está en `LOW`, el motor se mueve hacia adelante.
- Si el valor recibido es `0` y el interruptor está en `HIGH`, el motor se mueve en reversa.
- Cada movimiento realiza 400 pasos.

### Registro en SD
- Cada minuto, el sistema guarda en `datos.txt` el voltaje leído junto con la marca de tiempo actual.
