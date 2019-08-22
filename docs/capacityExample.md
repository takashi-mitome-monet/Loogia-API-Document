# 容量制約

配送ルートに割り当てられた[job](docs/job.md)の容量の和が[carrier](docs/carrier.md)の積載可能な容量を超過しないための条件。

具体的には、carriesに設定されるsizeを、各jobで要求されるsizeの和が超えなければ制約を満たす。一方、sizeの和が超過する場合は、挿入することによってcarrierのsizeを超えるjobは割り当てから除外される。

配送時では、各仕事(job)先で車両に集荷物を積んで行くが、容量を超過した場合は積むことができないため、その仕事は行われない。

## 容量制約を満たす

[input.jsonの例](instances/capacity.md)を元に手順を追っていく。

1. [carriers](carrier.md)内の各carrierの"capacities"に積積載可能な容量の最大値"size"を設定。



	```
	  "carriers": [
	    {
	    
	  　  ・・・
	      "capacities": [
	        {
	          "dimId": 0,
	          "size": 100000
	        }
	      ],
	      
	      ・・・
	    }
	  ]
	
	```

1. また[jobs](job.md)に各jobの"demands"にその作業で要求される"size"を設定。

	```　
	  "jobs": [
	    {
	    
	      ・・・  
	      "demands": [
	        {
	          "dimId": 0,
	          "size": 1
	        }
	      ]
	    },
	  ]
	
	```

<br>以上の操作で得られた[output.json](Output.json.md)は[こちら](instances/outputs/capacity.md)<br><br>


## 容量制約超過

一方、容量制約を超過したjobはunsignedjobへ追加される。<br>

本[input.jsonの例](instances/overCapacity.md)では"jobId": "1" のjobの容量を超過させている。

```
"jobs": [
    {
    
      ・・・
      {
      "jobId": "1",
      
      ・・・
      "demands": [
        {
          "dimId": 0,
          "size": 100000
        }
      ]
    },


```
<br>
結果では"jobId": "1" がなくなり、unassigndJobsに追加されていることが確認できる。<br>
output.jsonは[こちら](instances/outputs/overCapacity.md)