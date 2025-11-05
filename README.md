# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
  <img width="1908" height="1080" alt="Screenshot 2025-11-05 104618" src="https://github.com/user-attachments/assets/00f83ed9-4578-46c4-8dee-dcbd12c23eb7" />


2. Click **File → New STM32 Project**.
   <img width="1918" height="1079" alt="Screenshot 2025-11-05 104806" src="https://github.com/user-attachments/assets/fb56fcd7-5999-4787-8d91-f42aa16b48bc" />
   


3. Select the **target microcontroller** or board and click **Next**.
  <img width="1919" height="1080" alt="Screenshot 2025-11-05 110232" src="https://github.com/user-attachments/assets/8dd5ddc8-90c1-4ecc-b5f0-6d4a795c4411" />



4. Name the project.
   <img width="1920" height="1080" alt="Screenshot 2025-11-05 110323" src="https://github.com/user-attachments/assets/c7d4b09f-1324-480e-ab6d-e127bf6ab8b5" />


5. The corresponding `.ioc` file will be generated automatically.
  <img width="1920" height="1080" alt="Screenshot 2025-11-05 110401" src="https://github.com/user-attachments/assets/0b62cd50-7c0d-4295-959f-d1357d8d6aff" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1920" height="1080" alt="Screenshot 2025-11-05 110435" src="https://github.com/user-attachments/assets/9a6f822e-ce59-46bb-ace4-025c17586af1" />
   <img width="1918" height="1080" alt="Screenshot 2025-11-05 110514" src="https://github.com/user-attachments/assets/4722032d-df66-485b-8503-05f4f9b37c41" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1913" height="1080" alt="Screenshot 2025-11-05 110541" src="https://github.com/user-attachments/assets/cf107e49-0536-4d37-b580-c27e2ee84fec" />

 
8. Edit the generated main program as required.
   <img width="1918" height="1079" alt="Screenshot 2025-11-05 110555" src="https://github.com/user-attachments/assets/9789ca4d-aacd-4524-ac1d-a756e48288aa" />


9. Click **Project → Build All**.
    <img width="1915" height="1077" alt="Screenshot 2025-11-05 110708" src="https://github.com/user-attachments/assets/4c15f1f4-7d2e-4a84-8efa-33319b036546" />


10. Link the **HEX file** using the post-build process.
    <img width="1920" height="1080" alt="Screenshot 2025-11-05 110917" src="https://github.com/user-attachments/assets/00ef49a2-9520-4c0a-b90d-f587a71ae27e" />


11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1920" height="1080" alt="Screenshot 2025-11-05 110751" src="https://github.com/user-attachments/assets/0f151213-fafb-4849-a3a4-f394bf190e9b" />


13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

CASE 2: LED OFF

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




