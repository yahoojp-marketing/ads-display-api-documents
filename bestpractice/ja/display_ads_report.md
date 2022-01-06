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
}```

#### 2.	レポートの作成
ReportDefinitionServiceのaddを使用します。  <br>

##### ＜リクエストサンプル＞
```json
{
  "accountId": 111111,
  "operand": [
    {
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
      "reportCompressType": "ZIP",
      "reportDateRangeType": "LAST_7_DAYS",
      "reportDownloadEncode": "UTF8",
      "reportDownloadFormat": "CSV",
      "reportLanguage": "JA",
      "reportName": "test report 01",
      "sortFields": [
        {
          "field": "ACCOUNT_ID",
          "reportSortType": "ASC"
        }
      ]
    }
  ]
}
```

##### ＜レスポンスサンプル＞
```json
{
  "errors": null,
  "rid": "6ef3dba169e73bb6a11e5ddc85652f70",
  "rval": {
    "values": [
      {
        "errors": null,
        "operationSucceeded": true,
        "reportDefinition": {
          "accountId": 111111,
          "completeTime": null,
          "dateRange": null,
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
          "reportCompressType": "ZIP",
          "reportDateRangeType": "LAST_7_DAYS",
          "reportDownloadEncode": "UTF8",
          "reportDownloadFormat": "CSV",
          "reportJobStatus": "WAIT",
          "reportJobErrorDetail": null,
          "reportJobId": 222222,
          "reportLanguage": "JA",
          "reportName": "test report 01",
          "requestTime": "20211224185454",
          "reportSkipColumnHeader": "FALSE",
          "reportSkipReportSummary": "FALSE",
          "reportDecimalPartDisplayType": "SIMPLE_DISPLAY",
          "reportTypeCondition": null,
          "sortFields": [
            {
              "field": "ACCOUNT_ID",
              "reportSortType": "ASC"
            }
          ]
        }
      }
    ]
  }
}
```

#### 3.	レポート作成状況の確認
ReportDefinitionServiceのgetを使用します。<br>
作成状況の確認ができます。<br>
レスポンスのreportJobStatusがCOMPLETEDになったら、4に進みます。

##### ＜リクエストサンプル＞
```json
{
  "accountId": 111111,
  "numberResults": 10,
  "reportJobIds": [
    222222
  ],
  "startIndex": 1
}
```

##### ＜レスポンスサンプル＞
```json
{
  "errors": null,
  "rid": "1abd04462d335b6f9061b4837aa7a5c7",
  "rval": {
    "totalNumEntries": 1,
    "values": [
      {
        "errors": null,
        "operationSucceeded": true,
        "reportDefinition": {
          "accountId": 111111,
          "completeTime": "20211224185457",
          "dateRange": null,
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
          "reportCompressType": "ZIP",
          "reportDateRangeType": "LAST_7_DAYS",
          "reportDownloadEncode": "UTF8",
          "reportDownloadFormat": "CSV",
          "reportJobStatus": "COMPLETED",
          "reportJobErrorDetail": null,
          "reportJobId": 222222,
          "reportLanguage": "JA",
          "reportName": "test report 01",
          "requestTime": "20211224185454",
          "reportSkipColumnHeader": "FALSE",
          "reportSkipReportSummary": "FALSE",
          "reportDecimalPartDisplayType": "SIMPLE_DISPLAY",
          "reportTypeCondition": null,
          "sortFields": [
            {
              "field": "ACCOUNT_ID",
              "reportSortType": "ASC"
            }
          ]
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
  "accountId": 111111,
  "reportJobId": 222222
}
```

##### ＜レスポンスサンプル＞
※対象のデータがない場合、以下のようになります。<br>
※zip解凍した結果です。<br>
```csv
アカウントID,アカウント名,キャンペーンID,キャンペーン名,広告グループID,広告グループ名,広告ID,広告名,広告タイプ,リンク先URLID,リンク先URL,都道府県ID,都道府県,市区郡ID,市区郡,行政区ID,行政区,性別,年齢,月,日
Total,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--
```
