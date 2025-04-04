# Variable Tilt Hexacopter

## Overview

This repository contains a **Simscape/Simulink model** and a **ROS2 Gazebo simulation setup** for a **Variable Tilt Hexacopter**, designed to simulate and analyze the dynamics and control of a hexacopter with adjustable propeller tilting angles. The project supports both offline modeling and real-time robotic simulation to facilitate research in **geometric control, flight dynamics**, and **ROS-based deployment**.

---

## Repository Structure

```plaintext
📂 VariableTiltHexacopter
├── 📁 matlab
    ├── 📁 modelling_scripts/             # MATLAB scripts for modeling and analysis
│   │   ├── 📄 compute_params.slx         # Simulink for evaluating inertia tensors
│   │   └── 📄 fixed_wrench_analysis.mlx  # Livescript for wrench evaluation
│   ├── 📄 param.m                    # MATLAB script for hexacopter parameters
│   └── 📄 simulation.slx             # Simulink model
├── 📁 ros_ws/                        # ROS2 workspace
│   └── 📁 src/
│       └── 📁 hexacopter_description/
│           ├── 📁 launch/            # ROS2 launch files
│           ├── 📁 resource/          # Package resources
│           ├── 📁 scripts/           # (Planned) ROS2 nodes for control, etc.
│           ├── 📁 urdf/              # Xacro/URDF description of the hexacopter
│           ├── 📁 worlds/            # Gazebo SDF environments
│           ├── 📄 package.xml
│           └── 📄 setup.py
├── .gitignore
└── README.md
```

---

## Getting Started

### Prerequisites

#### MATLAB Simulation
- **MATLAB & Simulink** (R2021b or later recommended)
- **Simscape Multibody**

#### ROS2 Simulation
- **ROS2** (e.g., Foxy, Galactic, or Humble)
- **Gazebo Fortress/Ignition**
- **colcon** (ROS2 build tool)
- **xacro**, `ros_ign_gazebo` plugins, and other common ROS2 packages

---

## MATLAB Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/olanrewajufarooq/VariableTiltHexacopter.git
   cd VariableTiltHexacopter
   ```

2. Open MATLAB and navigate to the repo folder.

3. Run the parameter setup:
   ```matlab
   run('modelling_scripts/param.m')
   ```

4. Open and simulate the model:
   ```matlab
   open('modelling_scripts/simulation.slx')
   ```

   > View the physical model in Mechanics Explorer.

---

## ROS2 + Gazebo Usage

### 1. Build the workspace
```bash
cd ros_ws
source /opt/ros/humble/setup.bash  # or foxy, galactic depending on your setup
colcon build --packages-select hexacopter_description
source install/setup.bash
```

### 2. Launch the hexacopter in Gazebo Fortress
```bash
ros2 launch hexacopter_description spawn_robot.launch.py
```

> Make sure `gazebo` or `ign gazebo` is correctly sourced and installed.
---

## Features & Roadmap

✅ URDF/Xacro model of the hexacopter  
✅ ROS2 launch integration with Gazebo Fortress  
✅ World environments: `empty.sdf`, `warehouse.sdf`  

🚧 In Development / Planned:
- ROS2 nodes for tilt control and flight dynamics
- Sensor plugins (IMU, camera, lidar)
- Teleop via joystick/keyboard
- RViz integration and visualization enhancements

---

## Contributing

Feel free to fork this repo and contribute via pull requests. Open issues for bugs, feature suggestions, or integration help.

---

## License

[MIT License](LICENSE) – Free to use, modify, and distribute.

