# microservices-shop


## Services


### Discovery  Service (Eureka)
    
http://localhost:8761/


### Microservice Product
GET

     http://localhost:8090/products 

POST

    curl  --request POST 'localhost:8090/products' \
    --header 'Content-Type: application/json' \
    --data-raw '{
    "name":"Naikiss",
    "description":"Zapatos caros",
    "stock":4,
    "price":330,
    "category":{"id":1,"name": "shoes"}
    }'
### Microservice Customer
GET

    ttp://localhost:8091/customers

POST

    curl --request POST 'localhost:8091/customers' \
    --header 'Content-Type: application/json' \
    --data-raw '
        {
            "numberID":"40408083",
            "firstName": "Pedro",
            "lastName": "Tulio",
            "email": "pedroTulio@gmail.com",
            "photoUrl": "",
            "region": {
                "id": 1
            }
        }
    '

### Microservice Shopping
GET
    http://localhost:8092/invoices/1

POST

    curl  --request POST 'localhost:8092/invoices' \
    --header 'Content-Type: application/json' \
    --data-raw '{

        "numberInvoice": "002",
        "description": "Factura venta",
        "customerId": 1,
        "items": [
            {
                "quantity": 1,
                "priceItem": 178.89,
                "productId": 1
            },
    
            {
                "quantity": 2,
                "priceItem": 40.06,
                "productId": 3
            }
        ]
    }'

### Gateway Service 

Customer

    GET http://localhost:8085/customers

Products

    GET http://localhost:8085/products


Invoices

    GET http://localhost:8085/invoices
