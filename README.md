P.SIVA 212220040157
# Lab-Ex.-No---6-Design-simulate-an-environment-for-Welding-using-Robo-DK


 
## AIM:
  To Design & simulate an environment for welding operation using robodk 

## Software  Required:
Robodk

### Theory
When using robots for any process, the method requires amending to accommodate automation. The same is true of welding, which uses several tools not found in its manual equivalent. People don’t need programming the way robotic welders do.

The robot itself has an arm that can move in three dimensions for rectilinear types and through more planes with articulating versions. A wire feeder sends the filler wire to the robot as it needs it for a welding job. A high-heat torch at the end of the arm melts metal to enable the welding process. Because the temperatures reach thousands of degrees, using robots for this process keeps people safer.

Certified human operators still need to remain close to the robots. These workers should hold certification from the American Welding Society, AWS, which certify not only manual welders but also robotic welding arm operators. The operators program the controller using a teach pendant. This device sets new programs, moves the arm and changes parameters for the process. To start the welding, the operator uses the buttons on the operation box.

The tool in the robotic arm heats to melt metal to conjoin the desired pieces. As needed, a wire feeder delivers more metal wire to the arm and torch. When awaiting the next parts to weld, the arm moves the torch to the cleaner to clean any metal splatters from the arm, which could solidify in place without this process.

Because one of the primary reasons to have robotic welders is protecting human workers, these automated systems come with multiple safety features. Arc shields prevent the high-heat arc from mixing with oxygen. Enclosed areas protect operators from the temperatures and bright light.
### ROBOTIC WELDING PROCESSES
Welding requires a high level of education and skill. However, the number of professional welders does not meet the needs of the industry. According to the American Welding Society, by 2022, the industry will experience a shortage of 450,000 welders. Instead of letting critical projects these workers would complete fall behind, robots can pick up the slack.

Robots automate the process, which ensures higher accuracy, less waste and faster operation. With the range of machinery available, robots adapt to a wide variety of welding processes including arc, resistance, spot, TIG and more.


1. ARC WELDING
One of the most common types of robotic welding is the arc process. In this method, an electric arc generates extreme heat, up to 6,500 degrees Fahrenheit, which melts the metal. Molten metal joins parts together, solidifying into a stable connection after cooling. When a project requires a large volume of accurately conjoined metals, arc welding serves as an ideal application.

2. RESISTANCE WELDING
When projects need heat-treating or a way to lower costs, robots may use resistance welding. During this process, a current of electricity creates a pool of molten metal as it passes between the two metal bases. This molten metal joins the pieces of metal together.

3. SPOT WELDING
Some materials resist electrical currents, precluding them from other forms of welding. This situation frequently occurs in the automotive industry for piecing together parts of an automobile body. To overcome the issue, robotic welders use a variation of resistance welding to connect a pair of thin metal sheets in a single spot.

4. TIG WELDING
Robot welding applications requiring high levels of precision may require TIG welding. This method also goes by the term gas tungsten arc welding or GTAW. An electric arc passes between a tungsten electrode and the metal base.

5. MIG WELDING
Gas metal arc welding, also known as GMAW or MIG, is a fast and straightforward method that uses a high level of deposition. A wire moves continuously to the heated tip of the welder, which melts the wire, allowing for a large amount of molten metal to drip onto the base for joining the base to another piece.

6. LASER WELDING
When welding projects require accuracy for a high volume of parts, laser welding is the preferred method of metal joining. Small parts, such as jewelry or medical components often use laser welding.

7. PLASMA WELDING
Plasma welding offers the most significant degree of flexibility because the operator can easily change both the speed of gas passing through the nozzle and the temperature.



### Procedure 


 Import the 3d model in to the project  :
1. Go to the RoboDK tab in SolidWorks and select Auto Setup.
2. Select the welding paths. Make sure to also select the faces as they help orient the robot tool.
3. Now that you have imported the path from SolidWorks, you can go to RoboDK.
4. In the station tree, click Weld1 Settings which will open the Curve Follow Project.
5. Click Update to generate the program and then Simulate.
6. ![image](https://user-images.githubusercontent.com/36288975/173730531-c72ca3bd-9eb2-4a06-9e88-8a745cd0c5fd.png)
First, you should fix the path itself:
1. In the Curve Follow Project, click on Select Curve (going from 1 to 2, then 3 to 4, 5 to 6, 7 to 8, and 9
to 10).
2. The order from the welding sections makes sense. However, the welding direction does not seem to
make sense.
3. To switch the direction of a welding path (such as path 3 to 4), right click the path and select Reverse
direction – you can see that the arrows of that path changed direction.
4. You can do the same for path 5 to 6 and path 7 to 8.
5. Once your modifications are done, you can select Done on the right window.
6. Click Update to generate the program and Simulate to start the simulation.
Now that the order of the paths seems to make more sense, you can adjust the orientation of the tool along the
path to better improve the robot motion.
7. In the Curve Follow Project menu, click on Show preferred tool path. A variety of ghost tools will
appear to show you the orientation of the tool for different positions along the path.
8. The first tool orientation option that you can try is the Path to tool offset around the “Z” axis. To do so,
you can manually enter in a value or bring your mouse over it and use the scroll wheel to bring your value
up or down.
9. By doing this, you can see the orientation of the ghost tool changing
10. ![image](https://user-images.githubusercontent.com/36288975/173730657-fe5452ba-90f3-4dab-9a1f-39682983ef41.png)
11. In this case, the basic option does not seem to fix our problem. Fortunately, you can have more options to work
with; you can reveal them by clicking the blue plus button and change them according to your project.
10. You can change the rotation around the Z axis (rotz) to its original value, zero, and then click on the “+Z”
button.
11. As you can see with the ghost tools, the robot flange will always be on top of the part. Click Update and
then Simulate to simulate the result.
12. If you use the scroll bar, the new tool orientation facilitates the cable management of the tool; it has no
risk of interfering with the robot.
![image](https://user-images.githubusercontent.com/36288975/173730700-8782988f-bb79-465e-95f4-e4041b740c70.png)

1. Put back the default normal approach of 100 mm.
2. Add a movement, for example, along Z.
3. Set it to 50 mm.
4. Press Update and Simulate once you are finished.
5. Now the robot retracts normal to the welding path and then straight up
6. ![image](https://user-images.githubusercontent.com/36288975/173730741-29331e12-e805-44da-bc71-798894720348.png)

### PROGRAM
```
Name:K.sucharitha
Register Number:212221230021
```
```
import sys
import os
sys.path.append(os.path.abspath(r"""E:/RoboDK/Posts/""")) # temporarily add path to POSTS folder

from KUKA_KRC2 import *

try:
  from robodk.robomath import PosePP as p
except:
  # This will be removed in future versions of RoboDK
  from robodk import PosePP as p


print('Total instructions: 4')
r = RobotPost(r"""KUKA_KRC2""",r"""KUKA KR 210 R2700 extra""",6, axes_type=['R','R','R','R','R','R'], ip_com=r"""127.0.0.1""", api_port=20500, prog_ptr=2655981884352, robot_ptr=2655982579008)

r.ProgStart(r"""Prog1""")
r.RunMessage(r"""Program generated by RoboDK v5.4.1 for KUKA KR 210 R2700 extra on 25/06/2022 21:17:35""",True)
r.RunMessage(r"""Using nominal kinematics.""",True)
r.setFrame(p(0,0,0,0,0,0),210,r"""KUKA KR 210 R2700 extra Base""")
r.setTool(p(-4,0,371.3,0,45,0),-1,r"""Weld gun""")
r.MoveL(p(1762.65,254.573,1271.66,176.299,-31.2241,-168.47),[-12.061,-84.6905,82.1148,11.8405,81.1066,-9.23682],[0,0,0])
r.MoveL(p(1909.38,82.1936,244.394,173.458,-48.1296,-166.856),[-5.09436,-53.5834,91.9886,10.3442,56.2287,-8.17763],[0,0,0])
r.MoveL(p(913.203,11.8774,163.193,173.458,-48.1296,-166.856),[-6.20609,-86.1947,148.418,15.6926,33.1308,-16.7445],[0,0,0])
r.MoveL(p(1685.13,32.5589,6.33493,173.458,-48.1296,-166.856),[-4.1108,-52.2296,106.602,13.4094,40.4581,-11.6734],[0,0,0])
r.ProgFinish(r"""Prog1""")
r.ProgSave(r"""C:/Users/Sudharshna/Documents/RoboDK""",r"""Prog1""",True,r"""E:/RoboDK/Other/VSCodium/VSCodium.exe""")
```

### Simulation
![k6 1](https://user-images.githubusercontent.com/94226297/203840790-44917b1e-78a4-4d0a-8af3-8cf34d82aa30.png)
![k6 2](https://user-images.githubusercontent.com/94226297/203840847-72a20c77-92ae-4417-a824-7261c4aa0070.png)
![k6 3](https://user-images.githubusercontent.com/94226297/203840857-0a2e7eff-6f2a-4934-9b2c-f3f0f1115bd0.png)


### Result:
An environment for welding operation using robodk is Designed & simulated.




