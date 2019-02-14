2つのstopの間の経路情報。

## from\*

*object*

pathの始点の情報。

### stopId \*

*string*

出発地点のstopのID。

### parkingLocationIndex \*

*integer*

同じstopに対する停車位置候補のインデックス。

### geocode \*

*object*

#### lat, lng \*

*real*

緯度経度。

### heading \*

*integer (0〜359)*

出発地点における進行方向。

## to\*

*object*

pathの始点の情報。

### stopId \*

*string*

出発地点のstopのID。

### parkingLocationIndex \*

*integer*

同じstopに対する停車位置候補のインデックス。

### geocode \*

*object*

#### lat, lng \*

*real*

緯度経度。

### heading \*

*integer (0〜359)*

出発地点における進行方向。

## duration \*

*real (≧0)*

移動時間。

## distance \*

*real (≧0)*

経路の長さ。

## encodedpolyline \*

*string*

経路を線で描画するための情報。
