# RoutingEngine-IO
Input/Output definition for Optimind Routing Engines

## input.json
Web等のインターフェースからエンジン向けへ投げるデータ．Webとエンジンの間の翻訳モジュールがこれを解釈してエンジンごとに必要な形式へ変換する．

### 考慮事項
* 同一種類の車両でもその台数分情報を入力しなければならない
* Pick-up and Delivery を含めるか？どこまで含めるか？
 * pick-upとdeliveryがペアのもの，どこからどこへ運んでもいいもの
* ソルバーの計算時間などのメタデータ（？）を含めるか？
