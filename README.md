# 🛒 E-Commerce API Documentation

This project provides a Postman collection for testing an **E-Commerce API** that supports products, carts, and orders.  
It includes endpoints for browsing products, managing shopping carts, and handling orders with authentication.

---

## 📌 Endpoints Overview

### ✅ Status
- **GET /status**  
  Returns the status of the API.  
  Example response:
  ```json
  {
    "status": "UP"
  }
🛍️ Products

GET /products – Get all products (supports filters: category, results, available)

GET /products/:productId – Get a single product by ID

🛒 Cart

GET /carts/:cartId – Retrieve a cart

GET /carts/:cartId/items – Retrieve cart items

POST /carts – Create a new cart

POST /carts/:cartId/items – Add an item to cart

PATCH /carts/:cartId/items/:itemId – Modify an item in the cart

PUT /carts/:cartId/items/:itemId – Replace an item in the cart

DELETE /carts/:cartId/items/:itemId – Delete an item from the cart

Example: Add item to cart

{
  "productId": 1234,   // Unique product identifier
  "quantity": 2        // Quantity of the product (default = 1)
}

📦 Orders

GET /orders – Get all orders (requires authentication)

GET /orders/:orderId – Get a single order

POST /orders – Create a new order

PATCH /orders/:orderId – Update an order

DELETE /orders/:orderId – Delete an order

Example: Create an order

{
  "cartId": "ZFe4yhG5qNhmuNyrbLWa4", // The cart being ordered
  "customerName": "John Doe",        // Customer’s name
  "comment": "Leave at the front door" // Optional comment
}

🔑 API Authentication

Some endpoints (e.g., Orders) require authentication via a Bearer Token.

POST /api-clients – Register a new API client

Example request body:

{
  "clientName": "Hazem’s Client",     // Your client/app name
  "clientEmail": "hazem@example.com" // Fake/real email (not stored)
}


Response will include the access token, which must be sent in the header:

Authorization: Bearer YOUR_TOKEN

⚡ How to Use in Postman

Import this collection into Postman.

Create an environment with variables such as:

baseUrl – The API base URL

token – Your authentication token

cartId – A test cart ID

Test endpoints step by step:

Check /status

Browse products

Create cart & add items

Place an order

📖 Status Codes

200 OK – Request successful

201 Created – Resource created successfully

204 No Content – Action successful, no response body

400 Bad Request – Invalid request/parameters

401 Unauthorized – Missing or invalid authentication

404 Not Found – Resource not found

409 Conflict – Duplicate client registration

👨‍💻 Author

Hazem – API Testing & Documentation


👉 This file is **ready to be added** to your GitHub repo under `README.md`.  

Would you like me to also add **screenshots from Postman** (requests/responses) into this README so it looks more visual for stakeholders?

You said:
please generate Readme.md file to i can copy and past in github reame
ChatGPT said:

Got it 👍 — here’s the ready-to-copy README.md file you can paste directly into GitHub:

# 🛒 E-Commerce API Documentation

This project provides a Postman collection for testing an **E-Commerce API** that supports products, carts, and orders.  
It includes endpoints for browsing products, managing shopping carts, and handling orders with authentication.

---

## 📌 Endpoints Overview

### ✅ Status
- **GET /status**  
  Returns the status of the API.  
  Example response:
  ```json
  {
    "status": "UP"
  }

🛍️ Products

GET /products – Get all products (supports filters: category, results, available)

GET /products/:productId – Get a single product by ID

🛒 Cart

GET /carts/:cartId – Retrieve a cart

GET /carts/:cartId/items – Retrieve cart items

POST /carts – Create a new cart

POST /carts/:cartId/items – Add an item to cart

PATCH /carts/:cartId/items/:itemId – Modify an item in the cart

PUT /carts/:cartId/items/:itemId – Replace an item in the cart

DELETE /carts/:cartId/items/:itemId – Delete an item from the cart

Example: Add item to cart

{
  "productId": 1234,   // Unique product identifier
  "quantity": 2        // Quantity of the product (default = 1)
}

📦 Orders

GET /orders – Get all orders (requires authentication)

GET /orders/:orderId – Get a single order

POST /orders – Create a new order

PATCH /orders/:orderId – Update an order

DELETE /orders/:orderId – Delete an order

Example: Create an order

{
  "cartId": "ZFe4yhG5qNhmuNyrbLWa4", // The cart being ordered
  "customerName": "John Doe",        // Customer’s name
  "comment": "Leave at the front door" // Optional comment
}

🔑 API Authentication

Some endpoints (e.g., Orders) require authentication via a Bearer Token.

POST /api-clients – Register a new API client

Example request body:

{
  "clientName": "Hazem’s Client",     // Your client/app name
  "clientEmail": "hazem@example.com" // Fake/real email (not stored)
}


Response will include the access token, which must be sent in the header:

Authorization: Bearer YOUR_TOKEN

⚡ How to Use in Postman

Import this collection into Postman.

Create an environment with variables such as:

baseUrl – The API base URL

token – Your authentication token

cartId – A test cart ID

Test endpoints step by step:

Check /status

Browse products

Create cart & add items

Place an order

📖 Status Codes

200 OK – Request successful

201 Created – Resource created successfully

204 No Content – Action successful, no response body

400 Bad Request – Invalid request/parameters

401 Unauthorized – Missing or invalid authentication

404 Not Found – Resource not found

409 Conflict – Duplicate client registration

👨‍💻 Author

Hazem – API Testing & Documentation
