# job

配送・集荷などの業務を表す情報。

## id\*

*string*

jobのID。

## pickup\*

*object*

jobの集荷に関する情報。
集荷を行わないjob（例えばデポで荷物を積んでそれをトラックで配りに行くjob）の場合はnullを指定する。

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

jobの配送に関する情報。
配送を行わないjob（例えばトラックで荷物を集めて来てデポで降ろすというjob）の場合はnullを指定する。

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

*string*

要求量の種類を表すID。
[carrier](carrier.md)が持つcapacityのIDと対応する。
どのcarrierも持っていないIDを指定するとエラーとなる。

### size\*

*integer (≧0)*

消費する容量。