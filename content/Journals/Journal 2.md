[[2023-06-14]] - [[2023-06-28]]

### Branding
We started our brainstorming ideas for our [[Branding]].

As two high-schoolers looking to brand their passion project, we had multiple criteria for the aesthetic of our brand. We decided on Project Palsy since it was simple and reflected our goals at their core motives. Along with this, we chose a hand aesthetic for all of our logos.
![[Test.canvas|Test]]

Some ideas:

![[logo3.png | 340]]![[logo4alt.png | 340]]
![[logo2.png | 340]] ![[logo1.png | 340]]



### Hardware

The IMU we chose for this project was the MPU6050 since it struck a good balance between features, accuracy, and price. It has the ability to sense acceleration as well as rotation in six axis, affording us creative freedom in designing our therapy game. 

![[mpu6050.png]]
*3 Axis Accelerometer Gyroscope Module 6 DOF 6-axis Accelerometer*

For our first prototype, we decided to the the Arduino Uno R3, which allowed us to easily prototype our first iteration of the circuit. However, it comes with the drawback of missing the ability to USB output which limits it's use to just serial outputs. 

![[mcus.jpg]]
*Arduino Uni, Metro Mini, Pi Pico, Pro Micro*


![[imutest.gif]]
*IMU testing with serial monitor*

### Software
In order to test the sensors functionality, we used the Adafruits MPU6050 library create a test program.
> [IMU Test Code Github](https://github.com/SihoChoii/ProjectPalsy/blob/main/Software/v1/main/main.ino)
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

![[monkeyclip.gif]]
*Super Monkey Ball Gameplay*

Based on the constraints of the IMU and our desire to take a more rotation-based approach, the initial inspiration for our game was Super Monkey Ball.  While the game seems mechanically demanding, our approach would optimize gameplay to be slower and focus more on precise controls over Super Monkey Ball's rapid and speed based gameplay. This would allow for our game to both have an easier learning curve and build up on difficulty in levels, allowing for the steady growth in motor skills for our players. 

In order to make a game that is both visually appealing and within our criteria, we decided to use the industry standard game engine Unreal. The endless powerful tools that Unreal Engine has gives us creative freedom with our game design. 

![[unreal.gif]]
*Unreal Engine 5.2 Demo*

The properties of physics that our game will be using are demonstrated here:

![[Sequence 01.gif]]
*Ball Physics Demo*