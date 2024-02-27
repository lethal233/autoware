# Install Autoware-related messages on host machine

## Requirements

- ROS2 humble
- package build dependency

```sh
pip install catkin_pkg lark empy==3.3.4
sudo apt install -y ros-humble-geographic-msgs librange-v3-dev ros-humble-lanelet2
```

## Clone this repo

```sh
git clone -b msgs_install --single-branch https://github.com/lethal233/autoware.git
```

## import vcs repos

```sh
cd autoware
mkdir src
vcs import src < autoware.repos
vcs import src < simulator.repos
```

## Modifications

1. Modify `autoware/src/universe/autoware.universe/planning/planning_validator/CMakeLists.txt` to:

```makefile
cmake_minimum_required(VERSION 3.22)
project(planning_validator)
find_package(ament_cmake_auto REQUIRED)
ament_auto_find_build_dependencies()

rosidl_generate_interfaces(
  ${PROJECT_NAME}
  "msg/PlanningValidatorStatus.msg"
  DEPENDENCIES builtin_interfaces
)
ament_auto_package()
```

2. Modify `autoware/src/universe/autoware.universe/planning/planning_validator/package.xml` to:

<details>
  <summary> Click me </summary>

  ```xml
<?xml version="1.0"?>
<?xml-model href="http://download.ros.org/schema/package_format3.xsd" schematypens="http://www.w3.org/2001/XMLSchema"?>
<package format="3">
  <name>planning_validator</name>
  <version>0.1.0</version>
  <description>ros node for planning_validator</description>
  <maintainer email="takamasa.horibe@tier4.jp">Takamasa Horibe</maintainer>
  <maintainer email="kosuke.takeuchi@tier4.jp">Kosuke Takeuchi</maintainer>
  <license>Apache License 2.0</license>

  <author email="takamasa.horibe@tier4.jp">Takamasa Horibe</author>
  <author email="yutaka.shimizu@tier4.jp">Yutaka Shimizu</author>

  <buildtool_depend>ament_cmake_auto</buildtool_depend>
  <!-- <buildtool_depend>autoware_cmake</buildtool_depend> -->
  <build_depend>rosidl_default_generators</build_depend>

  <depend>autoware_auto_planning_msgs</depend>
  <!-- <depend>diagnostic_updater</depend> -->
  <depend>geometry_msgs</depend>
  <!-- <depend>motion_utils</depend> -->
  <depend>nav_msgs</depend>
  <!-- <depend>planning_test_utils</depend> -->
  <!-- <depend>rclcpp</depend> -->
  <!-- <depend>rclcpp_components</depend> -->
  <!-- <depend>tier4_autoware_utils</depend> -->
  <!-- <depend>vehicle_info_util</depend> -->
  <depend>visualization_msgs</depend>

  <!-- <test_depend>ament_cmake_ros</test_depend>
  <test_depend>ament_lint_auto</test_depend>
  <test_depend>autoware_lint_common</test_depend> -->

  <exec_depend>rosidl_default_runtime</exec_depend>
  <member_of_group>rosidl_interface_packages</member_of_group>

  <export>
    <build_type>ament_cmake</build_type>
  </export>
</package>

```
</details>



3. Modify `autoware/src/universe/autoware.universe/control/vehicle_cmd_gate/CMakeLists.txt` to:
```makefile
cmake_minimum_required(VERSION 3.5)
project(vehicle_cmd_gate)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)

rosidl_generate_interfaces(
  ${PROJECT_NAME}
  "msg/IsFilterActivated.msg"
  DEPENDENCIES builtin_interfaces
)

ament_export_dependencies(rosidl_default_runtime)
ament_package()

```

4. Modify `autoware/src/universe/autoware.universe/control/vehicle_cmd_gate/package.xml` to:

<details>
  <summary> Click me </summary>

  ```xml
<?xml version="1.0"?>
<?xml-model href="http://download.ros.org/schema/package_format3.xsd" schematypens="http://www.w3.org/2001/XMLSchema"?>
<package format="3">
  <name>vehicle_cmd_gate</name>
  <version>0.1.0</version>
  <description>The vehicle_cmd_gate package</description>
  <maintainer email="takamasa.horibe@tier4.jp">Takamasa Horibe</maintainer>
  <maintainer email="tomoya.kimura@tier4.jp">Tomoya Kimura</maintainer>
  <license>Apache License 2.0</license>

  <author email="hiroki.ota@tier4.jp">Hiroki OTA</author>

  <buildtool_depend>ament_cmake</buildtool_depend>
  <!-- <buildtool_depend>autoware_cmake</buildtool_depend> -->

  <build_depend>rosidl_default_generators</build_depend>

  <depend>autoware_adapi_v1_msgs</depend>
  <depend>autoware_auto_control_msgs</depend>
  <depend>autoware_auto_system_msgs</depend>
  <depend>autoware_auto_vehicle_msgs</depend>
  <!-- <depend>component_interface_specs</depend>
  <depend>component_interface_utils</depend>
  <depend>diagnostic_updater</depend> -->
  <depend>geometry_msgs</depend>
  <!-- <depend>motion_utils</depend>
  <depend>rclcpp</depend>
  <depend>rclcpp_components</depend>
  <depend>std_srvs</depend>
  <depend>tier4_api_utils</depend> -->
  <depend>tier4_control_msgs</depend>
  <depend>tier4_debug_msgs</depend>
  <depend>tier4_external_api_msgs</depend>
  <depend>tier4_system_msgs</depend>
  <depend>tier4_vehicle_msgs</depend>
  <!-- <depend>vehicle_info_util</depend> -->
  <depend>visualization_msgs</depend>

  <exec_depend>rosidl_default_runtime</exec_depend>

  <test_depend>ament_cmake_ros</test_depend>
  <test_depend>ament_lint_auto</test_depend>
  <test_depend>autoware_lint_common</test_depend>

  <member_of_group>rosidl_interface_packages</member_of_group>

  <export>
    <build_type>ament_cmake</build_type>
  </export>
</package>

```

</details>

5. Modify `autoware/src/universe/autoware.universe/control/control_validator/CMakeLists.txt` to:
```makefile
cmake_minimum_required(VERSION 3.22)
project(control_validator)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)

rosidl_generate_interfaces(
  ${PROJECT_NAME}
  "msg/ControlValidatorStatus.msg"
  DEPENDENCIES builtin_interfaces
)

ament_export_dependencies(rosidl_default_runtime)
ament_package()
```

6. Modify `autoware/src/universe/autoware.universe/control/control_validator/package.xml` to:

<details>
  <summary> Click me </summary>

  ```xml
<?xml version="1.0"?>
<?xml-model href="http://download.ros.org/schema/package_format3.xsd" schematypens="http://www.w3.org/2001/XMLSchema"?>
<package format="3">
  <name>control_validator</name>
  <version>0.1.0</version>
  <description>ros node for control_validator</description>
  <maintainer email="kyoichi.sugahara@tier4.jp">Kyoichi Sugahara</maintainer>
  <maintainer email="takamasa.horibe@tier4.jp">Takamasa Horibe</maintainer>
  <maintainer email="makoto.kurihara@tier4.jp">Makoto Kurihara</maintainer>
  <license>Apache License 2.0</license>

  <author email="kyoichi.sugahara@tier4.jp">Kyoichi Sugahara</author>
  <author email="takamasa.horibe@tier4.jp">Takamasa Horibe</author>
  <author email="makoto.kurihara@tier4.jp">Makoto Kurihara</author>

  <buildtool_depend>ament_cmake_auto</buildtool_depend>
  <buildtool_depend>autoware_cmake</buildtool_depend>
  <build_depend>rosidl_default_generators</build_depend>

  <depend>autoware_auto_planning_msgs</depend>
  <!-- <depend>diagnostic_updater</depend> -->
  <depend>geometry_msgs</depend>
  <!-- <depend>motion_utils</depend> -->
  <depend>nav_msgs</depend>
  <!-- <depend>rclcpp</depend> -->
  <!-- <depend>rclcpp_components</depend> -->
  <!-- <depend>tier4_autoware_utils</depend> -->
  <!-- <depend>vehicle_info_util</depend> -->
  <depend>visualization_msgs</depend>

  <test_depend>ament_cmake_ros</test_depend>
  <test_depend>ament_lint_auto</test_depend>
  <test_depend>autoware_lint_common</test_depend>

  <exec_depend>rosidl_default_runtime</exec_depend>
  <member_of_group>rosidl_interface_packages</member_of_group>

  <export>
    <build_type>ament_cmake</build_type>
  </export>
</package>
```
</details>


7. Modify `autoware/src/universe/autoware.universe/control/operation_mode_transition_manager/CMakeLists.txt` to:
```makefile
cmake_minimum_required(VERSION 3.14)
project(operation_mode_transition_manager)

find_package(ament_cmake_auto REQUIRED)
ament_auto_find_build_dependencies()

rosidl_generate_interfaces(
  ${PROJECT_NAME}
  "msg/OperationModeTransitionManagerDebug.msg"
  DEPENDENCIES builtin_interfaces
)
ament_auto_package()
```

8. Modify `autoware/src/universe/autoware.universe/control/operation_mode_transition_manager/package.xml` to:


<details>
  <summary> Click me </summary>

  ```xml
<package format="3">
  <name>operation_mode_transition_manager</name>
  <version>0.1.0</version>
  <description>The vehicle_cmd_gate package</description>
  <maintainer email="takamasa.horibe@tier4.jp">Takamasa Horibe</maintainer>
  <maintainer email="tomoya.kimura@tier4.jp">Tomoya Kimura</maintainer>
  <license>Apache License 2.0</license>

  <author email="takamasa.horibe@tier4.jp">Takamasa Horibe</author>

  <buildtool_depend>autoware_cmake</buildtool_depend>
  <build_depend>rosidl_default_generators</build_depend>

  <depend>autoware_auto_control_msgs</depend>
  <depend>autoware_auto_system_msgs</depend>
  <depend>autoware_auto_vehicle_msgs</depend>
  <!-- <depend>component_interface_specs</depend>
  <depend>component_interface_utils</depend> -->
  <depend>geometry_msgs</depend>
  <!-- <depend>motion_utils</depend>
  <depend>rclcpp</depend>
  <depend>rclcpp_components</depend> -->
  <depend>std_srvs</depend>
  <!-- <depend>tier4_autoware_utils</depend> -->
  <depend>tier4_control_msgs</depend>
  <depend>tier4_system_msgs</depend>
  <depend>tier4_vehicle_msgs</depend>
  <!-- <depend>vehicle_info_util</depend> -->

  <!-- <test_depend>ament_cmake_gtest</test_depend>
  <test_depend>ament_lint_auto</test_depend>
  <test_depend>autoware_lint_common</test_depend> -->

  <exec_depend>rosidl_default_runtime</exec_depend>
  <member_of_group>rosidl_interface_packages</member_of_group>

  <export>
    <build_type>ament_cmake</build_type>
  </export>
</package>
```

</details>


## Build packages

```sh

source /opt/ros/humble/setup.bash

colcon build --packages-select $(colcon list | awk '{print $1}' | grep 'msgs$') vehicle_cmd_gate planning_validator control_validator operation_mode_transition_manager autoware_lint_common autoware_cmake autoware_utils lanelet2_extension lanelet2_extension_python dummy_perception_publisher tier4_autoware_utils --symlink-install

```

It takes ~20 minutes to build these packages on 4-core CPU. 

## Source the environment

Under the directory `autoware`
```sh
source install/setup.bash
```

## Usage in Python

### Read rosbag files

```python
import sqlite3
from rosidl_runtime_py.utilities import get_message
from rclpy.serialization import deserialize_message
import sys
import argparse



class BagFileParser():
    def __init__(self, bag_file):
        self.bag_file = bag_file
        self.conn = sqlite3.connect(bag_file)
        self.cursor = self.conn.cursor()

        topics_data = self.cursor.execute("SELECT id, name, type FROM topics").fetchall()
        self.topic_msg_message = {name_of:get_message(type_of) for id_of, name_of, type_of in topics_data}
        
        self.fetch_all_msgs_sql = "select topics.name as topic, data as message, timestamp as t from messages join topics on messages.topic_id = topics.id order by timestamp desc";

    def __del__(self):
        self.conn.close()

    def read_messages(self):
        rows = self.cursor.execute(self.fetch_all_msgs_sql).fetchall()
        return rows
    
    def deserialize_data(self, data, topic_name):
        return deserialize_message(data, self.topic_msg_message[topic_name])

if __name__ == '__main__':
    f = BagFileParser("/path/to/rosbag_record_file")
    for topic, message, t in f.read_messages():
        if topic in interest_topics:
            msg = f.deserialize_data(message, topic)

```

### import Autoware data type

```python
from autoware_auto_planning_msgs.msg import Trajectory
import autoware_auto_perception_msgs.msg
import geometry_msgs.msg
import nav_msgs.msg
# ...
# ...
```
