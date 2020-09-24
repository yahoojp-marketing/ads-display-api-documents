# AuditLog item of Display Ads
1. [AuditLog field](#anchor1)
2. [active entity name](#anchor2)
3. [active event type](#anchor3)
4. [entity output item](#anchor4)
5. [column](#anchor5)

## Item
AuditLog item of Display Ad are as follows. *Data as of August 28, 2020.

#### 1.AuditLog field
<a id="anchor1"></a>

| name  |english|
|---|---|
| TIMESTAMP  |Last Updated|
| UPDATED_AT  |Updated by|
| SOURCE_TYPE  |Update Source|
| IO_NAME  |Account Name|
| IO_ID  |Account ID|
| CMPN_NAME  |Campaign Name|
| CMPN_ID  |Campaign ID|
| AD_GRP_NAME  |Ad Group Name|
| AD_GRP_ID  |Ad Group ID|
| AD_NAME  |Ad Name|
| AD_ID  |Ad ID|
| AD_TYPE  |Ad Type|
| MEDIA_NAME  |Media Name|
| MEDIA_ID  |Media ID|
| LIST_NAME  |List Name|
| LIST_ID  |List ID|
| RLST_TYPE  |Target List Type|
| CONVERSION_TRACKER_NAME  |Conversion Name|
| CONVERSION_TRACKER_ID  |Conversion ID|
| LABEL_NAME  |Label Name|
| LABEL_ID  |Label ID|
| ITEM_LIST_NAME  |Item List Name|
| ITEM_LIST_ID  |Item List ID|
| ITEM_SET_NAME  |Item Set Name|
| ITEM_SET_ID  |Item Set ID|
| ENTITY  |Entity|
| EVENT_TYPE  |Event Type|
| ITEM  |Item Name|
| BEFORE  |Before Update|
| AFTER  |After Updated|


#### 2.active entity name
<a id="anchor2"></a>

| entity |english|
|---|---|
| CAMPAIGN|Campaign|
| AD_GROUP|Ad Group|
| TARGET|Target|
| AD_GROUP_TARGET|Target|
| AD|Ad|
| MEDIA|Image|
| VIDEO|Video|
| IO|Account|
| TARGET_LIST|Target List|
| SEARCH_KEYWORD_LIST|Search Keyword List|
| PLACEMENT_URL_LIST|Placement List|
| CONVERSION_TRACKER|Conversion Analytics|
| LABEL|Label|
| CAMPAIGN_LABEL|Campaign|
| AD_GROUP_LABEL|Ad Group|
| AD_LABEL|Ad|
| FEED_ITEM_LIST|Item List|
| FEED_ITEM_SET|Item Set|

#### 3.active event type
<table id= 'anchor3'> 
<tr>
  <th>entity</th>
  <th>event type</th>
 </tr>

<tr>
  <td rowspan="4">CAMPAIGN</td>
  <td>Add</td>
</tr>
<tr>
  <td>Change Campaign Settings</td>
</tr>
<tr>
  <td>Delete Campaign</td>
</tr>
<tr>
  <td>Change Campaign Budget</td>
</tr>
 
<tr>
  <td rowspan="4">AD_GROUP</td>
  <td>Add</td>
 </tr>
 <tr>
  <td>Change Ad Group Settings</td>
 </tr>
 <tr>
  <td>Delete Ad Group</td>
 </tr>
  <tr>
  <td>Set Ad Group Bid</td>
 </tr>
 
 <tr>
  <td rowspan="2">TARGET</td>
  <td>Targeting</td>
 </tr>
  <tr>
  <td>Targeting Remove</td>
 </tr>
 
 <tr>
  <td rowspan="3">AD_GROUP_TARGET</td>
  <td>Add</td>
 </tr>
  <tr>
  <td>Change Bid adjustment</td>
 </tr>
 <tr>
 <td>Delete</td>
</tr>

<tr>
 <td rowspan="5">AD</td>
  <td>Add</td>
 </tr>
 <tr>
  <td>Change Ad Settings</td>
 </tr>
 <tr>
  <td>Delete Ad</td>
 </tr>
 <tr>
  <td>Ad Review</td>
 </tr>
 <tr>
  <td>Set Ad Bid</td>
 </tr>
 
 <tr>
  <td rowspan="4">MEDIA</td>
  <td>Add</td>
 </tr>
 <tr>
  <td>Change Image Settings</td>
 </tr>
 <tr>
  <td>Delete Images</td>
 </tr>
 <tr>
  <td>Image Review</td>
 </tr>
 
 <tr>
  <td rowspan="4">VIDEO</td>
  <td>Add</td>
 </tr>
 <tr>
  <td>Change Video Settings</td>
 </tr>
 <tr>
  <td>Delete Videos</td>
 </tr>
 <tr>
  <td>Video Review</td>
 </tr>

<tr>
 <td rowspan="3">IO</td>
 <td>Add</td>
</tr>
<tr>
 <td>Change Account Settings</td>
</tr>
<tr>
 <td>Set Account Budge</td>
</tr>

<tr>
 <td rowspan="3">TARGET_LIST</td>
 <td>Add</td>
</tr>
<tr>
 <td>Change Target List Settings</td>
</tr>
<tr>
 <td>Delete Target List</td>
</tr>

<tr>
 <td rowspan="4">SEARCH_KEYWORD_LIST</td>
 <td>Add</td>
</tr>
<tr>
 <td>Change Search Keyword List Settings</td>
</tr>
<tr>
 <td>Delete Search Keyword List</td>
</tr>
<tr>
 <td>Change Search Keyword Settings</td>
</tr>


<tr>
 <td rowspan="3">PLACEMENT_URL_LIST</td>
 <td>Add</td>
</tr>
<tr>
 <td>Change Placement List settings</td>
</tr>
<tr>
 <td>Delete Placement List</td>
</tr>

<tr>
 <td rowspan="2">CONVERSION_TRACKER</td>
 <td>Add</td>
</tr>
<tr>
 <td>Change Conversion Analytics Settings</td>
</tr>

<tr>
 <td rowspan="3">LABEL</td>
 <td>Add</td>
</tr>
<tr>
 <td>Change Label Settings</td>
</tr>
<tr>
 <td>Delete Label</td>
</tr>

<tr>
 <td rowspan="2">CAMPAIGN_LABEL</td>
 <td>Set Label</td>
</tr>
<tr>
 <td>Delete Label Settings</td>
</tr>

<tr>
 <td rowspan="2">AD_GROUP_LABEL</td>
 <td>Set Label</td>
</tr>
<tr>
 <td>Delete Label Settings</td>
</tr>

<tr>
 <td rowspan="2">AD_LABEL</td>
 <td>Set Label</td>
</tr>
<tr>
 <td>Delete Label Settings</td>
</tr>

<tr>
 <td rowspan="3">FEED_ITEM_LIST</td>
 <td>Add</td>
</tr>
<tr>
 <td>Change Item List Settings</td>
</tr>
<tr>
 <td>Delete Item List</td>
</tr>

<tr>
 <td rowspan="3">FEED_ITEM_SET</td>
 <td>Add</td>
</tr>
<tr>
 <td>Delete Item Set</td>
</tr>
</table>


#### 4.entity output item
<table id="anchor4">
<tr>
  <th>entity</th>
  <th>item</th>
 </tr>
 
<tr>
 <td rowspan="29">CAMPAIGN</td>
 <td>Campaign Name</td>
</tr>
<tr>
 <td>Display Settings</td>
</tr>
<tr>
 <td>Ad Distribution</td>
</tr>
<tr>
 <td>Daily budget</td>
</tr>
<tr>
 <td>Start Date</td>
</tr>
<tr>
 <td>End Date</td>
</tr>
<tr>
 <td>Frequency cap (previous) (impressions)</td>
</tr>
<tr>
 <td>Frequency cap (previous) (level)</td>
</tr>
<tr>
 <td>Frequency cap (previous) (time)</td>
</tr>
<tr>
 <td>Target CPA</td>
</tr>
<tr>
 <td>Campaign Type</td>
</tr>
<tr>
 <td>App ID/Package name</td>
</tr>
<tr>
 <td>App Name</td>
</tr>
<tr>
 <td>App OS</td>
</tr>
<tr>
 <td>Item List ID</td>
</tr>
<tr>
 <td>Bidding</td>
</tr>
<tr>
 <td>Campaign buying type</td>
</tr>
<tr>
 <td>Campaign goal</td>
</tr>
<tr>
 <td>Campaign bid strategy</td>
</tr>
<tr>
 <td>Bid (vCPM)</td>
</tr>
<tr>
 <td>Bid (CPC)</td>
</tr>
<tr>
 <td>Bid (CPV)</td>
</tr>
<tr>
 <td>Target CPA (tCPA)</td>
</tr>
<tr>
 <td>Frequency cap (impressions)</td>
</tr>
<tr>
 <td>Frequency cap (level)</td>
</tr>
<tr>
 <td>Frequency cap (time)</td>
</tr>
<tr>
 <td>Status change notified to</td>
</tr>
<tr>
 <td>Lifetime budget</td>
</tr>
<tr>
 <td>Reservation canceled</td>
</tr>


<tr>
 <td rowspan="18">AD_GROUP</td>
 <td>Ad Group Name</td>
</tr>
<tr>
 <td>Display Settings</td>
</tr>
<tr>
 <td>Bidding</td>
</tr>
<tr>
 <td>Ad Group Bid</td>
</tr>
<tr>
 <td>Target CPA</td>
</tr>
<tr>
 <td>Device</td>
</tr>
<tr>
 <td>Web page / App</td>
</tr>
<tr>
 <td>OS</td>
</tr>
<tr>
 <td>OS version (minimum)</td>
</tr>
<tr>
 <td>Carrier</td>
</tr>
<tr>
 <td>Dynamic Image Extensions</td>
</tr>
<tr>
 <td>Oldest OS version targeted</td>
</tr>
<tr>
 <td>Latest OS version targeted</td>
</tr>
<tr>
 <td>Item Set ID</td>
</tr>
<tr>
 <td>Bid (vCPM)</td>
</tr>
<tr>
 <td>Bid (CPC)</td>
</tr>
<tr>
 <td>Bid (CPV)</td>
</tr>
<tr>
 <td>Target CPA (tCPA)</td>
</tr>

<tr>
 <td rowspan="9">TARGET</td>
 <td>Day of Week / Hours</td>
</tr>
<tr>
 <td>Age</td>
</tr>
<tr>
 <td>Gender</td>
</tr>
<tr>
 <td>Geographic Location</td>
</tr>
<tr>
 <td>Interest Category</td>
</tr>
<tr>
 <td>Site Category</td>
</tr>
<tr>
 <td>Site Retargeting</td>
</tr>
<tr>
 <td>Search keyword</td>
</tr>
<tr>
 <td>Placement</td>
</tr>

<tr>
 <td rowspan="15">AD_GROUP_TARGET</td>
 <td>Day of Week / Hours</td>
</tr>
<tr>
 <td>Age</td>
</tr>
<tr>
 <td>Gender</td>
</tr>
<tr>
 <td>Geographic Location</td>
</tr>
<tr>
 <td>Interest Category</td>
</tr>
<tr>
 <td>Site Category</td>
</tr>
<tr>
 <td>Site Retargeting</td>
</tr>
<tr>
 <td>Search keyword</td>
</tr>
<tr>
 <td>Placement</td>
</tr>
<tr>
 <td>Device</td>
</tr>
<tr>
 <td>Carrier</td>
</tr>
<tr>
 <td>Web page/App</td>
</tr>
<tr>
 <td>OS</td>
</tr>
<tr>
 <td>OS version (minimum)</td>
</tr>
<tr>
 <td>Audience category</td>
</tr>

<tr>
 <td rowspan="47">AD</td>
 <td>Ad Name</td>
</tr>
<tr>
 <td>Display Settings</td>
</tr>
<tr>
 <td>Bid</td>
</tr>
<tr>
 <td>Ad Type</td>
</tr>
<tr>
 <td>Title</td>
</tr>
<tr>
 <td>Description1</td>
</tr>
<tr>
 <td>Description2</td>
</tr>
<tr>
 <td>Carrier (Feature Phone)</td>
</tr>
<tr>
 <td>App Name</td>
</tr>
<tr>
 <td>App ID / Package Name</td>
</tr>
<tr>
 <td>Button</td>
</tr>
<tr>
 <td>URL Scheme</td>
</tr>
<tr>
 <td>Media ID (Logo)</td>
</tr>
<tr>
 <td>Media ID (Logo 2)</td>
</tr>
<tr>
 <td>Media ID (Logo 3)</td>
</tr>
<tr>
 <td>Advertiser Indication</td>
</tr>
<tr>
 <td>Color Theme</td>
</tr>
<tr>
 <td>Disclaimer</td>
</tr>
<tr>
 <td>Prefix</td>
</tr>
<tr>
 <td>Suffix</td>
</tr>
<tr>
 <td>Base Color</td>
</tr>
<tr>
 <td>Media ID</td>
</tr>
<tr>
 <td>Display URL</td>
</tr>
<tr>
 <td>Destination URL</td>
</tr>
<tr>
 <td>Impression Beacon URL</td>
</tr>
<tr>
 <td>Viewing Beacon URL (start)</td>
</tr>
<tr>
 <td>Viewing Beacon URL (3 seconds)</td>
</tr>
<tr>
 <td>Viewing Beacon URL (10 seconds)</td>
</tr>
<tr>
 <td>Viewing Beacon URL (complete)</td>
</tr>
<tr>
 <td>Viewing beacon URL (25%)</td>
</tr>
<tr>
 <td>Viewing beacon URL (50%)</td>
</tr>
<tr>
 <td>Viewing beacon URL (75%)</td>
</tr>
<tr>
 <td>Creation Date</td>
</tr>
<tr>
 <td>Media ID (Video thumbnail)</td>
</tr>
<tr>
 <td>Third-party script tag src attribute URL</td>
</tr>
<tr>
 <td>Destination update/launch time</td>
</tr>
<tr>
 <td>Destination status</td>
</tr>
<tr>
 <td>Media ID (shrink main image)</td>
</tr>
<tr>
 <td>Media ID (left side image)</td>
</tr>
<tr>
 <td>Media ID (right side image)</td>
</tr>
<tr>
 <td>Media ID (center image)</td>
</tr>
<tr>
 <td>Preapprove ID</td>
</tr>
<tr>
 <td>Media ID (Campaign Banner)</td>
</tr>
<tr>
 <td>Media ID (Campaign Banner 2)</td>
</tr>
<tr>
 <td>Media ID (Campaign Banner 3)</td>
</tr>
<tr>
 <td>Media ID (Campaign Banner 4)</td>
</tr>
<tr>
 <td>Destination URL (Campaign Banner)</td>
</tr>

<tr>
 <td rowspan="3">MEDIA</td>
 <td>Display Settings</td>
</tr>
<tr>
 <td>Media Name</td>
</tr>
<tr>
 <td>Date Submitted</td>
</tr>
<tr>
 <td rowspan="3">VIDEO</td>
 <td>Display Settings</td>
</tr>
<tr>
 <td>Media Name</td>
</tr>
<tr>
 <td>Date Submitted</td>
</tr>
<tr>
 <td rowspan="20">IO</td>
 <td>Account Name</td>
</tr>
<tr>
 <td>Account Budget</td>
</tr>
<tr>
 <td>Primary Business Contact</td>
</tr>
<tr>
 <td>Agency Location</td>
</tr>
<tr>
 <td>Advertiser Location</td>
</tr>
<tr>
 <td>Account Created</td>
</tr>
<tr>
 <td>End Date</td>
</tr>
<tr>
 <td>Contact Name (Advertiser)</td>
</tr>
<tr>
 <td>Automatic Charge Amount</td>
</tr>
<tr>
 <td>Automatic Charge Setting</td>
</tr>
<tr>
 <td>Business ID for Card Holder  on Automatic Charge</td>
</tr>
<tr>
 <td>Display Settings</td>
</tr>
<tr>
 <td>Primary Business Contact (Yahoo! JAPAN Business ID)</td>
</tr>
<tr>
 <td>Fund Allocation</td>
</tr>
<tr>
 <td>Interest Match</td>
</tr>
<tr>
 <td>Agreed Terms & Agreements  (Order Accepted)</td>
</tr>
<tr>
 <td>Email Address</td>
</tr>
<tr>
 <td>Contact Mail Setting</td>
</tr>
<tr>
 <td>Auto-tagging</td>
</tr>
<tr>
 <td>Target List Status</td>
</tr>

<tr>
 <td rowspan="11">TARGET_LIST</td>
 <td>Target List Name</td>
</tr>
<tr>
 <td>Target List Description</td>
</tr>
<tr>
 <td>Target List Type</td>
</tr>
<tr>
 <td>Accumulation of Site Visitor History</td>
</tr>
<tr>
 <td>Setting the past visitors</td>
</tr>
<tr>
 <td>Effective period for the Site Visitor History Setting</td>
</tr>
<tr>
 <td>Duration of DMP configured data</td>
</tr>
<tr>
 <td>Target List Rule</td>
</tr>
<tr>
 <td>Source Target List Name</td>
</tr>
<tr>
 <td>Target List Size</td>
</tr>
<tr>
 <td>Share Status</td>
</tr>

<tr>
 <td rowspan="5">SEARCH_KEYWORD_LIST</td>
 <td>Search Keyword List Name</td>
</tr>
<tr>
 <td>Search Keyword List Description</td>
</tr>
<tr>
 <td>Duration</td>
</tr>
<tr>
 <td>Searches</td>
</tr>
<tr>
 <td>Search Keyword</td>
</tr>

<tr>
 <td rowspan="3">PLACEMENT_URL_LIST</td>
 <td>Placement List Name</td>
</tr>
<tr>
 <td>Placement List Description</td>
</tr>
<tr>
 <td>Placement URL</td>
</tr>

<tr>
 <td rowspan="11">CONVERSION_TRACKER</td>
 <td>Conversion Type</td>
</tr>
<tr>
 <td>Conversion Name</td>
</tr>
<tr>
 <td>Conversion Tracking Purpose</td>
</tr>
<tr>
 <td>Counting Period</td>
</tr>
<tr>
 <td>Counting Period (video view)</td>
</tr>
<tr>
 <td>Counting Type</td>
</tr>
<tr>
 <td>Conversion counting</td>
</tr>
<tr>
 <td>Value per Conversion</td>
</tr>
<tr>
 <td>App OS</td>
</tr>
<tr>
 <td>App ID/Package name</td>
</tr>
<tr>
 <td>Status</td>
</tr>

<tr>
 <td rowspan="4">LABEL</td>
 <td>Label Name</td>
</tr>
<tr>
 <td>Label Color</td>
</tr>
<tr>
 <td>Label Description</td>
</tr>
<tr>
 <td>Label</td>
</tr>

<tr>
 <td rowspan="1">CAMPAIGN_LABEL</td>
 <td>Label</td>
</tr>

<tr>
 <td rowspan="1">AD_GROUP_LABEL</td>
 <td>Label</td>
</tr>

<tr>
 <td rowspan="1">AD_LABEL</td>
 <td>Label</td>
</tr>

<tr>
 <td rowspan="8">FEED_ITEM_LIST</td>
 <td>Item List Name</td>
</tr>
<tr>
 <td>Ftp Feed Url</td>
</tr>
<tr>
 <td>Ftp User Name</td>
</tr>
<tr>
 <td>Ftp Schedule Time</td>
</tr>
<tr>
 <td>Ftp Schedule Week</td>
</tr>
<tr>
 <td>Ftp Schedule Interval</td>
</tr>
<tr>
 <td>Ftp Upload Type</td>
</tr>
<tr>
 <td>Ftp Status</td>
</tr>

<tr>
 <td rowspan="2">FEED_ITEM_SET</td>
 <td>Item Set Name</td>
</tr>
<tr>
 <td>Item Set Rule</td>
</tr>
</table>

#### 5.column
<table id="anchor5">
<tr>
  <th>item</th>
  <th>english</th>
 </tr>

<tr>
 <td rowspan="2">Display Settings</td>
 <td>OFF</td>
</tr>
<tr>
 <td>ON</td>
</tr>


<tr>
 <td rowspan="1">Daily budget</td>
 <td>None</td>
</tr>

<tr>
 <td rowspan="1">Bid</td>
 <td>None</td>
</tr>

<tr>
 <td rowspan="1">Frequency cap (previous) (impressions)</td>
 <td>None</td>
</tr>

<tr>
 <td rowspan="2">End Date</td>
 <td>None</td>
</tr>
<tr>
 <td>None</td>
</tr>

<tr>
 <td rowspan="4">Frequency cap (previous) (level)</td>
 <td>None</td>
</tr>
<tr>
 <td>Campaign</td>
</tr>
<tr>
 <td>Ad Group</td>
</tr>
<tr>
 <td>Ad</td>
</tr>

<tr>
 <td rowspan="6">Frequency cap (previous) (time)</td>
 <td>None</td>
</tr>
<tr>
 <td>Per Minute</td>
</tr>
<tr>
 <td>Hourly</td>
</tr>
<tr>
 <td>Daily</td>
</tr>
<tr>
 <td>Weekly</td>
</tr>
<tr>
 <td>Monthly</td>
</tr>

<tr>
 <td rowspan="3">Bidding</td>
 <td>Apply same Bidding with campaign</td>
</tr>
<tr>
 <td>Manual bidding</td>
</tr>
<tr>
 <td>Auto bidding (optimize conversion)</td>
</tr>

<tr>
 <td rowspan="1">Target CPA</td>
 <td>None</td>
</tr>

<tr>
 <td rowspan="1">Target CPA</td>
 <td>None</td>
</tr>

<tr>
 <td rowspan="2">Campaign Type</td>
 <td>Standard</td>
</tr>
<tr>
 <td>Mobile App</td>
</tr>

<tr>
 <td rowspan="2">App OS</td>
 <td>Android</td>
</tr>
<tr>
 <td>iOS</td>
</tr>


<tr>
 <td rowspan="5">Device</td>
 <td>PC</td>
</tr>
<tr>
 <td>Feature Phone</td>
</tr>
<tr>
 <td>Smartphone</td>
</tr>
<tr>
 <td>Tablet</td>
</tr>
<tr>
 <td>None</td>
</tr>

<tr>
 <td rowspan="3">OS</td>
 <td>Android</td>
</tr>
<tr>
 <td>iOS</td>
</tr>
<tr>
 <td>None</td>
</tr>

<tr>
 <td rowspan="3">Web page / App</td>
 <td>App</td>
</tr>
<tr>
 <td>Web</td>
</tr>
<tr>
 <td>None</td>
</tr>

<tr>
 <td rowspan="2">Dynamic Image Extensions</td>
 <td>ON</td>
</tr>
<tr>
 <td>OFF</td>
</tr>

<tr>
 <td rowspan="24">Ad Type</td>
 <td>Text (description 19-19)</td>
</tr>
<tr>
 <td>Text (description 33)</td>
</tr>
<tr>
 <td>Short Text (14, 19)</td>
</tr>
<tr>
 <td>Short Text (12, 12)</td>
</tr>
<tr>
 <td>Position specified text</td>
</tr>
<tr>
 <td>Text Ad(15-90)</td>
</tr>
<tr>
 <td>Responsive (image)</td>
</tr>
<tr>
 <td>Static Frame(300x250)-Square Banner (Top)</td>
</tr>
<tr>
 <td>Static Frame(300x250)-Wide Banner (Top)</td>
</tr>
<tr>
 <td>Static Frame(300x250)-Wide Banner (Middle)</td>
</tr>
<tr>
 <td>Dynamic</td>
</tr>
<tr>
 <td>Responsive (video)</td>
</tr>
<tr>
 <td>Banner (video)</td>
</tr>
<tr>
 <td>Brand panel quintuple</td>
</tr>
<tr>
 <td>Brand panel quintuple video</td>
</tr>
<tr>
 <td>Brand panel panorama</td>
</tr>
<tr>
 <td>Brand panel panorama video</td>
</tr>
<tr>
 <td>Top impact square</td>
</tr>
<tr>
 <td>Top impact square video</td>
</tr>
<tr>
 <td> Top impact quintuple</td>
</tr>
<tr>
 <td>Top impact video</td>
</tr>
<tr>
 <td>Top impact panorama</td>
</tr>
<tr>
 <td>Top impact panorama video</td>
</tr>
<tr>
 <td>Banner (image)</td>
</tr>
<tr>
 <td rowspan="6">Carrier</td>
 <td>docomo</td>
</tr>
<tr>
 <td>KDDI</td>
</tr>
<tr>
 <td>SoftBank</td>
</tr>
<tr>
 <td>Y!mobile</td>
</tr>
<tr>
 <td>Others</td>
</tr>
<tr>
 <td>All carriers</td>
</tr>

<tr>
 <td rowspan="3">Contact Mail Setting</td>
 <td>Do not receive</td>
</tr>
<tr>
 <td>Important only</td>
</tr>
<tr>
 <td>Receive</td>
</tr>

<tr>
 <td rowspan="49">Agency Location</td>
 <td>Hokkaido</td>
</tr>
<tr>
 <td>Aomori</td>
</tr>
<tr>
 <td>Iwate</td>
</tr>
<tr>
 <td>Miyagi</td>
</tr>
<tr>
 <td>Akita</td>
</tr>
<tr>
 <td>Yamagata</td>
</tr>
<tr>
 <td>Fukushima</td>
</tr>
<tr>
 <td>Ibaraki</td>
</tr>
<tr>
 <td>Tochigi</td>
</tr>
<tr>
 <td>Gunma</td>
</tr>
<tr>
 <td>Saitama</td>
</tr>
<tr>
 <td>Chiba</td>
</tr>
<tr>
 <td>Tokyo</td>
</tr>
<tr>
 <td>Kanagawa</td>
</tr>
<tr>
 <td>Niigata</td>
</tr>
<tr>
 <td>Toyama</td>
</tr>
<tr>
 <td>Ishikawa</td>
</tr>
<tr>
 <td>Fukui</td>
</tr>
<tr>
 <td>Yamanashi</td>
</tr>
<tr>
 <td>Nagano</td>
</tr>
<tr>
 <td>Gifu</td>
</tr>
<tr>
 <td>Shizuoka</td>
</tr>
<tr>
 <td>Aichi</td>
</tr>
<tr>
 <td>Mie</td>
</tr>
<tr>
 <td>Shiga</td>
</tr>
<tr>
 <td>Kyoto</td>
</tr>
<tr>
 <td>Osaka</td>
</tr>
<tr>
 <td>Hyogo</td>
</tr>
<tr>
 <td>Nara</td>
</tr>
<tr>
 <td>Wakayama</td>
</tr>
<tr>
 <td>Tottori</td>
</tr>
<tr>
 <td>Shimane</td>
</tr>
<tr>
 <td>Okayama</td>
</tr>
<tr>
 <td>Hiroshima</td>
</tr>
<tr>
 <td>Yamaguchi</td>
</tr>
<tr>
 <td>Tokushima</td>
</tr>
<tr>
 <td>Kagawa</td>
</tr>
<tr>
 <td>Ehime</td>
</tr>
<tr>
 <td>Kochi</td>
</tr>
<tr>
 <td>Fukuoka</td>
</tr>
<tr>
 <td>Saga</td>
</tr>
<tr>
 <td>Nagasaki</td>
</tr>
<tr>
 <td>Kumamoto</td>
</tr>
<tr>
 <td>Oita</td>
</tr>
<tr>
 <td>Miyazaki</td>
</tr>
<tr>
 <td>Kagoshima</td>
</tr>
<tr>
 <td>Okinawa</td>
</tr>
<tr>
 <td>Outside Japan</td>
</tr>
<tr>
 <td>N/A</td>
</tr>

<tr>
 <td rowspan="49">Advertiser Location</td>
 <td>Hokkaido</td>
</tr>
<tr>
 <td>Aomori</td>
</tr>
<tr>
 <td>Iwate</td>
</tr>
<tr>
 <td>Miyagi</td>
</tr>
<tr>
 <td>Akita</td>
</tr>
<tr>
 <td>Yamagata</td>
</tr>
<tr>
 <td>Fukushima</td>
</tr>
<tr>
 <td>Ibaraki</td>
</tr>
<tr>
 <td>Tochigi</td>
</tr>
<tr>
 <td>Gunma</td>
</tr>
<tr>
 <td>Saitama</td>
</tr>
<tr>
 <td>Chiba</td>
</tr>
<tr>
 <td>Tokyo</td>
</tr>
<tr>
 <td>Kanagawa</td>
</tr>
<tr>
 <td>Niigata</td>
</tr>
<tr>
 <td>Toyama</td>
</tr>
<tr>
 <td>Ishikawa</td>
</tr>
<tr>
 <td>Fukui</td>
</tr>
<tr>
 <td>Yamanashi</td>
</tr>
<tr>
 <td>Nagano</td>
</tr>
<tr>
 <td>Gifu</td>
</tr>
<tr>
 <td>Shizuoka</td>
</tr>
<tr>
 <td>Aichi</td>
</tr>
<tr>
 <td>Mie</td>
</tr>
<tr>
 <td>Shiga</td>
</tr>
<tr>
 <td>Kyoto</td>
</tr>
<tr>
 <td>Osaka</td>
</tr>
<tr>
 <td>Hyogo</td>
</tr>
<tr>
 <td>Nara</td>
</tr>
<tr>
 <td>Wakayama</td>
</tr>
<tr>
 <td>Tottori</td>
</tr>
<tr>
 <td>Shimane</td>
</tr>
<tr>
 <td>Okayama</td>
</tr>
<tr>
 <td>Hiroshima</td>
</tr>
<tr>
 <td>Yamaguchi</td>
</tr>
<tr>
 <td>Tokushima</td>
</tr>
<tr>
 <td>Kagawa</td>
</tr>
<tr>
 <td>Ehime</td>
</tr>
<tr>
 <td>Kochi</td>
</tr>
<tr>
 <td>Fukuoka</td>
</tr>
<tr>
 <td>Saga</td>
</tr>
<tr>
 <td>Nagasaki</td>
</tr>
<tr>
 <td>Kumamoto</td>
</tr>
<tr>
 <td>Oita</td>
</tr>
<tr>
 <td>Miyazaki</td>
</tr>
<tr>
 <td>Kagoshima</td>
</tr>
<tr>
 <td>Okinawa</td>
</tr>
<tr>
 <td>Outside Japan</td>
</tr>
<tr>
 <td>N/A</td>
</tr>

<tr>
 <td rowspan="2">Automatic Charge Setting</td>
 <td>OFF</td>
</tr>
<tr>
 <td>ON</td>
</tr>

<tr>
 <td rowspan="2">Display Settings by Yahoo! JAPAN</td>
 <td>OFF</td>
</tr>
<tr>
 <td>ON</td>
</tr>

<tr>
 <td rowspan="2">Interest Match</td>
 <td>ON</td>
</tr>
<tr>
 <td>OFF</td>
</tr>

<tr>
 <td rowspan="1">Effective period for the Site Visitor History Setting</td>
 <td>N/A</td>
</tr>

<tr>
 <td rowspan="5">Target List Type</td>
 <td>Default</td>
</tr>
<tr>
 <td>Rule</td>
</tr>
<tr>
 <td>Combination</td>
</tr>
<tr>
 <td>Similar</td>
</tr>
<tr>
 <td>Custom</td>
</tr>


<tr>
 <td rowspan="10">Target List Size</td>
 <td>1</td>
</tr>
<tr>
 <td>2</td>
</tr>
<tr>
 <td>3</td>
</tr>
<tr>
 <td>4</td>
</tr>
<tr>
 <td>5</td>
</tr>
<tr>
 <td>6</td>
</tr>
<tr>
 <td>7</td>
</tr>
<tr>
 <td>8</td>
</tr>
<tr>
 <td>9</td>
</tr>
<tr>
 <td>10</td>
</tr>

<tr>
 <td rowspan="3">Accumulation of Site Visitor History</td>
 <td>OFF</td>
</tr>
<tr>
 <td>ON</td>
</tr>
<tr>
 <td>''</td>
</tr>

<tr>
 <td rowspan="3">Setting the past visitors</td>
 <td>OFF</td>
</tr>
<tr>
 <td>ON</td>
</tr>
<tr>
 <td>''</td>
</tr>

<tr>
 <td rowspan="2">Conversion Type</td>
 <td>Web</td>
</tr>
<tr>
 <td>App</td>
</tr>

<tr>
 <td rowspan="2">Counting Type</td>
 <td>Many per click</td>
</tr>
<tr>
 <td>One per click</td>
</tr>

<tr>
 <td rowspan="7">Item List</td>
 <td>N/A</td>
</tr>
<tr>
 <td>Other</td>
</tr>
<tr>
 <td>Page Access</td>
</tr>
<tr>
 <td>Purchase / Sales</td>
</tr>
<tr>
 <td>Application</td>
</tr>
<tr>
 <td>Sales promotion</td>
</tr>
<tr>
 <td>Other</td>
</tr>
<tr>
 <td rowspan="2">Conversion counting</td>
 <td>Exclude</td>
</tr>
<tr>
 <td>Include</td>
</tr>
<tr>
 <td rowspan="2">App OS</td>
 <td>iOS</td>
</tr>
<tr>
 <td>Android</td>
</tr>
<tr>
 <td rowspan="2">Status</td>
 <td>On</td>
</tr>
<tr>
 <td>Off</td>
</tr>
<tr>
 <td rowspan="3">Auto-tagging</td>
 <td>Set</td>
</tr>
<tr>
 <td>Do not set</td>
</tr>
<tr>
 <td>Off (continue)</td>
</tr>
<tr>
 <td rowspan="2">Share Status</td>
 <td>Shared</td>
</tr>
<tr>
 <td>Unshared</td>
</tr>
<tr>
 <td rowspan="2">Target List Status</td>
 <td>Shared</td>
</tr>
<tr>
 <td>Unshared</td>
</tr>


<tr>
 <td rowspan="7">Ftp Schedule Week</td>
 <td>Sunday</td>
</tr>
<tr>
 <td>Monday</td>
</tr>
<tr>
 <td>Tuesday</td>
</tr>
<tr>
 <td>Wednesday</td>
</tr>
<tr>
 <td>Thursday</td>
</tr>
<tr>
 <td>Friday</td>
</tr>
<tr>
 <td>Saturday</td>
</tr>

<tr>
 <td rowspan="2">Ftp Upload Type</td>
 <td>Update Partially</td>
</tr>

<tr>
 <td>Update all</td>
</tr>
<tr>
 <td rowspan="2">Ftp Status</td>
 <td>Paused</td>
</tr>
<tr>
 <td>Active</td>
</tr>

<tr>
 <td rowspan="7">キャンペーン目的</td>
 <td>Brand awareness</td>
</tr>
<tr>
 <td>Video view</td>
</tr>
<tr>
 <td>Website traffic</td>
</tr>
<tr>
 <td>App promotion</td>
</tr>
<tr>
 <td>Conversion</td>
</tr>
<tr>
 <td>Item list promotion</td>
</tr>
<tr>
 <td>None</td>
</tr>
<tr>
 <td rowspan="2">Campaign buying type</td>
 <td>Auction</td>
</tr>
<tr>
 <td>Guaranteed</td>
</tr>

<tr>
 <td rowspan="6">Campaign bid strategy</td>
 <td>Auto-bidding</td>
</tr>
<tr>
 <td>Manual-bidding (vCPM)</td>
</tr>
<tr>
 <td>Manual-bidding (CPC)</td>
</tr>
<tr>
 <td>Manual-bidding (CPV)</td>
</tr>
<tr>
 <td>Auto-bidding (tCPA)</td>
</tr>
<tr>
 <td>None</td>
</tr>
<tr>
 <td rowspan="4">Frequency cap (level)</td>
 <td>None</td>
</tr>
<tr>
 <td>Campaign</td>
</tr>
<tr>
 <td>Ad Group</td>
</tr>
<tr>
 <td>Ad</td>
</tr>
<tr>
 <td rowspan="7">Frequency cap (time)</td>
 <td>None</td>
</tr>
<tr>
 <td>Per Minute</td>
</tr>
<tr>
 <td>Hourly</td>
</tr>
<tr>
 <td>Daily</td>
</tr>
<tr>
 <td>Weekly</td>
</tr>
<tr>
 <td>Monthly</td>
</tr>
<tr>
 <td>Lifetime</td>
</tr>
<tr>
 <td rowspan="2">Destination status</td>
 <td>Complete/launched</td>
</tr>
<tr>
 <td>Update/launch later</td>
</tr>
</table>
