Getting Started
---------------

Turn on Scout
+++++++++++++

* 먼저 로봇 양쪽의 비상 정지 스위치가 눌러져 있는지 확인하고 해제하십시오.
* 후면 패널의 **Q3** 버튼이 눌러져 있는지 확인하고 해제하십시오.
* **Q1** 키 스위치를 켜십시오. 배터리 전압 디스플레이와 전면, 후면 조명이 켜집니다.
* 배터리 전압을 확인하십시오. 배터리 잔량이 적을 경우에 경고음이 울립니다.
* **Q3** 버튼을 누르십시오.

Log In
++++++

로봇이 네트워크에 연결되면, ssh를 이용해서 원격으로 접속할 수 있습니다.

::

  $ sudo apt install ssh
  $ ssh scout@<ROBOT_IP>

**<ROBOT_IP>** 는 로봇 PC의 IPv4 네트워크 주소이고, 로봇 PC의 비밀번호는 **onground** 입니다.

.. note::
  로봇을 네트워크에 연결하기 위해서 모니터가 필요합니다.

ROS Network Setup
+++++++++++++++++

ROS는 분산 컴퓨팅 환경으로, 외부 디바이스에서 원격으로 ROS 인터페이스에 접근할 수 있습니다.
`ROS 네트워크 설정 <http://wiki.ros.org/ROS/NetworkSetup>`_  방법은 아래와 같습니다.

1. bashrc 스크립트 파일에서 **ROS_MASTER_URI**, **ROS_HOSTNAME** 환경 변수를 설정합니다. 

::

  $ vim ~/.bashrc

  # Add the following lines
  export ROS_MASTER_URI=http://<ROBOT_IP>:11311
  export ROS_HOSTNAME=<REMOTE_IP>

**<ROBOT_IP>** 는 로봇 PC의 IP 주소이고, **<REMOTE_IP>** 는 원격 PC의 IP 주소입니다.

2. Hostname과 IP 주소를 매핑하기 위하여 **/etc/hosts** 파일에 항목을 추가합니다.

  ::

    $ sudo vim ~/.bashrc

    # Add the following line
    <ROBOT_IP>    <ROBOT_HOSTNAME>

**<ROBOT_IP>** 는 로봇 PC의 IP 주소이고, **<ROBOT_HOSTNAME>** 는 로봇 PC의 Hostname 입니다. 
일반적으로 Hostname은 로봇의 시리얼 넘버로 설정되어 있습니다.

Visualize Data
++++++++++++++

ROS 네트워크 설정이 완료되면 원격 PC에서 rostopic 데이터를 확인할 수 있습니다. 
또한 `RViz <http://wiki.ros.org/rviz>`_ 를 이용하여 시각화된 데이터를 확인할 수 있습니다.

  ::

    $ rviz

.. figure:: _static/rviz.png
   :width: 100%
   :align: center
   :figclass: align-centered
   :alt: rviz

|