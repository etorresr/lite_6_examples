# lite_6_examples
Some examples of the use of  xArm-Python-SDK library

Before the use of the examples presented in this document is recomended to install all dependencies for the xArm-Python-SDK library. You can find a detailed information in https://github.com/xArm-Developer/xArm-Python-SDK?utm_source=officialwebsite&utm_medium=banner&utm_campaign=none

You must download:
```
git clone https://github.com/xArm-Developer/xArm-Python-SDK.git
cd xArm-Python-SDK
```
Then install dependencies as:
```
pip install build
python -m build
pip install dist/xarm_python_sdk-1.16.0-py3-none-any.whl
```
or:
```
pip install .
```
## Example 1: Using G-code, bidimensional drawing
G-code is a CNC (Control Numeric Control) programing for machinning tools. In this particular exercise, an image is drawed using the G-code of figure contour. For this purpose, Inkscape which is a free drawing program, is employed. For the G-code generation of image contour, the next steps must be followed:
* Open new document in inkscape an import one image from an specific path
* Select the option in menu _Trace_ and the option _Bit map vectorization_. A new menu will appear and the select border detection form the list of _Detection mode_.
* From menu _Archive_ select _Document properties_ and adjust the page to the dimensions of your image.
* At this point, from menu _Extensions_ select _Gcode generator_ and the option _Library tools_. For this exercise, the predefined selection is the best option. On the tool definitions, define the diameter tool in 5 mm, beacuse is the diameter of a comercial pencil, which will be the machinning tool in this case
* From from menu _Extensions_ select _Gcode generator_ and the option _Orientation points_ to define the origin of the image in a two dimensional reference. From the displayed  menu you have to chose the option _Two points mode_ 
* Finally from menu _Extensions_ select _Gcode generator_ and the option _Gcode path_ to define the name of output file and the path for saving it.

An step by step video can be found in the next <a href="https://youtu.be/H7UaoG4Wry4" title="video">link</a>

### Python program
For the use of the  xArm-Python-SDK library is important to work in the  xArm-Python-SDK/example/wrapper/common path, in order to be abble to acces the complements required. From the examples provided by the library, the program has to initialize the robot, as shown hereafter:
``` python
import os
import sys
import time
import re

sys.path.append(os.path.join(os.path.dirname(__file__), '../../..'))

from xarm.wrapper import XArmAPI

arm = XArmAPI(ip)
arm.motion_enable(enable=True)
arm.set_mode(0)
arm.set_state(state=0)

arm.move_gohome(wait=True)
```

