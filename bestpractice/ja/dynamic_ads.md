# 動的ディスプレイ広告機能
## 動的ディスプレイ広告とは
ウェブサイトを訪れたインターネットユーザーの行動履歴をもとに、各ユーザーの興味や関心に合わせた内容の広告を動的に生成、配信する広告タイプです。<br>
詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo.co.jp/yahooads/ydn/articledetail?lan=ja&aid=36349">動的ディスプレイ広告について</a><br><br>
このページでは、商品リストのアップロード、更新について解説します。<br>

#### 1.	商品リストの新規作成
FeedService:addで、Feed情報を新規登録します。

##### リクエストサンプル
```json
{
  "accountId": 1002390459,
  "operand": [
    {
      "accountId": 1002390459,
      "feedName": "test_0828_01"
    }
  ]
}
```

##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "c3b301c4d2760bee9772949b7a270f3e",
    "rval": {
        "values": [
            {
                "feed": {
                    "accountId": 1002390459,
                    "feedId": 1000007518,
                    "feedName": "test_0828_01",
                    "itemCount": null,
                    "approvedItemCount": null,
                    "disApprovedItemCount": null
                },
                "uploadLimits": null,
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```

#### 2. 商品情報のアップロード処理
次に、以下のような商品情報tsvファイルを作成し、FeedDataService:uploadを使って、商品情報をアップロードします。

|Item ID|Item Name|Description|Landing Page URL|Price|Sale Price|
|---|---|---|---|---|---|
|12340001|メンズバッグ|期間限定特別価格で販売|http://www.example.jp|3000|2500|
|12340002|レディースバッグ|お得なセール|http://www.example2.jp|2000|1500|

商品情報tsvファイルについて、詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo.co.jp/yahooads/ydn/articledetail?lan=ja&aid=36277">商品リストファイルの作成（動的ディスプレイ広告）</a>

##### リクエストサンプル
※リクエストボディには `multipart/form-data` 形式でnameを `file` とした商品情報tsvファイルを指定します。<br>
※`isDebug:true` とすることで、アップロード回数を消費せずにファイルアップロードリクエストが成功するかどうかを確認できます。<br>
https://ads-display.yahooapis.jp/api/v5/FeedDataService/upload?accountId=1002390459&feedId=1000007518&uploadType=UPDATE_ALL&isDebug=false

##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "018e8777dd275ef523f169c5d7199912",
    "rval": {
        "values": [
            {
                "errors": null,
                "feedData": {
                    "accountId": 1002390459,
                    "completeDate": null,
                    "errorCount": null,
                    "errorRate": null,
                    "feedId": 1000007518,
                    "fileUploadSrc": "API",
                    "fileUploadStatus": "UPLOADED",
                    "isDebug": false,
                    "itemListUploadId": 1000551417,
                    "itemListUploadType": "UPDATE_ALL",
                    "uploadDate": "20200903151342"
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 3. 商品情報の更新
FeedDataService:uploadで商品情報を更新します。更新方法には全件更新と部分更新（差分のみの更新）があります。<br>
今回は部分更新をするため、以下のような商品情報tsvファイルを作成します。<br>
※12340002、のみ更新。12340001、は更新なしのためtsvには記載なし。

|Item ID|Item Name|Description|Landing Page URL|Price|Sale Price|
|---|---|---|---|---|---|
|12340002|レディースエコバッグ|納得プライス|http://www.example3.jp|1500|1000|

##### リクエストサンプル
※部分更新のため、uploadTypeを、UPDATE_PARTにします。<br>
https://ads-display.yahooapis.jp/api/v5/FeedDataService/upload?accountId=1002390459&feedId=1000007518&uploadType=UPDATE_PART&isDebug=false

##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "efbf5d46e1eb452a90309c5d570e94c0",
    "rval": {
        "values": [
            {
                "errors": null,
                "feedData": {
                    "accountId": 1002390459,
                    "completeDate": null,
                    "errorCount": null,
                    "errorRate": null,
                    "feedId": 1000007518,
                    "fileUploadSrc": "API",
                    "fileUploadStatus": "UPLOADED",
                    "isDebug": false,
                    "itemListUploadId": 1000551418,
                    "itemListUploadType": "UPDATE_PART",
                    "uploadDate": "20200903151420"
                },
                "operationSucceeded": true
            }
        ]
    }
}
```

#### 4. 商品情報のリアルタイム更新
FeedItemService:setを使用すると、ItemIDを指定しての直接更新が可能です。またこの処理では、アップロード回数を消費しません。<br>
下の例では、itemId：12340002の商品を、価格：1000、セール価格：900、に更新しています。

##### リクエストサンプル
```json
{
  "accountId": 1002390459,
  "operand": [
    {
      "feedId": 1000007518,
      "itemId": "12340002",
      "price": 1000,
      "salePrice": 900
    }
  ]
}
```

##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "05dbab871b6c02fa4061c24f5929644f",
    "rval": {
        "values": [
            {
                "errors": null,
                "operationSucceeded": true,
                "requestReceived": true
            }
        ]
    }
}
```
#### 5. 部分更新時の商品情報の削除
FeedDataService:uploadで商品情報を部分更新するとき、商品リストファイルに「削除」列を追加することで、商品の削除が可能になります。<br>
※以下では、12340001を削除する方法を記載しています。12340002は記載していないので影響なしです。

|Item ID|Item Name|Description|Landing Page URL|Price|Sale Price|Delete|
|---|---|---|---|---|---|---|
|12340001|メンズバッグ|期間限定特別価格で販売|http://www.example.jp|3000|2500|1|
