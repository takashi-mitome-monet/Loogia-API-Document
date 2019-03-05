## 出力エラー

出力するエラーは以下の通り．

|エラーコード|エラーメッセージ|エラー内容|
|:--|:--|:--|
|NoBodyError|there is no body|HTTPボディが存在しない|
|RequestTimeoutMapError|map engine timeout, please reduce the number of stops or narrow area|地図エンジンにおいてタイムアウトが発生した|
|UnknownMapError|unknown error in map engine|地図エンジンにおいて不明なエラーが発生した|
|InvalidAsyncValueInputError|async must be boolean|asyncの値が真偽値ではない|
|InvalidCalculationTimeValueInputError|calculationTime must be Integer|calculationTimeの値が整数ではない|
|InvalidIgnoreReturnTripValueInputError|ignoreReturnTrip must be boolean|ignoreReturnTripの値が真偽値ではない|
|InvalidVersionInputError|version must be string|versionの値が文字列ではない|
|InvalidAsyncWithVersionInputError|async must be true if engine version specified|versionが指定されているがasyncがfalseである|
|NoCalculationTimeWithAsyncTrueInputError|calculationTime must be set if async is true|asyncがtrueであるがcalculationTimeが存在しない|
|VersionNotFoundInputError|unknown engine version is specified|存在しないバージョンが指定された|
|StopsAndSpotsCoexistInputError|stops and spots must not coexist in input|インプットにstopsキーとspotsキーの両方が存在する|
|NoStopsOrSpotsInputError|input has neither stops nor spots|インプットにstopsキーとspotsキーの両方とも存在しない|
|NoDepotInputError|input has no depot|depotが存在しない|
|NoDepotIdInputError|depot has no id|depotにIDが無いものがある|
|InvalidDepotIdInputError|depot has invalid type of id|depotにIDの形式が不正|
|NoDepotGeocodeInputError|depot (id:xx) has no geocode|depotにgeocodeが無いものがある|
|NoDepotLatLngInputError|depot (id:xx) has no lat or lng|depotに緯度経度が無いものがある|
|InvalidDepotLatLngInputError|depot (id:xx) has invalid format lat or lng|depotに緯度経度の形式が不正なものがある|
|NoStopInputError|input has no stop|stopが１つも無い|
|NoStopIdInputError|stop has no id|stopにIDが無いものがある|
|InvalidStopIdInputError|stop has invalid format id|stopにIDの形式が不正なものがある|
|NoStopGeocodeInputError|stop has no geocode|stopにgeocodeが無いものがある|
|NoStopLatLngInputError|stop has no lat or lng|stopに緯度経度が無いものがある|
|InvalidStopLatLngInputError|stop has invalid format lat or lng|stopに緯度経度の形式が不正なものがある|
|NoStopTimeWindowTypeInputError|stop time window type is not set|stopの時間枠タイプが設定されていない|
|InvalidStopTimeWindowTypeInputError|stop has invalid format time window type|stopの時間枠のタイプの形式が不正なものがある|
|NoStopTimeWindowRangeInputError|stop time window ranges are not set|stopの時間枠のタイプがrangesだがrangeが存在しない|
|NoStopReadyDueTimeInputError|stop time window range has no readyTime or dueTime|stopの時間枠のタイプがrangesだがrangeの中身が存在しない|
|InvalidStopReadyDueTimeValueInputError|stop time window range has invalid readyTime or dueTime value|stopの時間枠のreadyTimeまたはdueTimeの値が不正 (dueTimeの値がreadyTimeの値より小さいなど)|
|InvalidStopReadyDueTimeInputError|stop time window range has invalid format readyTime or dueTime|stopの時間枠のreadyTimeまたはdueTimeの形式が不正|
|NoStopDimIdInputError|stop dimId of demand is not set|stopのdemandのdimIdが存在しない|
|NoStopDemandSizeInputError|stop demand size is not set|stopのdemandのsizeが存在しない|
|InvalidStopDemandSizeInputError|stop has invalid format of demand size|stopのdemandのsizeの形式が不正|
|NoStopDimIdInCarrierCapacityInputError|stop dimId of demand is not exist in carrier capacity|stopのdemandのdimIdをcapacityとして持つcarrierが存在しない|
|NoStopServiceDurationInputError|stop service duration is not set|stopのserviceDurationが存在しない|
|NoStopServiceDurationGeneralInputError|stop service duration (general) is not set|stopのserviceDurationのgeneralが存在しない|
|InvalidStopServiceDurationInputError|stop service duration (general) is invalid format|stopのserviceDurationのgeneralの形式が不正|
|InvalidStopPriorityInputError|stop priority is invalid format|stopのpriorityの形式が不正|
|InvalidStopSkillInputError|stop skills is invalid format|stopのskillの形式が不正|
|InvalidStopUTurnCostInputError|stop uTurnCost is invalid format|stopのuTurnCostの形式が不正|
|NoStopServiceTypeInputError|some stop do not have service type|stopのserviceTypeが存在しない|
|NoSpotInputError|input has no spot|spotが１つも無い|
|NoSpotIdInputError|spot has no id|spotにIDが無いものがある|
|InvalidSpotIdInputError|spot has invalid format id|spotにIDの形式が不正なものがある|
|NoSpotLocationInputError|spot has no location|spotにlocationが無いものがある|
|NoSpotLocationGeocodeInputError|spot location has no geocode|spotが持つlocationにgeocodeが無いものがある|
|NoSpotLocationGeocodeLatLngInputError|spot location has no lat or lng|spotのlocationが持つgeocodeに緯度経度が無いものがある|
|InvalidSpotLocationGeocodeLatLngInputError|spot location has invalid format lat or lng|spotのlocationが持つgeocodeに緯度経度の形式が不正なものがある|
|InvalidSpotLocationUTurnCostInputError|spot location uTurnCost is invalid format|spotのlocationが持つuTurnCostの形式が不正|
|NoJobInputError|input has no job|jobが１つも無い|
|NoJobIdInputError|job has no id|jobにIDが無いものがある|
|InvalidJobIdInputError|job has invalid format id|jobにIDの形式が不正なものがある|
|NoJobPickupDeliveryInputError|job has neither pickup nor delivery|jobがpickupとdeliveryのどちらも持たない|
|NoJobPickupSpotIdInputError|pickup has no spotId|pickupがspotIdを持たない|
|InvalidJobPickupSpotIdInputError|pickup has invalid format spotId|pickupのspotIdに形式が不正なものがある|
|NoJobPickupTimeWindowTypeInputError|pickup time window type is not set|pickupの時間枠タイプが設定されていない|
|InvalidJobPickupTimeWindowTypeInputError|pickup has invalid format time window type|pickupの時間枠のタイプの形式が不正なものがある|
|NoJobPickupTimeWindowRangeInputError|pickup time window ranges are not set|pickupの時間枠のタイプがrangesだがrangeが存在しない|
|NoJobPickupReadyDueTimeInputError|pickup time window range has no readyTime or dueTime|pickupの時間枠のタイプがrangesだがrangeの中身が存在しない|
|InvalidJobPickupReadyDueTimeValueInputError|pickup time window range has invalid readyTime or dueTime value|pickupの時間枠のreadyTimeまたはdueTimeの値が不正 (dueTimeの値がreadyTimeの値より小さいなど)|
|InvalidJobPickupReadyDueTimeInputError|pickup time window range has invalid format readyTime or dueTime|pickupの時間枠のreadyTimeまたはdueTimeの形式が不正|
|NoJobPickupServiceDurationInputError|pickup service duration is not set|pickupのserviceDurationが存在しない|
|NoJobPickupServiceDurationGeneralInputError|pickup service duration (general) is not set|pickupのserviceDurationのgeneralが存在しない|
|InvalidJobPickupServiceDurationInputError|pickup service duration (general) is invalid format|pickupのserviceDurationのgeneralの形式が不正|
|NoJobDeliverySpotIdInputError|delivery has no spotId|deliveryがspotIdを持たない|
|InvalidJobDeliverySpotIdInputError|delivery has invalid format spotId|deliveryのspotIdに形式が不正なものがある|
|NoJobDeliveryTimeWindowTypeInputError|delivery time window type is not set|deliveryの時間枠タイプが設定されていない|
|InvalidJobDeliveryTimeWindowTypeInputError|delivery has invalid format time window type|deliveryの時間枠のタイプの形式が不正なものがある|
|NoJobDeliveryTimeWindowRangeInputError|delivery time window ranges are not set|deliveryの時間枠のタイプがrangesだがrangeが存在しない|
|NoJobDeliveryReadyDueTimeInputError|delivery time window range has no readyTime or dueTime|deliveryの時間枠のタイプがrangesだがrangeの中身が存在しない|
|InvalidJobDeliveryReadyDueTimeValueInputError|delivery time window range has invalid readyTime or dueTime value|deliveryの時間枠のreadyTimeまたはdueTimeの値が不正 (dueTimeの値がreadyTimeの値より小さいなど)|
|InvalidJobDeliveryReadyDueTimeInputError|delivery time window range has invalid format readyTime or dueTime|deliveryの時間枠のreadyTimeまたはdueTimeの形式が不正|
|NoJobDeliveryServiceDurationInputError|delivery service duration is not set|deliveryのserviceDurationが存在しない|
|NoJobDeliveryServiceDurationGeneralInputError|delivery service duration (general) is not set|deliveryのserviceDurationのgeneralが存在しない|
|InvalidJobDeliveryServiceDurationInputError|delivery service duration (general) is invalid format|deliveryのserviceDurationのgeneralの形式が不正|
|NoJobDimIdInputError|job demand dimId is not set|jobのdemandのdimIdが存在しない|
|NoJobDemandSizeInputError|job demand size is not set|jobのdemandのsizeが存在しない|
|InvalidJobDemandSizeInputError|job demand has invalid format size|jobのdemandのsizeの形式が不正|
|NoJobDimIdInCarrierCapacityInputError|job dimId of demand is not exist in carrier capacity|jobのdemandのdimIdをcapacityとして持つcarrierが存在しない|
|InvalidJobPriorityInputError|job priority is invalid format|jobのpriorityの形式が不正|
|InvalidJobSkillInputError|job skills is invalid format|jobのskillの形式が不正|
|NoCarrierStartLocationDepotInputError|carrier start location is not exist in depot|carrierのstart locationがdepotに存在しない|
|NoCarrierEndLocationDepotInputError|carrier end location is not exist in depot|carrierのend locationがdepotに存在しない|
|InputJSONFormatError|invalid format JSON is received|入力したJSONのパース中にエラーが発生した|
|FailGetPathsError|failed to get paths|pathsを取得できなかった|
|FailGetEuclideanDistancePathsError|failed to get euclidean distance paths|直線距離での距離行列を用いたpathsを取得できなかった|
|UnknownInputError|unknown error in reading input|インプットの読み込み中に不明なエラーが発生した|
|UnknownOptimizeError|unknown error in optimizing|最適化計算中に不明なエラーが発生した|
|UnknownRunEngineError|unknown error in running engine|最適化エンジンの実行中に不明なエラーが発生した|
|UnknownError|unknown error|不明なエラーが発生した|
|UseEuclideanDistancePathsError|failed get paths and use euclidean distance paths alternatively|正規のpathsの取得に失敗したため直線距離の距離行列をpathsとして代替する|