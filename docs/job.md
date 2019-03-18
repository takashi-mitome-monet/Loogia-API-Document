# job

配送・集荷などの業務を表す情報。

## jobId\*

*string*

jobのID。

## jobType

*string*

jobの業務種別を表す情報。`"pickup"`, `"delivery"`, `"pickupDelivery"`のうち、いずれかが割り当てられる。

* pickup: 特定の訪問先からデポに荷物を運ぶ業務
* delivery: デポから特定の訪問先に荷物を運ぶ業務
* pickupDelivery: 特定の訪問先から特定の訪問先に荷物を運ぶ業務

## pickup\*

*object*

jobTypeがpickupまたはpickupDeliveryである場合に与えられる情報。
jobTypeがdeliveryである場合はnullとする。

### id\*

*string*

pickupのID。

### spotId\*

*string*

訪問先である[spot](spot.md)のID。

### timeWindow\*

*object*

時間枠を表す[timeWindow](timeWindow.md)のオブジェクト。

### serviceDuration\*

*object*

訪問先における業務の実行にかかる時間を表す[serviceDuration](serviceDuration.md)のオブジェクト。

## delivery\*

*object*

jobTypeがdeliveryまたはpickupDeliveryである場合に与えられる情報。
jobTypeがpickupである場合はnullとする。

### id\*

*string*

deliveryのID。

### spotId\*

*string*

訪問先である[spot](spot.md)のID。

### timeWindow\*

*object*

時間枠を表す[timeWindow](timeWindow.md)のオブジェクト。

### serviceDuration\*

*object*

訪問先における業務の実行にかかる時間を表す[serviceDuration](serviceDuration.md)のオブジェクト。

## priority

*integer (1〜10)*

訪問の優先度を指定する。
値が小さい方が優先度が高い。
制約をすべて満たした上ですべての点を回りきれる解が見つからなかった場合に一部のjobがunassignedとなる。
その際に優先度が低いものがunassignedとなりやすくなる。

## skills

*array*

文字列の配列。
各文字列はjobが要求するスキルを表す。
[carrier](carrier.md)が持つskillと対応する。
要求するスキルを持つcarrierのみがこのjobを受け持つことができる。

## demands

*array*

訪問することで消費するcarrierの容量。
[carrier](carrier.md)のcapacityに対応する。

### dimId\*

*integer (≧0)*

要求量の種類を表すID。
[carrier](carrier.md)が持つcapacityのIDと対応する。
どのcarrierも持っていないIDを指定するとエラーとなる。

### size\*

*integer (≧0)*

消費する容量。