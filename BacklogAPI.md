# [S] Backlog API
----

I am updating this and trying to mess up this shit.


## Authorization and HTTP Header Information
All requests to the microservice will follow a standard authentication. Each request is authorized via an API Key and API Secret. Also, all request should contain both `requestUID` and `resourceOwnerId`.

#### Request Header Mapping
The following are the minimum required headers for each request:

| DataType   |           Field Name|Mandatory |           Description                      | Sample Value |
| ---------- | ----------------------- | ----------| -------------------------------------- | ------- |
| String |apiKey              |Yes   |The apiKey used to authenticate access | hbdjshdvfjhsdbvfjhsd |
| String |apiSecret           |Yes   |The api secret used to authenticate access |  sbdfjsbdjfsdjfhs |
| String |requestUID          |Yes   |Request Unique ID                      |d1f1d904-a599-4c28-b258-076f36eb63eb |
| String |resourceOwnerId     |Yes   |Resource Owner ID - Online or Mobile   | 001 |

###### Channel

```properties
apiKey: sdbfjsdfbjhdsfd
apiSecret: sjdbfjshdbfjsdhbfjsdb
```

----

## [POST] /v1/origins/applys
Invoking this endpoint allows client to validate his/her prequalification of credit card application

#### Request Mapping
The following are the minimum required fields in the request:

| Request| DataType   |           Field Name|Mandatory |           Description              | Sample Value |
| ------ | ---------- | ----------------------- | ----------| -------------------------------------- | ------- |
| Body   | String | token                      | Yes | Unique token (mandatory if bank initiated) |

###### Sample Request using Token
```JSON
{
    "token": "vsvdhgsvdfsdf",
}
```


#### Response Mapping
Returns the mobile information of the customer

| Response | DataType   |      Field          |          Description              | Sample Value |
| -------- | ---------- | ----------------------- | -------------------------------------- | ------- |
| Header | String |transactionId         | TransactionId from the preprocess leg  | 12027c4f-5146-4bfd-b563-1887104a96 |
| Body   | String |mobileNumber          | Masked mobile number of the customer | +91770****064 |
| Body   | String | token    | Customer Unique token | vsvdhgsvdfsdf |
| Body   | String | firstName    | Prequalified Customer First Name | Hanabi |


###### Successful Response
    + Headers
        transactionId: 12027c4f-5146-4bfd-b563-1887104a96

```json
{
    "status": "success",
    "code": "0",
    "description": "Success",
    "body": {
        "mobileNumber": "+91770****064",
        "customerCCPQToken": "f83df477843a93be1440b95ba29127f8091bd3fad4f0f6bed7529504fa93b1a080b8a8b381548d0b36947dece006b588",
        "firstName": "Angela"
    }
}
```

---
