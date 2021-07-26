# Dynamic Ads for Display
## What is "Dynamic Ads for Display"?
Dynamic Ads for Display automatically creates and delivers ads based on user’s behavioral property. It can display various ads dynamically based on the interests and concerns of the browsing user.<br>
For details, refer to the help below.<br>
・<a href="https://ads-help.yahoo.co.jp/yahooads/ydn/articledetail?lan=en&aid=22319">What is Dynamic Ads for Display</a><br><br>
This page explains how to upload and update the Item list.<br>

#### 1.	Add Item list
Add feed with FeedService:add.

##### Request sample
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

##### Response sample
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

#### 2. Upload product information
Add tsv file of product information, and upload it with FeedDataService:upload.

|Item ID|Item Name|Description|Landing Page URL|Price|Sale Price|
|---|---|---|---|---|---|
|12340001|Men's bags|Sold at a special price for a limited time|http://www.example.jp|3000|2500|
|12340002|Ladie's bags|Great deals|http://www.example2.jp|2000|1500|

For details, refer to the help abount tsv file below.<br>
・<a href="https://ads-help.yahoo.co.jp/yahooads/ydn/articledetail?lan=en&aid=22325">Create Item list file (Dynamic Ads for Display)</a><br><br>

##### Request sample
※Add product information file with `multipart/form-data` and `name:file` in request body.<br>
※Use `isDebug:true`, check whether the upload is successful without number of upload.<br>
https://ads-display.yahooapis.jp/api/v5/FeedDataService/upload?accountId=1002390459&feedId=1000007518&uploadType=UPDATE_ALL&isDebug=false

##### Response sample
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
#### 3. Set product information
Set product information with FeedDataService:upload. There are all updates and partial updates as update methods.<br>
In this part, add tsv file of product information below to partial updates.<br>
※set only 12340002 and write only it in tsv.

|Item ID|Item Name|Description|Landing Page URL|Price|Sale Price|
|---|---|---|---|---|---|
|12340002|Ladie's eco bags|Convincing sale|http://www.example3.jp|1500|1000|

##### Request sample
※UploadType:UPDATE_PART to partial updates.<br>
https://ads-display.yahooapis.jp/api/v5/FeedDataService/upload?accountId=1002390459&feedId=1000007518&uploadType=UPDATE_PART&isDebug=false

##### Response sample
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

#### 4. Real-time set Item list
Directly update by specifying itemID is possible with FeedItemService:set. This process does not cosume update count.<br>
For example, ItemId:12340002 is updated to price:1000 and salePrice:900.

##### Request sample
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

##### Response sample
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
#### 5. Delete product information when update part
When update part of product information with FeedDataService:upload, add delete column in product list file.<br>
※Below, delete 12340001 and keep 12340002.

|Item ID|Item Name|Description|Landing Page URL|Price|Sale Price|Delete|
|---|---|---|---|---|---|---|
|12340001|Men's bags|Sold at a special price for a limited time|http://www.example.jp|3000|2500|1|
