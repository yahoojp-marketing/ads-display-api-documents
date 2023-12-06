# ディスプレイ広告のターゲティング
## ターゲティングとは
<a href="https://ads-help.yahoo-net.jp/s/article/H000044455?language=ja">ターゲティング</a>とは、広告グループ単位であらかじめ特定の条件（地域、年齢など）を指定しておくことで、適切なユーザーに適切なタイミングで広告を表示をするための機能です。<br>
ターゲティングは1種類でも複数を組み合わせても構いません。<br>
ディスプレイ広告においては下記のターゲティングを利用できます。<br>
<br>
* “AD_SCHEDULE_TARGET” (曜日・時間帯ターゲティング)
* “GEO_TARGET” (地域ターゲティング)
* “AGE_TARGET” (年齢ターゲティング)
* “GENDER_TARGET” (性別ターゲティング)
* “SITE_CATEGORY” (サイトカテゴリーターゲティング)
* “AUDIENCE_LIST_TARGET” (オーディエンスリストターゲティング)
* “SEARCH_TARGET” (サーチターゲティング)
* “PLACEMENT_TARGET” (プレイスメントターゲティング)
* “DEVICE_TARGET” (デバイスターゲティング)
* “APP_TARGET” (ウェブ/アプリターゲティング)
* “OS_TARGET” (OSターゲティング)
* “OS_VERSION_TARGET” (OSバージョンターゲティング)
* “AUDIENCE_CATEGORY_TARGET” (オーディエンスカテゴリターゲティング)
* “POSITION_TARGET” (ポジションターゲティング)
* “CONTENTS_TARGET” (コンテンツターゲティング)
* “PLACEMENT_CATEGORY_TARGET” (プレイスメントカテゴリターゲティング)
* “PLACEMENT_CATEGORY_DETAIL_TARGET” (プレイスメントカテゴリ詳細ターゲティング)

## ディスプレイ広告APIでの実施方法
ディスプレイ広告APIではターゲティングを利用するために以下の5つのServiceを使用します。

##### 1. AccountAuthorityService
AccountAuthorityServiceでは、キャンペーン作成の際に必要となるキャンペーン目的に設定可能な値を取得できます。

##### 2. CampaignService
CampaignServiceでは、キャンペーンに関する情報の取得および追加・更新が実施できます。

##### 3. AdGroupService
AdGroupServiceでは、広告グループに関する情報の取得および追加・更新が実施できます。

##### 4. DictionaryService（地域ターゲティングを指定したい場合のみ）
DictionaryServiceでは、地域情報の一覧取得を実施できます。

##### 5. AdGroupTargetService
AdGroupTargetServiceでは、広告グループにおけるターゲティング設定情報に関する情報の取得および追加・更新が実施できます。

## シナリオ
ディスプレイAPIを使い、キャンペーン作成からターゲティング設定までのフローをご紹介します。<br>
本シナリオで設定するターゲティングは下記の通りとします。<br>
なお、入札価格調整率は％表記ではなく0.10～10.00の値を用います。（100%が1となります）<br>
たとえば、+30%の場合は1.3、-90%の場合は0.1のようになります。

<table class="standard">
  <tr>
　　<th>種別</th>
　　<th>ターゲティング設定</th>
　　<th>入札価格調整率</th>
　</tr>
　<tr>
　　<td>年齢ターゲティング</td>
　　<td>30才未満</td>
　　<td>1.5</td>
　</tr>
　<tr>
　　<td>地域ターゲティング</td>
　　<td>茨城県</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>地域ターゲティング</td>
　　<td>栃木県</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>地域ターゲティング</td>
　　<td>群馬県</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>地域ターゲティング</td>
　　<td>埼玉県</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>地域ターゲティング</td>
　　<td>千葉県千葉市中央区</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>地域ターゲティング</td>
　　<td>東京都港区</td>
　　<td>1.1</td>
　</tr>
　<tr>
　　<td>地域ターゲティング</td>
　　<td>神奈川県</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>曜日・時間帯ターゲティング</td>
　　<td>月曜日の19時から24時まで</td>
　　<td>0.9</td>
　</tr>
　<tr>
　　<td>曜日・時間帯ターゲティング</td>
　　<td>火曜日の19時から24時まで</td>
　　<td>1.2</td>
　</tr>
　<tr>
　　<td>曜日・時間帯ターゲティング</td>
　　<td>水曜日の19時から24時まで</td>
　　<td>1.2</td>
　</tr>
　<tr>
　　<td>曜日・時間帯ターゲティング</td>
　　<td>木曜日の19時から24時まで</td>
　　<td>1.2</td>
　</tr>
　<tr>
　　<td>曜日・時間帯ターゲティング</td>
　　<td>金曜日の19時から24時まで</td>
　　<td>1.3</td>
　</tr>
　<tr>
　　<td>性別ターゲティング</td>
　　<td>男性</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>デバイスターゲティング</td>
　　<td>スマートフォン</td>
　　<td>1.2</td>
　</tr>
</table>
<br>

#### 1. アカウント権限情報の取得
AccountAuthorityService:getを使用し、アカウント権限情報を取得します。<br>
ここで取得した情報は、次の手順のキャンペーン作成時にキャンペーン目的に設定する値として利用します。

##### ＜リクエストサンプル＞
```json
{
  "accountIds": [11111111]
}
```

##### ＜レスポンスサンプル＞
```json
{
  "errors": null,
  "rid": "1",
  "rval": {
    "totalNumEntries": 1,
    "values": [
      {
        "accountAuthority": {
          "accountId": 11111111,
          "authorities": [
            "CONVERSION",
            "APP_PROMOTION",
            "WEBSITE_TRAFFIC",
            "BRAND_AWARENESS",
            "ITEM_LIST",
            "MAX_VIEW",
            "MAX_CLICK",
            "MAX_CV",
            "VIDEO_VIEW"
          ]
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```


#### 2. キャンペーン作成
CampaignService:addを使用し、キャンペーンを作成します。<br>
ここでは、前の手順で取得した"CONVERSION"をキャンペーン目的に設定します。


##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "operand": [{
    "accountId": 11111111,
    "budget": {
      "amount": 100
    },
    "biddingStrategyConfiguration": {
      "biddingScheme": {
        "biddingStrategyType": "MAXIMIZE_CONVERSIONS"
      }
    },
    "campaignGoal": "CONVERSION",
    "campaignName": "ターゲティングテストキャンペーン",
    "userStatus": "ACTIVE"
  }]
}
```

##### ＜レスポンスサンプル＞
※長くなるため、一部、省略しています。
```json
{
  "errors": null,
  "rid": "2",
  "rval": {
    "values": [
      {
        "campaign": {
          "accountId": 11111111,
          "appId": null,
          "appName": null,
          "budget": {
            "amount": 100
          },
          "biddingStrategyConfiguration": {
            "biddingScheme": {
              "biddingStrategyType": "MAXIMIZE_CONVERSIONS",
              ...
              }
          },
          "campaignGoal": "CONVERSION",
          "campaignId": 2222222,
          "campaignName": "ターゲティングテストキャンペーン",
          "conversionOptimizer": {
            "conversionOptimizerTrainingStatus": "PROCESSING"
          },
          ...
          "endDate": "20371231",
          "endTime": "2359",
          ...
          "servingStatus": "SERVING",
          "startDate": "20231113",
          "startTime": "0000",
          "trackingUrl": null,
          "userStatus": "ACTIVE",
          ...
          "createdDate": "20231113",
          "vendorName": null,
          "conversionTracker": null
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```

#### 3. 広告グループ作成
AdGroupService:addを使用し、広告グループを作成します。

##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "operand": [{
    "accountId": 11111111,
    "adGroupName": "ターゲティングテストアドグループ",
    "campaignId": 2222222,
    "device":["SMARTPHONE"],
    "deviceApp": ["APP"],
    "deviceOs": ["IOS"],
    "userStatus": "ACTIVE"
  }]
}
```

##### ＜レスポンスサンプル＞
※長くなるため、一部、省略しています。
```json
{
  "errors": null,
  "rid": "3",
  "rval": {
    "values": [
      {
        "adGroup": {
          "accountId": 11111111,
          "biddingStrategyConfiguration": {
            "biddingScheme": {
              "campaignBiddingStrategyType": "MAXIMIZE_CONVERSIONS",
              ...
            }
          },
          "adGroupId": 333333333,
          "adGroupName": "ターゲティングテストアドグループ",
          "campaignId": 2222222,
          "campaignName": "ターゲティングテストキャンペーン",
          "customParameters": null,
          "device": [
            "SMARTPHONE"
          ],
          "deviceApp": [
            "APP"
          ],
          "deviceOs": [
            "IOS"
          ],
          ...
          "userStatus": "ACTIVE",
          "createdDate": "20231122"
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```


#### 4.	地域情報の一覧を取得
DictionaryService:getGeographicLocationを使用し、地域情報の一覧を取得します。<br>
ここで取得した一覧にあるコードは、後の手順で実施する地域ターゲティングの指定時に利用します。


##### ＜リクエストサンプル＞
```json
{
  "lang": "JA",
  "geographicLocationType": "TARGETING"
}
```

##### ＜レスポンスサンプル＞
※長くなるため、一部、省略しています。
```json
{
  "errors": null,
  "rid": "4",
  "rval": {
    "totalNumEntries": 48,
    "values": [
      {
        "errors": null,
        "geographicLocation": {
          "child": [
            {
              ...
                "code": "TC-CI-00000107",
                "fullName": "茨城県",
                "name": "茨城県",
                "order": "08000000",
                "parent": null
              },
              "operationSucceeded": true
            },
            ...
                "code": "TC-CI-00000108",
                "fullName": "栃木県",
                "name": "栃木県",
                "order": "09000000",
                "parent": null
              },
              "operationSucceeded": true
            },
            ...
                "code": "TC-CI-00000109",
                "fullName": "群馬県",
                "name": "群馬県",
                "order": "10000000",
                "parent": null
              },
              "operationSucceeded": true
            },
            ...
                "code": "TC-CI-00000110",
                "fullName": "埼玉県",
                "name": "埼玉県",
                "order": "11000000",
                "parent": null
              },
              "operationSucceeded": true
            },
            ...
                    {
                      "child": null,
                      "code": "TC-CI-00002025",
                      "fullName": "千葉県 千葉市 中央区",
                      "name": "中央区",
                      "order": "12002702",
                      "parent": "TC-CI-00000553"
                    },
                    ...
                    {
                      "child": null,
                      "code": "TC-CI-00000597",
                      "fullName": "東京都 港区",
                      "name": "港区",
                      "order": "13004700",
                      "parent": "TC-CI-00000112"
                    },
            ...
                "code": "TC-CI-00000113",
                "fullName": "神奈川県",
                "name": "神奈川県",
                "order": "14000000",
                "parent": null
              },
              "operationSucceeded": true
            },
            ...
        {
          "errors": null,
          "geographicLocation": {
            "child": null,
            "code": "TC-CI-00000073", 
            "fullName": "その他",
            "name": "その他",
            "order": "99999999",
            "parent": null
          }, 
        "operationSucceeded": true
      }
    ]
  }
}
```


#### 5.	ターゲティング設定
AdGroupTargetService:addを使用して、本シナリオで必要となるターゲティングを設定します。<br>
なお、年齢ターゲティングでは17歳以下は指定できないため、ここでは18歳～30歳未満までを対象とします。<br>
※デバイスターゲティングはAdGroupTargetService:setでのみ設定できるため、手順6～7で設定します。<br>
<br>
本手順で設定するターゲティングは以下の通りです。<br>
* “AGE_TARGET” (年齢ターゲティング)
* “GEO_TARGET” (地域ターゲティング)
* “AD_SCHEDULE_TARGET” (曜日・時間帯ターゲティング)
* “GENDER_TARGET” (性別ターゲティング)

##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "operand": [{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.5,
    "target": {
      "targetType": "AGE_TARGET",
      "ageTarget":  {
        "age": "GT_RANGE18_19"
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.5,
    "target": {
      "targetType": "AGE_TARGET",
      "ageTarget":  {
        "age": "GT_RANGE20_24"
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.5,
    "target": {
      "targetType": "AGE_TARGET",
      "ageTarget":  {
        "age": "GT_RANGE25_29"
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.0,
    "target": {
      "targetId": "TC-CI-00000107",
      "targetType": "GEO_TARGET",
      "geoTarget":  {
        "areaSearchType": "GEO"
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.0,
    "target": {
      "targetId": "TC-CI-00000108",
      "targetType": "GEO_TARGET",
      "geoTarget":  {
        "areaSearchType": "GEO"
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.0,
    "target": {
      "targetId": "TC-CI-00000109",
      "targetType": "GEO_TARGET",
      "geoTarget":  {
        "areaSearchType": "GEO"
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.0,
    "target": {
      "targetId": "TC-CI-00000110",
      "targetType": "GEO_TARGET",
      "geoTarget":  {
        "areaSearchType": "GEO"
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.0,
    "target": {
      "targetId": "TC-CI-00002025",
      "targetType": "GEO_TARGET",
      "geoTarget":  {
        "areaSearchType": "GEO"
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.1,
    "target": {
      "targetId": "TC-CI-00000597",
      "targetType": "GEO_TARGET",
      "geoTarget":  {
        "areaSearchType": "GEO"
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.0,
    "target": {
      "targetId": "TC-CI-00000113",
      "targetType": "GEO_TARGET",
      "geoTarget":  {
        "areaSearchType": "GEO"
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 0.9,
    "target": {
      "targetType": "AD_SCHEDULE_TARGET",
      "adScheduleTarget":  {
        "dayOfWeek": "MONDAY",
        "startHour": 19,
        "endHour": 24
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.2,
    "target": {
      "targetType": "AD_SCHEDULE_TARGET",
      "adScheduleTarget":  {
        "dayOfWeek": "TUESDAY",
        "startHour": 19,
        "endHour": 24
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.2,
    "target": {
      "targetType": "AD_SCHEDULE_TARGET",
      "adScheduleTarget":  {
        "dayOfWeek": "WEDNESDAY",
        "startHour": 19,
        "endHour": 24
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.2,
    "target": {
      "targetType": "AD_SCHEDULE_TARGET",
      "adScheduleTarget":  {
        "dayOfWeek": "THURSDAY",
        "startHour": 19,
        "endHour": 24
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.3,
    "target": {
      "targetType": "AD_SCHEDULE_TARGET",
      "adScheduleTarget":  {
        "dayOfWeek": "FRIDAY",
        "startHour": 19,
        "endHour": 24
      }
    }
  },{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.0,
    "target": {
      "targetType": "GENDER_TARGET",
      "genderTarget":  {
        "gender": "ST_MALE"
      }
    }
  }
  ]
}
```

##### ＜レスポンスサンプル＞
※長くなるため、一部、省略しています。
```json
{
  "errors": null,
  "rid": "5",
  "rval": {
    "values": [
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.5,
          "campaignId": 2222222,
          "target": {
            "adScheduleTarget": null,
            "ageTarget": {
              "age": "GT_RANGE18_19"
            },
            ...
            "targetId": "17",
            "targetSetting": null,
            "targetType": "AGE_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.5,
          "campaignId": 2222222,
          "target": {
            "adScheduleTarget": null,
            "ageTarget": {
              "age": "GT_RANGE20_24"
            },
            ...
            "targetId": "18",
            "targetSetting": null,
            "targetType": "AGE_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.5,
          "campaignId": 2222222,
          "target": {
            "adScheduleTarget": null,
            "ageTarget": {
              "age": "GT_RANGE25_29"
            },
            ...
            "targetId": "19",
            "targetSetting": null,
            "targetType": "AGE_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "target": {
            ...
            "geoTarget": {
              "areaSearchType": "GEO",
              "latitudeInMicroDegrees": null,
              "longitudeInMicroDegrees": null,
              "radius": null,
              "description": null,
              "geoNameEn": "ibaraki_pref",
              "geoNameJa": "茨城県"
            },
            ...
            "targetId": "TC-CI-00000107",
            "targetSetting": null,
            "targetType": "GEO_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "target": {
            ...
            "geoTarget": {
              "areaSearchType": "GEO",
              "latitudeInMicroDegrees": null,
              "longitudeInMicroDegrees": null,
              "radius": null,
              "description": null,
              "geoNameEn": "tochigi_pref",
              "geoNameJa": "栃木県"
            },
            ...
            "targetId": "TC-CI-00000108",
            "targetSetting": null,
            "targetType": "GEO_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "target": {
            ...
            "geoTarget": {
              "areaSearchType": "GEO",
              "latitudeInMicroDegrees": null,
              "longitudeInMicroDegrees": null,
              "radius": null,
              "description": null,
              "geoNameEn": "gunma_pref",
              "geoNameJa": "群馬県"
            },
            ...
            "targetId": "TC-CI-00000109",
            "targetSetting": null,
            "targetType": "GEO_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "target": {
            ...
            "geoTarget": {
              "areaSearchType": "GEO",
              "latitudeInMicroDegrees": null,
              "longitudeInMicroDegrees": null,
              "radius": null,
              "description": null,
              "geoNameEn": "saitama_pref",
              "geoNameJa": "埼玉県"
            },
            ...
            "targetId": "TC-CI-00000110",
            "targetSetting": null,
            "targetType": "GEO_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "target": {
            ...
            "geoTarget": {
              "areaSearchType": "GEO",
              "latitudeInMicroDegrees": null,
              "longitudeInMicroDegrees": null,
              "radius": null,
              "description": null,
              "geoNameEn": "chiba_pref chibashi chuoku",
              "geoNameJa": "千葉県 千葉市 中央区"
            },
            ...
            "targetId": "TC-CI-00002025",
            "targetSetting": null,
            "targetType": "GEO_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.1,
          "campaignId": 2222222,
          "target": {
            ...
            "geoTarget": {
              "areaSearchType": "GEO",
              "latitudeInMicroDegrees": null,
              "longitudeInMicroDegrees": null,
              "radius": null,
              "description": null,
              "geoNameEn": "tokyo_pref minatoku",
              "geoNameJa": "東京都 港区"
            },
            ...
            "targetId": "TC-CI-00000597",
            "targetSetting": null,
            "targetType": "GEO_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "target": {
            ...
            "geoTarget": {
              "areaSearchType": "GEO",
              "latitudeInMicroDegrees": null,
              "longitudeInMicroDegrees": null,
              "radius": null,
              "description": null,
              "geoNameEn": "kanagawa_pref",
              "geoNameJa": "神奈川県"
            },
            ...
            "targetId": "TC-CI-00000113",
            "targetSetting": null,
            "targetType": "GEO_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 0.9,
          "campaignId": 2222222,
          "target": {
            "adScheduleTarget": {
              "dayOfWeek": "MONDAY",
              "endHour": 24,
              "startHour": 19
            },
            ...
            "targetId": "as011924",
            "targetSetting": null,
            "targetType": "AD_SCHEDULE_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.2,
          "campaignId": 2222222,
          "target": {
            "adScheduleTarget": {
              "dayOfWeek": "TUESDAY",
              "endHour": 24,
              "startHour": 19
            },
            ...
            "targetId": "as021924",
            "targetSetting": null,
            "targetType": "AD_SCHEDULE_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.2,
          "campaignId": 2222222,
          "target": {
            "adScheduleTarget": {
              "dayOfWeek": "WEDNESDAY",
              "endHour": 24,
              "startHour": 19
            },
            ...
            "targetId": "as031924",
            "targetSetting": null,
            "targetType": "AD_SCHEDULE_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.2,
          "campaignId": 2222222,
          "target": {
            "adScheduleTarget": {
              "dayOfWeek": "THURSDAY",
              "endHour": 24,
              "startHour": 19
            },
            ...
            "targetId": "as041924",
            "targetSetting": null,
            "targetType": "AD_SCHEDULE_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.3,
          "campaignId": 2222222,
          "target": {
            "adScheduleTarget": {
              "dayOfWeek": "FRIDAY",
              "endHour": 24,
              "startHour": 19
            },
            ...
            "targetId": "as051924",
            "targetSetting": null,
            "targetType": "AD_SCHEDULE_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "target": {
            ...
            "genderTarget": {
              "gender": "ST_MALE"
            },
            ...
            "targetId": "ge0100",
            "targetSetting": null,
            "targetType": "GENDER_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```


#### 6.	デバイスターゲティングの設定確認
AdGroupTargetService:getを使用して、デバイスターゲティングに利用するための設定を確認します。<br>
ここで取得したtargetIdは、次の手順のデバイスターゲティングのSETで利用します。<br>
なお、手順3の広告グループ作成時にデバイスが設定されていない場合は、デバイスターゲティングに関するレスポンスが何もありません。<br>


##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "campaignIds": [2222222],
  "adGroupIds": [333333333],
  "targetTypes": ["DEVICE_TARGET"]
}
```

##### ＜レスポンスサンプル＞
```json
{
  "errors": null,
  "rid": "6",
  "rval": {
    "totalNumEntries": 1,
    "values": [
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "target": {
            "adScheduleTarget": null,
            "ageTarget": null,
            "appTarget": null,
            "audienceCategoryTarget": null,
            "deviceTarget": {
              "deviceType": "SMARTPHONE"
            },
            "genderTarget": null,
            "geoTarget": null,
            "isRemove": null,
            "osTarget": null,
            "osVersionTarget": null,
            "placementTarget": null,
            "searchTarget": null,
            "siteCategoryTarget": null,
            "audienceListTarget": null,
            "positionTarget": null,
            "placementCategoryTarget": null,
            "placementCategoryDetailTarget": null,
            "contentsTarget": null,
            "targetId": "de003",
            "targetSetting": "ACTIVE",
            "targetType": "DEVICE_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```




#### 7.	デバイスターゲティング設定
AdGroupTargetService:setを使用して、デバイスターゲティングを設定します。<br>
※入札価格調整率のみ設定可能です。


##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "operand": [{
    "campaignId": 2222222,
    "adGroupId": 333333333,
    "bidMultiplier": 1.2,
    "target": {
      "targetType": "DEVICE_TARGET",
      "targetId": "de003",
      "deviceTarget":  {
        "deviceType": "SMARTPHONE"
      }
    }
  }
  ]
}
```

##### ＜レスポンスサンプル＞
```json
{
  "errors": null,
  "rid": "7",
  "rval": {
    "values": [
      {
        "adGroupTargetList": {
          "accountId": 11111111,
          "adGroupId": 333333333,
          "bidMultiplier": 1.2,
          "campaignId": 2222222,
          "target": {
            "adScheduleTarget": null,
            "ageTarget": null,
            "appTarget": null,
            "audienceCategoryTarget": null,
            "deviceTarget": {
              "deviceType": "SMARTPHONE"
            },
            "genderTarget": null,
            "geoTarget": null,
            "isRemove": null,
            "osTarget": null,
            "osVersionTarget": null,
            "placementTarget": null,
            "searchTarget": null,
            "siteCategoryTarget": null,
            "audienceListTarget": null,
            "positionTarget": null,
            "placementCategoryTarget": null,
            "placementCategoryDetailTarget": null,
            "contentsTarget": null,
            "targetId": "de003",
            "targetSetting": "ACTIVE",
            "targetType": "DEVICE_TARGET"
          }
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```
