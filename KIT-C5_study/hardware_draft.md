## 大会の規定・満たしておかなければならない項目

【安全のための事項】

[1] ロボットのサイズ

ロボットは遊歩道を走行・歩行するのに適した人間のサイズを基本としたサイズとし、進行方向の横幅は 75cm 以内、長さは 120cm 以内とする。重量は最大 100kg 以下とするが、2-3人の人数で持ち運びできるよう 60kg以下を推奨する。 また、高さは最高部を 0.6m 以上、1.5m 以下とする。


[2] 動作速度

走行時の最高速度は 4km/h 以下。


[3] 非常停止スイッチの設置 

オペレータ以外にもそれが非常停止スイッチとわかり操作が可能であること。 非常停止スイッチは、ロボットが誤動作していても、ロボットを安全に停止させられることが求められる。したがって、ソフトウェアを介さないでロボットへの動力供給を断ち停止させるものなどであること。なお、非常停止の後もオペレータの操作により、その場から動作を再開できるよう配慮されていること。 


[4] ロボットの形状と外観 

ロボットは危険な突起部分等を有しない形状であること。また子供の手や足等を巻き込む恐れのない構造であること。高温あるいは感電の恐れのある露出部を有しないこと。

また、ロボットは、街の中を通行する人（や他のロボット）に見えやすい形と色であること。このため、ロボットは原則として地上高10cm-30cmの幅には、ロボットの平面形状（地面に投影した形状）に沿って外側から5cm以内のところに明6るい色の外面を有していること。その外面にはセンサ等のための隙間はあってよいが、大きな間の隙間は避けること。

 
[5] ロボットナンバーの表示

ロボットには、それが「つくばチャレンジ」に参加しているロボットであることを明らかとし、ロボットの個体を識別できるよう、規定されたサイズのロボットナンバーを各方向から見える位置に取り付け（または、貼り付ける）こと。

 
[6] 走行時の無線による操作の禁止

ロボットを、オペレータの操作により制御する場合、無線通信を用いず有線でロボットに接続すること。
 

[7] 非常停止の簡単な走行再開指示

ロボットが非常停止の後に、オペレータが走行の再開を指示する場合、簡単な操作で再開指示が与えられること。
 

[8] その他

　(1) ロボットは動作中騒音や振動を発生しないこと。  
　(2) ロボットは、市街地で働くロボットとして環境への調和を配慮した設計、デザインであること。  
　(3) ロボットは環境にやさしい機械としてエコロジーやエネルギー効率に配慮して設計・デザインされていること。  


* 巻き込み防止策
* 車輪への異物巻き込み防止策
* 高さ稼ぎ策0.6m
* 防雨策
* 緊急停止スイッチ実装


by有田さん
モータ駆動のみを殺す
システムを殺さずに。。



## 本機の構造

i-cart mini をベースに構築
そこに大会規定をみたすように高さ稼ぎや
巻き込み防止などの安全対策を施していった

ポリバケツ不採用

高さを稼ぐ形状を確定

* できるだけ工房にあるものを活用
* フレームと一体ではない
* 強度的に信頼のならないプラッチックをかぶせたとしてロボット暴走時の緊急スイッチ押下の衝撃力はどうなるのか
* 大きなカバーをかぶせたとしてメンテナンス性をどう確保するのか?
* 着脱式にするとして固定どうするのか?
* 技術力の不足を感じさせる

アルミを一本だけ高く立てて、高さを稼ぐ
その上に非常停止スイッチを設置して押しやすさを実現
本番前になって、周りにプラスチックダンボールを囲って他のロボットから認識できるように改良

バンパー　ー＞黄色いスポンジ



## 問題点・改善策

* 外装について, 『フレーム,機能部とハリボテ』思想では不十分である. 強度, 耐力, 保護能力, 維持管理その他全てについて不十分である.
	- 専用設計で作り起こす, 現状 FRP で専用に固めて作るのが有効かと思っている.(趣味用に一般的で, 完全な防水性を持つ)
	- 点検ハッチとかが付けたい
	- 役物をすべて正しい位置に格納できるようにしたい. そして全てに完全な固定と被覆を提供したい
	- いざとなればネジ6本くらいで全部外せるようにしたい

* フレームがガタガタギシギシ言ってどうにもならない  
→ロックタイトなどを使う  
→いつものネジ止めアルミフレームを止めにする  
	- もう少しマシな設計を試みる
	- 外皮にも応力を分散させたいし, 何より格好悪い <- 重要

* わかってたことだが, センサが坂を読んでいる
	- LIDAR とか導入しちゃう?

* タイヤが小さすぎて, 小石にも躓いている
	- 上半身に対して下半身が貧弱すぎる
	- 振動のせいだと思うけれど, odom が壊滅的
	- 最低でもサスほしい

* 制御ゲインが不適切で, スピンに入ると発散して死ぬ



## 原因

１回制の積極性のなさ  
とりかかりの遅さ  
ネジが足りないとか
