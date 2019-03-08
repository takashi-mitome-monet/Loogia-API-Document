# Input.json

Input.jsonの各キーが取る値についての解説。
キー名の直後の斜体文字がデータ型を表す。

|データ型|意味|
|---|---|
|integer|整数|
|real|実数|
|string|文字列|
|boolean|真偽値|
|array|配列|
|object|オブジェクト|

必須のキーにはキー名の後にアスタリスク(\*)をつける。

## async

*boolean*

計算を非同期で実行するかどうか。
非同期（`true`）の場合、リクエストがサーバーに渡った時点で200が返る。
ただしこの時点で200が返っても計算が成功することを保証するものではない。

同期（`false`）の場合、計算結果がbodyに入れられて返る。
ただしHTTP通信が30秒でタイムアウトする。

何も指定しない場合は同期（`false`）として動作する。

## restrictUturn

*boolean*

Uターンコストを考慮するかどうか。
考慮する（`true`）場合、各spotに設定された`uTurnCost`が有効となり、Uターンコストを加味したルートを探索する。

## balancing

*object*

ルートを均等化したい場合に入力するオブジェクト。入力された車両をすべて用いた上で均等化する。
均等化しないときはキー自体を渡さない。

### type

*string*

均等化のタイプ。各ルートの訪問先数を均等化したい場合は`"service"`を、 勤務時間を均等化したい場合は `"duration"` を指定。

### intensity

*integer (1~10)*

均等化の効き具合。値が大きいほど強く均等化する。指定しない場合、エンジン内部でのデフォルト値（intensity=3）で均等化する。

## ignoreReturnTrip

*boolean*

デポへの帰り道の距離を目的関数値として無視するかどうかを指定する。
`true` を指定するとデポへの帰り道を考えずに最適化計算が行われる。
carrierにcostを設定していても無視され、常に時間の最小化を目的として最適化される。

## calculationTime

*real (≧0)*

最適化の計算時間（秒）。
レスポンスまでにかかる時間ではない。

## callback

*object*

【非公開】計算結果のコールバック先。

### createResult, updateProgress

*object*

callback先の情報。
createResultは計算結果を通知する先、updateProgressは計算過程を通知する先。

#### url\*

*string*

コールバック先のURL。

#### meta

コールバック先にそのまま返すオブジェクト。

### headers

コールバック先に返すヘッダ。

## export

*object*

【非公開】計算結果の出力先。

### createResult, updateProgress

*object*

export先の情報。
createResultは計算結果を通知する先、updateProgressは計算過程を通知する先。

#### type\*

*string*

出力先の種類。
`"aws-s3"` と `"aws-dynamodb"` と `"local"` を指定可能。

|type|種類|
|:--|:--|
|`aws-s3`|AWS S3（未対応）|
|`local`|ソルバーが動作するOS上のローカルファイル|

#### bucket

*string*

typeに `"aws-s3"` を指定した場合に必須。
保存先のS3のバケット名を指定する。

#### table

*string*

typeに `"aws-dynamodb"` を指定した場合に必須。
保存先のDynamoDBのテーブル名を指定する。

#### key

*string*

typeに `"aws-s3"` または `"aws-dynamodb"` を指定した場合に必須。
`"aws-s3"` の場合、保存先のS3のキー名を指定する。
`"aws-dynamodb"` の場合、保存先のDynamoDBのkeyカラムの値を指定する。

#### path

*string*

typeに `"local"` を指定した場合に必須。
保存先の絶対パスを指定する。

## mapModuleOption

*object*

### restrictTurnRight

*boolean*

経路上で右折をしないルートのみに限定する。

### allowHighway

*string*

高速道路の使用に関する設定。
以下の値のうちいずれかを指定する。
キーが存在しないまたは値がnullである場合は `"Never"` として処理される。

|値|説明|
|:--|:--|
|`Always`|いつでも高速道路の使用を許可する|
|`OnFirstLeg`|デポから出発して最初の訪問先までの経路上でのみ高速道路の使用を許可する|
|`OnLastLeg`|最後の訪問先を出発してデポまでの経路上でのみ高速道路の使用を許可する|
|`OnFirstAndLastLegs`|デポから出発して最初の訪問先までと最後の訪問先を出発してデポまでの経路上でのみ高速道路の使用を許可する|
|`Never`|高速道路の使用を許可しない|

## carriers\*

*array*

[carrier](carrier.md)の配列。
ここで指定された車両を用いてルートを作成する。
すべての車両を使うとは限らない。

## depots\*

*array*

[depot](depot.md)の配列。集荷・配送の拠点を表す情報。
ここで指定したdepotを用いて車両の出発地点・帰着地点を決定する。

## spots\*

*array*

[spot](spot.md)の配列。
荷物を配送・集荷する訪問先を表す情報。ここで指定したspotのうち、
各jobに対してjobTypeがpickupまたはdeliveryの場合は1つ、pickupDeliveryの場合は2つが割り当てられる。

## jobs\*

*array*

[job](job.md)の配列。
制約、コストによってはここで指定したすべてのjobがルートに組み込まれるとは限らない。
ルートに組み込まれなかったjobはunassignedJobsとして[Output.json](Output.json.md)に出力される。

## paths\*

*array*

[path](path.md)の配列。
すべてのdepot/spot間に対して1つ以上のpathが必要。
配列の要素数がゼロの場合またはキーが存在しない場合またはnullの場合は内部で持っている地図データからパス情報を取得する。


