# Mediation-Reporting-API


## Introduction

This Mediation Reporting API provide publishers who integrated Adxmi SDK with a real-time access to a variety of data. Publishers can retrieve ad performance reporting programmatically. To access this API, you will need to perform the following steps:

1.	Become an Adxmi publisher.

2.	Integrate Adxmi SDK on your application.

3.	Make appropriate calls to the API endpoints.

*The API is only accessible by HTTP GET and returns data in JSON format.

## API Request

### API Request rul

http://reporting.yyapi.net/mediation

### Request Parameter

| Parameter   | Type   | Mandatory | Example     |Description    |
|-------------|--------|-----------|-------------------------|------------------------------------------------------------------------------------------------------------------|
| email      | string | Y         | email=example@gmail.com |Publisher’s email used to register on Adxmi website.                                                                        |
| key   | string( 32 characters )    | Y         | key=we2917n2is61o92s72m0d71bd9am37xj          |Unique key to access Adxmi API.            |
| start_date | string| Y         | start_date=20170715         |Assign the start date to retrieve report.  | 
| end_date | string| Y         | end_date=20170715         | Assign the end date to retrieve report. | 
| app_id        | string( 16 characters )    | N         | app_id=b3a3277b8fdd54bc                  |Publisher’s application id, used to access Adxmi Ads. All applications data would be responded if publisher wouldn’t set this parameter.                                                                |
| slot_id        | string  | N         | slot_id=320116255535293290              | Publishers can get data of specific slot_id. All the data would be responded if publisher wouldn’t set this parameter.      |
| country     | string  | N         | country=US,CN,AU        | Publishers can get data of specific countries.  all the data would be responded if publisher wouldn’t set this parameter.  |
| group_by | string| N        | group_by=country         | Publisher can specify the aggregation of data using this parameter. Data would be aggregated by Date in default if publisher wouldn’t set this parameter.<br> **Field:**<br> app_id <br> slot_id <br> country <br>  data. <br>
|  

### Example:
http://reporting.yyapi.net/mediation?email=example@gmail.com&key=we2917n2is61o92s72m0d71bd9am37xj9&start_date=20170715&end_date=20170720&group_by=slot_id

## Response Field

| Parameter | Type | Description |
| ---- | ---- | ---- |
| request | int | Count of ads requesting.|
| response  | int | Count of ads response from Adxmi server. |
| impression | int| Count of ads display with user’s device. |
| click | int | Count of clicks from user’s device. |
| revenue | float | The total revenue that publisher can get. |


### Example 1: Response grouped by date
```json
{
c: 0,
data: [
{
request: 48969419,
response: 48969419,
impression: 582406,
click: 4020,
revenue: 554.001,
date: "2017-07-15"
},
{
request: 50449840,
response: 50449840,
impression: 596584,
click: 4062,
revenue: 603.581,
date: "2017-07-16"
}
]
}
```

### Example 2: Response grouped by country
```json
{
c: 0,
data: [
{
request: 70,
response: 70,
impression: 0,
click: 0,
revenue: 0,
country: "AD"
},
{
request: 2000237,
response: 2000237,
impression: 20968,
click: 203,
revenue: 3.0615,
country: "AE"
},
{
request: 4998,
response: 4998,
impression: 98,
click: 14,
revenue: 0.0679,
country: "AF"
} 
]
}

```

