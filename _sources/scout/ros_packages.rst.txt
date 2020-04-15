ROS Packages
------------
Scout의 **ROS** 인터페이스를 구성하고 있는 패키지들은 다음과 같습니다.

scout_base
++++++++++

로봇 MCU와의 시리얼 통신을 위한 패키지입니다. 
그리고 피드백 데이터를 바탕으로 구현된 진단(diagnostic) 노드를 포함하고 있습니다. 

scout_base_controller
+++++++++++++++++++++
Differential drive controller를 구현한 패키지입니다.

scout_bringup
+++++++++++++
로봇의 전체 ROS 시스템을 실행시키는 실행(launch) 파일과 
설정 파일을 포함하고 있습니다.

scout_description
+++++++++++++++++
로봇의 좌표 체계를 정의한 URDF 파일과 시각화를 위한 3D mesh 파일을 포함하고 있습니다.

scout_navigation
++++++++++++++++
SLAM, Navigation 기능에 대한 설정, 실행 파일을 포함하고 있습니다.

scout_teleop
++++++++++++
블루투스 컨트롤러를 이용해서 로봇을 원격 조작할 수 있는 패키지입니다.

|