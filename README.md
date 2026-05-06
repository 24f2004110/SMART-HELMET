# 🪖 SMART HELMET: IoT-BASED SAFETY & ACCESS SYSTEM

### *Integrated Accident Detection, Alcohol Monitoring, and Physical Key-Inlet Control*

```
╔══════════════════════════════════════════════════════════════════╗
║   ███████╗███╗   ███╗ █████╗ ██████╗ ████████╗               ║
║   ██╔════╝████╗ ████║██╔══██╗██╔══██╗╚══██╔══╝               ║
║   ███████╗██╔████╔██║███████║██████╔╝   ██║                  ║
║   ╚════██║██║╚██╔╝██║██╔══██║██╔══██╗   ██║                  ║
║   ███████║██║ ╚═╝ ██║██║  ██║██║  ██║   ██║                  ║
║   ╚══════╝╚═╝     ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝   ╚═╝  v1.0            ║
╚══════════════════════════════════════════════════════════════════╝

  STATUS: [ ARMED ]  SENSORS: [ ACTIVE ]  VEHICLE: [ SECURED ]
```

---

## 🔩 SYSTEM OVERVIEW

**STABILIZER-X Smart Helmet** is an advanced safety ecosystem designed to integrate rider authentication, intoxication monitoring, and automated emergency response. The system ensures that a vehicle remains physically inaccessible unless the rider is wearing the helmet correctly and is confirmed sober.

**🚨 Emergency Response:** In the event of a crash or abnormal impact, the system instantly acquires the rider's real-time GPS location and automatically sends an emergency alert to family and predefined contacts through Telegram, ensuring rapid assistance.

**🛡️ Physical Access Barrier:** Unlike standard ignition-cut systems, this project features a mechanical lock. A servo-controlled mechanism blocks the actual key inlet (keyhole) on the vehicle, preventing the user from inserting the ignition key until all safety parameters are verified.

---

## 🧠 CORE OBJECTIVES

* **Accident Alert System:** Detects falls via an IMU and instantly sends a location-based alert to family via Telegram.
* **Physical Key Blocking:** Mechanically prevents the insertion of the ignition key using a servo-driven shutter over the key inlet.
* **Rider Verification:** Uses an IR sensor to confirm the helmet is physically worn before granting key access.
* **Intoxication Prevention:** Blocks key-inlet access if alcohol is detected in the rider's breath via an MQ-3 sensor.

---

## 🛠️ HARDWARE SPECIFICATIONS

| Component | Function | Detail |
| :--- | :--- | :--- |
| **MCU (Helmet)** | Arduino Uno/Nano | Processes sensor data and transmits safety status. |
| **MCU (Vehicle)** | ESP32 | Manages IoT alerts, GPS, and key-inlet servo control. |
| **IMU Sensor** | MPU6050 | Accelerometer/Gyroscope for accident detection. |
| **Alcohol Sensor**| MQ-3 | Detects intoxication levels in the rider's breath. |
| **Proximity Sensor**| IR Sensor | Confirms if the helmet is physically on the head. |
| **Wireless Link** | RF 433MHz Tx/Rx | Transmits safety "UNLOCK" signal from helmet to vehicle. |
| **Actuator** | Servo Motor | **Mechanically opens the physical shutter blocking the keyhole**. |

---

## 📐 SYSTEM ARCHITECTURE

```
[ HELMET UNIT (Arduino) ]             [ VEHICLE UNIT (ESP32) ]
  │                                     │
  ├─► IR Sensor (Wear Detection)        ├─► RF Receiver
  ├─► MQ-3 (Alcohol Detection)          ├─► Servo (KEY INLET SHUTTER)
  ├─► MPU6050 (Accident Sensing)        ├─► WiFi/Bluetooth Link
  └─► RF Transmitter ──(Wireless)───┐   └─► Mobile App (GPS/Telegram)
                                    ▼
                          [ SMARTPHONE INTERFACE ]
                           (MIT App Inventor App)
```

### Physical Access & Alert Flow
1.  **Sensing:** The system checks if the helmet is worn and the rider is sober.
2.  **Transmission:** A safety "GO" signal is sent via RF to the vehicle-mounted ESP32.
3.  **Mechanical Unlock:** The ESP32 rotates the **Servo Motor**, moving the physical barrier away from the keyhole.
4.  **Accident Detection:** During the ride, the MPU6050 monitors for high-impact forces.
5.  **Instant Alert:** If an accident is detected, the ESP32 fetches GPS data and sends an **instant location alert to family** via Telegram.

---

## ⚙️ SOFTWARE STACK

* **Arduino IDE:** For C++ firmware development for both MCU units.
* **MIT App Inventor:** Custom mobile application to bridge smartphone GPS data and the Telegram API.
* **Telegram Bot API:** Used by the ESP32 to push instant emergency notifications to predefined contacts.
* **Key Libraries:** `RCSwitch` (RF communication), `MPU6050` (Motion sensing), `ESP32Servo` (Access control).

---

## 📁 PROJECT STRUCTURE

```
helmet/
├── helmet_firmware/
│   └── accidentdetect.ino  
    └──E_reciver keyhole_control.ino 
├── docs/
│   ├── mit_appblock.png    ← MIT App Inventor Source
│   └── wiring_diagram.png
└── README.md
```

---

## 📜 CONCLUSION

The Smart Helmet provides a critical safety net by ensuring riders follow protocol before they can even insert their keys. By integrating **physical prevention** with **instant family alerts**, it significantly reduces the risks associated with human error and delayed accident response.

---

```
╔══════════════════════════════════════════════════════════╗
║           SMART HELMET // END OF DOCUMENTATION           ║
║    [ SYSTEM READY ] [ GPS LOCKED ] [ KEYHOLE SECURED ]   ║
╚══════════════════════════════════════════════════════════╝
```
