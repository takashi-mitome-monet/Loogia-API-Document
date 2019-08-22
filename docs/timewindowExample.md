# 時間制約

配送時に設定される時間の条件。<br>
「全体の時間枠」「各顧客の作業開始可能な時間枠」の2つに分けられる。<br>

* 全体の時間枠：　車両が出発可能な時刻・帰着しなければならない時刻を表す。<br>
* 各顧客の作業開始可能な時間枠：　各顧客の作業開始可能な時刻・作業を終了しなければならない時刻。<br>

全体の時間枠について、全体の仕事の終了時刻までに集荷地点に戻ることが可能でなければ仕事(job)の件数を減らす。

また各顧客の作業開始可能な時間枠について、配達不能な仕事先(job)が生じないよう各仕事のルート設計を行うが、移動時間や作業開始可能な時間枠の都合上、配達不能な仕事先が生じてしまうならば優先度などを考慮した上で仕事(job)を減らす。


## 時間制約を満たす

[input.jsonの例](instances/timeWindow.md)を元に手順を追っていく。


1. [carriers](carrier.md)のstartLocationに出発可能時刻、endLocationに帰着しなければならない時刻を設定する。

	```
	 "carriers": [
	 
	     ・・・
	    
	      "startLocation": {
	        "id": "NagoyakitaPostOffice",
	        "time": 1528678220
	      },
	      
	      ・・・
	      
	      "endLocation": {
	        "id": "NagoyakitaPostOffice",
	        "time": 1528722000
	      }
	  ],
	```

2. 	また各[job](job.md)のtimeWindowを入力し、各訪問先に作業可能な開始時間を設定。

	```
	 "jobs": [
	    {
	    
	    　・・・
	        "timeWindow": {
	          "ranges": [
	            {
	              "readyTime": 1528675200,
	              "dueTime": 1528686900
	            }
	          "type": "range"
	        },
	        
	     ・・・
	
	```

<br>以上の操作で得られた[output.json](Output.json.md)のコードは[こちら](instances/outputs/timeWindow.md)<br><br>

## 時間制約超過

一方、時間制約を超過したjobはunsignedjobへ追加される。<br>

本[input.jsonの例](instances/overTimeWindow.md)では"jobId": "1" のjobの時間を超過させている。

```
"jobs": [
    {
      "jobId": "1",
      
		・・・
		　
        "timeWindow": {
          "ranges": [
            {
              "readyTime": 1528780000,
              "dueTime": 1528781000
            }
          ],
          "type": "range"
        },
        
    ・・・

```
<br>結果では"jobId": "1" がunsignedjobに割り当てられていることが確認できる。<br>
output.jsonのコードは[こちら](instances/outputs/overTimeWindow.md)