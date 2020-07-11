# amiro_citrack
Example repository to run the AMiRo in the CITrack with a NetBoot machine in the loop.
It setups the simple package `amiro_in_the_loop`, so that you sense and control an AMiRo with a PC in the network.
Tracking and localization is provided by CITrack, which topics are provided by multimaster_fkie if you run `roslaunch amiro_in_the_loop master_sync.launch`.
Communication to the AMiRo is provided by the [AMiRo Bridges](https://github.com/autonomoussystemsengineering/amiro_bridges).

# Preliminaries

1. If you work on a NetBoot machine, you have to add the following lines to the bashrc to make RSB available for compilation and runtime:
```
F='/vol/robocup/nightly-2017-03-30'
ls $F >/dev/null
export PATH=$F/bin:$F/sbin:${PATH}
export MANPATH=$F/share/man:${MANPATH}
export PKG_CONFIG_PATH=$F/lib/pkgconfig:$F/lib64/pkgconfig:${PKG_CONFIG_PATH}
export LD_LIBRARY_PATH=$F/lib:$F/lib64:$F/usr/lib:${LD_LIBRARY_PATH}
export LIBRARY_PATH=$F/lib:$F/lib64:$F/usr/lib:${LIBRARY_PATH}
export CMAKE_PREFIX_PATH=$F:${CMAKE_PREFIX_PATH} 
```
2. Copy `amiro_in_the_loop/config/rsb.config` to the systems folder `~/.config`

3. Run a spread daemon on `alice.techfak.uni-bielefeld.de` which provides communication between your PC and the AMiRo

4. Run e.g. `roslaunch amiro_in_the_loop start_amiro_in_the_loop.launch` to receive CITrack localization and control the AMiRo Nr. 7 via ROS twist messages. 
