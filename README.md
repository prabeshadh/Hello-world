# PICK N DROP EXTERNAL API DOCUMENTATION #
--------------------------------------------
### PND EXTERNAL API COLLECTION ###
--------------------------------------------
#### What is PND External API? ####

##### PND External API service gives you the capability to integrate your online system with PND portal. Our API services currently provides you the capability to ####
<h5>

- ⦗✔⦘ Fetch particular order details 
- ⦗✔⦘ Fetch particular order log or order status
- ⦗✔⦘ Fetch order comments
- ⦗✔⦘ Create new comment for order
- ⦗✔⦘ Create a Pickup list

</h5>

##### API Limits #####


> 	Pickup list: 100 per day 

> 	Order view details (Details, Comment, Status): 6000 per day (prod)/1000 per day (dev)  

##### Every vendor is provided with an API token key, x-api-key, secret-key & api-key. Use these keys to make an api request into the server. #####
##### If you forgot the x-api-key, secret-key & api-key or want to request a new x-api-key, secret-key & api-key, contact our IT Admin. #####

-------------------------------------------------------------------------------------------------------------------

### Get Order Details ###
<h5>

**The Endpoint allows us to get the details of the order in our system. These details are the same as the details that you see in our system when you view the order page.** </h5>

<h5>

``` Dev: https://externalapi.pickndropnepal.com/api/v1/dev/orders?code=order_code ```
</h5>

``` Prod: https://externalapi.pickndropnepal.com/api/v1/prod/orders?code=order_code ```


##### Headers #####
<code>
	<style>
div {
  background-color: lightgrey;
  width: 300px;
  border: 1px lightgrey;
  }
</style>

<div>
 secret-key &emsp; &emsp; &emsp;  your secret-key
</div>
</code>

` x-api-key ` &emsp; &emsp; &emsp;  `your x-api-key `

` x-api-key ` &emsp; &emsp; &emsp;  `your api-keys `

` token     ` &emsp; &emsp; &emsp;  `default value<AUTH>`
	

##### Headers #####

`  code  order_code  your order code in system `
 














