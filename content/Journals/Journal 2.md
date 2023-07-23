---
title: "Journal 2"
tags:
- Journal
---

#gamedesign #graphicdesign #hardware #software 
### **Mission**:  Implementing exergaming to assist children with cerebral palsy, further enhancing their motor skills through performance and usability.
---
While we knew we wanted to focus on the development of a game to assist our patients the theoretical applications of exergaming were broad, and multiple solutions could be effective. Firstly, A decision matrix assisted us with choosing a method of approach to tackle our mission statement.

| Method                             | Cost (1-5) | Ease of Use (1-5) | Effectiveness (1-5) | Patient Engagement (1-5) | Accessibility (1-5) | Total |
|------------------------------------|:----------:|:-----------------:|:-------------------:|:------------------------:|:-------------------:|:-----:|
| Virtual Reality Therapy Games      |     3      |         4         |          5          |             5            |          3          |   20  |
| Motion-Controlled Games            |     4      |         5         |          4          |             4            |          4          |   21  |
| Cognitive Improvement Games        |     5      |         4         |          4          |             3            |          4          |   20   |
| Physical Therapy Apps              |     4      |         4         |          3          |             4            |          5          |   20  |
*decision matrix*

Realizing that motion controlled games were the most effective solution in our approach of exergaming, we knew that we needed an interface between reality and software that would allow for the user to stimulate a range of muscles, further improving fine-motor and coordination skills. 

### Hardware
Motivated by our own passion for virtual games, We decided to use a shape that would be similar to the Quest 2's controllers, since it has an ergonomic design for prolonged use. 

![measuring](images/J1/measuring.jpg)
*Measuring Controller*

Furthermore, we began to design a version of our controller on Autodesk, with a strong emphasis on organic and round shape. We also decided on small features such as a wrist strap addition to improve the quality and safety of use. The shape was kept simple in order to make it easier to fit the larger prototype electronic components. Our first model:

![[images/J1/caddingg.jpg]]
*Autodesk Fusion360: Modeling the Controller*

The IMU we chose for this project was the MPU6050 since it struck a good balance between features, accuracy, and price. It has the ability to sense acceleration as well as rotation in six axis, affording us creative freedom in designing our therapy game. 

![[images/J1/final imu.gif]]
*3 Axis Accelerometer Gyroscope Module 6 DOF 6-axis Accelerometer*

After gaining a rough idea of the final controller, we decided to start designing the internal specs. We began soldering and working on the internal hardware of our device, specifically the integration of the inertia measurement unit.

![soldering](images/J1/soldering.gif)
*Soldering the inertial measurement unit (IMU)*

The inertia measurement unit (IMU) will be a key factor in assisting the hand-eye-coordination of our patients. This will give us the ability to sense motion, and would be a key component in the exergaming interaction.

For our first prototype, we decided to the the Arduino Uno R3, which allowed us to easily prototype our first iteration of the circuit. However, it comes with the drawback of missing the ability to USB output which limits it's use to just serial outputs. 

![[images/J2/mcus.jpg]]
*Arduino Uni, Metro Mini, Pi Pico, Pro Micro*


![[images/J2/imutest.gif]]
*IMU testing with serial monitor*

### Software
In order to test the sensors functionality, we used the Adafruits MPU6050 library create a test program.
> [**IMU Test Code Github**](https://github.com/SihoChoii/ProjectPalsy/blob/main/Software/v1/main/main.ino)
```cpp
#include <Adafruit_MPU6050.h>
#include <Adafruit_Sensor.h>
#include <Wire.h>

Adafruit_MPU6050 mpu;

void setup(void) {
  Serial.begin(115200);
  while (!Serial)
    delay(10); // will pause Zero, Leonardo, etc until serial console opens

  Serial.println("Adafruit MPU6050 test!");

  // Try to initialize!
  if (!mpu.begin()) {
    Serial.println("Failed to find MPU6050 chip");
    while (1) {
      delay(10);
    }
  }
```
The test program reads the data off the IMU and prints values into the serial interface.

### Game Design
While brainstorming ideas for the game, we had to keep in mind several criteria, including the constraints of the IMU. While we initially took a more motion based approach to our game, we realized that the IMU did not have the ability to capture precise 3D motion. However, due to its gyroscope sensing capabilities we decided to focus on the rotational aspect on our game, which would still help train motor control.

Since rotation based movements mostly involve a shift in perception, we knew that it was necessary to make the game in 3D. 

![[images/J2/monkeyclip.gif]]
*Super Monkey Ball Gameplay*

Based on the constraints of the IMU and our desire to take a more rotation-based approach, the initial inspiration for our game was Super Monkey Ball.  While the game seems mechanically demanding, our approach would optimize gameplay to be slower and focus more on precise controls over Super Monkey Ball's rapid and speed based gameplay. This would allow for our game to both have an easier learning curve and build up on difficulty in levels, allowing for the steady growth in motor skills for our players. 

In order to make a game that is both visually appealing and within our criteria, we decided to use the industry standard game engine Unreal. The endless powerful tools that Unreal Engine has gives us creative freedom with our game design. 

![[images/J2/unreal.gif]]
*Unreal Engine 5.2 Demo*

The properties of physics that our game will be using are demonstrated here:

![[images/J2/Sequence 01.gif]]
*Ball Physics Demo*

Next Journal [[journals/Journal 3|Journal 3]]