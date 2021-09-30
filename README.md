# Hector Quadrator Drone Simulation on Gazebo
<b>Etapes Installation du simulateur : </b>
1. Creer le catkin_workspace</br>
	mkdir --parents hector_kajal_jyotika_ws/src</br></br>
   
2. Aller dans le workspace et lancer la commande catkin_make</br>
	cd hector_kajal_jyotika_ws</br>
	catkin_make</br>

3. Exécuter la commande de wstool</br>
	wstool init src https://raw.github.com/tu-darmstadt-ros-pkg/hector_quadrotor/kinetic-devel/tutorials.rosinstall</br>

4. Installation des packages</br>
	sudo apt install ros-melodic-gazebo-ros-control</br>
	sudo apt install ros-melodic-ros-control</br>
	sudo apt install ros-melodic-geographic-info</br>
	sudo apt install ros-melodic-joy</br>
	sudo apt install ros-melodic-teleop-twist-keyboard</br>
	sudo apt-get install libqt4-dev</br>

5. Lancer la commande catkin_make</br>


<b>Partie 1 Simulation du Drone:</b></br>
1. Aller dans le workspace et lancer la commande pour sourcer le workspace</br>
	cd ~/hector_kajal_jyotika_ws </br>
	source devel/setup.bash</br>

2. Lancer le simulateur de Gazebo dans un terminal</br>
	roslaunch hector_quadrotor_demo outdoor_flight_gazebo.launch</br>

3. Ouvrir un nouveau terminal et exécuter les commandes suivantes:</br>
	rosservice call /enable_motors "enable: true" </br>
	rosrun teleop_twist_keyboard teleop_twist_keyboard.py</br>

<b>Partie 2 Régulation en altitude:</b></br>
1. Aller dans le workspace</br>
	cd ~/hector_kajal_jyotika_ws </br>

2. Faire un git clone de https://github.com/klsobhee/hector_drone.git et copier le package kajal_jyotika_drone_control dans le repertoire src du workspace</br>

3. Aller dans le répertoire src et extraire les fichiers récupérés de git</br>

4. Faire un source devel/setup.bash et lancer la commande catkin_make</br>

5. Lancer la simulation en exécutant les commandes suivantes dans différents terminaux en allant de le workspace hector_kajal_jyotika_ws:</br>
	roslaunch hector_quadrotor_demo outdoor_flight_gazebo.launch</br>
	cd ~/hector_kajal_jyotika_ws</br>
	source devel/setup.bash</br>
	rosservice call /enable_motors "enable: true"</br>
	rosrun kajal_jyotika_drone_control altitude_service.py</br>
	rosservice call /altitude_service "altitude: data: '2'"</br>


<b>Part 3 Régulation en position:</b></br>
1. Aller dans le workspace et exécuter les commandes suivantes dans différents terminaux:</br>
	cd ~/hector_kajal_jyotika_ws </br>
	source devel/setup.bash</br>
	roslaunch hector_quadrotor_demo outdoor_flight_gazebo.launch</br>
	rosservice call /enable_motors "enable: true"</br>
	rosrun kajal_jyotika_drone_control drone_move_service.py</br>
	rosservice call /drone_move_service "altitude:</br>
	  data: '2'</br>
	horizontal_x:</br>
	  data: '3'</br>
	horizontal_y:</br>
	  data: '0'"</br>


<b>Part 4 Planification de mission:</b></br>
1. Aller dans le workspace et exécuter les commandes suivantes dans différents terminaux:</br>
	cd ~/hector_kajal_jyotika_ws</br>
	source devel/setup.bash</br>
	roslaunch hector_quadrotor_demo outdoor_flight_gazebo.launch</br>
	rosservice call /enable_motors "enable: true"</br>
	rosrun kajal_jyotika_drone_control drone_move_service.py</br>
	rosrun kajal_jyotika_drone_control waypoints.py</br>
