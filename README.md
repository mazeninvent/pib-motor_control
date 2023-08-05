# pib-motor_control
This ROS workspace includes one package "cerebra" including one node "motor_control". This node subscribes to "motor_settings" topic and recieves json messages from cerebra web application on local host.
Followingly the recieved message is split into motor name and value storing them in variables. Motor pin and bricklet retrieved from 2 dictionaries, one maping motors the connected servo bricklet (3 bricklets used) and one maps motor pin connected on servo bricklet.
After each message is retrieved an if conditions decides which servo bricklet is the motor connected to according to the number its maped to in the first dictionary. Then using Tinkerforge APIs, motors are moved with the value in message applied on pin that is mapped to motor name.
To run the node:


colcon build --packages-select cerebra
cd install
source setup.bash
ros2 run cerebra motor_control

Then navigate to local host from a web browser, moving the slider should print on terminal the shown message and if connected to hardware should move motors directly.
