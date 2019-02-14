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

車両のID。

## meta

*object*

メタデータを保持するオブジェクト。

## error

*object*

エラー情報を保持するオブジェクト。

