# PICK N DROP EXTERNAL API DOCUMENTATION #
--------------------------------------------
### PND EXTERNAL API COLLECTION ###
--------------------------------------------
#### What is PND External API? ####

###### PND External API service gives you the capability to integrate your online system with PND portal. Our API services currently provides you the capability to #####

- ⦗✔⦘ Fetch particular order details
- ⦗✔⦘ Fetch particular order log or order status
- ⦗✔⦘ Fetch order comments
- ⦗✔⦘ Create new comment for order
- ⦗✔⦘ Create a Pickup list

##### API Limits #####


``` Pickup list: 100 per day ```

``` Order view details (Details, Comment, Status): 6000 per day (prod)/1000 per day (dev)  ```

###### Every vendor is provided with an API token key, x-api-key, secret-key & api-key. Use these keys to make an api request into the server. ######
###### If you forgot the x-api-key, secret-key & api-key or want to request a new x-api-key, secret-key & api-key, contact our IT Admin. ######

-------------------------------------------------------------------------------------------------------------------

### Get Order Details ###

**The Endpoint allows us to get the details of the order in our system. These details are the same as the details that you see in our system when you view the order page.**

``` Dev: https://externalapi.pickndropnepal.com/api/v1/dev/orders?code=order_code ```

``` Prod: https://externalapi.pickndropnepal.com/api/v1/prod/orders?code=order_code ```

##### Headers #####

``` secret-key > > > <your secret-key> ```

``` x-api-key  <your x-api-key> ```

``` api-key  <your api-keys> ```

``` token  default value<AUTH> ```	

##### Headers #####

``` code  order_code  your order code in system ```
 