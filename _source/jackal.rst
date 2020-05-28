Jackal
======

Introduction
------------

.. figure:: _static/jackal/jackal.png
   :width: 100%
   :align: center
   :figclass: align-centered
   :alt: jackal

Jackal은 견고하고 가벼우며, 사용하기 쉬운 ROS 기반의 UGV입니다.
Jackal에는 IMU, GPS, PC가 포함되어 있습니다. 또한 URDF, 시뮬레이션, 데모 어플리케이션을 포함한
ROS 인터페이스를 제공하고 있습니다.

:download:`Download Jackal User Manual <_static/jackal/Jackal_User_Manual.pdf>`

:download:`Download Jackal Data Sheet <_static/jackal/Jackal_Data_Sheet.pdf>`

|

Technical Specifications
++++++++++++++++++++++++

.. figure:: _static/jackal/jackal_specifications.png
   :width: 100%
   :align: center
   :figclass: align-centered
   :alt: jackal specifications

|

What's Included
++++++++++++++++

+------------------------------------+----------+
| Name                               | Quantity |
+====================================+==========+
| Jackal UGV                         | 1        |
+------------------------------------+----------+
| 270 watt-hour lithium battery pack | 1        |
+------------------------------------+----------+
| 110V/220V universal charger        | 1        |
+------------------------------------+----------+
| Sony Bluetooth controller          | 1        |
+------------------------------------+----------+
| Jackal User Manual                 | 1        |
+------------------------------------+----------+

Expansions
''''''''''
Jackal의 기능을 확장하려면 **OnGround Robotics** 에서 제공하는 다음 액세서리를 고려하십시오.

* Spare Battery
* IMU
* LIDAR
* Camera
* GPS
* Onboard PC
* NVIDIA Jetson

|

Hardware Overview
-----------------

로봇의 외부 구성 요소로는 직경 190mm 바퀴, HMI 패널, 마운팅 상판이 있습니다.
HMI 패널은 아래 그림과 같으며, 왼쪽부터 모터 버튼, 통신, WiFi, 배터리 표시기 및
전원 버튼이 있습니다.

.. figure:: _static/jackal/jackal_hmi.png
   :width: 70%
   :align: center
   :figclass: align-centered
   :alt: hmi

   Jackal HMI

로봇의 내부에 접근하려면 로봇 전면 아래에 있는 래치를 이용하여 상판 덮개를 열어야 합니다.
Anderson Power Pole 커넥터는 로봇에 전원을 공급하기 위한 커넥터로, 로봇이 작동하려면 연결되어 
있어야 합니다. 흰색 Molex 커넥터는 배터리 충전을 위한 커넥터입니다. 로봇 후면에 있는 충전 단자를 
이용하거나, 배터리 충전기에 직접 연결하여 배터리를 충전할 수 있습니다.
두 커넥터 모두 로봇과 연결되어 있어야 합니다.

.. figure:: _static/jackal/jackal_battery_area.png
   :width: 90%
   :align: center
   :figclass: align-centered
   :alt: battery area

   Jackal battery area

로봇의 트레이를 고정하고 있는 나사를 풀면 트레이를 내릴 수 있습니다. 
로봇의 PC, 사용자를 위한 전원 보드, 추가 하드웨어 장착을 위한 공간을 확인할 수 있습니다.
트레이의 구성 요소와 사용자 전원 보드에 대한 내용은 아래 그림을 참조하십시오.
사용자 전원 보드는 4핀 Molex 단자와 스크류 터미널 단자로 제공됩니다.

.. figure:: _static/jackal/jackal_tray.png
   :width: 90%
   :align: center
   :figclass: align-centered
   :alt: tray

   Jackal tray

.. figure:: _static/jackal/jackal_user_power.png
   :width: 90%
   :align: center
   :figclass: align-centered
   :alt: user power

   User power

System Architecture
-------------------

Jackal은 32bit MCU와 Ubuntu가 설치된 x86 PC를 기반으로 구성되어 있습니다. 
MCU는 IMU, GPS로부터 데이터를 수신하고, IO 제어, 전원 공급 모니터링, 모터 제어 기능을 수행합니다.

MCU와 PC는 USB 연결을 이용하여 통신합니다. 통신 프로토콜으로는 rosserial을 사용하고,
rosserial_server 노드는 jackal_base 노드에 포함되어 있습니다. 로봇이 제공하는 ROS API는 아래 표와 같습니다.

.. 
  +--------------------+-----------------------------+----------------------------------------------------------------------------------+
  | Topic              | Message Type                | Purpose                                                                          |
  +====================+=============================+==================================================================================+
  | /cmd_vel           | geometry_msgs/Twist         | 로봇 구동을 위한  입력 토픽                                                      |
  +--------------------+-----------------------------+----------------------------------------------------------------------------------+
  | /odometry/filtered | nav_msgs/Odometry           | robot_localization 노드로부터 퍼블리싱되는 토픽. 엔코더, IMU, GPS를 이용하여 추정|
  +--------------------+-----------------------------+----------------------------------------------------------------------------------+
  | /imu/data          | sensor_msgs/IMU             | imu_filter_madgwick 노드로부터 퍼블리싱되는 토픽. IMU 데이터를 이용하여 방향 추정|
  +--------------------+-----------------------------+----------------------------------------------------------------------------------+
  | /navsat/fix        | geometry_msgs/TwistStamped  | GPS로부터 수신 받은 위치 데이터                                                  |
  +--------------------+-----------------------------+----------------------------------------------------------------------------------+
  | /navsat/vel        | geometry_msgs/TwistStamped  | GPS로부터 수신 받은 속도 데이터                                                  |
  +--------------------+-----------------------------+----------------------------------------------------------------------------------+
  | /cmd_drive         | jackal_msgs/Drive           | 로봇 컨트롤러의 출력. MCU로 전달되는 명령 데이터                                 |
  +--------------------+-----------------------------+----------------------------------------------------------------------------------+
  | /feedback          | jackal_msgs/Feedback        | 엔코더, 모터의 피드백 데이터                                                     |
  +--------------------+-----------------------------+----------------------------------------------------------------------------------+
  | /status            | jackal_msgs/Status          | 로봇의 전반적인 상태 데이터. diagnostics 노드로 전달                             |
  +--------------------+-----------------------------+----------------------------------------------------------------------------------+

+------------------------+--------------------------------+------------------------------------------------------+
| Topic                  | Message Type                   | Purpose                                              |
+========================+================================+======================================================+
| ``/cmd_vel``           | ``geometry_msgs/Twist``        | Input to Jackal’s kinematic controller.              |
|                        |                                | Publish here to make Jackal go.                      |
+------------------------+--------------------------------+------------------------------------------------------+
| ``/odometry/filtered`` | ``nav_msgs/Odometry``          | Published by robot_localization, a filtered          |                        
|                        |                                | localization estimate based on wheel odometry        |
|                        |                                | (encoders), integrated IMU, and integrated GPS.      |
+------------------------+--------------------------------+------------------------------------------------------+
| ``/imu/data``          | ``sensor_msgs/IMU``            | Published by imu_filter_madgwick, an                 |
|                        |                                | orientation estimate based on Jackal’s               |
|                        |                                | internal gyroscope, accelerometer, and magnetometer. |
+------------------------+--------------------------------+------------------------------------------------------+
| ``/navsat/fix``        | ``geometry_msgs/TwistStamped`` | Position fix from Jackal’s built in GPS receiver.    |
+------------------------+--------------------------------+------------------------------------------------------+
| ``/navsat/vel``        | ``geometry_msgs/TwistStamped`` | Velocity over ground according to the integrated     |
|                        |                                | GPS receiver.                                        |
+------------------------+--------------------------------+------------------------------------------------------+
| ``/cmd_drive``         | ``jackal_msgs/Driv``           | Output from Jackal’s kinematic controller, input     |
|                        |                                | to the motor controllers. Subscribe here for a       |
|                        |                                | lower-level look at what’s going on.                 |
+------------------------+--------------------------------+------------------------------------------------------+
| ``/feedback``          | ``jackal_msgs/Feedback``       | High-frequency inputs from Jackal’s encoders and     |
|                        |                                | motor current sensors.                               |
+------------------------+--------------------------------+------------------------------------------------------+
| ``/status``            | ``jackal_msgs/Status``         | Low-frequency status data for Jackal’s systems.      |
|                        |                                | This information is republished in human readable    |
|                        |                                | from on the diagnostics topic and is best consumed   |
|                        |                                | with the Robot Monitor.                              |
+------------------------+--------------------------------+------------------------------------------------------+

|

Getting Started
---------------

첫번째 단계는 로봇의 전원을 켜고, 수동으로 조작하는 것입니다. 로봇의 포장을 처음으로 풀었다면,
로봇의 상판 덮개를 열어서 배터리를 연결해야 합니다.

로봇 HMI의 전원 버튼을 누르면 LED가 점등됩니다. PC 부팅이 완료되면 통신 표시기의 LED가 
점등됩니다. 부팅이 완료될 때까지 약 30초가 걸립니다.

Sony Bluetooth 컨트롤러의 PS 로고 버튼을 눌러 컨트롤러와 로봇을 연결합니다. 페어링이 완료되면
컨트롤러의 전면에 LED가 점등됩니다. L1 트리거 버튼(Deadman Switch)을 누른 상태에서,
왼쪽 아날로그 스틱을 앞으로 밀면 로봇이 구동됩니다. R1 트리거 버튼(Turbo)을 누른 상태에서
조작하면, 로봇의 최대 속도가 증가합니다. 컨트롤러의 구성은 아래와 같습니다.

.. figure:: _static/jackal/jackal_controller.png
   :width: 90%
   :align: center
   :figclass: align-centered
   :alt: controller

   Sony bluetooth controller

Wireless Access
+++++++++++++++

로봇을 로컬 WiFi에 연결하려면, 먼저 유선 연결을 사용하여 내부 PC에 접속해야 합니다.
상판 덮개를 열고 트레이를 내린 다음, 이더넷 케이블을 PC의 LAN 포트에 연결하십시오.

Static IP Configuration
'''''''''''''''''''''''

사용자 PC의 IP 주소를 192.168.1.51과 같은 고정 IP로 설정하십시오. Ubuntu 환경에서의
작업 과정을 아래와 같습니다.

1. 오른쪽 상단의 아이콘들을 클릭하고, ``Wired Connected`` - ``Wired Settings`` 을 선택하십시오.
2. ``Wired`` 항목에서 ``+`` 버튼을 눌러 새로운 항목을 추가하십시오.
3. ``IPv4`` 탭을 선택하고 ``IPv4 Method`` 항목 중에서 ``Manual`` 을 선택하십시오.
4. ``Addresses`` 항목에 아래와 같이 ``Address`` 와 ``Netmask`` 를 입력하십시오.

.. figure:: _static/jackal/jackal_wired_connection.png
   :width: 70%
   :align: center
   :figclass: align-centered
   :alt: wired connection

   Wired connection setup

Connect to Jackal via SSH over ethernet
'''''''''''''''''''''''''''''''''''''''

다음 단계는 SSH를 이용하여 로봇에 연결하는 것입니다. 아래 명령어를 터미널 창에 입력하십시오.
비밀번호는 ``clearpath`` 입니다.

::

   $ ssh administrator@192.168.1.11

Connect Jackal to Wireless Network
''''''''''''''''''''''''''''''''''

SSH를 이용하여 로봇과 연결되면, 로컬 WiFi 네트워크를 설정할 수 있습니다. 이를 위해
WICD(wireless interface configuration deamon)을 이용합니다. 아래 명령어를 터미널 창에
입력하십시오.

::

   $ wicd-curses

.. note::
   기본 옵션으로 제공되는 PC에는 우분투 서버 버전이 설치되어 있습니다. GUI를 지원하지 않으므로, 
   터미널 창을 이용하여 모든 과정을 진행해야 합니다.

연결 가능한 네트워크들의 목록이 화면에 표시됩니다. 화살표 키를 이용하여 선택하고, 오른쪽 화살표 키를
누르면 설정창으로 이동됩니다. 대부분의 최신 네트워크는 WPA1/2 암호화 체계를 사용하므로, 이 옵션을
선택하고 비밀번호를 입력하십시오. 설정을 모두 마치면 ``F10`` 을 눌러 저장하고, ``C`` 를 눌러 
연결할 수 있습니다.

이제 무선 네트워크 IP와 SSH를 이용하여 로봇과 연결할 수 있습니다. 먼저 아래 명령어를 이용하여
IP 주소를 확인하십시오.

::

   $ ifconfig

확인된 무선 네트워크 IP와 SSH를 이용하여 다시 연결하십시오. 현재 연결된 SSH는 ``exit`` 명령어를
이용하여 종료할 수 있습니다.

::

   $ ssh administrator@<IP_OF_JACKAL>

이제 SSH를 이용하여 로봇의 PC를 제어할 수 있습니다. 패키지 다운로드, 업데이트 실행, 
파일 전송, 제거 등을 수행할 수 있습니다.

|

Remote ROS Connectivity
+++++++++++++++++++++++

ROS 인터페이스를 사용하기 위해서는, 원격 PC가 로봇의 ROS 마스터와 연결되어야 합니다.
이를 통해 원격 PC에서 ``rostopic list``, ``rostopic echo``, ``rosnode list`` 와 같은 ROS 
명령을 실행할 수 있습니다.

이를 위한 `ROS 네트워크 설정 <http://wiki.ros.org/ROS/NetworkSetup>`_  방법은 아래와 같습니다.

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

.. tip::
   Hostname은 ``hostname`` 명령을 터미널 창에 입력해서 확인할 수 있습니다.

|

Jackal Desktop Packages
+++++++++++++++++++++++

원격 PC에서 로봇을 제어하거나 모니터링하려면, 먼저 ROS를 설치해야 합니다.
자세한 내용은 `ROS Wiki <http://wiki.ros.org/melodic/Installation/Ubuntu>`_ 를 참고하십시오.

ROS를 설치한 후에, 아래 명령어를 이용하여 Jackal Desktop 패키지를 설치할 수 있습니다.

::

   $ sudo apt install ros-melodic-jackal-desktop

ROS 네트워크 설정을 마쳤으면 ROS에서 제공하는 시각화 도구인 `RViz <http://wiki.ros.org/rviz>`_
를 사용할 수 있습니다.

::

   $ roslaunch jackal_viz view_robot.launch

또한 로봇의 상태를 진단, 감시할 수 있는 RQT Robot Monitor를 실행할 수 있습니다.

::

  $ rosrun rqt_robot_monitor rqt_robot_monitor

|