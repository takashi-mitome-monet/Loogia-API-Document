# stop

訪問先の情報

## id\*

*string*

訪問先のID。

## geocodes\*

*array*

訪問先および停車位置候補位置の配列。
複数指定した場合、最適性を考慮しながら候補のうちの1つが選ばれる。

### lat\*

*real*

緯度。

### lng\*

*real*

経度。

## timeWindow\*

*object*

訪問可能時間を指定する情報。

### type

*string*

`"none"` または `"range"` を指定する。
`"none"` はどの時間でも訪問可能であることを表す。
`"range"` は訪問可能な時間の範囲としてrangesを指定する。

### ranges

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

### margin

*object*

時間帯の前後にマージンを設ける。

- early

*integer*

readyTime := readyTIme + early

- late

*integer*

dueTime := dueTime - late

## demands

*array*

訪問することで消費するcarrierの容量。
[carrier](carrier)のcapacityに対応する。

### dimensionId\*

*integer (≧0)*

要求量の種類を表すID。
[carrier](carrier)が持つcapacityのIDと対応する。
どのcarrierも持っていないIDを指定するとエラーとなる。

### size\*

*integer (≧0)*

消費する容量。

## serviceDuration\*

*object*

訪問することでかかる時間。
移動時間は含まれず、停車や作業にかかる時間に相当する。

### general\*

*integer*

かかる時間を指定。

### before

*object*

キーとして[stop](stop)のIDを指定し、値 (*integer*) としてそのstopの直前に訪問したときにかかる時間を指定する。

### after

*object*

キーとして[stop](stop)のIDを指定し、値 (*integer*) としてそのstopの直後に訪問したときにかかる時間を指定する。

beforeとafterがコンフリクトした際はafterを利用する

## priority

*integer (1〜10)*

訪問の優先度を指定する。
値が小さい方が優先度が高い。
制約をすべて満たした上ですべての点を回りきれる解が見つからなかった場合に一部のstopがunassignedとなる。
その際に優先度が低いものがunassignedとなりやすくなる。

## skills

*array*

文字列の配列。
各文字列はstopが要求するスキルを表す。
[carrier](carrier)が持つskillと対応する。
要求するスキルを持つcarrierのみがこのstopを訪問することができる。

## uturnCost

*real (≧0)*

このstopへ到着したときの道路上における進行方向と次のstopへ出発するときの道路上における進行方向を考え、それが一致しないときにかかるコストを設定する。
この値が大きいほど到着したときの方向と出発するときの方向を合わせるようにルートを作成する。