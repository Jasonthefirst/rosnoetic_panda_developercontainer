# ROSNoeticStandardContainer

This is a visual studio code development container with ros noetic installed. 

Install Visual studio code with the remote container extension, clone this repository and enjoy a container with everything for ROS and Panda installed. 

## Version

ROS: noetic


Robots: 
 - Panda

 Features:

 - ROS Noetic
 - Ros für Franka Panda
 - MoveIt vorkompiliert



## Installation

### lokale Windows installation
1. Visual Studio Code
(Erläuterung: https://code.visualstudio.com/docs/remote/containers)
2. WSL 
    (https://learn.microsoft.com/de-de/windows/wsl/install)
3. Docker https://docs.docker.com/desktop/install/windows-install/
4. Erstellt euch einen Fork von dem Repository
5. Cloned das Repository in die WSL Umgebung (git clone ...)
6. Öffnet das Repository in Visual Studio code mit "code ." in dem Repository Ordner.
7. Führt mit strg + shift + p "Remote-Containers: Open in Container" aus. Ihr seid nun in der Umgebung mit allen benötigten Paketen.


### auf dem Roboter PC

1. Erstellt euch einen Fork von dem Repository
2. Cloned das Repository in die WSL Umgebung (git clone ...)
3. Öffnet das Repository in Visual Studio code mit "code ." in dem Repository Ordner.
4. Führt mit strg + shift + p "Remote-Containers: Open in Container" aus. Ihr seid nun in der Umgebung mit allen benötigten Paketen.

### Funktionen:

#### Desktopumgebung
Geht in eurem Browser auf: http://localhost:6080/. Mit dem Passwort: "vscode" könnt ihr die Desktopumgebung des Systems im Container aufrufen.
Alle Fenster die ihr im Container öffnet, werden hier sichtbar. 

#### Panda Gazebo

##### cartesian impedance controller

Mit dem Befehl:
'roslaunch franka_gazebo panda.launch x:=-0.5 \
    world:=$(rospack find franka_gazebo)/world/stone.sdf \
    controller:=cartesian_impedance_example_controller \
    rviz:=true'
öffnet ihr einen Simulator + Visualisierer vom Panda Roboter mit einem kartesischen Impedanz Controller. Es sind nun alle RosTopics geladen um den (virtuellen) Roboter zu steuern.

##### moveit position controller

Mit dem Befehl

''' roslaunch panda_moveit_config demo_gazebo.launch rviz_tutorial:=true '''
könnt ihr einen Gazebo Simulator mit RVIZ und Moveit starten. Ihr müsst dazu noch in rviz eine MotionPlanning Visualisierung hinzufügen. Die entsprechenden Topics sind aber auch ohne das gestartet.


### Eigenen Code erstellen: 

Um ein eigenes ROS Package zu erstellen müsst ihr ein catkin package in /workspace/catkin_ws/src erstellen (oder reinclonen). http://wiki.ros.org/ROS/Tutorials/CreatingPackage

mit "catkin_make" in /workspace/catkin_ws wird dieses Package kompiliert und alle Funktionen stehen zur Verfügung nachdem ihr mit source /workspace/catkin_ws/devel/setup.bash den Workspace gesourced habt.


## Fehlerbehebung:

### Probleme beim Clonen in einen Remote development container
Falls das Clonen eines Remote Developmentcontainers nicht funktionieren sollte, probiert ob ihr es in den Folder "workspace" clonen könnt. 


### Probleme beim Starten des Containers
Eventuell ist keine geeignete GPU vorhanden. Kommentiert dann den Teil:

''' deploy:
      resources:
        reservations:
          devices:
            - capabilities: ["gpu"]
'''

im Dockerfile aus. 