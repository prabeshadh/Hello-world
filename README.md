# PICK N DROP EXTERNAL API DOCUMENTATION #
--------------------------------------------
### PND EXTERNAL API COLLECTION ###
--------------------------------------------
#### **What is PND External API?** ####

#### PND External API service gives you the capability to integrate your online system with PND portal. Our API services currently provides you the capability to ####
<h5>

- ⦗✔⦘ Fetch particular order details 
- ⦗✔⦘ Fetch particular order log or order status
- ⦗✔⦘ Fetch order comments
- ⦗✔⦘ Create new comment for order
- ⦗✔⦘ Create a Pickup list

</h5>

##### API Limits #####

<h5>

> 	Pickup list: 100 per day 

> 	Order view details (Details, Comment, Status): 6000 per day (prod)/1000 per day (dev)  

</h5>


##### Every vendor is provided with an API token key, x-api-key, secret-key & api-key. Use these keys to make an api request into the server.
##### If you forgot the x-api-key, secret-key & api-key or want to request a new x-api-key, secret-key & api-key, contact our IT Admin. #####

-------------------------------------------------------------------------------------------------------------------

### Get Order Details ###
<h5>

**The Endpoint allows us to get the details of the order in our system. These details are the same as the details that you see in our system when you view the order page.** </h5>

<h5>

``` 
Dev: https://externalapi.pickndropnepal.com/api/v1/dev/orders?code=order_code 
```
</h5>

``` 
Prod: https://externalapi.pickndropnepal.com/api/v1/prod/orders?code=order_code 
```


##### **Headers** #####

`secret-key` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `your secret-key`

` x-api-key ` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `your x-api-key `

` x-api-key ` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `your api-keys `

` token     ` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `default value<AUTH>`
	

##### **Prams** #####

`code` &emsp; &emsp; &emsp; `order_code` &emsp; &emsp; &emsp;  `your order code in system`

##### **Example:** #####

```

curl -X GET https://externalapi.pickndropnepal.com/api/v1/dev/orders?code=AO0220527-230
-H "token: AUTH" -H "api-key: <your api-key>" -H "x-api-key: <your x-api-key>" 
-H "secret-key: <your-secret key>"

```
##### **Result:** #####

``` json
{
    "success": true,
    "status_code": 200,
    "order_code": "AO0220527-230",
    "cod_amount": 123.5,
    "delivery_charge": 100.0,
    "current_status": "RECEIVED",
    "last_updated_at": "2022-05-27 20:04:47"
}
```
-------
### Get Order Status ###
**The Endpoint allows us to get the status of the particular orders in our system. The Api will provide all the status done in a particular order. Status will be in a descending order.**

```
DEV: https://externalapi.pickndropnepal.com/api/v1/dev/orders/statuslogs?code=order_code
```
```
PROD: https://externalapi.pickndropnepal.com/api/v1/prod/orders/statuslogs?code=order_code
```
##### **Headers** #####

`secret-key` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `your secret-key`

` x-api-key ` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `your x-api-key `

` x-api-key ` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `your api-keys `

` token     ` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `default value<AUTH>`

##### **Prams** #####

`code` &emsp; &emsp; &emsp; `order_code` &emsp; &emsp; &emsp;  `your order code in system`
##### **Example:** #####
```

curl -X GET https://externalapi.pickndropnepal.com/api/v1/dev/orders/statuslogs?code=AO0220527-230 
-H "token: AUTH" -H "api-key: <your api-key>" -H "x-api-key: <your x-api-key>" 
-H "secret-key: <your-secret key>"

```
##### **Result:** #####
```json
{
    "status_code": 200,
    "success": true,
    "logs": [
        {
            "order_code": "AO0220527-230",
            "status": "RECEIVED",
            "created_at": "2022-05-27 20:04:45",
            "remarks": "item received"
        }
    ]
}
```
----------

### Get Order Comment ###
**The Endpoint allows us to get the comment of the particular orders in our system. The Api will provide all the comments done in a particular order. Comment will be in a descending order.**
```
DEV: https://externalapi.pickndropnepal.com/api/v1/dev/orders/comments?code=order_code
```
```
PROD: https://externalapi.pickndropnepal.com/api/v1/prod/orders/comments?code=order_code
```
##### **Headers** #####

`secret-key` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `your secret-key`

` x-api-key ` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `your x-api-key `

` x-api-key ` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `your api-keys `

` token     ` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `default value<AUTH>`

##### **Prams** #####
`code` &emsp; &emsp; &emsp; &emsp; `order_code` &emsp; &emsp; &emsp; &emsp;  `your order code in system`
##### Example: #####
```

curl -X GET https://externalapi.pickndropnepal.com/api/v1/dev/orders/comments?code=AO0220527-230 
-H "token: AUTH" -H "api-key: <your api-key>" -H "x-api-key: <your x-api-key>" 
-H "secret-key: <your-secret key>"

```
##### **Result:** #####
```json
{
    "success": true,
    "status_code": 200,
    "comments":
    [
        {
            "order_code": "AO0220527-230",
            "comments": "test comment",
            "commented_by":
            {
                "id": "C99161D2D1FB43F1A0196479AE731FEC",
                "full_name": "A one",
                "email": "tobeupdated@pickndropnepal.com"
            },
             "commented_type": "VENDOR",
             "posted_date_time": "2022-05-27 20:36:19"
        }
    ]
}
```
----------

### **Possible Error in Get Requests:** ###
```
* When token, x-api-key, api-key & secret-key is not provided:
Response Status 401:
{
    "message": "Unauthorized"
}
* When Unknown order Code Provided:
Response status 404:
{
    "message": "Either order code is not found in the system or not received yet!",
    "success": false,
}
* When comments are not found in the system
{
    "success": False,
    "status_code": 404,
    "message": "Comments not available right now!"
}
* When logs not found in the system
{
    "success": False,
    "status_code": 404,
    "message": "Order Logs are not available right now!"
}
* Internal Server Error--> When server has problem
* Limit Exceeded --> when exceed the limit of access
* Forbidden --> When x-api-key is not valid

```
### Post Create Pickup List ###
**This endpoint allows you to create a pickup list from your system. Vendors must provide necessary details from their end to create a pickup list through this endpoint.**
```
DEV: https://externalapi.pickndropnepal.com/orders/v1/dev/pickuplist
```
```
PROD: https://externalapi.pickndropnepal.com/orders/v1/prod/pickuplist
```
**Headers**
`secret-key` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;   `your secret-key`

` x-api-key ` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `your x-api-key `

` x-api-key ` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `your api-keys `

` token     ` &emsp; &emsp; &emsp; &emsp; &emsp; &emsp;  `default value<AUTH>`

**Prams**
| Parameters 	 | Requirement | Description 
|----------------|-------------|-------------------	 	
| is_paid		 |	required   |	Whether the customer has paid the COD of package or not
|package_price	 |  required   |	Price of the package	



