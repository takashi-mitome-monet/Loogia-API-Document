# Usage.json

Usage.jsonの各キーが取る値についての解説。
キー名の直後の斜体文字がデータ型を表す。

|データ型|意味|
|---|---|
|integer|整数|
|real|実数|
|string|文字列|
|boolean|真偽値|
|array|配列|
|object|オブジェクト|

## since, until

*integer (0〜253402300799)* or *string*

計算時間を集計する期間を指定する。
UNIX時間を整数で入力するかISO8601形式を文字列で入力する。
sinceとuntilはどちらもUNIX時間またはどちらもISO8601形式である必要がある。

ISO8601形式では以下のフォーマットを許容する。

|フォーマット|例|例の解釈（世界協定時）|
|:--|:--|:--|
|*[year]*-*[month]*-*[day][timezone]*|2019-01-01+00:00|2019年1月1日0時0分0秒|
|*[year]*-*[month]*-*[day]*T*[hour]*:*[minute][timezone]*|2019-01-01T12:30Z|2019年1月1日12時30分0秒|
|*[year]*-*[month]*-*[day]*T*[hour]*:*[minute]*:*[second][timezone]*|2019-01-01T12:00:00+09:00|2019年1月1日21時0分0秒|

APIバージョンをまたいで集計される。