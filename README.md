# 🛒 Simple Grocery Store API

This API allows you to place a grocery order which will be ready for pick-up in the store.  
You can browse products, manage carts, and create orders through the API.

Base URL:https://simple-grocery-store-api.click/
---

## 📂 Endpoints

- **Status**
- **Products**
  - Get all products
  - Get a product
- **Cart**
  - Get a cart
  - Get cart items
  - Create a new cart
  - Add an item to cart
  - Modify an item in the cart
  - Replace an item in the cart
  - Delete an item in the cart
- **Orders**
  - Get all orders
  - Get a single order
  - Create a new order
  - Update an order
  - Delete an order
- **API Authentication**
  - Register a new API client
## ✅ Status

**GET** `/status`  

Returns the status of the API.  

**Example response**:
```json
{
  "status": "UP"
}
status: UP → API is running

Any other response → API not functioning correctly

s
Get all products

GET /products

Returns a list of products from the inventory.

Query Parameters:

Name	Type	Required	Description
category	string	No	meat-seafood, fresh-produce, candy, bread-bakery, dairy, eggs, coffee
results	integer	No	Number of results (1–20). Default = 20
available	boolean	No	Filter by availability

Status Codes:

200 OK → Success

400 Bad Request → Invalid parameters

Example response:

[
  {
    "id": 4643,
    "category": "coffee",
    "name": "Starbucks Coffee Variety Pack, 100% Arabica",
    "inStock": true
  },
  {
    "id": 4646,
    "category": "coffee",
    "name": "Ethical Bean Medium Dark Roast, Espresso",
    "inStock": true
  }
]

Get a product

GET /products/:productId

Returns a single product from the inventory.

Parameters:

Name	Type	In	Required	Description
productId	integer	path	Yes	ID of the product
product-label	boolean	query	No	Return label in PDF

Status Codes:

200 OK → Success

404 Not Found → Product not found

🛒 Cart
Get a cart

GET /carts/:cartId

Returns a cart by ID.

Status Codes:

200 OK → Success

404 Not Found → Cart not found

Get cart items

GET /carts/:cartId/items

Returns all items in the cart.

Create a new cart

POST /carts

Creates a new cart and returns the cartId.

Example response:

{
  "created": true,
  "cartId": "bx0-ycNjqIm5IvufuuZ09"
}

Add an item to cart

POST /carts/:cartId/items

Request body:

{
  "productId": 1234,
  "quantity": 2
}


Status Codes:

201 Created → Item added

400 Bad Request → Invalid parameters

Modify an item in the cart

PATCH /carts/:cartId/items/:itemId

Request body:

{
  "quantity": 3
}

Replace an item in the cart

PUT /carts/:cartId/items/:itemId

Request body:

{
  "productId": 1234,
  "quantity": 1
}

Delete an item in the cart

DELETE /carts/:cartId/items/:itemId

Removes item from the cart.

📦 Orders
Get all orders

GET /orders

Requires Authorization header.

Get a single order

GET /orders/:orderId

Requires Authorization header.

Create a new order

POST /orders

Request body:

{
  "cartId": "ZFe4yhG5qNhmuNyrbLWa4",
  "customerName": "John Doe"
}

Update an order

PATCH /orders/:orderId

Request body:

{
  "customerName": "Jane Doe",
  "comment": "Please deliver between 5–6 PM"
}

Delete an order

DELETE /orders/:orderId

Requires Authorization header.

🔐 API Authentication

Some endpoints require authentication via Bearer Token.

Example header:

Authorization: Bearer YOUR_TOKEN

Register a new API client

POST /api-clients

Request body:

{
  "clientName": "Postman Demo Client",
  "clientEmail": "example@test.com"
}


Status Codes:

201 Created → Client registered, token returned

400 Bad Request → Invalid request

409 Conflict → Email already registered

🚀 Getting Started

Clone this repo

Import collection into Postman

Test endpoints using the provided base URL

