# ディスプレイ広告（運用型）で目的別キャンペーンを入稿する


## ディスプレイ広告（運用型）とは

[ヤフーのバナー広告「ディスプレイ広告（運用型）」](https://promotionalads.yahoo.co.jp/service/displayads/)をご参照ください。


## Yahoo!広告 APIでの入稿方法

Yahoo!広告 APIでは、ディスプレイ広告（運用型）（以下、運用型と表記）のキャンペーン（以下、目的別キャンペーンと表記）や広告グループ、広告の作成に、以下のサービスを利用します。

- CampaignService
- AdGroupService
- AdGroupAdService

利用するサービスはディスプレイ広告（YDN）（以下、YDNと表記）と同様ですが、作成リクエストや更新リクエストで必要となる項目が、YDNとは異なります。
ここでは運用型のキャンペーンや広告グループ、広告を作成する手順について、詳しく説明します。


## 目的別キャンペーン、広告グループ、広告を作成する手順

### 1. 目的別キャンペーンとは

目的別キャンペーンを作成する際には、広告出稿の目的（以下、キャンペーン目的と表記）を指定する必要があります。

また、アカウント毎に利用可能なキャンペーン目的が異なるため、事前に利用可能なキャンペーン目的を `AccountAuthorityService/get` で確認する必要があります。

詳細は `AccountAuthority` オブジェクトを参照してください。


### 2. 目的別キャンペーンを作成する

CampaignServiceのaddを利用します。
リクエストのAPI仕様については、 `Campaign` オブジェクトを参照してください。

目的別キャンペーンの作成で必要となる項目は、以下のとおりです。  
※YDNと共通する項目は省略しています。

<table>
<tr><th>フィールド</th><th>要不要</th><th>補足</th></tr>
<tr><td>campaignGoal</td><td>必須</td><td>AccountAuthorityService/getで取得した値から、設定する目的を入力</td></tr>
<tr><td>budget.amount</td><td>必須</td><td>1日の予算</td></tr>
<tr><td>campaignBiddingStrategy</td><td>必須</td><td>詳細はYahoo!広告ヘルプ「<a href="https://ads-help.yahoo-net.jp/s/article/H000044352?language=ja">入札戦略について</a>」を参照してください。</td></tr>
<tr><td>viewableFrequencyCap</td><td>任意</td><td>　</td></tr>
</table>

**注意事項**

`Campaign` オブジェクトにおける以下のフィールドは、YDNで作成したキャンペーン専用です。目的別キャンペーンでは設定できません。フィールドによっては固定値が設定されていますが、目的別キャンペーンでは無効な値になります。

<table>
<tr><th>無効化されるフィールド</th><th>補足</th></tr>
<tr><td>adProductType</td><td>　</td></tr>
<tr><td>type</td><td>「STANDARD」が固定値として設定</td></tr>
<tr><td>budget.budgetDeliveryMethod</td><td>「STANDARD」が固定値として設定</td></tr>
<tr><td>biddingStrategy</td><td>　</td></tr>
<tr><td>frequencyCap</td><td>　</td></tr>
<tr><td>conversionOptimizer</td><td>「manualCampaignConversionOptimizer」が固定値として設定</td></tr>
</table>


**＜リクエストサンプル＞**

```json
{
    "accountId": 1001351414,
    "operand": [{
        "campaignName": "campaign_add_1585643284275",
        "userStatus": "PAUSED",
        "startDate":"20210301",
        "endDate":"20230101",
        "budget": {
          "amount": 100
        },
        "campaignGoal": "WEBSITE_TRAFFIC",
        "campaignBiddingStrategy": {
          "campaignBiddingStrategyType": "MAX_CPC",
          "maxCpcBidValue": 100
        },
        "viewableFrequencyCap": {
          "frequencyLevel": "CAMPAIGN",
          "frequencyTimeUnit": "DAY",
          "vImps":1
        }
    }]
}
```


### 3. 広告グループを作成する

AdGroupServiceのaddを利用します。

リクエストのAPI仕様については、 `AdGroup` オブジェクトを参照してください。

目的別キャンペーン配下の広告グループ作成に必要な項目は、以下のとおりです。  
※YDNと共通する項目は省略しています。

<table>
<tr><th>フィールド</th><th>要不要</th><th>補足</th></tr>
<tr><td>adGroupBiddingStrategy</td><td>任意</td><td>詳細はYahoo!広告ヘルプ<a href="https://ads-help.yahoo-net.jp/s/article/H000044352?language=ja">入札戦略について</a>を参照してください。</td></tr>
</table>

**注意事項**

`AdGroup` オブジェクトの以下のフィールドは、YDNで作成した広告グループ専用です。運用型の広告グループでは設定できません。フィールドによっては固定値が設定されていますが、運用型の広告グループでは無効な値になります。

<table>
<tr><th>無効化されるフィールド</th><th>補足</th></tr>
<tr><td>bid</td><td>　</td></tr>
<tr><td>dynamicImageExtensions</td><td>　</td></tr>
<tr><td>smartDeviceCarriers</td><td>　</td></tr>
<tr><td>conversionOptimiser</td><td>「manualConversionOptimizer」が固定値として設定</td></tr>
</table>


**＜リクエストサンプル＞**

```json
{
  "accountId": 1001351414,
  "operand": [{
    "campaignId": 25571069,
    "adGroupName": "adgroup_add_1585643455861",
    "device":["NONE"],
    "deviceApp":["NONE"],
    "deviceOs":["NONE"],
    "userStatus": "PAUSED",
    "adGroupBiddingStrategy": {
      "maxCpcBidValue": 50
    }
  }]
}
```


### 4. 入札戦略を設定する

目的別キャンペーンで入札戦略を設定するには、 `CampaignServiceCampaignBiddingStrategy` オブジェクトの `campaignBiddingStrategyType` フィールドで示される入札戦略のタイプと、対応する入札価格のフィールドを同時に指定してリクエストします。  
※ `campaignBiddingStrategyType` フィールドと入札価格のフィールドの関係は、`CampaignServiceCampaignBiddingStrategy` オブジェクトを参照してください。

例えば、最大入札価格（MAX_CPC）を設定する場合、以下のようにリクエストします。

```json
"campaignBiddingStrategy": {
  "campaignBiddingStrategyType": "MAX_CPC",
  "maxCpcBidValue": 100
}
```


**広告グループで入札戦略を設定するには**

- 広告グループでは、キャンペーンの入札戦略が引き継がれます。  
- 広告グループ単位で入札価格を設定する場合は、キャンペーンの入札戦略に対応した入札価格として利用されます。

**注意事項**

YDNで作成したキャンペーンを目的別キャンペーンに変換した場合、過去に設定した入札価格はそのまま保持されますが、 `campaignBiddingStrategyType` フィールドに対応する値のみが配信に利用されます。


### 5. ターゲティングを設定する

YDNのキャンペーンと目的別キャンペーンでは、設定できるターゲティングが異なります。  
詳細は以下のとおりです。

|                       ターゲティング | YDNのキャンペーン | 目的別キャンペーン | 備考                                                                                                                                                     |
|-------------------------------------:|:----------------:|:------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
|           曜日・時間帯ターゲティング |        ○         |         ○          |                                                                                                                                                          |
|                   地域ターゲティング |        ○         |         ○          | TC-CI-00000073は「その他」の地域コードです。DictionaryServiceのgetGeographicLocationでは取得できず、地域ターゲティグでは指定できません。        |
|                   年齢ターゲティング |        ○         |         ○          |                                                                                                                                                          |
|                   性別ターゲティング |        ○         |         ○          |                                                                                                                                                          |
| インタレストカテゴリーターゲティング |        ○         |         -          | 目的別キャンペーンでは指定できません。                                                                                                                   |
|       サイトカテゴリーターゲティング |        ○         |         ○          |                                                                                                                                                          |
|               サイトリターゲティング |        ○         |         ○          |                                                                                                                                                          |
|                 サーチターゲティング |        ○         |         ○          |                                                                                                                                                          |
|         プレイスメントターゲティング |        ○         |         ○          |                                                                                                                                                          |
|               デバイスターゲティング |        ○         |         ○          | YDNのキャンペーンの「アプリキャンペーン」<br>もしくは<br>目的別キャンペーン「アプリ訴求」<br>の場合は設定必須、かつSMARTPHONEかTABLETのみ設定可能です。 |
|               キャリアターゲティング |        ○         |         -          | 目的別キャンペーンでは指定できません。                                                                                                                   |
|          ウェブ/アプリターゲティング |        ○         |         ○          |                                                                                                                                                          |
|                     OSターゲティング |        ○         |         ○          | YDNのキャンペーンの「アプリキャンペーン」<br>もしくは<br>目的別キャンペーン「アプリ訴求」<br>の場合、Campaignで指定したappOsと同じOSが設定されます。      |
|           OSバージョンターゲティング |        ○         |         ○          | YDNのキャンペーンの「アプリキャンペーン」<br>もしくは<br>目的別キャンペーン「アプリ訴求」<br>の場合のみ指定できます。                                     |
| オーディエンスカテゴリターゲティング |        -         |         ○          | YDNのキャンペーンでは指定できません。                                                                                                                     |


### 6. 広告を作成する

AdGroupAdServiceのaddを利用します。  
リクエストのAPI仕様については、 `AdGroupAd` オブジェクトをご参照ください。

**注意事項**

`AdGroupAd` オブジェクトの以下のフィールドは、YDNで作成した広告専用です。運用型の広告では設定できません。

<table>
<tr><th>無効化されるフィールド</th><th>補足</th></tr>
<tr><td>bid</td><td>　</td></tr>
</table>


**＜リクエストサンプル＞**

```json
{
  "accountId": 1001351414,
  "operand": [{
    "adGroupId": 206751726,
    "campaignId": 25571069,
    "adName": "ad_add_1585643894021",
    "userStatus": "PAUSED",
    "ad": {
      "adType": "TEXT_LONG_AD1",
      "textAd": {
          "description": "description",
          "description2": "description2",
          "headline": "headline",
          "displayUrl": "www.yahoo.co.jp",
          "url": "https://www.yahoo.co.jp"
      }
    }
  }]
}
```


## 自動入札（目標単価指定）を利用する

目的別キャンペーンでは、自動入札を入札戦略「目標単価指定（tCPA）」で設定します。  
ここでは、キャンペーン、または広告グループで目標単価指定（tCPA）を利用する方法をご紹介します。

目標単価指定（tCPA）の利用可否については[入札戦略について](https://ads-help.yahoo-net.jp/s/article/H000044352?language=ja)を参照してください。  
対象のキャンペーンが条件を満たしている場合は、 `CampaignServiceManualCampaignConversionOptimizer` オブジェクトの `conversionOptimizerEligibilityFlg` フィールドが `ENABLE` で返却されます。

以下は、各ステップにおけるレスポンスおよびリクエストの例です。

**ConversionOptimizerオブジェクトのレスポンス例**

キャンペーンが目標単価指定（tCPA）を利用できない場合の `CampaignServiceManualCampaignConversionOptimizer` のレスポンス例です。

```json
"conversionOptimizer": {
  "autoCampaignConversionOptimizer": null,
  "conversionOptimizerType": "MANUAL",
  "manualCampaignConversionOptimizer": {
    "conversionOptimizerEligibilityFlg": null,
    "conversionOptimizerTrainingStatus": null
  }
}
```

目標単価指定（tCPA）を利用できる場合の `CampaignServiceManualCampaignConversionOptimizer` のレスポンス例です。

```json
"conversionOptimizer": {
  "autoCampaignConversionOptimizer": null,
  "conversionOptimizerType": "MANUAL",
  "manualCampaignConversionOptimizer": {
    "conversionOptimizerEligibilityFlg": "ENABLE",
    "conversionOptimizerTrainingStatus": null
  }
}
```

**CampaignServiceCampaignBiddingStrategyオブジェクトによる目標単価指定（tCPA）のリクエスト例**

キャンペーンの `CampaignServiceCampaignBiddingStrategy` オブジェクトによる目標単価指定（tCPA）のリクエスト例です。

```json
"campaignBiddingStrategy": {
  "campaignBiddingStrategyType": "TARGET_CPA",
  "targetCpaBidValue": 50
}
```

※入札戦略タイプは、キャンペーンのみで変更が可能です。
