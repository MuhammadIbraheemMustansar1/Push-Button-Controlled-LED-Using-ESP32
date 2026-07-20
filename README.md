# Push-Button-Controlled-LED-Using-ESP32
Built a push button-controlled LED system using ESP32. The LED turns ON when the button is pressed and OFF when released using INPUT_PULLUP, digitalRead(), and digitalWrite(). Demonstrates GPIO input/output and switch interfacing.
# Objective
To control an LED using a push button.

1. Press the button → LED turns ON.
2. Release the button → LED turns OFF.
# Components Required
1. ESP32 DevKit V1
2. Breadboard
3. Push Button
4. Red LED
5. 220 Ω resistor
6. Jumper wires
7. USB cable
# Circuit Connections
1. LED
2. GPIO 2 → 220 Ω resistor → LED (+)
3. LED (−) → GND
4. Push Button
5. One side → GPIO 4
6. Opposite side → GND

The ESP32 uses its internal pull-up resistor, so no external resistor is required.
# Images
<img width="1600" height="1200" alt="WhatsApp Image 2026-07-19 at 9 24 12 PM" src="https://github.com/user-attachments/assets/3bc76e6f-d90a-460e-a325-c84c420dadc3" />
<img width="719" height="403" alt="WhatsApp Image 2026-07-19 at 9 26 01 PM" src="https://github.com/user-attachments/assets/72f03991-57fc-46b5-8cfa-c0b12b965f27" />


# Program
void setup() {
  pinMode(2, OUTPUT);
  pinMode(4, INPUT_PULLUP);
}

void loop() {

  if (digitalRead(4) == LOW) {
    digitalWrite(2, HIGH);
  }
  else {
    digitalWrite(2, LOW);
  }

}
# Working Principle
1. GPIO 2 is configured as an output.
2. GPIO 4 is configured as an input with the internal pull-up resistor enabled.
3. When the button is not pressed, GPIO 4 remains at HIGH (3.3 V) because of the internal pull-up resistor.
4. When the button is pressed, GPIO 4 is connected to GND, so it becomes LOW (0 V).
5. The ESP32 continuously reads GPIO 4.
6. If GPIO 4 is LOW, the LED is turned ON.
7. If GPIO 4 is HIGH, the LED is turned OFF.
# New Functions Learned
pinMode()

Configures the mode of a GPIO pin.

# Example:

pinMode(2, OUTPUT);
digitalRead()

# Reads the current state of a digital input pin.

Returns:

HIGH
LOW

# Example:

digitalRead(4);
digitalWrite()

# Sets a digital output pin to HIGH or LOW.

# Example:

digitalWrite(2, HIGH);
INPUT_PULLUP

INPUT_PULLUP enables the ESP32's internal pull-up resistor.

# Purpose:

Prevents the input pin from floating.
Keeps the input at HIGH when the button is not pressed.
Limits current when the button is pressed.
Logic Table
Button State	GPIO 4	LED
Released	HIGH	OFF
Pressed	LOW	ON
Concepts Learned
Digital Input
Digital Output
Push Button
Internal Pull-up Resistor
HIGH and LOW logic levels
Reading input using digitalRead()
Controlling output using digitalWrite()
Decision making using if...else
# Result

The push button successfully controls the LED:

Pressing the button turns the LED ON.
Releasing the button turns the LED OFF.
