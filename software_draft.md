# ソフトウェアについて簡単に説明
（来てくれている一回生のために）

## ROS Kinetic Kame で開発

ソフト構成

* navigation
* gmapping
* yp-spur (モータ駆動)　<- モータに直接司令を出している
* urg_node(LRFドライバ)  <-  センサからの情報受け取り

## 自立移動に必要な機能とは。。

* 地図を作成

* コース取りをあらかじめ設定(waypoint)

* 障害物を回避する動作

## 具体的には。。

1. 自分のシルエットや各パーツの位置関係 (Transform Configuration (tf))
2. （赤外線でスキャニングしながら検出物までの距離を測定する）
   センサーの読み取り(Sensor Information)
3. コンピューター上でのシュミレートと実際の動作の一致(Odometry Information)
4. コントローラーからの司令の読み取り( Base Controller)
5. コンピューターからの司令をモーターに伝える

==

1. [!?]
2. hokuyo_node
3. ypspur_ros_bridge
4. ypspur_ros_bridge
5. yp-spur　<-- C言語

<既存のプログラム(PKG)を再利用できるので１から全部を作る必要がない>
--> ROSのいいところ

作らなきゃ。
1. tfのデータ設定　　set_up launch
2. goal sender(goalはnavigationに渡す目標位置
3. teleop


yp-spur以外、先輩らが全部作ったのかと思っていました

# fifth_robot_pkg

fifth_*は基本的に設定ファイル

## fifth_robot_2nav/
設定ファイルが主
* 直進速度
* 旋回速度
* 自分のシルエットの把握

## fifth_robot_launch/
ロボットを起動させるためのファイルが、
teleopやnavigationなどの機能別に分けて置いてある

## fifth_robot_map/

## goal_sender/

 hokuyo\_node
 |
 |  sensor\_msgs <- param(topic)
 |
 | goal_sender
 | |
 | |  goal <- Action
 | |
 V V
 move\_base
 |
 |  cmd\_vel <- param(topic)
 |
 V
ypspur\_ros\_bridge

## teleop_master/
teleop\_master\_node.cpp <- node

joy
|
|  joystickの情報[膨大なデータ] <- param(topic)
|
V
teleop\_twist\_joy[cmd_velとして必要なものを抽出]
|
|  source(cmd\_vel)  <- param(topic)
|
V
teleop\_master\_node[周波数を落として受け流す] <- バグ防止
|
|  cmd\_vel  <- param(topic)
|
V
ypspur\_ros\_bridge

## third_party/
外部からの提供が主
* driver_common from <ros-drivers>     ROS device driversさん
* hokuyo_node   from <ros-drivers>
* ros_waypoint_generator from AriYuさん

## yaml_reader/
navigationがgoal(最終到達目標)しか受け付けない
waypointをgoalとして渡して
ある程度近づいたら次のgoalに更新されるように設定
それによりwaypoint（もどき）を実装することができる
