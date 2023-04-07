# ROS2-how-does-it-work-

# ROS2 : how does it work ?

- 'rospy' is replaced by 'rclpy'
- mavros was used to communicate with the PX4, now it is PX4 messages 'px4 msgs.msg' which is mode direct.

## Node
### Structure 
- subscriber or publisher has this structure : msg_type/‘topic’/px4 comment

- every node is unique and there is just one node per class (Node)
in the node, we can define any parameters 

- time fonction : 

```
import clock 
```
example : 
![Screenshot 2023-04-07 141908](https://user-images.githubusercontent.com/118521344/230658189-e5b828fe-b785-4b42-ba7d-b96efaf588e8.png)


### Topic 
publisher = output = out

![Screenshot 2023-04-07 142039](https://user-images.githubusercontent.com/118521344/230658373-beae46e7-17e2-4421-8304-bdaa081f9184.png)

Explanations : 

```
/vehicle_status
```
pick a name of a module in the PX4 user guide (messages) : [https://docs.px4.io/main/en/middleware/uorb_graph.html](https://docs.px4.io/main/en/middleware/uorb_graph.html)

```
/fmu
```
When there is direct communication with the PX4

### PX4 comment 

usually 10

### Setpoint

no case check

Ttrajectory setpoint : use the PX4 user guide to define the trajectory 
[https://docs.px4.io/main/en/msg_docs/](https://docs.px4.io/main/en/msg_docs/)
![Screenshot 2023-04-07 142137](https://user-images.githubusercontent.com/118521344/230658499-a5f02f87-ca10-416e-b7a1-58d3e70cc9c0.png)

![Screenshot 2023-04-07 142233](https://user-images.githubusercontent.com/118521344/230658603-0dbca1a7-d0b8-42fa-83a1-3834f703d37c.png)


uint8 = interger coded with 8 bits

### main 
![Screenshot 2023-04-07 142307](https://user-images.githubusercontent.com/118521344/230658667-b7bd3b21-4ab0-4652-98e2-ca1902ee4b8e.png)

is on his own 

### comments 
Not all subscribers have a publisher and vice versa because we are connected with the px4 and don’t see the information of the px4.

Be careful om NED to FLU conversion, we have to convert/align the origins of the drone and of the target.
 ![Screenshot 2023-04-07 142341](https://user-images.githubusercontent.com/118521344/230658730-ed80a50b-46ab-4700-9f3d-47474120baff.png)

