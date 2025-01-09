

# **Touch Sensor Controlled Fan and LED** 🌟  

This repository demonstrates a simple project that uses a touch sensor to control a fan and an LED using an ESP32 microcontroller. The fan and LED turn on or off based on the touch sensor's value.

---

## **✨ Features**  

- **Touch Sensor Integration**  
  - Uses the ESP32's built-in touch sensor for detecting touch inputs.  

- **Device Control**  
  - Controls a fan and LED based on the touch sensor's threshold value.  

- **Serial Monitoring**  
  - Outputs real-time sensor readings and device status to the Serial Monitor for debugging and monitoring.  

---

## **🔧 Hardware Components**  

- **ESP32** microcontroller  
- **Touch sensor** (or use ESP32's built-in touch pins)  
- **LED**  
- **Fan** (low-power DC fan or motor driver-controlled fan)  
- Resistors (appropriate value for the LED and other components)  
- Jumper wires  
- Breadboard (optional)  
- Power supply (e.g., USB cable, battery pack)  

---

## **🛠 Software Requirements**  

- **Arduino IDE** (for coding and uploading to ESP32)  
- **ESP32 Board Libraries** (install via Arduino IDE Board Manager)  

---

## **🔌 Circuit Connections**  

- **Touch Sensor**: Connect to ESP32's GPIO14 (or any available touch pin).  
- **Fan**: Connect to GPIO12 (use a driver circuit if required).  
- **LED**: Connect to GPIO13 with a current-limiting resistor.  
- **Power Supply**: Power the ESP32 via USB or an appropriate external power source.  

---

## **⚙️ Configuration**  

1. Install the **ESP32 board library** in the Arduino IDE.  
2. Connect the hardware components as described above.  
3. Open the `TouchSensor_Fan_LED.ino` file in Arduino IDE.  

4. Adjust the **`threshold` value** in the code to match your sensor's sensitivity:  
   ```cpp
   const int threshold = 20; // Adjust based on your environment
   ```  
5. Upload the code to your ESP32 board using the Arduino IDE.  

---

## **🚀 Usage Instructions**  

1. Power up the ESP32 and open the Serial Monitor in the Arduino IDE.  
2. Touch the sensor to turn the fan and LED **on**.  
3. Release the sensor to turn the fan and LED **off**.  
4. Monitor the touch sensor readings and device status in the Serial Monitor.  

---

## **💡 Code Overview**  

Here’s the core logic of the project:  

```cpp
// Define pin numbers
const int touchPin = 14; 
const int fan = 12;
const int led = 13;

const int threshold = 20; // Adjust based on environment
int touchValue; // Variable to store touch sensor readings

void setup() {
  Serial.begin(115200);
  delay(1000);
  pinMode(fan, OUTPUT);  
  pinMode(led, OUTPUT);
}

void loop() {
  touchValue = touchRead(touchPin); 
  Serial.print(touchValue);

  if (touchValue < threshold) { // If touch detected
    digitalWrite(fan, HIGH);
    digitalWrite(led, HIGH);
    Serial.println(" - FAN on");
  } else { // If no touch detected
    digitalWrite(fan, LOW);
    digitalWrite(led, LOW);
    Serial.println(" - FAN off");
  }
  delay(100);
}
```  

---

## **📜 License**  

This project is licensed under the **[MIT License](LICENSE)**. Feel free to use and modify it for your own projects.  

---

## **💬 Feedback**  

If you have any suggestions or issues, feel free to open an **Issue** or submit a **Pull Request**.  

---

