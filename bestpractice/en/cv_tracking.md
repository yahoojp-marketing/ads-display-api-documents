# Conversion Tracking
## What is "Conversion"?
Conversion is the number of users who clicked on an Ads and performed some "result" action.<br>
By measuring this, you can see how well your Ads is performing.<br>
For details, refer to the help below.<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000045014?language=en_US">Conversion Analytics</a>

## How to operate from Display Ads API
Display Ads API uses ConversionTrackerService, to get, add and update conversion tracker information.<br>
By using this service, you can get the number of conversions from the advertisements displayed in display advertisements, and you can check how well the advertisements are performing.<br>
The conversion tag is shared with the ad management tool and API.

## Sample Scenario
Company A sells Product B for 10,000 yen. Create a conversion tracker to track conversions on your web page.

<table class="standard">
  <tr>
　　<th>Item</th>
　　<th>Value</th>
　　<th>Explain</th>
　</tr>
　<tr>
　　<td>category</td>
　　<td>PURCHASE</td>
　　<td>Conversion tracker info categories</td>
　</tr>
　<tr>
　　<td>conversionTrackerName</td>
　　<td>（Name it easy to understand）</td>
　　<td>Name of Conversion Tracker</td>
　</tr>
　<tr>
　　<td>conversionTrackerType</td>
　　<td>WEB_CONVERSION</td>
　　<td>Type of Conversion</td>
　</tr>
　<tr>
　　<td>measurementPeriod</td>
　　<td>30</td>
　　<td>Conversion measurement period（● days）</td>
　</tr>
　<tr>
　　<td>status</td>
　　<td>ENABLED</td>
　　<td>Status of Conversion Tracker Information</td>
　</tr>
　<tr>
　　<td>userRevenueValue</td>
　　<td>10000</td>
　　<td>Sales of one conversion when the sales amount is fixed（● yen）※Value of Product B</td>
　</tr>
</table>
<br>

#### 1.	Add Conversion Tracker Information
At first, add Conversion Tracker Information with ConversionTrackerService:add.

##### Request sample
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

##### Response sample
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

#### 2. Get comversion tags to measure
Get comversion tags to measure with ConversionTrackerService:get.

##### Request sample
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

##### Response sample
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

#### 3. Add tags into website and start to measure conversion
Add tags of snippet(webConversion) into website. <br><br>

#### 4. Get conversion measured
Get conversion measured with ConversionTrackerService:get.

##### Request sample
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

##### Response sample
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

#### 5.	Set Conversion Tracker Information
Then set Conversion Tracker Information, use ConversionTrackerService:set.<br>
In the following, Set category of Conversion Tracker Information from PURCHASE to PAGE_VIEW.

##### Request sample
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

##### Response sample
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
