# Create a campaign by objective on Display Ads (Auction)


## What is Display Ads (Auction)

Refer to the introduction on [ヤフーのバナー広告「ディスプレイ広告（運用型）」](https://promotionalads.yahoo.co.jp/service/displayads/) (Japanese context only). Currently available for limited users.


## How to create a campaign on Yahoo! Ads API

For creating a campaign, ad group and ads of Display Ads (Auction), following services of Yahoo! Ads API will be used.

- CampaignService
- AdGroupService
- AdGroupAdService

On creating and updating requests of Display Ads (Auction), some required items of these services are different from the one on YDN.
Follow the steps below to learn about how to create a campaign, ad group and ads of Display Ads (Auction).


## Steps to create a campaign by goal, ad group and ads

### 1. Campaign by goal

When you create a campaign, a goal of the campaign set to achieve a business goal is required.

Since available campaign goals vary by each account, you need to check available campaign goals in advance.

See also `Account` object for more detail.


### 2. Create a campaign by goal

Use "add" of CampaignService.
See also `Campaign` object for more detail of API request specification.

Required items on creating a campaign by goal are as follows.  
※Common items with YDN are omitted.

<table>
<tr><th>Field</th><th>Required?</th><th>Note</th></tr>
<tr><td>campaignGoal</td><td>Required</td><td>Enter a campaign goal from the value acquired on accountAuthorities of AccountService/get</td></tr>
<tr><td>budget.amount</td><td>Required</td><td>Campaign Daily Budget</td></tr>
<tr><td>campaignBiddingStrategy</td><td>Required</td><td>More detail is described on Yahoo! Ads Help "<a href="https://ads-help.yahoo.co.jp/yahooads/display/articledetail?lan=ja&aid=51518">入札戦略について (Bidding Strategy)</a>" (Japanese context only).</td></tr>
<tr><td>viewableFrequencyCap</td><td>Optional</td><td>　</td></tr>
</table>

**Note**

Following fields on `Campaign` object are for YDN campaign only. These are not available for campaigns by goal on Display Ads (Auction). Fixed values on some fields are invalid for campaigns by goal.

<table>
<tr><th>Ignored field</th><th>Note</th></tr>
<tr><td>adProductType</td><td>　</td></tr>
<tr><td>campaignType</td><td>"STANDARD" is set as fixed value</td></tr>
<tr><td>budget.budgetDeliveryMethod</td><td>"STANDARD" is set as fixed value</td></tr>
<tr><td>biddingStrategy</td><td>　</td></tr>
<tr><td>frequencyCap</td><td>　</td></tr>
<tr><td>conversionOptimizer</td><td>"manualCampaignConversionOptimizer" is set as fixed value</td></tr>
</table>


**Request Sample**

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


### 3. Create an ad group

Use "add" of AdGroupService.

See also `AdGroup` object for more detail of API request specification.

Required items on creating an ad group in a campaign by goal are as follows.  
※Common items with YDN are omitted.

<table>
<tr><th>Field</th><th>Required?</th><th>Note</th></tr>
<tr><td>adGroupBiddingStrategy</td><td>Optional</td><td>More detail is described on Yahoo! Ads Help "<a href="https://ads-help.yahoo.co.jp/yahooads/display/articledetail?lan=ja&aid=51518">入札戦略について (Bidding Strategy)</a>" (Japanese context only).</td></tr>
</table>

**Note**

Following fields on `AdGroup` object are for YDN ad group only. These are not available for ad group of Display Ads (Auction). Fixed values on some fields are invalid for ad group of Display Ads (Auction).

<table>
<tr><th>Ignored field</th><th>Note</th></tr>
<tr><td>bid</td><td>　</td></tr>
<tr><td>dynamicImageExtensions</td><td>　</td></tr>
<tr><td>smartDeviceCarriers</td><td>　</td></tr>
<tr><td>conversionOptimiser</td><td>"manualConversionOptimizer" is set as fixed value</td></tr>
</table>


**Request Sample**

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


### 4. Set Bidding Strategy

When setting a bidding strategy on campaign by goal, specify both of bidding strategy type described on the `campaignBiddingStrategyType` field of `CampaignServiceCampaignBiddingStrategy` object and applicable bid field together for request.  
※See also `CampaignServiceCampaignBiddingStrategy` object for relation between `campaignBiddingStrategyType` field and bid field.

For example, when setting max bid (MAX_CPC), describe the request as follows.

```json
"campaignBiddingStrategy": {
  "campaignBiddingStrategyType": "MAX_CPC",
  "maxCpcBidValue": 100
}
```


**Set Bidding Strategy on Ad Group**

- Bidding strategy set on campaign will be applied to ad groups.  
- When setting a bid by each ad group, the bid will be used as applicable for campaign's bidding strategy.

**Note**

When migrating YDN campaign to campaign by goal, the bid on the campaign can be applied to the migrated campaign but only values applicable for 'campaignBiddingStrategyType' field will be used on ad delivery.


### 5. Set Targeting

Targeting settings available on campaigns by goal of Display Ads (Auction) are different from YDN campaign.  
See also `AdGroupTarget` object for more detail of API request specification.


### 6. Create Ads

Use "add" of AdGroupAdService.  
See also `AdGroupAd` object for more detail of API request specification.

**Note**

Following fields on `AdGroupAd` object are for YDN ads only. These are not available for ads of Display Ads (Auction).

<table>
<tr><th>Ignored field</th><th>Note</th></tr>
<tr><td>bid</td><td>　</td></tr>
</table>


**Request Sample**

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


## Use Auto-bidding (tCPA)

For campaigns by goal, auto bidding can be set with bidding strategy "tCPA".  
Follow the introduction below for using "tCPA" on campaign or on ad group.

About the availability of tCPA is described on [入札戦略について (Bidding Strategy)](https://ads-help.yahoo.co.jp/yahooads/display/articledetail?lan=ja&aid=51518) (Japanese context only).  
When the campaign can use tCPA, it responds "ENABLE" on `conversionOptimizerEligibilityFlg` field of `CampaignServiceManualCampaignConversionOptimizer` object.

Following is a sample response and request of each step.

**Response Sample of ConversionOptimizer object**

Sample: Response of `CampaignServiceManualCampaignConversionOptimizer` when the campaign cannot use tCPA.

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

Sample: Response of `CampaignServiceManualCampaignConversionOptimizer` when the campaign can use tCPA.

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

**Request Sample of tPCA by CampaignBiddingStrategy object**

Sample: Request of tCPA by `CampaignServiceCampaignBiddingStrategy` object for campaign.

```json
"campaignBiddingStrategy": {
  "campaignBiddingStrategyType": "TARGET_CPA",
  "targetCpaBidValue": 50
}
```

※`campaignBiddingStrategyType` can be modified only by campaign.
