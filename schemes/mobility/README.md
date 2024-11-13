
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
The base of the robot is designed around the LEGO Education Spike Prime, and the robot is connected to a Raspberry Pi4, ultrasonic sensor, camera, cooling fan, and battery.In addition, the 3D model was used to fix the camera to prevent image distortion while the robot is running, and two ultrasonic sensors were installed on either side of the robot to keep it parallel to the wall at all times.



---
## Front wheel operation
Increasing the distance between the wheels of the vehicle has the advantage of making the steering more agile, allowing for fine angle adjustment and easier corner turning. For rough control of the wheels, the angle of the wheels is changed by turning the motor.

<img src="https://github.com/user-attachments/assets/6f9f1256-ed30-45a7-9028-a625afa71738" width="80%">
<img src="https://github.com/user-attachments/assets/69ac39ab-4336-4025-8576-68c0d6a789da" width="80%">


For a detailed explanation of the design, please click [here](https://github.com/Hart1109/TeikyoRobostar-WRO-FE-2024/blob/main/body%20information/Steering%20wheel%20assembly.pdf).

## Rear wheel operation

Differential gears are used for the rear wheel drive mechanism. The function of this component is to allow for the speed difference between the inner and outer wheels and distribute the output to both wheels, sending more power to the less loaded tire.

<img src="https://github.com/user-attachments/assets/160e2bfe-47aa-4d1a-8a16-add7da2ee733" width="80%">


This mechanism enables smooth obstacle avoidance and cornering.

---

## 3Dmodels（camera mount）

<img src="https://github.com/user-attachments/assets/0a22118f-7ee8-48ca-98de-bd604f6a1db9" width="80%">

This component is used to secure the Raspberry Pi Camera.
