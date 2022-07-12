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

>  ``` Pickup list: 100 per day ```



> `	Order view details (Details, Comment, Status): 6000 per day (prod)/1000 per day (dev)  `

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

```
secret-key									your secret-key
```

```
x-api-key  									your x-api-key
```

``` 
api-key 									your api-keys 
```

``` 
token 										default value<AUTH>
```
	

##### **Prams** #####

```
code 				order_code					your order code in system
```


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

```
secret-key									your secret-key
```

```
x-api-key  									your x-api-key
```

``` 
api-key 									your api-keys 
```

``` 
token 										default value<AUTH>
```
##### **Prams** #####

```
code 				order_code					your order code in system
```

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

```
secret-key									your secret-key
```

```
x-api-key  									your x-api-key
```

``` 
api-key 									your api-keys 
```

``` 
token 										default value<AUTH>
```

##### **Prams** #####

```
code 			    order_code					your order code in system
```

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
--------------------------------
### Post Create Pickup List ###
**This endpoint allows you to create a pickup list from your system. Vendors must provide necessary details from their end to create a pickup list through this endpoint.**
```
DEV: https://externalapi.pickndropnepal.com/orders/v1/dev/pickuplist
```
```
PROD: https://externalapi.pickndropnepal.com/orders/v1/prod/pickuplist
```
**Headers**

```
secret-key									your secret-key
```

```
x-api-key  									your x-api-key
```

``` 
api-key 									your api-keys 
```

``` 
token 										default value<AUTH>
```

**Prams**
| Parameters 	 | Requirement | Description 
|----------------|-------------|-------------------	 	
| is_paid		 |	required   |	Whether the customer has paid the COD of package or not
|package_price	 |  required   |	Price of the package	
|customer_fullname| required   |	Customer name
|customer_primary_mobile_Number| required|	Customer mobile number
|customer_Secondary_mobile_Number|	Optional|	Customer secondary mobile number
|customer_location|	required|	Customer address
|dest_branch_code|	required|	Destination branch name

**Example:**
```
curl -X POST -H "Content-Type: application/json" -H "api-key:<your api-key>"
 -H "secret-key:<your secret-key>" -H "x-api-key:<your x-api-key>" 
 -H "token: AUTH" https://externalapi.pickndropnepal.com/orders/v1/dev/pickuplist
--data-raw "{
    "orders": [
        {
            "is_paid":true,
            "package_price":123.50,
            "customer_full_name":"John Doe",
            "customer_primary_mobile_number":"9801235800",
            "customer_secondary_mobile_number":"",
            "customer_location":"Gushinghal,Sanepa, Lalitpur",
            "dest_branch_code":"KTM"
        }
    ]
}"
```
**Result:**
```json
{
    "message": "Order list created successfully",
    "success": true,
    "status_code": 201,
    "order_codes": 
        [
           "ordercode1"
        ]
}
```
------------------------------
### Post Create an order comment ###
**This endpoint allows you to create a comment from your system. Vendor must provide necessary details from their end to create a comment through this endpoint.**
```language
DEV: https://externalapi.pickndropnepal.com/api/v1/dev/orders/comment
```
```
PROD: https://externalapi.pickndropnepal.com/api/v1/prod/orders/comment
```
##### **Headers** #####

```
secret-key									your secret-key
```

```
x-api-key  									your x-api-key
```

``` 
api-key 									your api-keys 
```

``` 
token 										default value<AUTH>
```

**Prams**

| Parameters | Requirement | Description 
|------------|-------------|----------------
|order_code |	required	|Order code in system
|comment	|required	|Text comment for the package

**Example:**
```
curl -X POST -H "Content-Type: application/json" 
-H "api-key:<your api-key>" -H "secret-key:<your secret-key>" 
-H "x-api-key:<your x-api-key>" -H "token: AUTH" 
https://externalapi.pickndropnepal.com/api/v1/dev/orders/comment
--data-raw '{
    “comment”: "test comment",
    "order_code":" AO0220527-230"
}'

```
**Result:**
```json
{
    "success": true,
    "status_code":201,
    "message": "Comment successfully posted!"
}
```
--------------------------------------
**Errors when fields are missing:**
```
*When order code in not found in the system
{
     "message": "Unauthorized!",
     "success": False,
     "status_code": 401
}
*When payload does not contain requested parameters 
{
     "message": "Please pass order_code and comment in request payload!",
     "success": false,
     "status_code": 400
}
* When provided api-key doesn’t belong to the user
{
     "message": "Unauthorized!",
     "success": False,
     "status_code": 401
}
*When orders item payload does not contain require parameters
{
     "message": "Some item does not have is_paid, package_price, 
     customer_full_name, customer_primary_mobile_number, 
     customer_secondary_mobile_number, dest_branch_code and customer_location, fields and values",
     "success": False,
     "status_code": 400
}
*When length of orders array in payload is not in between 0 and 50
{
     "message": "Orders size must be in between 0 and 50.",
     "success": False,
     "status_code": 400
}
*When order attributes in payload is not array
{
     "message": "Orders data must be in Array!",
     "success": False,
     "status_code": 400
}
*When payload not contains orders
{
     "message": "Request payload must have orders. Please pass required item values.",
     "success": False,
     "status_code": 400
}
*When server has problem
{
     "status_code": 500,
     "success": False,
     "message": "Something went wrong, Please try again later."
}
```
*Please use this api endpoints very carefully.*  

*No Spamming or running scripts to overload the server.*

-----------------------------------------------------------


![](logo.png)

**Phone: - 9801235800**

**Gurshingal, Lalitpur**

[**Pick N Drop**](http://www.pickndropnepal.com)

<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<!-- Add icon library -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
<style>
.btn {
  background-color: DodgerBlue;
  border: none;
  color: white;
  padding: 12px 30px;
  cursor: pointer;
  font-size: 20px;
}

/* Darker background on mouse-over */
.btn:hover {
  background-color: RoyalBlue;
}
</style>
</head>
<body>
<a href="/Hello-world/README.md" download=>
<button class="btn"><i class="fa fa-download"></i> Download</button>
</body>
</html>





