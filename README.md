# STM32 Power Saving Project

## Overview
This project demonstrates power saving techniques on an STM32F4 microcontroller using FreeRTOS. It was developed by Phạm Lê Ngọc Sơn to showcase power optimization strategies in embedded systems.

## Hardware Requirements
- STM32F407VG Discovery Board
- USB-to-Serial converter (for UART communication)
- Jumper wires for connections

## Project Structure
The project is organized as follows:

```
STM32_Power_Saving/
├── Core/                  # Core application code
│   ├── Inc/               # Header files
│   └── Src/               # Source files including main.c and freertos.c
├── Drivers/               # STM32 HAL and device drivers
├── Middlewares/           # FreeRTOS middleware
├── .settings/             # Project settings
├── Debug/                 # Debug artifacts
└── *.launch               # Launch configurations for debugging
```

## Key Features
1. **FreeRTOS Implementation**: Uses FreeRTOS for task management and scheduling
2. **Power Saving Mode**: Implements the `__WFI()` (Wait For Interrupt) instruction in the idle hook to reduce power consumption
3. **Dual Task System**:
   - LED Task: Toggles an LED (PD15) every second
   - UART Task: Reports the LED state via UART communication

## Power Saving Strategy
The project demonstrates power saving through:
- Using the FreeRTOS idle hook to enter low-power mode when no tasks are running
- Implementing the `__WFI()` function to put the CPU into sleep mode until an interrupt occurs
- Simple task design that minimizes CPU usage

## How to Use

### Setup
1. Connect the STM32F407 Discovery board to your computer
2. If using UART monitoring:
   - Connect PC9 to the RX pin of your USB-to-Serial converter
   - Connect PC8 to the TX pin of your USB-to-Serial converter
   - Connect GND to the GND pin of your USB-to-Serial converter

### Building the Project
1. Open the project in STM32CubeIDE
2. Build the project using the build button or press Ctrl+B
3. Flash the program to your STM32F4 board

### Monitoring
1. Open a serial terminal (e.g., PuTTY, Tera Term, or Arduino Serial Monitor)
2. Configure with baud rate 115200, 8 data bits, no parity, 1 stop bit
3. You should see messages reporting the LED state every second

## Launch Configurations
The project includes multiple launch configurations for different demonstration scenarios:
- `STM32_FreeRTOS_Led_Button.launch`: Basic LED and button functionality
- `STM32_FreeRTOS_Led_Button_IT.launch`: LED and button with interrupts
- `STM32_FreeRTOS_Task_Priority.launch`: Demonstrates task priority management
- `STM32_FreeRTOS_vTaskDelay.launch`: Shows task delay functionality

## License
This software is licensed under the BSD 3-Clause License. See the LICENSE file for details.

## Author
Phạm Lê Ngọc Sơn

## Acknowledgments
- STMicroelectronics for the STM32 HAL libraries
- FreeRTOS for the real-time operating system