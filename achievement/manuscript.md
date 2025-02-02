## 1
自律移動ロボット開発プロジェクトCIR-KITです。  
CIR−KITの成果報告をいたします。

## 2
私たちCIR−KITは
「屋内外の」「人の生活空間」で活用できる
自律移動型ロボットの
開発に取り組んでいます。

## 3
CIR-KIT がこれまでに開発したロボットです。

## 4
2018年度の活動計画では、
3次元測域センサを導入し自律走行における安定性を向上させることを第一に掲げました。
これにより、障害物の認識や自己位置推定の精度向上に期待できるということでした。
そのほか、ロボットの設計を見直し、メンテナンスのしやすさなど機能性の向上を掲げました。

## 5
従来使用していた2次元のセンサでは、
平面上にある物体のみを認識することが出来ます。
このようにセンサが認識することができる平面上に
障害物があった場合は対処することが出来ますが、

## 6
逆に平面上にないものは
全て死角となってしまいます。
この場合、センサで検知できていない木の枝にぶつかってしまいます。

## 7
この問題はセンサの位置を工夫することで
ある程度対処することはできますが、

## 8
実環境の様々な地形や状況に対処するには
限界があります。
この場合は、足元にある障害物を認識することができません

## 9
しかし、2018年度から導入した3次元センサによって
認識できる領域が格段に広がりました。

## 10, 11
これによって、位置や形状によらず検知することができます。

## 12
また、このような障害物ですと、
2次元センサでは、このラインを読み取った場合
この間を通れると判断してしまうことがあり、
障害物認識が難しいです。
この問題も3次元センサの導入によって
解決することができ、
障害物の認識能力や回避性能が大幅に向上しました。

## 13
またさらに、
認識できる領域が拡大する分、取得できる特徴量も増加し、
自己位置推定の精度向上にもつながりました。

## 14
これらにより、学内で行った走行実験では
1km近い距離を安定して自律走行することに成功しました。

## 15
CIR−KITは毎年、つくばチャレンジという自律走行実験会で
成果を挙げることを目標としています.
今年度より、大会の走行コースやルールが大きく変更されました。

具体的には、走行コースは特徴量が取りづらく、凹凸のおおい、
自己位置推定が破綻しやすいコースどりになりました。
また2台同時出走など、ルールが変更され
より障害物の認識・回避能力が求められるものとなり
大会が全体として難化した年でした。

## 16
しかし、CIR-KITは2018年度の開発を経て、
これらの変化に十分に対応できるよう改良することができました。

## 17
しかし、本番走行での結果は90ｍと、悔やまれる結果となってしましました。
原因は本番直前のモータ回りの不具合で、
これにより計算した経路に沿って走行することが困難になってしまい
９０ｍ地点で走行不可となってしまいました。

## 18
今後の展開としては
まず、モータ等の部品の取り換えや足回りの設計や部品の見直しをし、
足回りの強化に取り組み
ロバストで確実な走行を実現しようと考えております。
また、3次元の環境地図を用いた自己位置推定機能を実現し、
より高い精度での自律走行を実現していこうと考えております

## 19
3次元地図を用いた自己位置推定については、
ものつくり工房等の狭い空間では実現することができていますので
近い将来、導入する予定です。



