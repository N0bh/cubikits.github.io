---
layout: project
title: Passive Buzzer Module
---

# Description

The buzzer used in this project is a passive buzzer. It doesn't generate sound on its own but requires external pulse signals to operate. Varying the frequency of these pulses produces different tones. With an Arduino, you can easily program melodies, making it a fun and straightforward way to create music.

# Specification

- Working voltage: 3.3-5v
- Interface type: digital
- Size: 30*20mm
- Weight: 4g

# Hardware Setup

|     Module    |   Lorfi L   |
|---------------|-------------|
| Signal        | PB5         |
| VCC           | 5V          |
| GND           | GND         |

Connect the Signal pin of sensor to Digital Input of the Lorfi board, negative pin to GND port, positive pin to 5V port.

<p style="text-align: center;">
  <img src="\assets\Images\LORFI_Components\Lorfi-L_Modules\8.png" alt="Centered Image" width="900" />
</p>

#### Using directly Lorfi-L

You can find complete <a href="/docs/Hardware_Guide.html">Lorfi-L IO pinout here</a>.

*MIGHT NEED TO ADD NOTES ON POWER REQUIREMENTS, PIN CONSIDERATIONS, ETC.*

#### Using Lorfi Interface board

You can find complete guide for <a href="/docs/Hardware_Guide.html">Lorfi Interface here</a>.

*MIGHT NEED TO ADD NOTES ON POWER REQUIREMENTS, PIN CONSIDERATIONS, ETC.*

## Software Setup

Lorfi-L is based on RAK3172 LoRaWAN module. This must be added to Arduino IDE.

Here's the guide on <a href="/docs/Software_Guide.html">how to add RAK3172 on your Arduino IDE</a>.

Once RAK3172 is added, you can now select it from the board selection.

<p style="text-align: center;">
  <img src="\assets\Images\LORFI_Components\Software-Guide_Images\Software_Guide4.png" alt="Centered Image" width="900" />
</p>

If failing, test the UART connection by checking the version. Use `AT+VER=?` command with baud rate of 115200. In case of MCU brick, revive the RAK3172 by following this [guide from RAKwireless](https://learn.rakwireless.com/hc/en-us/articles/26687606549911-How-To-Guide-STM32CubeProgrammer-for-RAK-Modules).

## Sample Code:
```c
#define LED PB5  //set digital IO pin of the buzzer
void setup() {
  pinMode(buzzer, OUTPUT);  // set digital IO pin pattern, OUTPUT to be output
}
void loop() {
  unsigned char i, j;  //define variable
  while (1) {
    for (i = 0; i < 80; i++)  // output a frequency sound
    {
      digitalWrite(buzzer, HIGH);  // sound
      delay(1);                    //delay1ms
      digitalWrite(buzzer, LOW);   //not sound
      delay(1);                    //ms delay
    }
    for (i = 0; i < 100; i++)  // output a frequency sound
    {
      digitalWrite(buzzer, HIGH);  // sound
      digitalWrite(buzzer, LOW);   //not sound
      delay(2);                    //2ms delay
    }
  }
}
```

## Expected Output

Once the code is succesfully uploaded you must see the following output or behavior.

*ADD HERE IMAGE OF SUCCESSFUL UPLOAD*

*ADD HERE IMAGE OF EXPECTED OUTPUT IN SERIAL IF ANY*

## FAQ
