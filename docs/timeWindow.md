# timeWindow

訪問可能時間を指定する情報。

## type

*string*

`"none"` または `"range"` を指定する。
`"none"` はどの時間でも訪問可能であることを表す。
`"range"` は訪問可能な時間の範囲としてrangesを指定する。

## ranges

*object*

typeにrangeを指定した場合に必要。
訪問可能時間帯の情報を表す。

### readyTime\*

*integer*

訪問可能時間帯の開始時刻。

### dueTime\*

*integer*

訪問可能時間帯の終了時刻。

## margin

*object*

時間帯の前後にマージンを設ける。

### early

*integer*

readyTime := readyTIme + early

### late

*integer*

dueTime := dueTime - late