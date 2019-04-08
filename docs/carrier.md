# carrier

## id\*

*string*

carrierの中でユニークなID。

## skills

*array*

文字列の配列。
各文字列はcarrierが持つスキルを表す。
[job](job.md)が要求するskillと対応する。

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
[depot](depot.md)のIDと対応する。
depotsに含まれるdepotに同一のIDを持つものが無い場合エラーとなる。

### time\*

*integer*

startLocationでは出発する時刻を表す。
endLocationでは帰着の期限を表し、この時刻までに帰るためにいくつかのjobをunassignedとする場合がある。

## capacities

*object*

[job](job.md)が要求するdemandに対応するcarrierの容量。
各carrierはこの容量を超えない範囲でjobを訪問することができる。

### dimId\*

*string*

容量の種類を表すID。
[job](job.md)が持つdemandのIDと対応する。
jobが持っていないIDを指定しても動く。

### size\*

*integer (≧0)*

容量の上限。
この範囲でjobを訪問することができる。


## multipleTrips

*object*

回転オプションの内容を記述するオブジェクト。

### maxTripNum\*

*integer (1〜10)*

回転数の上限を指定する正の整数。
0以下、または11以上の整数を入力するとエラーとなる。
1を指定すると通常のVRPと同様の動作をする。

### serviceDurationAtDepot\*

*integer*

途中に寄ったデポで荷物を積み下ろしするための作業時間。


## cost

*object*

未実装
