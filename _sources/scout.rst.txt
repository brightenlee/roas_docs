Scout
=====

Introduction
------------

.. figure:: _static/scout/scout.png
  :width: 100%
  :align: center
  :figclass: align-centered
  :alt: scout

.. figure:: _static/scout/customized_scout.png
  :width: 100%
  :align: center
  :figclass: align-centered
  :alt: customized scout

Scout은 다양한 응용 시나리오를 고려한 다목적 UGV로 설계되었습니다.
``CAN``, ``RS232`` 통신을 지원하며, 2차 연구개발을 위하여 ``ROS``, ``ROS2(Beta)`` 를 지원합니다.
Navigation, Computer Vision 어플리케이션을 위하여 Stereo Camera, Lidar, GPS, IMU, Manipulator 등과 
같은 추가 구성 요소들을 Scout에 설치할 수 있습니다.
이를 바탕으로 자율 주행 교육 및 연구, 실내외 보안 순찰, 환경 모니터링 등의 목적으로 사용할 수 있습니다.

:download:`Download Scout User Manual <_static/scout/Scout_2.0_User_Manual.pdf>`

|

Component List
++++++++++++++

+-----------------------------+----------+
| Name                        | Quantity |
+=============================+==========+
| Robot body                  | x 1      |
+-----------------------------+----------+
| Battery charger (AC 220V)   | x 1      |
+-----------------------------+----------+
| Aviation plug (male, 4-pin) | x 2      |
+-----------------------------+----------+
| USB to RS232 cable          | x 1      |
+-----------------------------+----------+
| Remote control transmitter  | x 1      |
+-----------------------------+----------+

|

Tech Specifications
+++++++++++++++++++

+---------------------------------------+-----------------------------------------------+
| Specs                                 | Values                                        |
+=======================================+===============================================+
| L × W × H (mm)                        | 930 x 699 x 348                               |
+---------------------------------------+-----------------------------------------------+
| Front and rear wheels separation (mm) | 498                                           |
+---------------------------------------+-----------------------------------------------+
| Right and left wheels separation (mm) | 583                                           |
+---------------------------------------+-----------------------------------------------+
| Weight of vehicle body (kg)           | 62                                            |
+---------------------------------------+-----------------------------------------------+
| Battery type                          | Lithium battery 24V 30aH                      |
+---------------------------------------+-----------------------------------------------+
| Motor                                 | DC brushless 4 X 200W                         |
+---------------------------------------+-----------------------------------------------+
| Reduction gearbox                     | 1:30                                          |
+---------------------------------------+-----------------------------------------------+
| Drive type                            | Independent four-wheel drive                  |
+---------------------------------------+-----------------------------------------------+
| Suspension                            | Independent suspension with single rocker arm |
+---------------------------------------+-----------------------------------------------+
| Steering                              | Four-wheel differential steering              |
+---------------------------------------+-----------------------------------------------+
| Safety equipment                      | Servo brake/anti-collision tube               |
+---------------------------------------+-----------------------------------------------+
| No-load highest speed (m/s)           | ≤ 1.5                                         |
+---------------------------------------+-----------------------------------------------+
| Minimum turning radius                | Be able to turn on a pivot                    |
+---------------------------------------+-----------------------------------------------+
| Maximum climbing capacity             | ≥ 30°                                         |
+---------------------------------------+-----------------------------------------------+
| Minimum ground clearance (mm)         | 135                                           |
+---------------------------------------+-----------------------------------------------+
| Control mode                          | Remote control / Control command mode         |
+---------------------------------------+-----------------------------------------------+
| RC transmitter                        | 2.4G/extreme distance 1km                     |
+---------------------------------------+-----------------------------------------------+
| Communication interface               | CAN / RS232                                   |
+---------------------------------------+-----------------------------------------------+

|

Overview
--------

.. figure:: _static/scout/scout_front_view.png
  :width: 90%
  :align: center
  :figclass: align-centered
  :alt: front view

  Scout front view

.. figure:: _static/scout/scout_rear_view.png
  :width: 100%
  :align: center
  :figclass: align-centered
  :alt: rear view

  Scout rear view

충돌 방지 펜스는 로봇 주위에 설치되어 충돌시 차체의 손상을 줄입니다.

조명은 로봇의 전면과 후면에 설치되어 있습니다. 
전면에는 백색 조명이 설치되어 있고, 후면에는 적색 조명이 설치되어 있습니다.

로봇 양쪽에 비상 정지 스위치가 설치되어 있습니다.
로봇이 비정상적으로 동작 할 때 로봇의 전원을 즉시 차단할 수 있습니다.

DC 전원 및 통신 인터페이스를 위한 방수 커넥터는 로봇의 상단과 후면에 있습니다.
로봇과 외부 구성 요소를 유연하게 연결할 수 있고, 외부 요인으로부터 로봇 내부를 보호할 수 있습니다.
로봇의 상단에는 알루미늄 프로파일이 설치되어 있어, 추가 디바이스들을 쉽게 설치할 수 있습니다.

|

Indication
++++++++++

사용자는 전압 디스플레이, 신호음 및 조명을 통해서 로봇의 상태를 확인할 수 있습니다.

* **Voltage:** 배터리의 현재 전압은 로봇 후면에 있는 인터페이스에서 확인할 수 있습니다. 
  전압은 1V 단위로 표시됩니다.

* **Battery:** 배터리 전압이 22.5V보다 낮으면 경고음이 울립니다. 배터리 전압이 22V보다 
  낮아지면 로봇은 전원 공급을 차단하여 배터리 손상을 방지합니다. 

* **Power on:** 로봇 전면과 후면의 조명이 켜집니다. 

|

Electrical Interface
++++++++++++++++++++

Scout은 4핀 항공 커넥터 2개와 DB9(RS232) 커넥터 1개를 제공합니다.
로봇의 상단과 후면에 항공 커넥터가 있으며, 전원 단자와 CAN 통신 단자로 구성되어 있습니다.

.. warning::

   배터리의 전압이 일정 전압 아래로 떨어지면 전원 공급이 차단됩니다.

Top Electrical Interface
''''''''''''''''''''''''

.. figure:: _static/scout/scout_top_electrical_interface.png
  :width: 100%
  :align: center
  :figclass: align-centered
  :alt: top electrical interface

  Top electrical interface

|

.. image:: _static/scout/scout_top_aviation_connector.png
  :width: 25%
  :align: left
  :alt: top aviation connector

* Top aviation connector

+---------+----------+-------------------------+-------------------------------+
| Pin No. | Pin Type | Function and Definition | Remarks                       |
+=========+==========+=========================+===============================+
| 1       | Power    | VCC                     | Power positive, 23-29.2V, 10A |
+---------+----------+-------------------------+-------------------------------+
| 2       | Power    | GND                     | Power negative                |
+---------+----------+-------------------------+-------------------------------+
| 3       | CAN      | CAN_H                   | CAN bus high                  |
+---------+----------+-------------------------+-------------------------------+
| 4       | CAN      | CAN_L                   | CAN bus low                   |
+---------+----------+-------------------------+-------------------------------+

|

.. image:: _static/scout/scout_top_db9_connector.png
  :width: 25%
  :align: left
  :alt: top db9 connector

* Top db9 connector

+---------+------------+
| Pin No. | Definition |
+=========+============+
| 2       | RS232-RX   |
+---------+------------+
| 3       | RS232-TX   |
+---------+------------+
| 5       | GND        |
+---------+------------+



|

Rear Electrical Interface
'''''''''''''''''''''''''

.. figure:: _static/scout/scout_rear_electrical_interface.png
  :width: 100%
  :align: center
  :figclass: align-centered
  :alt: rear electrical interface

  Rear electrical interface

+-----+----------------------------------------+
| No. | Definition                             |
+=====+========================================+
| Q1  | Main electrical switch                 |
+-----+----------------------------------------+
| Q2  | Charging interface                     |
+-----+----------------------------------------+
| Q3  | Power supply switch of drive system    |
+-----+----------------------------------------+
| Q4  | DB9 serial port                        |
+-----+----------------------------------------+
| Q5  | Interface for CAN and 24V power supply |
+-----+----------------------------------------+
| Q6  | Display of battery voltage             |
+-----+----------------------------------------+

|

.. image:: _static/scout/scout_rear_aviation_connector.png
  :width: 25%
  :align: left
  :alt: rear aviation connector

* Rear aviation connector

+---------+----------+-------------------------+-------------------------------+
| Pin No. | Pin Type | Function and Definition | Remarks                       |
+=========+==========+=========================+===============================+
| 1       | Power    | VCC                     | Power positive, 23-29.2V, 5A  |
+---------+----------+-------------------------+-------------------------------+
| 2       | Power    | GND                     | Power negative                |
+---------+----------+-------------------------+-------------------------------+
| 3       | CAN      | CAN_H                   | CAN bus high                  |
+---------+----------+-------------------------+-------------------------------+
| 4       | CAN      | CAN_L                   | CAN bus low                   |
+---------+----------+-------------------------+-------------------------------+

|

Remote Control
++++++++++++++

.. figure:: _static/scout/scout_rc_transmitter.png
  :width: 70%
  :align: center
  :figclass: align-centered
  :alt: rc transmitter

  RC transmitter

RC 조종기를 이용하여 로봇을 수동으로 조작할 수 있습니다. 
모든 스위치를 중립 상태(상단으로 위치)로 두고, 두 개의 전원 버튼을 누르면 조종기를 켤 수 있습니다.
조종기에는 2개의 스로틀이 있습니다. S1과 S2를 이용하여 각각 선속도과 각속도 명령을 보낼 수 있습니다.
SWB 스위치를 중간 위치에 있으면 원격 제어 모드가 활성화되고, 하단 위치에 있으면 명령 모드가
활성화됩니다.
SWC 스위치를 이용하면 조명 제어 모드(NC, NO, BL)를 전환할 수 있습니다.

|

Light Control
+++++++++++++

로봇의 전면과 후면에 조명이 설치되어 있으며, 제어 인터페이스는 사용자에게 개방되어 있습니다.

* **NC:** 조명이 항시 꺼집니다.

* **NO:** 조명이 항시 켜집니다.

* **BL:** 조명이 점차적으로 켜졌다가 꺼졌다가를 반복합니다.

* **CUSTOM:** 지정한 밝기로 조명이 켜집니다.

|

Coordinate System
++++++++++++++++++

.. figure:: _static/scout/scout_coordinate.png
  :width: 90%
  :align: center
  :figclass: align-centered
  :alt: coordinate

  Coordinate

Scout의 기준 좌표계는 위와 같습니다. 로봇의 차체는 좌표계의 X축과 평행합니다.

|

Charging
++++++++

사용자에게 로봇과 함께 10A 배터리 충전기를 제공합니다.
충전 절차는 아래와 같습니다.

1. 로봇의 전원이 꺼져 있는지 확인하십시오.
2. 로봇 후면의 충전 인터페이스와 배터리 충전기의 플러그를 연결하십시오.
3. 배터리 충전기의 전원을 켜십시오.

.. note::

   현재 배터리의 전압이 22V인 경우, 완전히 재충전하는데 약 3~5시간이 필요합니다.
   완전 충전된 배터리의 전압은 26.5V 입니다.

|

Development
+++++++++++

Scout은 사용자가 개발할 수 있도록 ``CAN``, ``RS232`` 통신 인터페이스를 제공합니다.
통신 인터페이스를 이용하여 사용자가 직접 로봇을 제어할 수 있습니다.

|

Dimensions
+++++++++++

.. figure:: _static/scout/scout_dimensions.png
  :width: 90%
  :align: center
  :figclass: align-centered
  :alt: dimensions

  Dimensions

ROS Packages
------------

Scout의 ``ROS`` 인터페이스를 구성하고 있는 패키지들은 다음과 같습니다.

* ``scout_base`` :
  로봇 MCU와의 시리얼 통신을 위한 패키지입니다. 
  그리고 피드백 데이터를 바탕으로 구현된 진단(diagnostic) 노드를 포함하고 있습니다. 

* ``scout_base_controller`` :
  Differential drive controller를 구현한 패키지입니다.

* ``scout_bringup`` :
  로봇의 전체 ROS 시스템을 실행시키는 실행(launch) 파일과 설정 파일을 포함하고 있습니다.

.. note::

  scout_bringup 패키지에 있는 실행 파일(``scout_bringup.launch``)을 이용해서
  전체 ROS 시스템을 실행 시킬 수 있습니다. 그리고 실행 파일의 ``robot_name`` 
  변수 설정틀 통해서 로봇의 모델(Scout V1, V2, Mini)을 선택할 수 있습니다.

* ``scout_description`` :
  로봇의 좌표 체계를 정의한 URDF 파일과 시각화를 위한 3D mesh 파일을 포함하고 있습니다.

* ``scout_navigation`` :
  SLAM, Navigation 기능에 대한 설정, 실행 파일을 포함하고 있습니다.

* ``scout_teleop`` :
  블루투스 컨트롤러를 이용해서 로봇을 원격 조작할 수 있는 패키지입니다.

|

ROS API Overview
----------------

사용자가 상위 어플리케이션을 쉽게 개발할 수 있도록 ``ROS`` 표준 인터페이스를 제공합니다.
`REPs(ROS Enhancement Proposals) <https://www.ros.org/reps/rep-0000.html>`_ 를 
준수하여 호환성과 접근성을 높였습니다.

Feedback Interface
++++++++++++++++++

로봇의 피드백 데이터에는 3가지가 있습니다. 로봇 베이스에 대한 피드백, 모터에 대한 피드백,
조명 제어에 대한 피드백이 있습니다.

* **rostopic name:** ``/scout_base/base_feedback``

.. code::

  Header header

  string robot_name

  BaseState base_state
    string state             # NORMAL, STOP
    string control_mode      # REMOTE, CAN, SERIAL, NONE
    float64 battery_voltage  # Actual voltage (V)
    string battery_state     # Under-voltage, Over-voltage

  float64 linear_speed   # Linear speed (m/s)
  float64 angular_speed  # Angular speed (rad/s)

* **rostopic name:** ``/scout_base/motor_feedback``

.. code::

  Header header

  MotorState[4] motor_states
    string id             # front_right, front_left, rear_left, rear_right
    float64 current       # Actual current (A)
    float64 velocity      # Actual speed of motor (rad/s)
    float64 temperature   # Actual temperature of motor (C)
    string communication  # Communication state with motor

  string current_state      # Current state of motors
  string temperature_state  # Temperature state of motors

* **rostopic name:** ``/scout_base/light_feedback``

.. code::

  Header header
  
  bool control_enable  # Lighting control enable flag

  LightState[2] light_states
    string id         # FRONG, REAR
    string mode       # The current mode (NC, NO, BL, CUSTOM)
    uint8 brightness  # The current brightness of light (0 - 100)

Diagnostic Interface
++++++++++++++++++++

사용자가 로봇의 상태를 모니터링할 수 있도록 진단(diagnostic) 정보를 제공합니다.
진단 정보는 topic과 rqt gui를 이용해서 확인할 수 있습니다.
rqt gui를 실행시키는 명령어는 아래와 같습니다.

::

  $ rosrun rqt_robot_monitor rqt_robot_monitor

Base Interface
++++++++++++++

로봇은 `geometry_msgs/Twist <http://docs.ros.org/api/geometry_msgs/html/msg/Twist.html>`_ 
메세지 타입의 ``/scout_base_controller/cmd_vel`` 토픽을 구독(subscribe)합니다. 
사용자는 이 토픽을 이용해서 로봇을 제어할 수 있습니다.

사용자는 /scout_base_controller/cmd_vel 토픽을 바로 이용할 수 있지만,
일반적으로 어플리케이션은 /teleop/cmd_vel, /move_base/cmd_vel, /cmd_vel 토픽을 이용합니다.
이 토픽들의 데이터는 설정된 우선 순위에 따라 /scout_base_controller/cmd_vel 토픽으로 전달됩니다.
이와 같은 mux 시스템은 `twist_mux <http://wiki.ros.org/twist_mux>`_ 패키지를 이용하여
구현되어 있습니다.

Light Interface
+++++++++++++++

로봇의 전면과 후면에 설치되어 있는 조명의 제어 인터페이스는 사용자에게 개방되어 있습니다.
사용자는 ``/scout_base/light_command`` 토픽을 이용해서 조명을 제어할 수 있습니다.

.. code::

  # Lighting Mode
  # 0: NC / 1: NO / 2: BL / 3: CUSTOM

  uint8 front_mode        # Lighting Mode
  uint8 front_brightness  # Only for CUSTOM mode

  uint8 rear_mode         # Lighting Mode
  uint8 rear_brighteness  # Only for CUSTOM mode

|

Getting Started
---------------

Turn on Scout
+++++++++++++

* 먼저 로봇 양쪽의 비상 정지 스위치가 눌러져 있는지 확인하고 해제하십시오.
* 후면 패널의 ``Q3`` 버튼이 눌러져 있는지 확인하고 해제하십시오.
* ``Q1`` 키 스위치를 켜십시오. 배터리 전압 디스플레이와 전면, 후면 조명이 켜집니다.
* 배터리 전압을 확인하십시오. 배터리 잔량이 적을 경우에 경고음이 울립니다.
* ``Q3`` 버튼을 누르십시오.

Log In
++++++

로봇이 네트워크에 연결되면, ssh를 이용해서 원격으로 접속할 수 있습니다.

::

  $ sudo apt install ssh
  $ ssh scout@<ROBOT_IP>

``<ROBOT_IP>`` 는 로봇 PC의 IPv4 네트워크 주소이고, 로봇 PC의 비밀번호는 ``onground`` 입니다.

.. note::
  로봇을 네트워크에 연결하기 위해서 모니터가 필요합니다.

ROS Network Setup
+++++++++++++++++

ROS는 분산 컴퓨팅 환경으로, 외부 디바이스에서 원격으로 ROS 인터페이스에 접근할 수 있습니다.
`ROS 네트워크 설정 <http://wiki.ros.org/ROS/NetworkSetup>`_  방법은 아래와 같습니다.

1. bashrc 스크립트 파일에서 ``ROS_MASTER_URI``, ``ROS_HOSTNAME`` 환경 변수를 설정합니다. 

.. code-block:: bash

  $ vim ~/.bashrc

  # Add the following lines
  export ROS_MASTER_URI=http://<ROBOT_IP>:11311
  export ROS_HOSTNAME=<REMOTE_IP>

``<ROBOT_IP>`` 는 로봇 PC의 IP 주소이고, ``<REMOTE_IP>`` 는 원격 PC의 IP 주소입니다.

2. Hostname과 IP 주소를 매핑하기 위하여 ``/etc/hosts`` 파일에 항목을 추가합니다.

.. code-block:: bash

  $ sudo vim ~/.bashrc

  # Add the following line
  <ROBOT_IP>    <ROBOT_HOSTNAME>

``<ROBOT_IP>`` 는 로봇 PC의 IP 주소이고, ``<ROBOT_HOSTNAME>`` 는 로봇 PC의 Hostname 입니다. 
일반적으로 Hostname은 로봇의 시리얼 넘버로 설정되어 있습니다.

Visualize Data
++++++++++++++

ROS 네트워크 설정이 완료되면 원격 PC에서 rostopic 데이터를 확인할 수 있습니다. 
또한 `RViz <http://wiki.ros.org/rviz>`_ 를 이용하여 시각화된 데이터를 확인할 수 있습니다.

::

  $ rviz

.. figure:: _static/scout/scout_rviz.png
  :width: 100%
  :align: center
  :figclass: align-centered
  :alt: rviz

  RViz

|