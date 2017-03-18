# ソフトウェアについて簡単に説明    
来てくれている一回生のために  

## 自立移動に必要な機能とは。。  
  
* 地図作成  
  
* コース取りをあらかじめ設定(waypoint)  
  
* ゴールへ向かったり障害物を回避したりする動作  
  
## 具体的には。。  
  
1. 自分のシルエットや各パーツの位置関係 (Transform   Configuration (tf))  
2. （赤外線でスキャニングしながら検出物までの距離を測定する）  
   センサーの読み取り(Sensor Information)  
3. コンピューター上でのシュミレートと実際の動作の一致(Odometry Information)  
4. コントローラーからの司令の読み取り( Base Controller)  
5. コンピューターからの司令をモーターに伝える  
  
==  
  
1. [!?]  
2. hokuyo\_node  
3. ypspur\_ros\_bridge  
4. ypspur\_ros\_bridge  
5. yp-spur　<-- C言語  
  
<既存のプログラム(PKG)を再利用できるので１から全部を作る必要がない>  
--> ROSのいいところ    
  
作らなきゃ。    
1. tfのデータ設定　　set\_up launch  
2. goal sender(goalはnavigationに渡す目標位置  
3. teleop    
  
yp-spur以外、先輩らが全部作ったのかと思っていました    
  
## ROS Kinetic Kame で開発  
  
ソフト構成  
  
* navigation(move\_base(経路計画とナビゲーション), amcl(地図とセンサから自己位置推定), map\_server(地図管理))  
* slam\_gmapping(gmapping(自己位置とセンサから地図を作成))  
* yp-spur(モータに直接司令を出している)  
* urg\_node(LRFドライバ)(センサからの情報受け取り)  
 
  
# fifth\_robot\_pkg  
  
fifth_\*は基本的に設定ファイル    
  
## fifth\_robot\_2nav/  
設定ファイルが主  
* 直進速度  
* 旋回速度  
* 自分のシルエットの把握  
  
## fifth\_robot\_launch/  
ロボットを起動させるためのファイルが、    
teleopやnavigationなどの機能別に分けて置いてある    
  
## fifth\_robot\_map/  
navigation時に読む地図(pgm)と読む際に必要な設定ファイル  
  
## goal\_sender/  
  
|map\_server    
|    
|    
|    
| hokuyo\_node    
| |    
| |  sensor\_msgs <- param(topic)  
| |  
| | goal\_sender  
| | |  
| | |  goal <- Action  
| | |  
V V V  
move\_base  
|  
|  cmd\_vel <- param(topic)  
|  
V  
ypspur\_ros\_bridge  
  
## teleop\_master/  
teleop\_master\_node.cpp <- node  
  
joy  
|  
|  joystickの情報[膨大なデータ] <- param(to  pic)  
|  
V   
teleop\_twist\_joy[cmd\_velとして必要なも  のを抽出]  
|  
|  source(cmd\_vel)  <- param(topi  c)  
|  
V  
teleop\_master\_node[周波数を落として受け流す]   <- バグ防止  
|  
|  cmd\_vel  <- param(topic)  
|  
V  
ypspur\_ros\_bridge  
  
## third\_party/  
外部からの提供が主  
* driver\_common from <ros-drivers>     ROS device   driversさん
* hokuyo\_node   from <ros-drivers>  
* ros\_waypoint\_generator from AriYuさん  
  
<!--  
## yaml\_reader/  
navigationがgoal(最終到達目標)しか受け付けない  
waypointをgoalとして渡して  
ある程度近づいたら次のgoalに更新されるように設定  
それによりwaypoint（もどき）を実装することができる  
-->    
