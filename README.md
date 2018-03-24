
# Hector Quadrotor Simulator Install
> Instalação do simulador do Hector Quadrotor

Hector Quadrotor was not installed by default on *ROS Kinetic*. To use it, you must install dependencies and compile git code.
> O Hector Quadrotor não está presente na instalação padrão do ROS Kinetic. Para usa-la é necessário instalar as dependências e compilar o código do git.

### Install dependencies :
> Instalando dependências

This is *manual* way to install necessary packages :
>Esta é a maneira manual de instalar os pacotes necessários.

```
sudo apt-get install ros-kinetic-ros-control ros-kinetic-ros-controllers ros-kinetic-gazebo-ros-control ros-kinetic-unique-identifier ros-kinetic-geographic-info ros-kinetic-laser-geometry ros-kinetic-tf-conversions ros-kinetic-tf2-geometry-msgs ros-kinetic-joy libgazebo7 
```

If you want to use `rosdep` and install all dependencies.
> Se preferir você pode instalar as dependências usando *rosdep*.


### Create a workspace and Clone sources
>Criando o espaço de trabalho e Clonando os códigos.

`
mkdir catkin_ws 
`
That tools (wstool) is simular to *git clone* to download sources.
> Essa ferramenta (wstool) é similar ao *git clone* para baixar códigos.

```
wstool init src https://raw.github.com/tu-darmstadt-ros-pkg/hector_quadrotor/kinetic-devel/tutorials.rosinstall
```

`
cd src
`

```
git clone https://github.com/ros-simulation/gazebo_ros_pkgs.git
```

*Install dependencies with* `rosdep` : 
> Instalando dependências que podem está faltando, usando o *rosdep*:

`
cd catkin_ws
`

` rosdep install --from-paths . --ignore-src --rosdistro=kinetic
`

### Build and Environment setup
> Contruir e Configurar o ambiente

`
cd catkin_ws
`

` catkin_make
`

` source devel/setup.bash
`

### Start simulation: 
> Iniciando a simulação
```
roslaunch hector_quadrotor_demo outdoor_flight_gazebo.launch
```
the simulation will be opened on **gazebo** and **rviz**.
> A simulação será aberta no *gazebo* e *rviz*.

### Control: 
>Controle:

You need to open a new shell.
> Você precisa de abrir um novo terminal.

The quadrotor accepts [geometry/Twists](http://docs.ros.org/api/geometry_msgs/html/msg/Twist.html) messages on `cmd_vel` topic. You can send messages via coding, gamepads or keyboard.
> O quadrotor recebe [geometry/Twists](http://docs.ros.org/api/geometry_msgs/html/msg/Twist.html) mensagens no topic *cmd_vel*. Você pode enviar mensagens via codigos, manetes ou teclados.

#### **Gamepads:** 
>Xbox: `roslaunch hector_quadrotor_teleop xbox_controller.launch`<br>
> Logitech: `roslaunch hector_quadrotor_teleop logitech_gamepad.launch joy_dev:=<input>`

 #### **Keyboard:** 
 >`rosrun teleop_twist_keyboard teleop_twist_keyboard.py`


More information on [tutorial](http://wiki.ros.org/hector_quadrotor/Tutorials/Quadrotor%20outdoor%20flight%20demo)
> Você pode ter mais informações em [tutorial](http://wiki.ros.org/hector_quadrotor/Tutorials/Quadrotor%20outdoor%20flight%20demo)
