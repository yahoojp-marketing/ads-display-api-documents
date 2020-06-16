# Display Ads Report
## What is “Performance Report”?
Performance Report is a function of confirming performance of Campaign, Ad Group, Ad, etc. 
Customizing is possible when creating report, like setting item display, performance period, etc.
Creating report will be more easier by using the recommended report setting.<br>

Report functions supported in Campaign Management Tool are also available from API.   
  
## How to operate from Display Ads API
To display the performance report, use the two services below from Display Ads API.    
ReportDefinitionService can retrieve and add/download the report. 

# Scenario Sample
This is introducing the process from creating to downloading the report, to retrieve Performance Report, using Display Ads API. 

#### 1.	Retrieve Field of Template
Use getReportFields of ReportDefinitionService.
Retrieving list of available report fields by designating ReportCategory.
Each report fields encapsulate the Field Name, Display Name, and XML Attribute

##### Request Sample
```json
{
  "type": "AD"
}
```

##### Response Sample
I omit a part.
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

#### 2.	Create Report 
Use add of ReportDefinitionService.  

##### Request Sample
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
      "lang": "EN",
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

##### Response Sample
I omit a part.
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
                    "lang": "EN",
                    "reportJobErrorDetail": null,
                    "reportJobId": 11111111,
                    ...
                }
            }
        ]
    }
}
```
#### 3. Confirm the Report Status
Use get of ReportService. Can confirm the report creation status. <br>
Also, when jobStatus of response is "completed", go to 4.

##### Request Sample
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

##### Response Sample
I omit a part.
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
                    "lang": "EN",
                    "reportJobErrorDetail": null,
                    "reportJobId": 11111111,
                    ...
                }
            }
        ]
    }
}
```

#### 4. Download Report
Use download of ReportDefinitionService.  
Download report from ReportList.  

##### Request Sample
```json
{
  "accountId": 11111111,
  "reportJobId": 11111111
}
```

##### Response Sample
If no date, it looks like this.<br>
result of unzip.<br>
```csv
Account ID,Account Name,Campaign ID,Campaign Name,Ad Group ID,Ad Group Name,Ad ID,Ad Name,Ad Type,Destination URL ID,Destination URL,Prefecture ID,Prefectures,City ID,City,Ward ID,Ward,Gender,Age,Month,Daily
Total,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--
```
