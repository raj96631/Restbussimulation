# Rest Bus Simulation for Automotive ECUs (Dummy Project)

This dummy project simulates a Rest Bus environment using Vector CANoe and CAPL. It's based on a message configuration provided in `Message_Config.xlsx`.

##  Features
- Simulates automotive ECUs (BCM, GWM, IPC, etc.)
- Handles:
  - Event-based messages
  - Periodic messages
  - Event + Periodic hybrid types
- CAPL automation for message transmission
- DBC placeholder file for signal definitions

##  Files Included
- `Message_Config.xlsx`: CAN message and signal definitions
- `capl/rest_bus_simulation.can`: CANoe CAPL script for simulation
- `dbc/custom_simulation.dbc`: Placeholder DBC file (not functional)
- `panels/custom_panel.cfg`: Panel UI config (optional/dummy)

##  Sample Message Details
| MSG Name          | MSG ID | Type            | DLC | Cycle Time | Signals Count |
|------------------|--------|-----------------|-----|-------------|----------------|
| ABS_Msg_Data_CAN | 0x413  | Event Periodic  |  8  | 1500 ms     | 4              |

### Signals:
- `HMI_MID_Sgnl_1_Rq` (4 bits, Unsigned, SED)
- `HMI_MID_Sgnl_2_Rq` (4 bits, Unsigned, SED)
- `HMI_MID_Sgnl_3_Rq` (4 bits, Unsigned, SED)
- `MID_Data_Rq`       (8 bits, Unsigned, range)

##  Tools Used
- Vector CANoe
- CAPL (CAN Access Programming Language)

> ⚠ This is a **dummy project** meant for GitHub portfolios or interview demonstration only.
