Husky
======

Introduction
------------

.. figure:: _static/husky/husky.png
   :width: 100%
   :align: center
   :figclass: align-centered
   :alt: husky

Husky는 견고하고 사용하기 쉬운 ROS 기반의 UGV입니다. Husky는 프로토 타입 개발과
리서치 어플리케이션 개발에 적합합니다.

:download:`Download Husky User Manual <_static/husky/Husky_User_Manual.pdf>`

:download:`Download Husky Data Sheet <_static/husky/Husky_Data_Sheet.pdf>`

|

Technical Specifications
++++++++++++++++++++++++

.. figure:: _static/husky/husky_specifications.png
   :width: 100%
   :align: center
   :figclass: align-centered
   :alt: husky specifications


|

What's Included
++++++++++++++++

+-----------------------------------+----------+
| Name                              | Quantity |
+===================================+==========+
| Husky UGV                         | 1        |
+-----------------------------------+----------+
| 24V Sealed Lead-Acid Battery Pack | 1        |
+-----------------------------------+----------+
| Battery Door Cover                | 1        |
+-----------------------------------+----------+
| Battery Charger                   | 1        |
+-----------------------------------+----------+
| Lockout Key                       | 2        |
+-----------------------------------+----------+
| Power Connector                   | 3        |
+-----------------------------------+----------+

Expansions
''''''''''
Husky의 기능을 확장하려면 **OnGround Robotics** 에서 제공하는 다음 액세서리를 고려하십시오.

* Spare Battery
* IMU
* LIDAR
* Camera
* GPS
* Onboard PC
* NVIDIA Jetson
* Robot Arm

|

Hardware Overview
-----------------

.. figure:: _static/husky/husky_front.png
   :width: 100%
   :align: center
   :figclass: align-centered
   :alt: husky front

.. figure:: _static/husky/husky_rear.png
   :width: 100%
   :align: center
   :figclass: align-centered
   :alt: husky rear

|

Status Panel
++++++++++++

상태 패널은 차체 후면에 위치한 LED 인디게이터로, 로봇의 현재 상태에 대한 정보를 제공합니다.

.. |icon1| image:: _static/husky/husky_panel_battery.png 
   :width: 20pt
   :height: 20pt

.. |icon2| image:: _static/husky/husky_panel_comm.png
   :width: 20pt
   :height: 20pt

.. |icon3| image:: _static/husky/husky_panel_error.png
   :width: 20pt
   :height: 20pt

.. |icon4| image:: _static/husky/husky_panel_estop.png
   :width: 20pt
   :height: 20pt

.. |icon5| image:: _static/husky/husky_panel_charge.png
   :width: 20pt
   :height: 20pt

+---------+----------------------------------------------------------------------------------------+
| Icon    | Description                                                                            |
+=========+========================================================================================+
| |icon1| | **Battery status** The four LED segments provide an approximate indication of          |
|         | the relative lifetime remaining in the battery.                                        |
+---------+----------------------------------------------------------------------------------------+
| |icon2| | **Communication status** When green, Husky is receiving a stream of correctly-formatted|
|         | motion commands, and is ready to drive. When yellow, Husky is receiving commands,      |
|         | but will not drive due to emergency stop or another error.                             |
|         | When red, serial communications are currently timed-out.                               |
+---------+----------------------------------------------------------------------------------------+
| |icon3| | **General error status** Illuminates red when Husky will not drive due to an error     |
|         | state. Such states include emergency stop, insufficient battery power, or an           |
|         | unspecified software error.                                                            |
+---------+----------------------------------------------------------------------------------------+
| |icon4| | **Emergency stop status** Illuminates red when Husky will not drive due to             |
|         | he emergency stop being activated, either onboard or wireless (if available).          |
+---------+----------------------------------------------------------------------------------------+
| |icon5| | **Charge Indicator** Illuminates red when Husky user power is being supplied           |
|         | externally.                                                                            |
+---------+----------------------------------------------------------------------------------------+

|

Orientation References
++++++++++++++++++++++

로봇의 기준 좌표계는 아래 그림과 같이 ISO 8855를 기반으로 합니다. 로봇이 양의 선속도 값을 명령으로
받으면, 양의 X축 방향으로 이동합니다.

.. figure:: _static/husky/husky_frame.png
   :width: 100%
   :align: center
   :figclass: align-centered
   :alt: husky frame

|

Pinout Refrences
++++++++++++++++

로봇은 호스트 장치와 통신하기 위해 DE-9 암 커넥터를 제공합니다. 이 커넥터의 핀 배치는 아래 그림과
같습니다.

.. figure:: _static/husky/husky_pinout.png
   :width: 60%
   :align: center
   :figclass: align-centered
   :alt: husky pinout


+-----+------+-----+--------------------+
| Pin | Name | Dir | Description        |
+=====+======+=====+====================+
| 2   | RX   | IN  | Data from Platform |
+-----+------+-----+--------------------+
| 3   | TX   | OUT | Data to Platform   |
+-----+------+-----+--------------------+
| 5   | GND  | N/A | Common Ground      |
+-----+------+-----+--------------------+

|

System Specifications
---------------------

+------------------------------+-----------------+---------------+
| Specifications               | Values                          |
+==============================+=================+===============+
| Dimensions                   | 990 mm length   | 39 in length  |
|                              +-----------------+---------------+
|                              | 670 mm width    | 26.4 in width |
|                              +-----------------+---------------+
|                              | 390 mm height   | 14.6 in height|
+------------------------------+-----------------+---------------+
| Track                        | 555 mm          | 21.9 in       |
+------------------------------+-----------------+---------------+
| Wheelbase                    | 512 mm          | 20.2 in       |
+------------------------------+-----------------+---------------+
| Weight                       | 50 kg           | 110 lbs       |
+------------------------------+-----------------+---------------+
| Maximum Payload [#f1]_       | 75 kg           | 165 lbs       |
+------------------------------+-----------------+---------------+
| All-terrain Payload [#f2]_   | 20 kg           | 44 lbs        |
+------------------------------+-----------------+---------------+
| Speed (max)                  | 1.0 m/s         | 3.3 ft/s      |
+------------------------------+-----------------+---------------+
| Ground clearance             | 130mm           | 5 in          |
+------------------------------+-----------------+---------------+
| Climb grade                  | 45°             | 100% slope    |
+------------------------------+-----------------+---------------+
| Traversal grade              | 30°             | 58% slope     |
+------------------------------+-----------------+---------------+
| Operating Ambient Temperature| -10 to 30 o C   | 14 to 86 o F  |
+------------------------------+-----------------+---------------+
| Operating time               | 3 hours typical                 |
|                              +---------------------------------+
|                              | 8 hours standby (no motion)     |
+------------------------------+---------------------------------+
| Battery                      | 24V 20Ah Sealed Lead Acid       |
+------------------------------+---------------------------------+
| Battery charger              | short-circuit, over-current     |
|                              +---------------------------------+
|                              | reverse voltage protection      |
+------------------------------+---------------------------------+
| Charge time                  | 10 hours                        |
+------------------------------+---------------------------------+
| User Power                   | 5V / 12V / 24V Each fused at 5A |
+------------------------------+---------------------------------+
| Communication                | RS-232 115200 Baud              |
+------------------------------+---------------------------------+
| Wheel Encoders               | 78,000 ticks/m                  |
+------------------------------+---------------------------------+
| Internal Sensing             | Battery Status                  |
|                              +---------------------------------+
|                              | Wheel odometry                  |
+                              +---------------------------------+
|                              | Motor currents                  |
+------------------------------+---------------------------------+

.. [#f1] Continuous operation on relatively flat terrain with wide turns
.. [#f2] Vehicle climbing 30° grade with high-mounted payload, or turning in place in high-friction conditions

|

Safety
------

General Warnings
++++++++++++++++

* Husky는 견고하고 고성능의 UGV입니다. 본인과 타인의 안전을 위하여 로봇을 지면에서 띄운 다음에,
  초기 테스트와 소프트웨어 개발을 수행하십시오. 

* 시작할 때는 휠 속도를 낮추십시오. 로봇의 제어 루프는 0.1 m/s의 낮은 속도를 정확하게 유지할 수
  있습니다. 

* 로봇이 구동 중일 때는 로봇의 전면과 후면에 설치된 범퍼를 주의하십시오.

E-Stop and Lockout
++++++++++++++++++

빨간색 비상 정지 버튼(E-Stop)와 잠금장치는 아래 그림과 같이 로봇 후면에 있습니다. 로봇 모터 드라이버의 
전원 공급 장치는 비상 정지 버튼와 연결된 릴레이와 연결되어 있습니다. 비상 정지 상태면 상태 패널의 
비상 정지 표시기가 빨간색으로 켜지고, 로봇은 움직이지 않습니다. 비상 정지 상태가 해제되기 전에 
명령이 중지되면 로봇은 움직이지 않습니다. 그러나 명령이 계속 전송되면, 로봇은 비상 정지 상태가
해제되면 바로 구동됩니다.

항상 비상 정지 버튼에 접근할 수 있는지 확인하십시오. 로봇 상판에 물건을 탑재할 때
비상 정비 버튼을 막지 않도록 주의하십시오.

잠금장치 역시 로봇이 움직이지 못하도록 합니다. 잠금 상태일 때는 로봇의 전원이 켜져 있지만 모터는 
구동되지 않습니다.

.. figure:: _static/husky/husky_estop_lockout.png
   :width: 90%
   :align: center
   :figclass: align-centered
   :alt: husky estop lockout

|

Electrical System
+++++++++++++++++

로봇은 전동 휠체어, 골프 카트 등에서 사용되는 24V 납축전지 1개로 구동됩니다. 로봇 배터리는
1800W를 공급할 수 있으며, 이로 인해 로봇의 모터는 뛰어난 성능을 발휘할 수 있습니다.
그러나 상해를 입힐 수도 있으므로 다음 주의사항을 준수하십시오.

* 배터리에 연결된 플러그를 함부로 조작하지 마십시오.

* 퓨즈를 확인 및 교체하고, 배터리 플러그를 연결 및 분리하는 것 외에는 퓨즈 패널을 함부로
  조작하지 마십시오.

* 배터리 커버를 장착하지 않은 상태로 로봇을 구동하지 마십시오. 커버가 없으면
  배터리가 제자리에 고정되지 않으므로, 퓨즈 패널이 손상될 위험이 있습니다.

* 당사에서 제공하는 충전기로만 배터리를 충전하십시오.

* 배터리를 올바르게 폐기하십시오.

Lifting and transport
+++++++++++++++++++++

로봇을 수동으로 운반할 때, 사용자의 안전과 로봇의 수명을 보장하려면 다음 사항을 준수하십시오.

* 두 사람이 로봇의 앞뒤 범퍼를 잡아 들어 올려야 합니다. 배터리를 제거하면 로봇의 무게를 줄일 
  수 있습니다.

* 단거리 운송 시에는 E-Stop 버튼을 이용하고, 장거리 운송 시에는 전원이 커졌는지 확인하십시오.

* 모터가 손상될 수 있으므로 로봇을 수동으로 밀지 않는 것이 좋습니다.

Performance Recommendations
+++++++++++++++++++++++++++

로봇에는 소프트웨어 점검과 보호를 위한 제한이 포함되어 있습니다. 그러나 로봇을 사용하는 동안
''/status'' 및 ''/diagnostics'' rostopic을 모니터링하는 것이 좋습니다. 이 rostopic은
전압, 전류, 온도 및 시스템의 일반적인 상태에 관한 정보를 제공합니다.

총 전류 소모량에는 모터 드라이버가 포함되어 있지 않고, MCU와 사용자 전원 단자에서 소비하는
전류만 포함됩니다. 로봇의 모터의 전류 소모량은 약 8A 입니다. 그러나 거친 지형에서 구동할 때는
전류가 급상승합니다. 전류 소모를 줄이려면 로봇을 더 넓은 반경으로 회전하도록 제어하십시오.

온도는 모터 드라이버와 모터 케이스에서 측정됩니다. 시스템의 제한 온도는 50C° 입니다. 
제한 온도에 도달하면 시스템은 종료됩니다.

|

Getting Started
---------------

Remote ROS Connectivity
+++++++++++++++++++++++

ROS 인터페이스를 사용하기 위해서는, 원격 PC가 로봇의 ROS 마스터와 연결되어야 합니다.
이를 통해 원격 PC에서 ``rostopic list``, ``rostopic echo``, ``rosnode list`` 와 같은 ROS 
명령을 실행할 수 있습니다.

이를 위한 `ROS 네트워크 설정 <http://wiki.ros.org/ROS/NetworkSetup>`_  방법은 아래와 같습니다.

1. bashrc 스크립트 파일에서 ``ROS_MASTER_URI``, ``ROS_HOSTNAME`` 환경 변수를 설정합니다. 

::

  $ vim ~/.bashrc

  # Add the following lines
  export ROS_MASTER_URI=http://<ROBOT_IP>:11311
  export ROS_HOSTNAME=<REMOTE_IP>

``<ROBOT_IP>`` 는 로봇 PC의 IP 주소이고, ``<REMOTE_IP>`` 는 원격 PC의 IP 주소입니다.

2. Hostname과 IP 주소를 매핑하기 위하여 ``/etc/hosts`` 파일에 항목을 추가합니다.

  ::

    $ sudo vim ~/.bashrc

    # Add the following line
    <ROBOT_IP>    <ROBOT_HOSTNAME>

``<ROBOT_IP>`` 는 로봇 PC의 IP 주소이고, ``<ROBOT_HOSTNAME>`` 는 로봇 PC의 Hostname 입니다. 
일반적으로 Hostname은 로봇의 시리얼 넘버로 설정되어 있습니다.

.. note::
   Hostname은 ``hostname`` 명령을 터미널 창에 입력해서 확인할 수 있습니다.

Connecting Power
++++++++++++++++

로봇의 배터리는 완전치 충전된 상태로 설치되어 있지만, 안전을 위해 운송 중에는 분리되어 있습니다.
배터리를 다시 연결하는 방법은 아래와 같습니다.

1. 로봇의 주전원 버튼이 **OFF** 위치에 있고, 비상 정지가 활성화되어 있는지 확인하십시오.

2. 배터리 커버의 래치 버튼을 누르면서 커버를 분리하십시오.

3. 배터리 플러그를 퓨즈 패널의 커넥터에 연결하십시오. 딸각 소리가 날 때까지 밀어 넣어
   단단히 고정하십시오.

4. 배터리 커버를 제자리에 장착하십시오.

.. figure:: _static/husky/husky_battery_area.png
   :width: 90%
   :align: center
   :figclass: align-centered
   :alt: husky battery area

로봇의 전원을 켜려면 상태 패널 위에 있는 전원 버튼을 누르십시오. 파란색 LED가 표시됩니다.
PC와 로봇이 통신하게 되면 통신 상태 표시등이 초록색으로 바뀝니다. 비상 정지 버튼을 누르면서
정지 상태 표시등이 빨간색으로 표시됩니다.

User Bay Power Connections
++++++++++++++++++++++++++

사용자 전원 단자는 최대 5A의 5V, 12V 및 24V 를 제공합니다. 각 터미널에는 탈부착식 커넥터가
장착되어 있습니다. 2mm 폭의 일자 드라이버를 사각형 구멍에 삽입하면, 바로 옆에 있는 둥근 구멍이
열립니다. 이 둥근 구멍에 전선을 밀어 넣은 다음, 드라이버를 제거하면 전선이 고정됩니다.

.. |connector01| image:: _static/husky/husky_power_connector_01.png 
   :height: 230pt
   :align: middle

.. |connector02| image:: _static/husky/husky_power_connector_02.png
   :height: 230pt
   :align: middle

|connector01| |connector02|

사용자 전원 단자를 사용할 때, 극성이 올바른지 확인하십시오. 그리고 최대 전류를 초과하자 마십시오.

|

Using ROS
---------

|