# Input.json

各キーが取る値についての解説。
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
非同期（`true`）の場合，リクエストがサーバーに渡った時点で200が返る。
ただしこの時点で200が返っても計算が成功することを保証するものではない。

同期（`false`）の場合，計算結果がbodyに入れられて返る。
ただしHTTP通信が30秒でタイムアウトする。

何も指定しない場合は同期（`false`）として動作する。

## version

*string*

最適化エンジンのバージョンを指定する。
バージョン番号やステージ（`dev`, `prod`）などを指定可能。
何も指定しない場合はAPIのURLで指定されたステージで実行される。

## calculationTime

*real (≧-1)*

最適化の計算時間（秒）。
レスポンスまでにかかる時間ではない。
-1 を指定すると自動で最適な計算時間が設定される

## callback

*object*

【非公開】計算結果のコールバック先。

### createResult, updateProgress

*object*

callback先の情報。
createResultは計算結果を通知する先，updateProgressは計算過程を通知する先。

#### url\*

*string*

コールバック先のURL。

#### meta

コールバック先にそのまま返すオブジェクト。

### headers

コールバック先に返すヘッダ。

## export

*object*

計算結果の出力先。

### createResult, updateProgress

*object*

export先の情報。
createResultは計算結果を通知する先，updateProgressは計算過程を通知する先。

#### type\*

*string*

出力先の種類。
`"aws-s3"` と `"local"` を指定可能。

|type|種類|
|--|--|
|aws-s3|AWS S3（未対応）|
|local|ソルバーが動作するOS上のローカルファイル|

#### bucket

*string*

typeに `"aws-s3"` を指定した場合に必須。
保存先のS3のバケット名を指定する。

#### key

*string*

typeに `"aws-s3"` を指定した場合に必須。
保存先のS3のキー名を指定する。

#### path

*string*

typeに `"local"` を指定した場合に必須。
保存先の絶対パスを指定する。

## mapModuleOption

*object*

地図エンジンにそのまま渡す。

## carriers\*

*array*

[carrier](carrier.md)の配列。
ここで指定された車両を用いてルートを作成する。
すべての車両を使うとは限らない。

## stops\*

*array*

[stop](stop.md)の配列。
制約，コストによってはここで指定したすべてのstopを訪れるとは限らない。
ルートに組み込まれなかった点はunassignedとして出力される。

## paths

*array*

[path](path.md)の配列。
すべてのdepot/stop間に対して1つ以上のpathが必要。
配列の要素数がゼロの場合またはキーが存在しない場合またはnullの場合は内部で持っている地図データからパス情報を取得する。


