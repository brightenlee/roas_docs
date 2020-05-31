Basic
=====

What is ROS?
------------

.. figure:: _static/ros.png
   :width: 50%
   :align: center
   :figclass: align-centered
   :alt: jackal

**ROS** (Robot Operating System)는 로봇의 구성 요소를 제어하기 위한 기능들을 제공하는 
오픈 소스 기반의 시스템입니다. ROS 시스템은 노드(Node)라 불리는 분산된 프로세스로 구성되며, 
이 노드는 다른 노드와 메세지를 통해 데이터를 주고받을 수 있습니다.

Why ROS?
--------

ROS는 로봇 관련 다양한 라이브러리 및 패키지와 유용한 개발도구를 제공합니다. 이를 이용하여
개발 시간과 노력을 단축할 수 있어, 많은 분야에서 사용되고 있습니다.  

ROS의 대표적인 특징은 아래와 같습니다.   

**분산 프로세스**

* 각 노드는 독립적으로 실행되면서 유기적으로 데이터를 주고받을 수 있습니다. 

**이기종 하드웨어 간의 데이터 송수신** 

* 메세지 통신만 가능하다면, 운영체제와 프로그래밍 언어에 상관없이 메시지를 통해 
  데이터를 주고받을 수 있습니다. 

**다양한 개발 도구 제공**

* 시각화된 로봇의 외형과 동작 표현 및 센서 데이터를 확인할 수 있는 **RViz**
* 그래프화된 노드, 토픽의 연결 정보 및 센서 데이터를 확인할 수 있고, GUI 개발을 위한 
  Qt 기반의 프레임 워크를 제공하는 **rqt**
* 물리엔진을 탑재하여 3차원 시뮬레이션을 지원하는 **Gazebo** 

**로봇 관련 다양한 기능 제공**

* 다양한 센서 드라이버 
* 로봇 관련 라이브러리 제공 (Geometry, Kinemetic, Reverse Kinemetic 등) 
* 주변을 감지하며 현재 위치를 추종 및 지도를 제작할 수 있는 **SLAM**
* 지도 내에서 장애물을 회피하며 최적의 경로로 목적지를 찾아가는 **Navigation**
* 매니퓰레이터(ManiPulator) 라이브러리와 GUI 형태의 도구를 제공하는 **MoveIt!**

.. figure:: _static/ros/ros_user.png
  :width: 100%
  :align: center
  :figclass: align-centered
  :alt: ros user

  ROS 커뮤니티 사이트의 연도별 사용자 수 (metrics.ros.org) 

Before Start
------------

ROS는 Ubuntu, Linux Mint, Windows, Mac OS 등과 같은 운영체제에서 지원되고 있습니다.
하지만 우분투 LTS 버전과 개발주기를 맞추는 ROS의
`Release <http://wiki.ros.org/Distributions/ReleasePolicy>`_ 정책을 고려했을 때, 
호환성과 안정성이 높은 우분투 LTS 버전과 그에 맞는 ROS 버전을 추천합니다. 

.. tip::

  운영체제: `Ubuntu 18.04.4 LTS (Bionic Beaver) 
  <https://releases.ubuntu.com/18.04.4/?_ga=2.232275679.1396873088.1590573170-1749618178.1590573170>`_

  ROS 버전: `ROS Melodic Morenia <http://wiki.ros.org/melodic>`_

Installing Ubuntu and ROS
+++++++++++++++++++++++++

Ubuntu와 ROS 설치 방법은 아래의 링크를 참고하십시오.

* `Ubuntu 설치 <https://ubuntu.com/tutorials/tutorial-guidelines#1-overview>`_

  .. note::
    Ubuntu 설치 시에 언어는 영어로 선택하는 것을 추천합니다. 파일 경로에 한글이 포함되어 
    있을 경우 정상적으로 설치되지 않는 문제가 발생할 수 있습니다. 또한 에러 메세지를 정확하게 
    파악하기 어렵습니다.

* `ROS 설치 <http://wiki.ros.org/melodic/Installation/Ubuntu>`_

Configuring Environment
+++++++++++++++++++++++

ROS를 사용하기 위해서 필요한 `환경 설정 <http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment>`_
들은 아래와 같습니다.

* **Create ROS Workspace**

  `catkin <http://wiki.ros.org/catkin/conceptual_overview>`_ 은 ROS의 공식 빌드 시스템입니다. 
  사용자는 이를 사용하여 직접 프로젝트를 빌드할 수 있습니다. catkin을 사용하기 위해 아래와
  같이 작업 공간을 설정하십시오.

  .. code-block:: bash

    $ mkdir -p ~/catkin_ws/src
    $ cd ~/catkin_ws/src
    $ catkin_init_workspace

    $ cd ~/catkin_ws/
    $ catkin_make

* **Environment setup**

  ROS를 사용하기 위해서는 ``source`` 명령어를 이용하여 환경 설정 파일을 불러와야 합니다. 터미널 창을
  새로 열 때마다 자동으로 환경 설정 파일을 불러올 수 있도록 ``.bashrc`` 파일을 수정하십시오.

  .. code-block:: bash

    $ vim ~/.bashrc

  자동으로 ROS의 환경 설정 파일과 catkin 작업 공간의 환경 설정 파일을 불러올 수 있도록 ``.bashrc`` 
  파일에 아래의 내용을 추가하십시오.

  .. code-block:: bash

    source /opt/ros/melodic/setup.bash
    source ~/catkin_ws/devel/setup.bash

* **ROS network setup**

  ROS는 분산 컴퓨팅 환경을 제공합니다. 네트워크 구성을 통해서 Master와 다수의 Host의 연결이 
  가능합니다. 이를 위한 `네트워크 설정 <http://wiki.ros.org/ROS/NetworkSetup>`_  방법은 아래와 
  같습니다.

  1. bashrc 스크립트 파일에서 ``ROS_MASTER_URI``, ``ROS_HOSTNAME`` 환경 변수를 설정하십시오. 

  .. code-block:: bash

    $ vim ~/.bashrc

    # Add the following lines
    export ROS_MASTER_URI=http://<MASTER_IP>>:11311
    export ROS_HOSTNAME=<REMOTE_IP>

  2. Hostname과 IP 주소를 매핑하기 위하여 ``/etc/hosts`` 파일에 아래의 내용을 추가합니다.

  .. code-block:: bash

    $ sudo vim ~/.bashrc

    # Add the following line
    <MASTER_IP>    <ROBOT_HOSTNAME>

  .. tip::
    Hostname은 ``hostname`` 명령을 터미널 창에 입력해서 확인할 수 있습니다.
  
Using ROS
---------

* `ROS Tutorials <http://wiki.ros.org/ROS/Tutorials>`_

|