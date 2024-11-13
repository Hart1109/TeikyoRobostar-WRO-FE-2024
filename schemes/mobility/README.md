
#  Mobility Management

## Motor Overview

### Selected motor
・SPIKE Prime L angular motor

<img src="https://github.com/user-attachments/assets/a2222927-08bf-4b27-9904-c22923fee463" width="60%">

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
Easy to assemble and reassemble, making it suitable for fine-tuning of robots.In addition, the L motor for high output and high torque for both the front and rear wheels. It is a reliable and proven motor that was used by the winning team of tha WRO 2023 World Championships.

### Implementation Methods
The use of high-torque motors for the front and rear wheels is expected to shorten the competition time.

---
## Brief explanation of car body structure
The base of the robot is designed around the LEGO Education Spike Prime, and the robot is connected to a Raspberry Pi4, ultrasonic sensor, camera, cooling fan, mobile battery, and battery box.In addition, the 3D model was used to fix the camera to prevent image distortion while the robot is running, and two ultrasonic sensors were installed on either side of the robot to keep it parallel to the wall at all times.



---
## Front wheel operation
The steering mechanism of the front wheels is controlled by a single axis to increase the drive range and reduce the width between wheels to accommodate sudden steering changes.

<img src="https://github.com/user-attachments/assets/958800dc-e9b3-40af-af6e-9ccca911bb80" width="40%"> <img src="https://github.com/user-attachments/assets/bd08f922-3c61-40c0-bbdf-5b9dbd5a63fd" width="40%">

For a detailed explanation of the design, please click [here](https://github.com/Hart1109/TeikyoRobostar-WRO-FE-2024/blob/main/body%20information/Steering%20wheel%20assembly.pptx).

## Rear wheel operation

Differential gears are used for the rear wheel drive mechanism. The function of this component is to allow for the speed difference between the inner and outer wheels and distribute the output to both wheels, sending more power to the less loaded tire.

<img src="https://github.com/user-attachments/assets/283928fe-7b5d-4fbe-aee9-ac663344da60" width="40%"> <img src="https://github.com/user-attachments/assets/86642ce5-f85e-44c9-b939-74db68aa2e1c" width="40%">

This mechanism enables smooth obstacle avoidance and cornering.

---

## 3Dmodels（camera mount）

<img src="https://github.com/user-attachments/assets/9047ef77-e4df-469d-b5cf-bab34d28aab1" width="40%"> <img src="https://github.com/user-attachments/assets/42b3b964-5741-4c37-821a-ea41e05218da" width="32.3%">

This component is used to secure the Raspberry Pi Camera.
 
<img src="https://github.com/user-attachments/assets/01e89ff1-d887-44af-b72c-defe6bc9d7c9" width="40%"> <img src="https://github.com/user-attachments/assets/b71c8bf3-c8c7-4383-b966-d268f1d41ea7" width="40%">

For the design, detailed holes were created to facilitate heat exhaust. In addition, the camera's image can be fine-tuned by expanding the range of motion.

