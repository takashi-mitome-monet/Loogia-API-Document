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

*real (≧0)*

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


### startLocation\*, endLocation\*

*object*

それぞれcaririerの出発場所と帰着場所に関する情報。

#### id\*

*string*

出発／帰着するデポのID。
[depot](#depot)のIDと対応する。
depotsに含まれるdepotに同一のIDを持つものが無い場合エラーとなる。

#### time\*

*integer*

startLocationでは出発する時刻を表す。
endLocationでは帰着の期限を表し、この時刻までに帰るためにいくつかのstopをunassignedとする場合がある。

### capacities

*object*

[stop](#stop)が要求するdemandに対応するcarrierの容量。
各carrierはこの容量を超えない範囲でstopを訪問することができる。

#### dimensionId\*

*integer (≧0)*

容量の種類を表すID。
[stop](#stop)が持つdemandのIDと対応する。
stopが持っていないIDを指定しても動く。

#### size\*

*integer (≧0)*

容量の上限。
この範囲でstopを訪問することができる。

### cost

*object*

未実装

## stop

### id\*

*string*

訪問先のID。

### geocodes\*

*array*

訪問先および停車位置候補位置の配列。
複数指定した場合、最適性を考慮しながら候補のうちの1つが選ばれる。

#### lat\*

*real*

緯度。

#### lng\*

*real*

経度。

### timeWindow\*

*object*

訪問可能時間を指定する情報。

#### type

*string*

`"none"` または `"range"` を指定する。
`"none"` はどの時間でも訪問可能であることを表す。
`"range"` は訪問可能な時間の範囲としてrangesを指定する。

#### ranges

*object*

typeにrangeを指定した場合に必要。
訪問可能時間帯の情報を表す。

- readyTime\*

*integer*

訪問可能時間帯の開始時刻。

- dueTime\*

*integer*

訪問可能時間帯の終了時刻。

- gradient

*integer (≧0)*

readyTimeからdueTimeの中で早く訪問したい場合に0より大きい値を指定する。

#### margin

*object*

時間帯の前後にマージンを設ける。

- early

*integer*

readyTime := readyTIme + early

- late

*integer*

dueTime := dueTime - late

### demands

*array*

訪問することで消費するcarrierの容量。
[carrier](#carrier)のcapacityに対応する。

#### dimensionId\*

*integer (≧0)*

要求量の種類を表すID。
[carrier](#carrier)が持つcapacityのIDと対応する。
どのcarrierも持っていないIDを指定するとエラーとなる。

#### size\*

*integer (≧0)*

消費する容量。

### serviceDuration\*

*object*

訪問することでかかる時間。
移動時間は含まれず、停車や作業にかかる時間に相当する。

#### general\*

*integer*

かかる時間を指定。

#### before

*object*

キーとして[stop](#stop)のIDを指定し、値 (*integer*) としてそのstopの直前に訪問したときにかかる時間を指定する。

#### after

*object*

キーとして[stop](#stop)のIDを指定し、値 (*integer*) としてそのstopの直後に訪問したときにかかる時間を指定する。

### priority

*integer (1〜10)*

訪問の優先度を指定する。
値が小さい方が優先度が高い。
制約をすべて満たした上ですべての点を回りきれる解が見つからなかった場合に一部のstopがunassignedとなる。
その際に優先度が低いものがunassignedとなりやすくなる。

### skills

*array*

文字列の配列。
各文字列はstopが要求するスキルを表す。
[carrier](#carrier)が持つskillと対応する。
要求するスキルを持つcarrierのみがこのstopを訪問することができる。

### uturnCost

*real (≧0)*

このstopへ到着したときの道路上における進行方向と次のstopへ出発するときの道路上における進行方向を考え、それが一致しないときにかかるコストを設定する。
この値が大きいほど到着したときの方向と出発するときの方向を合わせるようにルートを作成する。



