# ubody-controller

ubody-controller is a Python library designed from the ground up to work with any Dynamixel motor on the market with few
to no modifications as an extension of [dynamixel-controller](https://github.com/UGA-BSAIL/dynamixel-controller)
from UGA B-SAIL.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install ubody-controller.

```bash
git clone https://github.com/Jyumpp/ubody-controller.git
pip install .
```

## Usage
#### Import:
```python
from dynio_sense import *
```

#### Port handling:
```python
dxl_io = dxl.DynamixelIO('portname') # your port for U2D2 or other serial device
```

#### Pre-made sensory body declaration:
```python
ubody = dxl_io.new_ubody(0)      # U-BODY with ID 0 
```

#### Sensory Body Control:
See [documentation](https://github.com/Jyumpp/ubody-controller/blob/master/docs.md) for full list of functions 
and their usage.
```python
ubody.ports_enable()
ubody.ports_disable()
ubody.set_ports(True, True, True)
```

#### Pre-made motor declarations:
See [documentation](https://github.com/Jyumpp/ubody-controller/blob/master/docs.md) for full list of motors. 
See below for sample:
```python
ax_12 = dxl_io.new_ax12(1)       # AX-12 protocol 1 with ID 1
mx_64_1 = dxl_io.new_mx64(2, 1)  # MX-64 protocol 1 with ID 2
mx_64_2 = dxl_io.new_mx64(3, 2)  # MX-64 protocol 2 with ID 3
```

#### Motor Control:
See [documentation](https://github.com/Jyumpp/ubody-controller/blob/master/docs.md) for full list of functions 
and their usage.

The most prevalent functions are pre-implemented as methods for the motor objects. 
These include:
```python
motor.torque_enable()
motor.torque_disable()
motor.set_acceleration(acceleration)
motor.set_velocity_mode()
motor.set_velocity(velocity)
motor.set_position_mode()
motor.set_position(position)
motor.set_angle(angle) 
motor.set_extended_position_mode()
motor.set_position(position)
position = motor.get_position()
angle = motor.get_angle()
current = motor.get_current()
torque = motor.get_torque()
```
All other values can be easily read from or written to using their [control table](http://emanual.robotis.com/) name.
Example:
```python
motor.write_control_table("LED", 1) # Turns the LED on
speed = motor.read_control_table("Present_Speed") # Returns present velocity
```
## Contributing
This project is currently designed as a class project and is not presently accepting contributions. This will be updated
when this status changes.

## License
[Apache 2.0](https://choosealicense.com/licenses/apache-2.0/)