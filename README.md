# import_collada_file_in_gazebo
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
**TBD**
