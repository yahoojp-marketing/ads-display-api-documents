# Targeting [Display Ads]
## What is targeting ?
<a href="https://ads-help.yahoo-net.jp/s/article/H000044455?language=en_US#c02">Targeting</a> is functionality for delivering ads to internet users who fulfill specified criteria by specifying in advance such criteria as gender and region at the ad group level.<br>
Targeting can be set only for one type or by combining multiple items.<br>
In display ads, the following targeting options are available:<br>
<br>
* “AD_SCHEDULE_TARGET” (Day of week/hours targeting)
* “GEO_TARGET” (Geographic locations targeting)
* “AGE_TARGET” (Age targeting)
* “GENDER_TARGET” (Gender targeting)
* “SITE_CATEGORY” (Site category targeting)
* “AUDIENCE_LIST_TARGET” (Audience list targeting)
* “SEARCH_TARGET” (Search keywords targeting)
* “PLACEMENT_TARGET” (Placement targeting)
* “DEVICE_TARGET” (Devices targeting)
* “APP_TARGET” (Web/App targeting)
* “OS_TARGET” (OS targeting)
* “OS_VERSION_TARGET” (OS Version Targeting)
* “AUDIENCE_CATEGORY_TARGET” (Audience category targeting)
* “POSITION_TARGET” (Position targeting)
* “CONTENTS_TARGET” (Contents targeting)
* “PLACEMENT_CATEGORY_TARGET” (Placement category targeting)
* “PLACEMENT_CATEGORY_DETAIL_TARGET” (Placement category detail targeting)

## How to operate from Display Ads API
To utilize targeting in the Display Ads API, the following five services are used:

##### 1. AccountAuthorityService
You can get the values that can be set for the campaign goal, which is necessary when creating a campaign.

##### 2. CampaignService
You can get/add/set/remove information about campaigns.

##### 3. AdGroupService
You can get/add/set/remove information about ad groups.

##### 4. DictionaryService (only if you want to set Geographic locations targeting) 
You can get a list of region information.

##### 5. AdGroupTargetService
You can get/add/set/remove information about targeting setting information in an ad group.

## Scenerio Sample
Company A will utilize the Display Ads API to perform campaign creation and targeting setup.<br>
The targeting settings in this scenario are as follows:<br>
Note: Bid adjustment values are represented as decimal numbers ranging from 0.10 to 10.00. (100% is represented as 1).<br>
　　　For example, a +30% adjustment would be 1.3, and a -90% adjustment would be 0.1.<br>

<table class="standard">
  <tr>
　　<th>Target Type</th>
　　<th>Targeting</th>
　　<th>Bid adjustment rate</th>
　</tr>
　<tr>
　　<td>Age targeting</td>
　　<td>Under 30 years old</td>
　　<td>1.5</td>
　</tr>
　<tr>
　　<td>Geographic locations targeting</td>
　　<td>Ibaraki Prefecture</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>Geographic locations targeting</td>
　　<td>Tochigi Prefecture</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>Geographic locations targeting</td>
　　<td>Gunma Prefecture</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>Geographic locations targeting</td>
　　<td>Saitama Prefecture</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>Geographic locations targeting</td>
　　<td>Chuo Ward, Chiba City, Chiba Prefecture</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>Geographic locations targeting</td>
　　<td>Minato Ward, Tokyo</td>
　　<td>1.1</td>
　</tr>
　<tr>
　　<td>Geographic locations targeting</td>
　　<td>Kanagawa Prefecture</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>Day of week/hours targeting</td>
　　<td>from 19:00 to 24:00 on Monday</td>
　　<td>0.9</td>
　</tr>
　<tr>
　　<td>Day of week/hours targeting</td>
　　<td>from 19:00 to 24:00 on Tuesday</td>
　　<td>1.2</td>
　</tr>
　<tr>
　　<td>Day of week/hours targeting</td>
　　<td>from 19:00 to 24:00 on Wednesday</td>
　　<td>1.2</td>
　</tr>
　<tr>
　　<td>Day of week/hours targeting</td>
　　<td>from 19:00 to 24:00 on Thursday</td>
　　<td>1.2</td>
　</tr>
　<tr>
　　<td>Day of week/hours targeting</td>
　　<td>from 19:00 to 24:00 on Friday</td>
　　<td>1.3</td>
　</tr>
　<tr>
　　<td>Gender targeting</td>
　　<td>Men</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>Device targeting</td>
　　<td>Smartphone</td>
　　<td>1.2</td>
　</tr>
</table>
<br>

#### 1. Get account permission information
The AccountAuthorityService:get is used to get account permission information.<br>
The information obtained here will be used as the value set for the campaign objective when creating the campaign in the next step.

##### Request Sample
```json
{
  "accountIds": [11111111]
}
```

##### Response Sample
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


#### 2. Create Campaign
The CampaignService:add method is used to create a campaign.<br>
Here, set the 'CONVERSION' obtained in the previous step as the campaign objective.


##### Request Sample
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
    "campaignName": "TargetingTestCampaign",
    "userStatus": "ACTIVE"
  }]
}
```

##### Response Sample
Note: Due to length constraints, some parts have been omitted.
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
          "campaignName": "TargetingTestCampaign",
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

#### 3. Create Ad group
The AdGroupService:add method is used to create a campaign.

##### Request Sample
```json
{
  "accountId": 11111111,
  "operand": [{
    "accountId": 11111111,
    "adGroupName": "TargetingTestAdgroup",
    "campaignId": 2222222,
    "device":["SMARTPHONE"],
    "deviceApp": ["APP"],
    "deviceOs": ["IOS"],
    "userStatus": "ACTIVE"
  }]
}
```

##### Response Sample
Note: Due to length constraints, some parts have been omitted.
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
          "adGroupName": "TargetingTestAdgroup",
          "campaignId": 2222222,
          "campaignName": "TargetingTestCampaign",
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


#### 4.	Get a List of Geographic Locations
The DictionaryService:getGeographicLocation method is used to retrieve a list of geographic locations.<br>
The codes obtained from this list will be used to specify geographic targeting in the subsequent steps.

##### Request Sample
```json
{
  "lang": "EN",
  "geographicLocationType": "TARGETING"
}
```

##### Response Sample
Note: Due to length constraints, some parts have been omitted.
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
                "fullName": "ibaraki_pref",
                "name": "ibaraki_pref",
                "order": "08000000",
                "parent": null
              },
              "operationSucceeded": true
            },
            ...
                "code": "TC-CI-00000108",
                "fullName": "tochigi_pref",
                "name": "tochigi_pref",
                "order": "09000000",
                "parent": null
              },
              "operationSucceeded": true
            },
            ...
                "code": "TC-CI-00000109",
                "fullName": "gunma_pref",
                "name": "gunma_pref",
                "order": "10000000",
                "parent": null
              },
              "operationSucceeded": true
            },
            ...
                "code": "TC-CI-00000110",
                "fullName": "saitama_pref",
                "name": "saitama_pref",
                "order": "11000000",
                "parent": null
              },
              "operationSucceeded": true
            },
            ...
                    {
                      "child": null,
                      "code": "TC-CI-00002025",
                      "fullName": "chiba_pref chibashi chuoku",
                      "name": "chuoku",
                      "order": "12002702",
                      "parent": "TC-CI-00000553"
                    },
                    ...
                    {
                      "child": null,
                      "code": "TC-CI-00000597",
                      "fullName": "tokyo_pref minatoku",
                      "name": "minatoku",
                      "order": "13004700",
                      "parent": "TC-CI-00000112"
                    },
            ...
                "code": "TC-CI-00000113",
                "fullName": "kanagawa_pref",
                "name": "kanagawa_pref",
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
            "fullName": "other",
            "name": "other",
            "order": "99999999",
            "parent": null
          }, 
        "operationSucceeded": true
      }
    ]
  }
}
```


#### 5.	Targeting Settings
We will use the AdGroupTargetService:add method to set the targeting required for this scenario.<br>
Please note that those who are 17 years old or younger cannot be specified in age targeting. Therefore, we will target ages from 18 to under 30 here.<br>
※Device targeting can only be set with the AdGroupTargetService:set, so we will set it in steps 6 and 7.<br>
<br>
The targeting to be set in this step is as follows.<br>
* "AGE_TARGET" (Age targeting)
* "GEO_TARGET" (Geographic location targeting)
* "AD_SCHEDULE_TARGET" (Day of week/hours targeting)
* "GENDER_TARGET" (Gender targeting)

##### Request Sample
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

##### Response Sample
Note: Due to length constraints, some parts have been omitted.
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


#### 6. Confirm Device Targeting Settings
Use the AdGroupTargetService:get method to confirm the current device targeting settings.<br>
The targetId obtained here will be used in the SET for device targeting in the following step. <br>
Note that, if no device was set up during the creation of the ad group in Step 3, there will be no response regarding device targeting.<br>

##### Request Sample
```json
{
  "accountId": 11111111,
  "campaignIds": [2222222],
  "adGroupIds": [333333333],
  "targetTypes": ["DEVICE_TARGET"]
}
```

##### Response Sample
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

#### 7.	Device Targeting Settings
Use the AdGroupTargetService:set to set up device targeting. <br>
Note that nly the bid adjustment rate can be set.

##### Request Sample
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

##### Response Sample
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
