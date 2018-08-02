# input.json

### depots (array)
[depot](#depot)の配列。
計算に用いるデポの候補の集合。
[carrier](#carrier)の出発・帰着場所として指定されたデポが計算に使用される。

### calculationTime (int)
最適化の計算時間（秒）。
レスポンスまでにかかる時間ではない。

### callback (object)
[callback](#callback)

### export (object)
[export](#export)

### mapModuleOption (object)
[mapModuleOption](#mapModuleOption)

### carriers (array)
[carrier](#carrier)の配列。
ここで指定された車両を用いてルートを作成する。
すべての車両を使うとは限らない。

### stops (array)
[stop](#stop)の配列。
制約，コストによってはここで指定したすべてのstopを訪れるとは限らない。
ルートに組み込まれなかった点はunassignedとして出力される。

### matrix (array)
[path](#path)の配列。
すべてのdepot/stop間に対して1つ以上のpathが必要。
配列の要素数がゼロの場合またははキーが存在しない場合またはnullの場合は内部で持っている地図データからパス情報を取得する。

## depot

### id (string)

depotとstopの中でユニークなID。

### geocode (object)

depotの場所の緯度・経度。

#### lat

緯度。

#### lng

経度。

## carrier

### id (string)

carrierの中でユニークなID。

### skills (array)

文字列の配列。
各文字列はcarrierが持つスキルを表す。
[stop](#stop)が持つskillと対応する。

### break (object)

#### type (string)

`"none"` または `"range"`

#### ranges (array)

rangeの配列。
typeにrangeを指定した場合に必要。

#### range

各rangeは `readyTime` と `dueTime` を


