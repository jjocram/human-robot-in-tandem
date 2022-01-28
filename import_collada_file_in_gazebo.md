# Import Collada file (3D model) in Gazebo simulator
A step by step guide on how to import (3D model) collada file in Gazebo simulator

## 1. Find the model
You can search the model in any places. I can suggest:
- [3D Warehouse](https://3dwarehouse.sketchup.com)

## 2A. Create a world file with the model
Create the file `world_name.world`
```xml
<?xml version="1.0"?>
<sdf version="1.4">
  <world name="default">
    <include>
      <uri>model://ground_plane</uri>
    </include>
    <include>
      <uri>model://sun</uri>
    </include>
    <model name="my_mesh">
      <pose>0 0 0  0 0 0</pose>
      <static>true</static>
      <link name="body">
        <visual name="visual">
          <geometry>
            <mesh><uri>file://PATH_TO_THE_FILE.dae</uri></mesh>
          </geometry>
        </visual>
      </link>
    </model>
  </world>
</sdf>
```
and launch gazebo
```bash
gazebo world_name.world
```

## 2B. Create a model file to use in your world
1. Create new a directory in `.gazebo/models/` with the name of the model you want to use. 
2. Inside this new directory create 2 files
  - `model_name.sdf`
```xml
<?xml version='1.0'?>
<sdf version='1.5'>
  <model name='warehouse_1'>
    <static>true</static>
    <link name="curve1">
      <visual name="visual">
            <geometry>
                <mesh>
                    <uri>file://PATH_TO_THE_FILE.dae</uri>
                </mesh>
            </geometry>
        </visual>
        <collision name="collision">
            <geometry>
                <mesh>
                    <uri>file://PATH_TO_THE_FILE.dae</uri>
                </mesh>
            </geometry>
        </collision>
    </link>
  </model>
</sdf>
```
  - `model.config` **this name is mandatory** and attention to the name in the `<sdf>` tag, it has to be the same as the one created above
```xml
<?xml version="1.0"?>
<model>
  <name>Model name</name>
  <version>1.0</version>
  <sdf version='1.5'>model_name.sdf</sdf>

  <author>
   <name>Name Surname</name>
   <email>email@mail.com</email>
  </author>

  <description>
    Description of the model
  </description>
</model>
```
