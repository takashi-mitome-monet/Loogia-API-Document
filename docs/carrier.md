# carrier

## id\*

*string*

carrierの中でユニークなID。

## skills

*array*

文字列の配列。
各文字列はcarrierが持つスキルを表す。
[stop](stop)が要求するskillと対応する。

## break

*object*

carrierがとる休憩に関する情報。

### type

*string*

休憩の指定方法。
`"none"` または `"range"`

### ranges

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

### duration

*integer*

休憩をとる期間の長さ。


## startLocation\*, endLocation\*

*object*

それぞれcaririerの出発場所と帰着場所に関する情報。

### id\*

*string*

出発／帰着するデポのID。
[depot](depot)のIDと対応する。
depotsに含まれるdepotに同一のIDを持つものが無い場合エラーとなる。

### time\*

*integer*

startLocationでは出発する時刻を表す。
endLocationでは帰着の期限を表し、この時刻までに帰るためにいくつかのstopをunassignedとする場合がある。

## capacities

*object*

[stop](stop)が要求するdemandに対応するcarrierの容量。
各carrierはこの容量を超えない範囲でstopを訪問することができる。

### dimId\*

*integer (≧0)*

容量の種類を表すID。
[stop](stop)が持つdemandのIDと対応する。
stopが持っていないIDを指定しても動く。

### size\*

*integer (≧0)*

容量の上限。
この範囲でstopを訪問することができる。

## cost

*object*

未実装
