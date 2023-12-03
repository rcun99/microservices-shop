# microservices-shop


## Services


### Discovery  Service (Eureka)
    
http://localhost:8761/


### Microservice Product
GET

    curl -X GET http://localhost:8090/products  -H 'Accept: application/json' | jq '.'

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

    curl -X GET http://localhost:8091/customers    -H 'Accept: application/json' | jq '.'

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
    curl -X GET http://localhost:8092/invoices/1 -H 'Accept: application/json' | jq '.'

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

    curl -X GET http://localhost:8080/customers    -H 'Accept: application/json' | jq '.'

Products

    curl -X GET http://localhost:8080/products  -H 'Accept: application/json' | jq '.'


Invoices

    curl -X GET http://localhost:8080/invoices/1 -H 'Accept: application/json' | jq '.'
