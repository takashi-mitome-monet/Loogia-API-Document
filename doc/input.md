# input.json

各キーが取る値についての解説。
キー名の横のカッコ内がデータ型を表す。

|データ型|意味|
|---|---|
|integer|整数|
|real|実数|
|string|文字列|
|array|配列|
|object|オブジェクト|

必須のキーにはキー名の後にアスタリスク(\*)をつけている。

### depots\*

*array*
[depot](#depot)の配列。
計算に用いるデポの候補の集合。
[carrier](#carrier)の出発・帰着場所として指定されたデポが計算に使用される。

### calculationTime

*real (≧0*
最適化の計算時間（秒）。
レスポンスまでにかかる時間ではない。

### callback

*object*
[callback](#callback)

### export

*object*
[export](#export)

### mapModuleOption

*object*
[mapModuleOption](#mapModuleOption)

### carriers\*

*array*
[carrier](#carrier)の配列。
ここで指定された車両を用いてルートを作成する。
すべての車両を使うとは限らない。

### stops\*

*array*
[stop](#stop)の配列。
制約，コストによってはここで指定したすべてのstopを訪れるとは限らない。
ルートに組み込まれなかった点はunassignedとして出力される。

### matrix\*

*array*
[path](#path)の配列。
すべてのdepot/stop間に対して1つ以上のpathが必要。
配列の要素数がゼロの場合またははキーが存在しない場合またはnullの場合は内部で持っている地図データからパス情報を取得する。

## depot

### id\*

*string*
depotとstopの中でユニークなID。

### geocode\*

*object*
depotの場所の座標。

#### lat\*

*real*
緯度。

#### lng\*

*real*
経度。

## carrier

### id\*

*string*
carrierの中でユニークなID。

### skills

*array*
文字列の配列。
各文字列はcarrierが持つスキルを表す。
[stop](#stop)が要求するskillと対応する。

### break

*object*
carrierがとる休憩に関する情報。

#### type

*string*
休憩の指定方法。
`"none"` または `"range"`

#### ranges

*array*
rangeの配列。
typeにrangeを指定した場合に必要。
各rangeは休憩を取ることができる期間を表し、 `readyTime` と `dueTime` を持つ。

- readyTime

*integer*
期間の開始時刻。

- dueTime

*integer*
期間の終了時刻。

#### duration

*integer*
休憩をとる期間の長さ。



