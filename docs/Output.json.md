# Output.json

Output.jsonの各キーが取る値についての解説。
キー名の直後の斜体文字がデータ型を表す。

|データ型|意味|
|---|---|
|integer|整数|
|real|実数|
|string|文字列|
|boolean|真偽値|
|array|配列|
|object|オブジェクト|

## solution

*object*

解を表すオブジェクト。

### unassignedJobs

*array*

解に割り当てられなかったjobを保持する配列。

### carriers

*array*

解に割り当てられた車両の情報を保持する配列。

* route

*array*

1つの車両が受け持つ[route](route.md)に含まれる訪問先を、出発地点から帰着地点まで並べた配列。

* id

*string*

車両（carrier）のID。

## meta

*object*

メタデータを保持するオブジェクト。

## error

*object*

エラー情報を保持するオブジェクト。

## info

*object*

APIの実行に関する情報を保持するオブジェクト。

### calculationTime

*integer*

最適化計算にかかった秒数。
5秒ごとに切り上げられる。
入力のcalculationTimeで最適化計算の時間を指定することができるが実際に動く秒数は多少前後するため、指定した値と一致するとは限らない。

### version

*string*

実行されたAPIのバージョン。
