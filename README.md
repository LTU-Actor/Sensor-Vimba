# Vimba

Packages and configurations to run a Vimba publisher node. Includes correctly running on a Jetson TX2

## Setup

Setup instructions: https://github.com/LTU-AutoEV/LTU-AutoEV-Core/wiki/Setting-up-vimba-publisher-on-Jetson-TX2 

Launch:

```
roslaunch avt_vimba_camera mono_camera.launch 
```


## Details

This package contains modified versions of [avt_vimba_camera](http://wiki.ros.org/avt_vimba_camera) and [image_pipeline](http://wiki.ros.org/image_pipeline).

The included **`avt_vimba_camera`** package is modified to support armv8. The code is provided by this pull request: https://github.com/srv/avt_vimba_camera/pull/30. Launch and configuration files are also modified for the mako camera we have. See `avt_vimba_camera/launch/mono_camera.launch` and `avt_vimba_camera/calibration`.

The included **`image_pipeline`** package is modified to only include specific sub-packages needed by `avt_vimba_camera`. Currently, this is only the `image_proc` package.

## Upgrading or Changing Camera

It may be necessary to upgrade this package to support a new camera or new ROS version.

To use a different camera, simply change the guid and ip values in `avt_vimba_camera/launch/mono_camera.launch`. Also rename the file in `avt_vimba_camera/calibration` to match the new camera's guid.

To update software, pull the code from the respective repositories:

  - **`avt_vimba_camera`**: https://github.com/srv/avt_vimba_camera
    - Also ensure than the armv8 PR has been merged: https://github.com/srv/avt_vimba_camera/pull/30
    - If not, [check out the pull request locally](https://help.github.com/articles/checking-out-pull-requests-locally/)
  - **`image_pipeline`**: https://github.com/ros-perception/image_pipeline

