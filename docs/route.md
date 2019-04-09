# route

## serviceType

*string*

訪問先で行う業務の種別を表す文字列。pickup, delivery, start, end, loadUnloadのいずれかで与えられる。

|pickup |delivery |start |end |loadUnload |
|---|---|---|---|---|
|集荷地点 |配送地点 |出発地点 |帰着地点 |積み下ろし地点<br>（回転オプションで利用）|

## arrivalTime

*integer*

訪問先への到着時刻を表す整数。

## serviceDuration

*integer*

訪問先で作業を行うのに必要な時間を表す整数。単位は秒。

## travelDuration

*integer*

現在の訪問先から次の訪問先まで移動するのに必要な時間を表す整数。単位は秒。

## geocode

*object*

訪問先における停車位置の緯度・経度を保持するオブジェクト。
[spot](spot.md)のlocationsとして複数の緯度経度を入力した場合その中で１つが選ばれる。

* lat

*real*

緯度。

* lng

*real*

経度。

## startTime

*integer*

訪問先に到着した後、作業を開始する時刻を表す整数。

## id

*string*

訪問先のID。

## polyline

*string*

現在の訪問先から次の訪問先までの移動経路を地図上で表示するために用いる情報。圧縮された文字列で与えられる。
