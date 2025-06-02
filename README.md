# Licencias de Open Source

## ¿Qué es una licencia Open Source? 

Una licencia open source es un documento legal que regula los términos bajo los cuales se puede usar, modificar y distribuir un software. Sin una licencia explícita, el software por defecto tiene todos los derechos reservados, lo que significa que los usuarios no pueden legalmente reutilizar el código, modificarlo ni distribuirlo, aunque el código fuente esté públicamente visible (por ejemplo, en GitHub). 

Las licencias open source buscan fomentar la colaboración, la innovación y la transparencia, estableciendo reglas claras para: 
• Garantizar que el software esté disponible para todos. 
• Proteger los derechos de los creadores originales. 
• Evitar conflictos legales entre desarrolladores, empresas y comunidades. 
• El movimiento del software libre, iniciado por Richard Stallman con la Free 

Software Foundation (FSF) en los años 80, y posteriormente el concepto de open source impulsado por la Open Source Initiative (OSI), han dado lugar a una ecosistema legal y filosófico robusto que sustenta miles de proyectos en todo el mundo. Una licencia open source, según la Open Source Initiative (OSI), debe permitir: 
• Uso libre del software 
• Acceso al código fuente 
• Distribución libre 
• Creación de trabajos derivados 
• No discriminación de personas o grupos 
• Neutralidad en cuanto a tecnología y campos de uso

## Tipos de licencias de código abierto

Las licencias open source se clasifican generalmente en 3 tipos principales según su nivel de restricciones: 
1. Permisivas: Permiten gran libertad a los usuarios: pueden copiar, modificar y redistribuir el código, incluso integrándolo en software propietario, siempre y cuando se mantengan los avisos de derechos de autor. 
2. Copyleft débil: Permiten combinar el código con software propietario, pero los archivos modificados del software licenciado deben mantenerse como open source. 
3. Copyleft fuerte: Obligan a que todo trabajo derivado (incluso si se combina con otro software) también sea distribuido bajo la misma licencia. Se utiliza para asegurar que el software y todas sus derivaciones permanezcan libres.

Se puede checar la Tabla comparativa de las Licencias de Open Source y verificar que la Apache y MIT License son las más aptas de utilizar para llevar a cabo el trabajo.

# Burn the Bootloader en Arduino Nano 33 IoT
El bootloader (cargador de arranque) es un componente esencial en cualquier sistema computacional o embebido. Es el primer software que se ejecuta cuando se enciende un dispositivo y su función principal es inicializar el hardware y cargar el sistema operativo o el firmware de la aplicación desde una memoria no volátil a la memoria RAM.
Para quemar, flashear o programar el Bootloader en el Arduino Nano 33 IoT se siguen los pasos y recomendaciones descritos en la documentación [Procedimiento para Programar el Bootloader Arduino Nano 33 IoT](https://github.com/nicolbrigit/Persiana-solar/blob/main/Procedimiento%20para%20programar%20el%20Bootolader%20en%20Arduino%20Nano%2033%20IoT.pdf)

# Prueba de concepto Energy - Monitoreo y control de motor via BLE

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
El código es "new_prueba_concepto"

## 🛠️ Hardware utilizado

- [Diagrma Eléctrico](https://github.com/nicolbrigit/Persiana-solar/blob/main/Diagrama%20electrico%20new_prueba_concepto%20.png)
- [Diagrama físico](https://github.com/nicolbrigit/Persiana-solar/blob/main/Diagrama%20f%C3%ADsico%20new_prueba_concepto.png)
- [Diagrama a bloques]() 

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

# Recomendaciones y prupuestas de mejora
A partir de los resultados obtenidos, así como de las observaciones realizadas durante el 
desarrollo del proyecto “Construcción de BSW (Software Embebido Base) en tabletas 
comunes de desarrollo para proyectos IoT”, se proponen las siguientes recomendaciones, 
orientadas a fortalecer y ampliar la utilidad del sistema en futuros desarrollos: 
1. Realizar pruebas prolongadas en tiempo real.
Se sugiere ejecutar pruebas de concepto del sistema completo (hardware y software) en 
condiciones reales durante lapsos prolongados, por ejemplo, en ciclos de 24 horas 
continuas. Esto permitirá detectar posibles fallas intermitentes, problemas de 
estabilidad o rendimiento, y ayudará a validar la confiabilidad del sistema en 
escenarios reales de uso. 
2. Agregar un módulo de reloj en tiempo real (RTC). 
Se recomienda integrar un módulo de reloj en tiempo real (RTC) como parte del 
sistema, con el fin de contar con referencias temporales precisas durante el 
almacenamiento de datos y el monitoreo de señales. Esto facilitará la trazabilidad y el 
análisis de datos recolectados por el sistema. 
3. Probar el sistema con diferentes protocolos de comunicación.
Para aumentar la versatilidad del BSW, sería útil realizar pruebas de funcionalidad 
utilizando diferentes medios de comunicación. Específicamente, se sugiere probar la 
conectividad vía Wi-Fi como alternativa al Bluetooth Low Energy (BLE), evaluando el 
89 
rendimiento, alcance y estabilidad de cada protocolo según el tipo de aplicación. 
Estas recomendaciones tienen el propósito de fortalecer la arquitectura del software embebido 
base, mejorar su confiabilidad en operación continua y ampliar sus capacidades de 
comunicación y registro, optimizando así su impacto positivo en los procesos tecnológicos de 
la empresa.
