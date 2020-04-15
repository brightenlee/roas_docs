ROS API Overview
----------------

사용자가 상위 어플리케이션을 쉽게 개발할 수 있도록 **ROS** 표준 인터페이스를 제공합니다.
최대한 `REPs(ROS Enhancement Proposals) <https://www.ros.org/reps/rep-0000.html>`_ 를 
준수하여 호환성과 접근성을 높였습니다.

Feedback Interface
++++++++++++++++++

로봇의 피드백 데이터에는 3가지가 있습니다. 로봇 베이스에 대한 피드백, 모터에 대한 피드백,
조명 제어에 대한 피드백이 있습니다.

**rostopic name: /scout_base/driver_feedback**

.. code::

  Header header

  string robot_name

  DriverState driver_state
    string state             # NORMAL, STOP
    string control_mode      # REMOTE, CAN, SERIAL, NONE
    float64 battery_voltage  # Actual voltage (V)
    string battery_state     # under-voltage, over-voltage

  float64 linear_speed   # Linear speed (m/s)
  float64 angular_speed  # Angular speed (rad/s)

**rostopic name: /scout_base/motor_feedback**

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

**rostopic name: /scout_base/light_feedback**

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
메세지 타입의 **/scout_base_controller/cmd_vel** 토픽을 구독(subscribe)합니다. 
사용자는 이 토픽을 이용해서 로봇을 제어할 수 있습니다.

사용자는 /scout_base_controller/cmd_vel 토픽을 바로 이용할 수 있지만,
일반적으로 어플리케이션은 /teleop/cmd_vel, /move_base/cmd_vel, /cmd_vel 토픽을 이용합니다.
이 토픽들의 데이터는 설정된 우선 순위에 따라 /scout_base_controller/cmd_vel으로 전달됩니다.
이와 같은 mux 시스템은 `twist_mux <http://wiki.ros.org/twist_mux>`_ 패키지를 이용하여
구현되어 있습니다.

Light Interface
+++++++++++++++

로봇의 전면과 후면에 설치되어 있는 조명의 제어 인터페이스는 사용자에게 개방되어 있습니다.
사용자는 **/scout_base/light_command** 토픽을 이용해서 조명을 제어할 수 있습니다.

.. code::

  # Lighting Mode
  # 0: NC / 1: NO / 2: BL / 3: CUSTOM

  uint8 front_mode        # Lighting Mode
  uint8 front_brightness  # Only for CUSTOM mode

  uint8 rear_mode         # Lighting Mode
  uint8 rear_brighteness  # Only for CUSTOM mode

|