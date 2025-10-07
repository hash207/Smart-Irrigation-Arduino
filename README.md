# Smart-Irrigation-Arduino

## Overview

The Smart Irrigation system is an IoT-based project designed to monitor soil moisture levels and transmit data wirelessly using MQTT. It consists of two main components:

1. **Node_YL69**: Responsible for connecting to WiFi, publishing soil moisture data to an MQTT broker, and handling MQTT communication.
2. **YL69**: Reads soil moisture data using the YL-69 sensor and displays it on an LCD screen.

## Features

- **Soil Moisture Monitoring**: Uses the YL-69 sensor to measure soil moisture levels.
- **MQTT Communication**: Publishes soil moisture data to an MQTT broker for remote monitoring.
- **LCD Display**: Displays real-time soil moisture readings on a 16x2 LCD screen.
- **WiFi Connectivity**: Connects to a WiFi network for seamless data transmission.

## Components

- **YL-69 Soil Moisture Sensor**
- **ESP8266 WiFi Module**
- **16x2 LCD Display**
- **Arduino Board**
- **MQTT Broker** (e.g., `broker.emqx.io`)

## How It Works

### Node_YL69

1. Connects to a WiFi network using the provided SSID and password.
2. Publishes soil moisture data to the MQTT topic `hash/YL-69`.
3. Subscribes to the topic `HashESP1` for receiving messages (currently unused in the code).

### YL69

1. Reads analog data from the YL-69 sensor connected to pin `A0`.
2. Displays the soil moisture value on the LCD screen.
3. Sends the data to the serial port for transmission to the Node_YL69 component.

## Setup Instructions

1. **Hardware Connections**:
   - Connect the YL-69 sensor to the Arduino's analog pin `A0`.
   - Connect the LCD display to the specified pins (`RS=12`, `En=11`, `D4=5`, `D5=4`, `D6=3`, `D7=2`).
   - Connect the ESP8266 module to the Arduino for WiFi and MQTT communication.

2. **Software Configuration**:
   - Update the WiFi credentials (`ssid` and `password`) in `Node_YL69.ino`.
   - Ensure the MQTT broker address (`mqtt_server`) and port (`mqtt_port`) are correct.

3. **Upload Code**:
   - Upload `Node_YL69.ino` to the ESP8266 module.
   - Upload `YL69.ino` to the Arduino board.

4. **Run the System**:
   - Power on the components.
   - Monitor the soil moisture data on the LCD and via the MQTT broker.

## Topics Used

- **Publish**: `hash/YL-69` (soil moisture data)
- **Subscribe**: `HashESP1` (currently unused)

## Dependencies

- `ESP8266WiFi` library
- `PubSubClient` library
- `LiquidCrystal` library
- `SoftwareSerial` library

## Future Improvements

- Add functionality to control irrigation based on soil moisture levels.
- Implement bidirectional communication for remote control via MQTT.
- Enhance the user interface on the LCD display.

## License

This project is open-source and available for educational purposes.
