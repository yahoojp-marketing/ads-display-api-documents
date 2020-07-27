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
      "reportDownloadEncode": "UTF-8",
      "reportDownloadFormat": "CSV",
      "reportLanguage": "EN",
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

##### Response Sample
```json
{
    "errors": null,
    "rid": "51ca5746bc4bf4075eef078e14463b8b",
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
                    "frequencyRange": null,
                    "reportCompressType": "ZIP",
                    "reportDateRangeType": "LAST_7_DAYS",
                    "reportDownloadEncode": "UTF-8",
                    "reportDownloadFormat": "CSV",
                    "reportJobStatus": "WAIT",
                    "reportJobErrorDetail": null,
                    "reportJobId": 222222,
                    "reportLanguage": "EN",
                    "reportName": "test report 01",
                    "requestTime": "20200722191736",
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
#### 3. Confirm the Report Status
Use get of ReportService. Can confirm the report creation status. <br>
Also, when jobStatus of response is "completed", go to 4.

##### Request Sample
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

##### Response Sample
```json
{
    "errors": null,
    "rid": "4af57c41216af87b6f5de4449bc82318",
    "rval": {
        "totalNumEntries": 1,
        "values": [
            {
                "errors": null,
                "operationSucceeded": true,
                "reportDefinition": {
                    "accountId": 111111,
                    "completeTime": "20200722191737",
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
                    "frequencyRange": null,
                    "reportCompressType": "ZIP",
                    "reportDateRangeType": "LAST_7_DAYS",
                    "reportDownloadEncode": "UTF-8",
                    "reportDownloadFormat": "CSV",
                    "reportJobStatus": "COMPLETED",
                    "reportJobErrorDetail": null,
                    "reportJobId": 222222,
                    "reportLanguage": "EN",
                    "reportName": "test report 01",
                    "requestTime": "20200722191736",
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

#### 4. Download Report
Use download of ReportDefinitionService.  
Download report from ReportList.  

##### Request Sample
```json
{
  "accountId": 111111,
  "reportJobId": 222222
}
```

##### Response Sample
If no date, it looks like this.<br>
result of unzip.<br>
```csv
Account ID,Account Name,Campaign ID,Campaign Name,Ad Group ID,Ad Group Name,Ad ID,Ad Name,Ad Type,Destination URL ID,Destination URL,Prefecture ID,Prefectures,City ID,City,Ward ID,Ward,Gender,Age,Month,Daily
Total,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--
```
