# CUBLab

![Image of Lab](Lab_Photo.png)

The photo above demonstrates how everything looks once it is up and running. The red boxes represent the obstacles, the green boxes represent the targets, and the blue line is the path that the DeepRacer robot has taken to get to the obstacle. The cameras can be seen above the arena, which are responsible for tracking the locations of each rigid body within the arena, as well as the movement of the DeepRacer robot. 

## Lab Organization
![Diagram of Lab](Lab_Diagram.png)

As can be seen from the diagram, the lab is set up with two servers connected to the router. The CUBLab Media Server is connected to the Cameras Switch, which powers the 8 OptiTrack cameras surrounding the arena in the lab. It is also connected via HDMI to 4 projectors spaced around the arena. The router also connects to the DeepRacer robot via Wi-Fi. 

## Required Software

### OptiTrack Motive

[OptiTrack Motive](https://optitrack.com/software/) is the software used alongside with the 8 cameras in the lab to track rigid body data within the arena. 

### Ventuz

[Ventuz](https://www.ventuz.com/downloads/) is the software used to congiure the images from all 4 projectors into one, without overlaps of the images. 

### OptiTrackRESTServer

The [OptiTrackRESTServer application](https://github.com/HyConSys/OptiTrackRESTServer) is the localization server, used to retrieve each rigid body's location within the arena. 

### NDIRestServer

The [NDIRestServer application](https://github.com/HyConSys/NDIRestServer) is used to present the images corresponding to the locations of the various rigid bodies within the arena, and present them using a Ventuz presentation.

### DeepRacer-utils

[Deepracer-utils](https://github.com/HyConSys/deepracer-utils) is a series of code and examples which are used to access and control the AWS DeepRacer.

## Starting the Lab

1. First make sure that the cameras, all four projectors, the DeepRacer and the Compute Module are turned on and running.

2. Open up terminal and type in the following command:

    ```
    cd D:/Workspace/ArenaManager
    python AutoDeploy.py
    ```

    This command will run the GUI application for quick deployment.

    ![GUI Setup](GUI_Setup.png)
3. Click on the "Initialize Environment" button located on the top-left corner. All necessary software will begin starting up, the process will take approximately 30 seconds.

4. Once everything is up and running, start placing markers to the scene, or place virtual objects by selecting the object type, enter object size (leave blank for default sizes), and click on the simulation on the right to place object where mouse is pointed. Move added object position by click and drag black dots centered on each object (marker objects cannot be moved).

    ![GUI Complete](GUI_Complete.png)
    
5. Save the current configuration by clicking File -> Save Current Objects Configuration, or Ctrl + S, which will save the all virtual objects position and sizes into a .json file. Load other .json files by clicking File -> Load Objects Configuration, or Ctrl + O. Undo last edit by clicking Edit -> Undo or Ctrl + Z.

6. Now we can start running the symbolic controller for the DeepRacer by clicking on button "Run DeepRacer Symbolic Control". Symbolic control server in Compute Module will start running and script [sym_control.py](https://github.com/HyConSys/deepracer-utils/tree/main/examples/sym_control) in DeepRacer will fetch valid actions from symbolic control server to reach and avoid. Make sure at least one target is placed for the controller to run successfully. Move targets or obstacles on the fly, the symbolic controller will notice the changes and adjust to approprieate actions.

7. Click on button "Manual Drive" to use arrow keys to manually drive the DeepRacer. Hit "Esc" on keyboard to exit manual drive.

## Video Demo

For video demos, visit [HyConSys Lab Youtube](https://www.youtube.com/channel/UCcI8WWWJ7LFaPKLJnH9tNXA)
