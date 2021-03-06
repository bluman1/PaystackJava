# PaystackJava
A Java based API wrapper for the Paystack API


A Java API wrapper for the facilitation of quick and easy development and integration of Java based applications with the the Paystack API.

PaystackJava removes the grunt involved in consuming the Paystack API and implements a diverse array of helper methods to enable rapid prototyping and testing. 

## Links
- Project: https://github.com/IyanuAdelekan/PaystackJava


## Getting started
### Dependencies:
- Unirest (Installation procedures here: https://github.com/Mashape/unirest-java#installing)

### PaystackJava installation:
- Download PaystackJava
- Add jar file as a Module to your Java project:
- On Intellij IDEA: File -> Project Structure -> Modules -> Dependencies Tab -> Add -> JARs or Directories -> Attach jar
- On Netbeans: Project properties -> Libraries -> Compile -> ADD JAR/folder -> Add Jar


## Examples

To create a new Paystack customer:
```java
Customers customers = new Customers();
customers.createCustomer("[email]","[first_name]","[last_name]","[phone]","[metadata]");
```

To fetch a customer
```java
Customers customers = new Customers();
customers.fetchCustomer("[id_or_customer_code]");
```

But what if you want to get the server JSON respone?
```java
Customers customers = new Customers();
JSONObject jsonObject = new JSONObject(customers.fetchCustomer("[id_or_customer_code]"));
```

Want to initialize a Paystack transaction?
```java
Transactions transactions = new Transactions();
transactions.initializeTransaction("[reference]","[amount]","[email]","[plan]","[callback_url]");
```

Don't like using strings to make your API requests?
```java
ApiQuery apiQuery = new ApiQuery();
apiQuery.putParams("name","Offering collections");
new Pages().createPage(apiQuery);
```

Or maybe you just love using HashMaps
```java
HashMap<String,Object> query = new HashMap();
query.put("name","Offering collections");
new Pages().createPage(query);
```


**Remember to always shut down the API connection once you are done making requests**
#### PaystackJava utilizes a background event loop and your Java application won't be able to exit until you manually shutdown all the threads by invoking:
```java
ApiConnection.shutDown();
```

## NOTE
### PaystackJava utilizes a Keys.json file for the management of api key resources. This file must be placed in your root project directory and has the following structure:
```json
{
  "API_KEYS":{
    "KEY_IN_USE": "sk_test_xxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
    "TEST_SECRET_KEY": "sk_test_xxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
    "TEST_PUBLIC_KEY": "pk_test_xxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
    "LIVE_SECRET_KEY": "sk_live_xxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
    "LIVE_PUBLIC_KEY": "pk_live_xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
  }
}
```
### The value attached to KEY_IN_USE is the value used for Authorization by PaystackJava

## Utilities at a glance
### ApiConnection {Class}:
#### methods:
- connectAndQuery [JSONObject]
- connectAndQueryWithGet [JSONObject]
- connectAndQueryWithPut [JSONObject]
- shutDown [void]

### ApiQuery {Class}:
#### methods:
- newQuery [void]
- putParams [JSONObject]

### PaystackInline {Class}:
#### methods:
- paystackStandard [JSONObject]
- verifyTransactions [JSONObject]
- chargeReturningCustomer [JSONObject]
- updateCustomer [JSONObject]

### Customers {Class}:
#### methods:
- createCustomer [JSONObject]
- listCustomers [JSONObject]
- fetchCustomer [JSONObject]
- updateCustomer [JSONObject]

### Customers {Class}:
#### methods:
- createCustomer [JSONObject]
- listCustomers [JSONObject]
- fetchCustomer [JSONObject]
- updateCustomer [JSONObject]

### Transactions {Class}:
#### methods:
- initializeTransaction [JSONObject]
- verifyTransaction [JSONObject]
- listTransactions [JSONObject]
- fetchTransaction [JSONObject]
- chargeAuthorization [JSONObject]
- chargeToken [JSONObject]
- exportTransactions [JSONObject]

### Plans {Class}:
#### methods:
- listPlans [JSONObject]
- fetchPlan [JSONObject]
- updatePlan [JSONObject]
- updateCustomer [JSONObject]

### Pages {Class}:
#### methods:
- createPage [JSONObject]
- listPages [JSONObject]
- fetchPage [JSONObject]
- updatePage [JSONObject]

License
----

MIT License
