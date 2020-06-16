# ディスプレイ広告レポート
## パフォーマンスレポートとは
パフォーマンスレポートはキャンペーン、広告グループ、広告などのパフォーマンスを確認するためのレポートです。<br>
レポート作成の際に、レポートの種類、表示項目、集計期間などを設定することで、広告主様のニーズにあわせたカスタマイズが可能です。<br>
また、お勧めのレポート設定を利用し、簡単にレポートを作成することもできます。<br>
<br>
広告管理ツールで提供しているレポート機能をAPIでもサポートしています。<br>

## ディスプレイ広告APIでの実施方法
ディスプレイ広告APIではレポートを表示するために、ReportDefinitionService、というServiceを使用します。  
ReportDefinitionServiceでは、レポート出力項目の取得およびレポート作成・取得・ダウンロードを行います。<br>

# シナリオ
パフォーマンスレポート取得のため、ディスプレイ広告APIを使い以下のレポートの作成からダウンロードまでのフローをご紹介します。  

#### 1.	レポートのフィールド情報の取得
ReportDefinitionServiceのgetReportFieldsを使用します。<br>
ReportCategoryを指定して、レポートフィールドのリストを取得します。<br>
各レポートフィールドにはフィールド名、表示名、xml属性があります。<br>

##### ＜リクエストサンプル＞
```json
{
  "type": "AD"
}
```

##### ＜レスポンスサンプル＞
※長くなるため、一部、省略しています。
```json
{
    "errors": null,
    "rid": "11111111",
    "rval": {
        "errors": null,
        "fields": [
            {
                "displayFieldNameEN": "Account ID",
                "displayFieldNameJA": "アカウントID",
                "fieldName": "ACCOUNT_ID",
                "fieldType": "LONG",
                "filterable": true,
                "impossibleCombinationFields": null,
                "xmlAttributeName": "accountID"
            },
        ...
        ],
        "operationSucceeded": true
    }
}
```

#### 2.	レポートの作成
ReportDefinitionServiceのaddを使用します。  <br>

##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "dateRangeType": "LAST_7_DAYS",
      "fields": [
        "ACCOUNT_ID",
        "ACCOUNT_NAME",
        "CAMPAIGN_ID",
        "CAMPAIGN_NAME",
        "ADGROUP_ID",
        "ADGROUP_NAME",
        "AD_ID",
        "AD_NAME",
        "AD_TYPE",
        "URL_ID",
        "URL_NAME",
        "PREF_ID",
        "PREF_NAME",
        "CITY_ID",
        "CITY_NAME",
        "WARD_ID",
        "WARD_NAME",
        "GENDER",
        "AGE",
        "MONTH",
        "DAY"
      ],
      "filters": [
        {
          "field": "ACCOUNT_ID",
          "filterOperator": "NOT_EQUALS",
          "values": [
            "100"
          ]
        }
      ],
      "lang": "JA",
      "reportName": "Test Report",
      "sortFields": [
        {
          "field": "ACCOUNT_ID",
          "reportSortType": "ASC"
        }
      ],
      "zip": "ON"
    }
  ]
}
```

##### ＜レスポンスサンプル＞
※長くなるため、一部、省略しています。
```json
{
    "errors": null,
    "rid": "11111111",
    "rval": {
        "values": [
            {
                "errors": null,
                "operationSucceeded": true,
                "reportDefinition": {
                    "accountId": 11111111,
                    "completeTime": null,
                    "dateRange": null,
                    "dateRangeType": "LAST_7_DAYS",
                    "downloadEncode": "UTF-8",
                    "downloadFormat": "CSV",
                    "fields": [
                        "ACCOUNT_ID",
                        ...
                    ],
                    "filters": [
                        {
                            "field": "ACCOUNT_ID",
                            "filterOperator": "NOT_EQUALS",
                            "values": [
                                "100"
                            ]
                        }
                    ],
                    "frequencyRange": null,
                    "jobStatus": "WAIT",
                    "lang": "JA",
                    "reportJobErrorDetail": null,
                    "reportJobId": 11111111,
                    ...
                }
            }
        ]
    }
}
```


#### 3.	レポート作成状況の確認
ReportDefinitionServiceのgetを使用します。<br>
作成状況の確認ができます。<br>
レスポンスのjobStatusがCOMPLETEDになったら、4に進みます。

##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "numberResults": 10,
  "reportJobIds": [
    11111111
  ],
  "startIndex": 1
}
```

##### ＜レスポンスサンプル＞
※長くなるため、一部、省略しています。
```json
{
    "errors": null,
    "rid": "11111111",
    "rval": {
        "totalNumEntries": 1,
        "values": [
            {
                "errors": null,
                "operationSucceeded": true,
                "reportDefinition": {
                    "accountId": 11111111,
                    "completeTime": "20200522101201",
                    "dateRange": null,
                    "dateRangeType": "LAST_7_DAYS",
                    "downloadEncode": "UTF-8",
                    "downloadFormat": "CSV",
                    "fields": [
                        "ACCOUNT_ID",
                        ...
                    ],
                    "filters": [
                        {
                            "field": "ACCOUNT_ID",
                            "filterOperator": "NOT_EQUALS",
                            "values": [
                                "100"
                            ]
                        }
                    ],
                    "frequencyRange": null,
                    "jobStatus": "COMPLETED",
                    "lang": "JA",
                    "reportJobErrorDetail": null,
                    "reportJobId": 11111111,
                    ...
                }
            }
        ]
    }
}
```

#### 4. レポートのダウンロード
ReportDefinitionServiceのdownloadを使用します。<br>
作成したレポートをダウンロードします。

##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "reportJobId": 11111111
}
```

##### ＜レスポンスサンプル＞
※対象のデータがない場合、以下のようになります。<br>
※zip解凍した結果です。<br>
```csv
アカウントID,アカウント名,キャンペーンID,キャンペーン名,広告グループID,広告グループ名,広告ID,広告名,広告タイプ,リンク先URLID,リンク先URL,都道府県ID,都道府県,市区郡ID,市区郡,行政区ID,行政区,性別,年齢,月,日
Total,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--
```
