# Rest Bus Simulation for Automotive ECUs (Dummy Project)

This dummy project simulates a Rest Bus environment using Vector CANoe and CAPL. It's based on message configuration provided in `Message_Config.xlsx`.

## Features
- Simulates various automotive ECUs (like BCM, GWM, IPC)
- CAPL script supports:
  - Event-based messages
  - Periodic messages
  - Event + Periodic hybrid types
- DBC placeholder for signal definition

## Files
- `Message_Config.xlsx`: Signal, message type, and signal properties
- `capl/rest_bus_simulation.can`: CAPL implementation
- `dbc/custom_simulation.dbc`: Placeholder (not functional in dummy repo)
- `panels/custom_panel.cfg`: Placeholder for GUI

## Message Types Covered
| MSG Name       | MSG ID | Msg Type       | DLC | Signals Count |
|----------------|--------|----------------|-----|----------------|
| ABS_Msg_Data_CAN | 0x413 | Event Periodic |  8  |      4         |

## Tools Used
- Vector CANoe
- CAPL (CAN Access Programming Language)

> 🧪 Dummy project for portfolio/demo purposes. No actual vehicle data.
