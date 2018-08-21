# GraphQL-database
 This is an example graphQL database, running a JSON server API, and a graphQL server with a simple browser interface. Creating it has helped me understand GraphQL a little better while also satisfying my curioisity to create a functional customer database for an online store.

### To Run
Open two terminal screens and input the following commands, one in each terminal.

`npm run dev:server`  to start the graphQL server on localhost:4000

`npm run json:server` to start our database API with stored data on localhost:3000

Congratulations! You're up and running.
You can now navigate to `localhost:3000/customers` to view all customers that have been added to the database or navigate to `localhost:4000/graphql` and make queries using the GraphiQL browser interface. 


###Queries and Mutations
Unlike interacting with multiple endpoints in a typical REST API, graphQL only utilizes one endpoint that accepts queries and mutations and returns data objects. But it is structured in such a way as to return exactly which fields you're asking for in the query. 


#Query customer a customer by id and retrieve all fields you're asking for :
```
{
  customer(id:"1"){
    name,
    age,
    email
  }
}
```
    which returns
                    ```
                    {
                    "data": {
                        "customer": {
                        "name": "Andrew Carr",
                        "age": 29,
                        "email": "real@email.com"
                        }
                      }
                    }
                    ```
#Or query all customers for specific fields: 
```
{
  customers {
    name,
    age
  }
}
```

Aside from queries, mutations are also available to make changes to the data.
Here you can addCustomer, editCustomer, or deleteCustomer.


#Add a new customer.
    ```
mutation{
  addCustomer(name:"John Doe", email:"johnD@hello.com", age:25){
    id,
    name,
    email,
    age
  }
}
    ```


#Edit a customer.
```
mutation{
  editCustomer(id:"xn761g" name:"John Doe"){
    id,
    name,
  }
}

```
 Notice the id being passed as an argument is required to identify the existing customer, but every other argument passed in the editCustomer mutation will be updated. 


#Delete a Customer. 
```
mutation{
  deleteCustomer(id: "808"){
    id
  }

}
```
Notice by requesting the id field in the curlybraces returns the response "null" signifying the customer with the requested id has been deleted. If it returns an error, then the requested id doesn't exist in the database.


Further documentation on GraphQL queries can be found <a href="https://graphql.org/learn/queries/">here</a>.