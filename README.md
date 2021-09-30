# Hector Quadrator Drone Simulation on Gazebo
<b>Etapes Installation du simulateur : </b>
1. Creer le catkin_workspace
	mkdir --parents hector_kajal_jyotika_ws/src
   
2. Aller dans le workspace et lancer la commande catkin_make
	cd hector_kajal_jyotika_ws
	catkin_make

3. Exécuter la commande de wstool
	wstool init src https://raw.github.com/tu-darmstadt-ros-pkg/hector_quadrotor/kinetic-devel/tutorials.rosinstall

4. Installation des packages
	sudo apt install ros-melodic-gazebo-ros-control
	sudo apt install ros-melodic-ros-control
	sudo apt install ros-melodic-geographic-info
	sudo apt install ros-melodic-joy
	sudo apt install ros-melodic-teleop-twist-keyboard
	sudo apt-get install libqt4-dev

5. Lancer la commande catkin_make


<b>Partie 1 Simulation du Drone:</b>
1. Aller dans le workspace et lancer la commande pour sourcer le workspace
	cd ~/hector_kajal_jyotika_ws 
	source devel/setup.bash

2. Lancer le simulateur de Gazebo dans un terminal
	roslaunch hector_quadrotor_demo outdoor_flight_gazebo.launch

3. Ouvrir un nouveau terminal et exécuter les commandes suivantes:
	rosservice call /enable_motors "enable: true" #activation du moteur
	rosrun teleop_twist_keyboard teleop_twist_keyboard.py #téléopération du drone

<b>Partie 2 Régulation en altitude:</b>
1. Aller dans le workspace
	cd ~/hector_kajal_jyotika_ws 

2. Faire un git clone de https://github.com/klsobhee/hector_drone.git

3. Aller dans le répertoire src et extraire les fichiers récupérés de git

4. Faire un source devel/setup.bash et lancer la commande catkin_make

5. Lancer la simulation en exécutant les commandes suivantes dans différents terminaux en allant de le workspace hector_kajal_jyotika_ws:
	roslaunch hector_quadrotor_demo outdoor_flight_gazebo.launch
	cd ~/hector_kajal_jyotika_ws
	source devel/setup.bash
	rosservice call /enable_motors "enable: true"
	rosrun kajal_jyotika_drone_control altitude_service.py
	rosservice call /altitude_service "altitude: data: '2'"


<b>Part 3 Régulation en position:</b>
1. Aller dans le workspace et exécuter les commandes suivantes dans différents terminaux:
	cd ~/hector_kajal_jyotika_ws 
	source devel/setup.bash
	roslaunch hector_quadrotor_demo outdoor_flight_gazebo.launch
	rosservice call /enable_motors "enable: true"
	rosrun kajal_jyotika_drone_control drone_move_service.py
	rosservice call /drone_move_service "altitude:
	  data: '2'
	horizontal_x:
	  data: '3'
	horizontal_y:
	  data: '0'"


<b>Part 4 Planification de mission:</b>
1. Aller dans le workspace et exécuter les commandes suivantes dans différents terminaux:
	cd ~/hector_kajal_jyotika_ws
	source devel/setup.bash
	roslaunch hector_quadrotor_demo outdoor_flight_gazebo.launch
	rosservice call /enable_motors "enable: true"
	rosrun kajal_jyotika_drone_control drone_move_service.py
	rosrun kajal_jyotika_drone_control waypoints.py
