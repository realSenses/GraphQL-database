# GraphQL-database
 This is an example graphQL database, running a JSON server API, and a graphQL server with a simple browser interface. Creating it has helped me understand GraphQL a little better while also satisfying my curiousity to create a functional customer database for an online store.

## To Run
Open two terminal screens and input the following commands, one in each terminal.

`npm run dev:server`  to start the graphQL server on localhost:4000

`npm run json:server` to start our database API with stored data on localhost:3000

Congratulations! You're up and running.
You can now navigate to `localhost:3000/customers` to view all customers that have been added to the database or navigate to `localhost:4000/graphql` and make queries using the GraphiQL browser interface. 


## GraphQL 
 The GraphQL Server leverages two types of requests: simple queries that retrieve data from the JSON server, and mutations that change the data. In the GraphiQL browser, you can input both, and view the responses.

### Query a customer by id and retrieve requested fields:
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
### Or request all customers for specified fields: 
```
{
  customers {
    name,
    age
  }
}
```

##Mutations

### Add a new customer.
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

### Edit a customer.
```
mutation{
  editCustomer(id:"xn761g" name:"John Doe"){
    id,
    name,
  }
}

```
 Notice the id being passed as an argument is required to identify the existing customer, but every other argument passed in the editCustomer mutation will be updated. 


### Delete a Customer. 
```
mutation{
  deleteCustomer(id: "808"){
    id
  }

}
```
Notice by requesting the id field in the curlybraces, the response will be "null" which signifies the customer with the requested id has been deleted. If it returns an error, then the requested id does not exist in the database.


Further documentation on GraphQL queries can be found <a href="https://graphql.org/learn/queries/">here</a>.
