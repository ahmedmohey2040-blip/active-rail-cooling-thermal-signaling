# Active Rail Cooling and Thermal Signaling System for Railway Safety (ARCTSS)

## Project Overview

The **Active Rail Cooling and Thermal Signaling System (ARCTSS)** is an academic railway safety prototype designed to monitor rail temperature, activate an active cooling system, and provide thermal warning signals according to the detected rail temperature.

The project addresses the effect of high rail temperatures on **Continuous Welded Rail (CWR)** systems, where thermal expansion can generate compressive stresses and increase the risk of track deformation and thermal buckling, particularly in hot-climate regions.

The proposed system combines **thermal monitoring, active cooling, automatic control, and thermal signaling** into one integrated system.

---

## Project Objectives

The main objectives of the ARCTSS project are:

- Continuous monitoring of rail temperature.
- Detecting abnormal increases in rail temperature.
- Activating an automatic cooling system when predefined temperature conditions are reached.
- Reducing thermal stress and the risk of rail deformation and track buckling.
- Providing real-time thermal status through a three-color semaphore.
- Integrating railway track engineering with railway signaling concepts.
- Reducing dependence on manual temperature monitoring.
- Developing an academic prototype that can be further developed toward real railway applications.

---

## System Concept

The ARCTSS prototype operates through four main stages:

1. **Temperature Sensing**  
   A DS18B20 temperature sensor continuously measures the temperature of the rail model.

2. **Data Processing**  
   An ATmega328P microcontroller processes the temperature readings and compares them with predefined thermal thresholds.

3. **Cooling Control**  
   Relays are used to control the cooling pump and fan according to the thermal condition.

4. **Thermal Signaling**  
   A three-color semaphore provides a visual indication of the rail thermal condition.

### Thermal States

| Thermal Condition | Signal | System Response |
|---|---|---|
| Normal | 🟢 Green | Normal monitoring |
| Warning | 🟡 Yellow | Cooling response is activated |
| Critical | 🔴 Red | Full cooling and warning alarm |

---

## Main Components

The prototype consists of the following main components:

- ATmega328P Microcontroller
- DS18B20 Temperature Sensor
- Infrared Sensor
- Relay Modules
- Water Pump
- Cooling Fan
- Heating Coil
- LCD 16×2 I2C Display
- Buzzer
- Green, Yellow, and Red LEDs
- Coolant Tank
- Hoses and Cooling Channels
- Railway Rail Model
- Power Supply
- Electrical Wires and Connectors

---

## Cooling System

The prototype uses a **closed-loop cooling concept**.

The coolant is stored in a tank and circulated through cooling channels positioned along the rail model. The coolant absorbs heat from the rail and returns to the tank, while the cooling system assists in reducing the coolant temperature before continued circulation.

The cooling system consists mainly of:

- Coolant tank
- Water pump
- Cooling channels
- Hoses
- Cooling fan
- Relay-controlled operation

The prototype demonstrates the concept of active thermal regulation rather than relying only on passive heat dissipation.

---

## Temperature Monitoring

The **DS18B20 digital temperature sensor** is used to monitor the rail temperature.

### Sensor Specifications

| Parameter | Value |
|---|---|
| Operating Voltage | 3.0–5.5 V |
| Temperature Range | -55°C to +125°C |
| Accuracy | ±0.5°C |
| Resolution | 9–12 bit |
| Communication | One-Wire |

The temperature data is continuously sent to the microcontroller for processing and system control.

---

## Thermal Signaling System

The thermal semaphore provides a simple visual representation of the rail thermal condition.

- **Green:** Normal thermal condition.
- **Yellow:** Warning condition and cooling response.
- **Red:** Critical thermal condition and maximum warning.

The signaling concept demonstrates how thermal information can be integrated with railway signaling principles to provide an immediate indication of track thermal status.

---

## Control System

The control system is based on an **ATmega328P microcontroller** programmed through the Arduino development environment.

The controller:

- Reads the temperature sensor.
- Detects the thermal condition.
- Controls the cooling pump.
- Controls the cooling fan.
- Controls the heating element during testing.
- Controls the thermal semaphore.
- Activates warning buzzers.
- Displays temperature and system status on the LCD.

The final prototype uses the ATmega328P integrated into a custom PCB instead of relying on a complete Arduino UNO board.

---

## Prototype Design

The academic model consists of a metallic rail model mounted on a stable base.

Cooling channels are installed along the rail model and connected to the coolant circulation system. Temperature and infrared sensors are positioned to monitor the system during operation.

A heating element is used to simulate high-temperature conditions during testing.

The prototype integrates the mechanical, thermal, electrical, and control subsystems into one experimental model.

---

## Real-System Concept

The prototype represents an academic model of a potential industrial railway thermal safety system.

For a real railway application, the proposed concept can be developed using:

- Industrial cooling channels.
- Heavy-duty removable clamps.
- Industrial pumps.
- Cooling plants and heat exchangers.
- Distributed rail temperature sensors.
- Industrial PLC-based control systems.
- Railway signaling integration.
- Centralized monitoring and communication systems.

The real-system concept is designed to be compatible with railway maintenance activities by using removable cooling modules that can be detached when required for maintenance operations and reinstalled afterward.

---

## Railway Safety Application

High rail temperatures can cause thermal expansion in continuously welded rails. Because rail movement is restricted by the track structure and fastening system, thermal expansion can generate compressive stresses.

If track resistance is insufficient, excessive thermal stress may contribute to:

- Rail deformation
- Track misalignment
- Lateral buckling
- Loss of track stability
- Operational disruption

The ARCTSS concept aims to address this problem through **continuous monitoring, active cooling, and thermal warning**.

---

## Project Workflow

```text
Rail Temperature
       ↓
Temperature Sensor
       ↓
ATmega328P Controller
       ↓
Thermal Condition Detection
       ↓
 ┌───────────────┬────────────────┬────────────────┐
 │    Normal     │    Warning     │    Critical    │
 │    Green      │     Yellow     │      Red       │
 │               │                │                │
 │ Monitoring    │ Cooling ON     │ Full Cooling   │
 │               │ Warning        │ Alarm          │
 └───────────────┴────────────────┴────────────────┘
Hardware Connections

Main prototype connections include:

Component	Microcontroller Pin	Function
Green LED	D8	Normal condition
Yellow LED	D7	Warning condition
Red LED	D9	Critical condition
Buzzer 1	D5	Warning alarm
Buzzer 2	D6	Danger alarm
DS18B20	D2	Temperature measurement
IR Sensor	D3	Object/train detection
Pump Relay	D10	Pump control
Fan Relay	D11	Fan control
Heater Relay	D12	Heating control
LCD SDA	A4	I2C Data
LCD SCL	A5	I2C Clock
Testing

The prototype was tested under controlled thermal conditions using a heating element to simulate rail temperature increase.

The testing process focused on:

Temperature measurement.
Sensor response.
Cooling system activation.
Pump operation.
Fan operation.
Thermal semaphore response.
Buzzer activation.
LCD status display.
Overall interaction between the system components.

The prototype demonstrates the intended integration between thermal monitoring, cooling control, and railway thermal signaling.

Economic Evaluation

The estimated prototype cost is approximately:

4,115 EGP

The cost includes the main electronic, mechanical, cooling, and signaling components required to construct the academic model.

The economic evaluation is intended for the prototype implementation and does not represent the cost of an industrial railway deployment.

Future Development

Future development of the ARCTSS concept may include:

Industrial-grade temperature sensors.
Distributed temperature monitoring along railway sections.
PLC-based industrial control.
Improved cooling channels and heat exchangers.
Remote monitoring and data logging.
IoT communication.
Predictive thermal analysis.
Integration with centralized railway traffic control.
Integration with modern railway signaling and train control systems.
Testing on different track geometries and environmental conditions.
Development of a larger-scale field prototype.
Project Information

Institution:
Higher Institute of Transport Technology (HITT)

Department:
Railways Signals Control Systems Technology

Project Title:
Active Rail Cooling and Thermal Signaling System for Railway Safety

Abbreviation:
ARCTSS

Project Year:
2026

Project Team
Ahmed Mohamed Mohey El-Din
Khaled Mahmoud Ali Sahsah
Ahmed Saber Basher Mohamed
Ahmed Ibrahim Hussien Ahmed
Mahmoud Salah Farag Seyam
Supervisors
Prof. Dr. Taha Abdel Mohimen
Professor of Physics and Engineering Mathematics, Faculty of Electronic Engineering, Menoufia University.
Eng. Nagi Mohamed Elsayed
Signals Engineer, Egyptian National Railways Authority (ENR).
Eng. Fawzy Zaki Embaby
Railway Track Engineer, Egyptian National Railways Authority (ENR).
Dr. Fares Abdel-Salam
Director General, Higher Institute of Transport Technology.
Project Type

This project is an academic graduation prototype developed to demonstrate the concept of active rail cooling and thermal signaling for railway safety.

The prototype is intended for educational and experimental purposes and provides a foundation for future engineering development and real-world railway applications.

Author

Ahmed Mohamed Mohey El-Din

Railways Signals Control Systems Technology
Higher Institute of Transport Technology (HITT)
