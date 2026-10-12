Hardware Interface
==================

The ``mujoco_ros2_control/MujocoSystemInterface`` implements ``hardware_interface::SystemInterface`` to bridge ROS 2 control with MuJoCo simulation.

Configuration Parameters
------------------------

The hardware interface is configured inside the URDF ``<ros2_control>`` tag.

Hardware Parameters (inside ``<hardware>``):

- ``mujoco_model`` (optional): Path to the MuJoCo XML/MJCF model file. If not specified, the model is extracted or generated from the robot description.
- ``mimic_joint_tendons`` (optional): Boolean indicating whether tendons are used to model mimic joints.

Joint Parameters (inside ``<joint>``):

- ``mujoco_name`` (optional): Name of the corresponding joint or actuator in the MuJoCo model if it differs from the URDF joint name.
- ``mimic`` (optional): Specification of mimic joints, containing attributes ``joint`` and ``multiplier``.

Command Interfaces:

- ``position``: Drives joint position (requires position actuator or PID control in MuJoCo).
- ``velocity``: Drives joint velocity (requires velocity actuator or motor control).
- ``effort``: Direct torque/force actuator command.

State Interfaces:

- ``position``: Current joint position reading.
- ``velocity``: Current joint velocity reading.
- ``effort``: Current joint effort reading calculated from actuator forces or sensor measurements.

Sensor Interfaces:

MuJoCo sensors can be exposed via the ``<sensor>`` tag inside ``<ros2_control>``, supporting IMUs, force-torque sensors, and generic state interfaces.
