# Building and Launching Guidelines

Pre requisites are :-

- Follow the [Husarion docx](https://github.com/husarion/husarion_ugv_ros/tree/ros2-devel) and build the workspace. (Make sure you are cloning the `ros2-devel` branch)

#

#### Build

- Clone this Package in your workspace (Other than that of the Husarion workspace)
  ```bash
  git clone https://github.com/ArpitKrSingh7/final_simulation.git
  ```

Now as you already have cloned this package just enter `colcon build` and done.

#

#### Launch

For launching this package make sure these two steps you have followed

- Make sure to `source install/setup.bash` the husarion workspace which you have cloned earlier.
- Then `source install/local_setup.bash` this workspace in the same terminal as before.

  After you complete the above steps , make sure you are in Your Workspace .

  Now to launch enter

  ```bash
  ros2 launch sim_worlds_ercremote_pkg simulation.launch.py
  ```

The husarion bot will spawn in the mars world along with gazebo and Rviz , if everything is correctly done!

## Some extra info

- In the config folder we have components.yaml , You can add remove components accordingly.
- To change world while launching , you can change the `final_world.launch.py` file (by default `mars.sdf`).
- In config folder we have `start_positions.yaml` , by default it's `1` , but you can always change it from the launch file!

- To change the texture you can edit the `model.mtl` file at `sim_worlds_ercremote_pkg/models/mars_yard/meshes/model.mtl`. (Two Textures are given there i.e texture.png and texture2.png)

- If you are getting Controllers Failed message check your husarion_ws.

  ```
      spawner_common_args = [
        "--controller-manager",
        "controller_manager",
        "--switch-timeout",
        "10",
        "--ros-args",
        "--log-level",
        log_level,
        "--log-level",
        limit_log_level_to_info("rcl", log_level),
    ]
  ```

  Copy this and replace with the existing Node in `husarion_ws/src/husarion_ugv_ros/husarion_ugv_controller/launch/controller.launch.py` This will basically increase the timeout time.
