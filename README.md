# test_project

## How to build and run on Hololens 2

1. Install [Unity Hub](https://unity.com/download) on windows machine.
2. Go to installs tab and in "Install Editor" choose 2020.3.xx version (basically latest 2020 version of unity).
3. During the "Install Editor" steps in the platform section make sure the check for "Universal Windows Platform" and "Windows" for build support.
4. Clone this repository if not done so yet.
5. In the "Projects" tab of Unity Hub click "Open" and choose the folder of the cloned repository. 
6. The project should open automatically after step 5. If not, just click on it in the hub.
7. Make sure, that in the hierarchy "TestingScene" is shown. If not, in the "Project" section of the editor go to Assets->Scenes and double click on the TestingScene
8. Click on the "ROSCommunication" element in the hierarchy and change "Ros Bridge Server Url" to ws://{IP_OF_ROS_MACHINE_TO_BE_USED}:9090
9. Go to File->Build settings. UWP should already be chosen. If not, cleck on it and press "Switch Platform"
10. For the settings, they should be the following:    

    Architecture: ARM64

    Build Type: D3D Project

    Target SDK Version: Latest installed

    Minimum Platform Version: 10.0.10240.0

    Everything else should be left as is.

11. Click build and choose folder for the built project to be saved to. I strongly advice to NOT put it in the repository folder. After build is finished, the folder with the built project should open automatically.
