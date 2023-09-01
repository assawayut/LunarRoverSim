# Lunar-Rover-Simulator
(This is the repository for the Lunar Rover Simulator test version, where only executable files exist. The full source code version, with RL interface, will be released soon.)

An open-source lunar rover simulator based on PyBullet aiming to serve as a tool to test the locomotion of rover on realistic lunar environment.  

<img src='figure/sim_interface.gif' width=800>

## Installation
This repository consists of self-contained executable simulator files bundled with all required packages. So, further installation is not required in this test version.

Linux (tested on x64 Ubuntu 22.04)
```sh
git clone https://github.com/assawayut/LunarRoverSim.git
cd linux
```

Windows (tested on x64 Windows 10)
```sh
# clone from window branch
git clone --branch window https://github.com/assawayut/LunarRoverSim.git
cd windows
```

## Usage
### LUVMI-X model
```sh
cd linux # (Windows) cd windows
./main_luvmix # (Windows) double click on main_luvmix.exe
```

### VIPER model
```sh
cd linux # (Windows) cd windows
./main_viper # (Windows) double click on main_viper.exe
```

## Interface
Simulator GUI consists of the option to enable/disable each lunar environmental effect, the slider bars for applied torques, and the option to use camera sensors.

To enable each environmental effect, move the corresponding slider bar to "1". For the temperature, the value of ambient temperature can also be adjusted through slider bar.

<img src="figure/env_gui.png" width=200> <img src="figure/motor_gui.png" width=200 height=263>


Since the source code is currently not accessible, the parameters can be changed or adjusted only in YAML files.
To change the lunar terrain, go to `init_config.yaml` and change the number after `terrain_index`, for the main type of terrain, and/or after `terrain_index2`, for the subtype of terrain. The properties of terrain can be modified under their corresponding terrain name.

<img src="figure/init_config.png" width=400>

To change the values of lunar environment parameter, go to `param_config.yaml` and change the values after each parameter.

<img src="figure/param_config.png" width=400>

There are currently two control modes; *Individual motors control* and *Differential drive control*. TO change the mode, go to `init_config.yaml` and change the number after `control_mode`

## Logger
### State
The state of rover base and all joint will be logged into the text file named `state_logger_<rover_name>.txt`. Inside the file, each line represents the state in the form of [simulation time, position, orientation, linear velocity, angular velocity, position and velocity of each joint]. The option to enable/disable state logger can be adjusted via GUI.

### Camera
Three types of images from camera sensor; RGB, Depth, Segmentation, are logged to folder name `/logger_img/<rover_name>/<imag_type>`, and only logged after both `Camera` and `Camera logger` GUIs are enable (to prevent the elongation of simulation time step)

## TODO
- Check the type of logged images again
- Test on Windows OS -> Works fine for Windows 10

