
#  Mobility Management

## Motor Overview

### Selected motor
・SPIKE Prime M angular motor

<img src="https://github.com/user-attachments/assets/7f43d8ca-7428-43b3-a3ea-33a17a66cb67" width="60%">

・SPIKE Prime L angular motor

<img src="https://github.com/user-attachments/assets/a2222927-08bf-4b27-9904-c22923fee463" width="60%">

### Specification of motor
・SPIKE Prime M angular motor
| part | performance |
| ------------- | ------------- |
| Output voltage | 5～9[V] |
| Rotation sensor  | one revolution:360count  |
| Wire  | 250mm |
| No Load |Torque: 0 Ncm <br> Speed: 185 RPM ± 15% <br> Current Consumption: 110 mA ± 15%|
| Maximum Efficiency | Torque: 3.5 Ncm <br> Speed: 135 RPM ± 15% <br> Current Consumption: 280 mA ± 15% |
| Stall | Torque: 18 Ncm <br> Speed: 0 RPM <br> Current Consumption: 800 mA ± 15% |

### Specification of motor
・SPIKE Prime L angular motor
| part | performance |
| ------------- | ------------- |
| Output voltage | 5～9[V] |
| Rotation sensor  | one revolution:360count  |
| Wire  | 250mm |
| No Load |Torque: 0 Ncm <br> Speed: 175 RPM ± 15% <br> Current Consumption: 135 mA ± 15%|
| Maximum Efficiency | Torque: 8 Ncm <br> Speed: 135 RPM ± 15% <br> Current Consumption: 430 mA ± 15% |
| Stall | Torque: 25 Ncm <br> Speed: 0 RPM <br> Current Consumption: 1400 mA ± 15% |

### Reasons for choice
Easy to assemble and reassemble, making it suitable for fine-tuning of robots.In addition, stable driving is achieved by using the M motor for fast response and the L motor for high output and high torque for both the front and rear wheels.It is a reliable and proven motor that was used by the winning team of the WRO 2023 World Championships.

### Implementation Methods
The front wheels use M motors for instant steering control, while the rear wheels use high-power L motors to shorten the time.

---

## Operation of front and rear wheels
The steering mechanism of the front wheels is controlled by a single axis to increase the drive range and reduce the width between wheels to accommodate sudden steering changes.

<img src="https://github.com/user-attachments/assets/958800dc-e9b3-40af-af6e-9ccca911bb80" width="40%"> <img src="https://github.com/user-attachments/assets/bd08f922-3c61-40c0-bbdf-5b9dbd5a63fd" width="40%">

For a detailed explanation of the design, please click [here](https://github.com/Hart1109/TeikyoRobostar-WRO-FE-2024/blob/main/body%20information/Steering%20wheel%20assembly.pptx).

