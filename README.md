# test_project

## How to build and run on Hololens 2
1.Install Visual Studio 2022 and in Visual Studio Installer add:
    
    .NET desktop development,
        
    Desktop development with C++,
        
    Universal Windows Platform development,
    
    Game development with Unity
    
2. Install [Unity Hub](https://unity.com/download) on windows machine.
3. Go to installs tab and in "Install Editor" choose 2020.3.xx version (basically latest 2020 version of unity).
4. During the "Install Editor" steps in the platform section make sure the check for "Universal Windows Platform" and "Windows" for build support.
5. Clone this repository if not done so yet.
6. In the "Projects" tab of Unity Hub click "Open" and choose the folder of the cloned repository. 
7. The project should open automatically after step 6. If not, just click on it in the hub.
8. Make sure, that in the hierarchy "TestingScene" is shown. If not, in the "Project" section of the editor go to Assets->Scenes and double click on the TestingScene
9. Click on the "ROSCommunication" element in the hierarchy and change "Ros Bridge Server Url" to ws://{IP_OF_ROS_MACHINE_TO_BE_USED}:9090
10. Go to File->Build settings. UWP should already be chosen. If not, cleck on it and press "Switch Platform"
11. For the settings, they should be the following:    

    Architecture: ARM64

    Build Type: D3D Project

    Target SDK Version: Latest installed

    Minimum Platform Version: 10.0.10240.0

    Everything else should be left as is.

12. Click build and choose folder for the built project to be saved to. I strongly advice to NOT put it in the repository folder. After build is finished, the folder with the built project should open automatically.
13. In the generated folder go to Il2CppOutputProject->IL2CPP->external->google->sparsehash->internal and open sparseconfig.h
14. Look for line ```#define SPARSEHASH_HASH_NO_NAMESPACE  hash_compare``` (should be line 63) and add this right before it:
```
    #define _SILENCE_STDEXT_HASH_DEPRECATION_WARNINGS

    #include <hash_map>
```
16. Open .sln file with Visual Studio 2022 and open the tab Project->Publish->Create App Package:

    In the opened windows choose sideloading
    
    Certificate should already be there, but if not, follow the steps from the link in the bottom of the window
    
    For the version choose ONLY ARM64 and switch from debug to release
    
    Click create and wait for the package to be build.
