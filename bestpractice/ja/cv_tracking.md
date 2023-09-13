# コンバージョントラッキング機能
## コンバージョンとは
広告をクリックしたユーザーが、何らかの「成果」となる行動をとった数です。これを計測することで、広告がどの程度成果を上げているかなどを確認できます。<br>
詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044362?language=ja">コンバージョン測定とは</a>

## ディスプレイ広告API での実施方法
ディスプレイ広告APIでは、コンバージョントラッカー情報（コンバージョン測定タグおよび、タグごとのパフォーマンスデータ）の取得および追加・更新を行うために、ConversionTrackerService、を使用します。<br>
本サービスを利用することで、ディスプレイ広告で掲載されている広告からのコンバージョン数（商品の購入や会員登録、資料請求などサイト上で何らかの成約に至った件数）を取得することができ、広告がどの程度成果を上げているかなどを確認できます。<br>
コンバージョンタグは広告管理ツールとAPIで共有しています。

## シナリオ
A社は商品B（1万円）を販売しているが、ウェブページでコンバージョンを計測するための、コンバージョントラッカーを作成する。

<table class="standard">
  <tr>
　　<th>項目</th>
　　<th>値</th>
　　<th>項目の説明</th>
　</tr>
　<tr>
　　<td>category</td>
　　<td>PURCHASE（購入/販売）</td>
　　<td>コンバージョントラッカー情報のカテゴリ</td>
　</tr>
　<tr>
　　<td>conversionTrackerName</td>
　　<td>（分かりやすい名称を）</td>
　　<td>コンバージョントラッカーの名称</td>
　</tr>
　<tr>
　　<td>conversionTrackerType</td>
　　<td>WEB_CONVERSION</td>
　　<td>コンバージョンの種別</td>
　</tr>
　<tr>
　　<td>measurementPeriod</td>
　　<td>30</td>
　　<td>コンバージョン計測期間（●日）</td>
　</tr>
　<tr>
　　<td>status</td>
　　<td>ENABLED（ウェブページへのアクセスを記録する）</td>
　　<td>コンバージョントラッカー情報のステータス</td>
　</tr>
　<tr>
　　<td>userRevenueValue</td>
　　<td>10000</td>
　　<td>売上金額が固定のときの、1コンバージョンの売上（●円）※商品Bの値段</td>
　</tr>
</table>
<br>

#### 1.	トラッカー情報の登録
はじめに、ConversionTrackerService:addを使い、コンバージョントラッカー情報を追加します。

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "operand": [
    {
      "category": "PURCHASE",
      "conversionTrackerName": "Pro_B_CV",
      "conversionTrackerType": "WEB_CONVERSION",
      "measurementPeriod": 30,
      "status": "ENABLED",
      "userRevenueValue": 10000
    }
  ]
}
```

##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "02f056b7b9acec932c5b9d80c1c76a9d",
    "rval": {
        "values": [
            {
                "conversionTracker": {
                    "accountId": 111111,
                    "allConversionValue": null,
                    "allConversions": null,
                    "viewThroughConversions": null,
                    "appConversion": null,
                    "category": "PURCHASE",
                    "conversionTrackerId": 222222,
                    "conversionTrackerName": "Pro_B_CV",
                    "conversionTrackerType": "WEB_CONVERSION",
                    "conversionValue": null,
                    "conversionValueViaAdClick": null,
                    "conversions": null,
                    "conversionsViaAdClick": null,
                    "countingType": "MANY_PER_CLICK",
                    "crossDeviceConversions": null,
                    "excludeFromBidding": "FALSE",
                    "measurementPeriod": 30,
                    "measurementPeriodView": 1,
                    "mostRecentConversionDate": null,
                    "status": "ENABLED",
                    "userRevenueValue": 10000,
                    "webConversion": {
                        "snippet": [
                            {
                                "tag": "<script type=\"text/javascript\" language=\"javascript\">\n  /* <![CDATA[ */\n  var yahoo_ydn_conv_io = \"6asbtt0OLDUxHpzn5ru9\";\n  var yahoo_ydn_conv_label = \"2TU9U6IWZFPTMZVVMI4727707\";\n  var yahoo_ydn_conv_transaction_id = \"\";\n  var yahoo_ydn_conv_value = \"10000\";\n  /* ]]> */\n</script>\n<script type=\"text/javascript\" language=\"javascript\" charset=\"UTF-8\" src=\"https://b90.yahoo.co.jp/conv.js\"></script>",
                                "webConversionSnippetType": "JS"
                            },
                            {
                                "tag": "<img src=\"https://b90.yahoo.co.jp/c?yahoo_ydn_conv_io=6asbtt0OLDUxHpzn5ru9&yahoo_ydn_conv_label=2TU9U6IWZFPTMZVVMI4727707&yahoo_ydn_conv_transaction_id=&yahoo_ydn_conv_value=10000&guid=ON\" width=\"1\" height=\"1\" border=\"0\" />",
                                "webConversionSnippetType": "IMG"
                            }
                        ]
                    }
                },
                "errors": null,
                "operationSucceeded": true,
                "statsPeriodCustomDate": null
            }
        ]
    }
}
```
<br>

#### 2. コンバージョン計測タグの取得
次に、ConversionTrackerService:getを使い、コンバージョン計測タグを取得します。

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "conversionTrackerIds": [
    222222
  ],
  "conversionTrackerTypes": [
    "WEB_CONVERSION"
  ],
  "numberResults": 1,
  "startIndex": 1,
  "statuses": [
    "ENABLED"
  ]
}
```

##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "dd94f200a5b0cf4b8f9e32e72a8507ef",
    "rval": {
        "period": {
            "periodEndDate": {
                "periodDate": "20200807",
                "periodTime": "160000"
            },
            "periodStartDate": {
                "periodDate": "20200807",
                "periodTime": "000000"
            }
        },
        "totalAllConversionValue": "0",
        "totalAllConversions": 0,
        "totalConversionValue": "0",
        "totalConversionValueViaAdClick": "0",
        "totalConversions": 0,
        "totalConversionsViaAdClick": 0,
        "totalCrossDeviceConversions": 0,
        "totalNumEntries": 1,
        "values": [
            {
                "conversionTracker": {
                    "accountId": 111111,
                    "allConversionValue": null,
                    "allConversions": null,
                    "viewThroughConversions": null,
                    "appConversion": null,
                    "category": "PURCHASE",
                    "conversionTrackerId": 222222,
                    "conversionTrackerName": "Pro_B_CV",
                    "conversionTrackerType": "WEB_CONVERSION",
                    "conversionValue": null,
                    "conversionValueViaAdClick": null,
                    "conversions": null,
                    "conversionsViaAdClick": null,
                    "countingType": "MANY_PER_CLICK",
                    "crossDeviceConversions": null,
                    "excludeFromBidding": "FALSE",
                    "measurementPeriod": 30,
                    "measurementPeriodView": 1,
                    "mostRecentConversionDate": null,
                    "status": "ENABLED",
                    "userRevenueValue": 10000,
                    "webConversion": {
                        "snippet": [
                            {
                                "tag": "<script type=\"text/javascript\" language=\"javascript\">\n  /* <![CDATA[ */\n  var yahoo_ydn_conv_io = \"6asbtt0OLDUxHpzn5ru9\";\n  var yahoo_ydn_conv_label = \"2TU9U6IWZFPTMZVVMI4727707\";\n  var yahoo_ydn_conv_transaction_id = \"\";\n  var yahoo_ydn_conv_value = \"10000\";\n  /* ]]> */\n</script>\n<script type=\"text/javascript\" language=\"javascript\" charset=\"UTF-8\" src=\"https://b90.yahoo.co.jp/conv.js\"></script>",
                                "webConversionSnippetType": "JS"
                            },
                            {
                                "tag": "<img src=\"https://b90.yahoo.co.jp/c?yahoo_ydn_conv_io=6asbtt0OLDUxHpzn5ru9&yahoo_ydn_conv_label=2TU9U6IWZFPTMZVVMI4727707&yahoo_ydn_conv_transaction_id=&yahoo_ydn_conv_value=10000&guid=ON\" width=\"1\" height=\"1\" border=\"0\" />",
                                "webConversionSnippetType": "IMG"
                            }
                        ]
                    }
                },
                "errors": null,
                "operationSucceeded": true,
                "statsPeriodCustomDate": null
            }
        ]
    }
}
```
<br>

#### 3. タグをウェブサイトに埋め込み、計測を開始する
上記の、ConversionTrackerService:get、で取得した、snippetのtag（webConversion）を、ウェブサイトに埋め込んで、計測を開始します。<br><br>

#### 4. コンバージョンの計測結果を取得する
再び、ConversionTrackerService:getを使い、コンバージョンの計測結果を取得します。

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "conversionTrackerIds": [
    222222
  ],
  "conversionTrackerTypes": [
    "WEB_CONVERSION"
  ],
  "numberResults": 1,
  "startIndex": 1,
  "statuses": [
    "ENABLED"
  ]
}
```

##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "dd94f200a5b0cf4b8f9e32e72a8507ef",
    "rval": {
        "period": {
            "periodEndDate": {
                "periodDate": "20200807",
                "periodTime": "160000"
            },
            "periodStartDate": {
                "periodDate": "20200807",
                "periodTime": "000000"
            }
        },
        "totalAllConversionValue": "10000000",
        "totalAllConversions": 1000,
        "totalConversionValue": "100000000",
        "totalConversionValueViaAdClick": "100",
        "totalConversions": 10000,
        "totalConversionsViaAdClick": 50,
        "totalCrossDeviceConversions": 30,
        "totalNumEntries": 1,
        "values": [
            {
                "conversionTracker": {
                    "accountId": 111111,
                    "allConversionValue": 10000000,
                    "allConversions": 1000,
                    "viewThroughConversions": null,
                    "appConversion": null,
                    "category": "PURCHASE",
                    "conversionTrackerId": 222222,
                    "conversionTrackerName": "Pro_B_CV",
                    "conversionTrackerType": "WEB_CONVERSION",
                    "conversionValue": 100000000,
                    "conversionValueViaAdClick": 100,
                    "conversions": 10000,
                    "conversionsViaAdClick": 50,
                    "countingType": "MANY_PER_CLICK",
                    "crossDeviceConversions": 30,
                    "excludeFromBidding": "FALSE",
                    "measurementPeriod": 30,
                    "measurementPeriodView": 1,
                    "mostRecentConversionDate": null,
                    "status": "ENABLED",
                    "userRevenueValue": 10000,
                    "webConversion": {
                        "snippet": [
                            {
                                "tag": "<script type=\"text/javascript\" language=\"javascript\">\n  /* <![CDATA[ */\n  var yahoo_ydn_conv_io = \"6asbtt0OLDUxHpzn5ru9\";\n  var yahoo_ydn_conv_label = \"2TU9U6IWZFPTMZVVMI4727707\";\n  var yahoo_ydn_conv_transaction_id = \"\";\n  var yahoo_ydn_conv_value = \"10000\";\n  /* ]]> */\n</script>\n<script type=\"text/javascript\" language=\"javascript\" charset=\"UTF-8\" src=\"https://b90.yahoo.co.jp/conv.js\"></script>",
                                "webConversionSnippetType": "JS"
                            },
                            {
                                "tag": "<img src=\"https://b90.yahoo.co.jp/c?yahoo_ydn_conv_io=6asbtt0OLDUxHpzn5ru9&yahoo_ydn_conv_label=2TU9U6IWZFPTMZVVMI4727707&yahoo_ydn_conv_transaction_id=&yahoo_ydn_conv_value=10000&guid=ON\" width=\"1\" height=\"1\" border=\"0\" />",
                                "webConversionSnippetType": "IMG"
                            }
                        ]
                    }
                },
                "errors": null,
                "operationSucceeded": true,
                "statsPeriodCustomDate": null
            }
        ]
    }
}
```
<br>

#### 5.	トラッカー情報の更新
コンバージョントラッカーの情報を更新したい場合は、ConversionTrackerService:setを使います。<br>
以下では、コンバージョントラッカー情報のカテゴリを、PURCHASE（販売）からPAGE_VIEW（主要なページの閲覧）に更新しています。

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "operand": [
    {
      "category": "PAGE_VIEW",
      "conversionTrackerId": 222222,
      "conversionTrackerType": "WEB_CONVERSION"
    }
  ]
}
```

##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "b6b0c4891ee01526a4a43e110a8fe441",
    "rval": {
        "values": [
            {
                "conversionTracker": {
                    "accountId": 111111,
                    "allConversionValue": 10000000,
                    "allConversions": 1000,
                    "viewThroughConversions": null,
                    "appConversion": null,
                    "category": "PAGE_VIEW",
                    "conversionTrackerId": 222222,
                    "conversionTrackerName": "Pro_B_CV",
                    "conversionTrackerType": "WEB_CONVERSION",
                    "conversionValue": 100000000,
                    "conversionValueViaAdClick": 100,
                    "conversions": 10000,
                    "conversionsViaAdClick": 50,
                    "countingType": "MANY_PER_CLICK",
                    "crossDeviceConversions": 30,
                    "excludeFromBidding": "FALSE",
                    "measurementPeriod": 30,
                    "measurementPeriodView": 1,
                    "mostRecentConversionDate": null,
                    "status": "ENABLED",
                    "userRevenueValue": 10000,
                    "webConversion": {
                        "snippet": [
                            {
                                "tag": "<script type=\"text/javascript\" language=\"javascript\">\n  /* <![CDATA[ */\n  var yahoo_ydn_conv_io = \"6asbtt0OLDUxHpzn5ru9\";\n  var yahoo_ydn_conv_label = \"2TU9U6IWZFPTMZVVMI4727707\";\n  var yahoo_ydn_conv_transaction_id = \"\";\n  var yahoo_ydn_conv_value = \"10000\";\n  /* ]]> */\n</script>\n<script type=\"text/javascript\" language=\"javascript\" charset=\"UTF-8\" src=\"https://b90.yahoo.co.jp/conv.js\"></script>",
                                "webConversionSnippetType": "JS"
                            },
                            {
                                "tag": "<img src=\"https://b90.yahoo.co.jp/c?yahoo_ydn_conv_io=6asbtt0OLDUxHpzn5ru9&yahoo_ydn_conv_label=2TU9U6IWZFPTMZVVMI4727707&yahoo_ydn_conv_transaction_id=&yahoo_ydn_conv_value=10000&guid=ON\" width=\"1\" height=\"1\" border=\"0\" />",
                                "webConversionSnippetType": "IMG"
                            }
                        ]
                    }
                },
                "errors": null,
                "operationSucceeded": true,
                "statsPeriodCustomDate": null
            }
        ]
    }
}
```
