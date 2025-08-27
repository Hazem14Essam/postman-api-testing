# 🛒 Simple Grocery Store API


This repository contains a **Postman collection** for testing an E-Commerce API.  
It allows you to explore products, manage shopping carts, and handle orders with authentication.  
  

**Base URL:**  
```
https://simple-grocery-store-api.click/
```

---

## 📂 Endpoints Overview

- **Status**
  - Check API health
- **Products**
  - Get all products
  - Get product details
- **Cart**
  - Create and manage carts
  - Add, update, replace, or delete items
- **Orders**
  - Create, view, update, and delete orders
- **Authentication**
  - Register API clients and get access tokens

---

## ✅ Status

### **GET /status**

Returns the health status of the API.

**Example Response**
```json
{
  "status": "UP"
}
```

- `UP` → API is running  
- Any other response → API not functioning correctly  

---

## 🛍️ Products

### **GET /products**

Returns a list of products from the inventory.

| Parameter   | Type     | Required | Description |
|-------------|----------|----------|-------------|
| category    | string   | No       | e.g. meat-seafood, fresh-produce, coffee |
| results     | integer  | No       | Limit number of results (1–20). Default = 20 |
| available   | boolean  | No       | Filter only available items |

**Status Codes**  
- `200 OK` → Success  
- `400 Bad Request` → Invalid parameters  

**Example Response**
```json
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
```

---

### **GET /products/:productId**

Fetches details of a single product.

| Parameter   | Type     | In   | Required | Description |
|-------------|----------|------|----------|-------------|
| productId   | integer  | path | Yes      | Unique product ID |
| product-label | boolean | query | No     | If true, returns product label in PDF |

**Status Codes**  
- `200 OK` → Success  
- `404 Not Found` → Product not found  

---

## 🛒 Cart

### **POST /carts**

Creates a new shopping cart.

**Example Response**
```json
{
  "created": true,
  "cartId": "bx0-ycNjqIm5IvufuuZ09"
}
```

---

### **GET /carts/:cartId**

Retrieve a cart by ID.  

- `200 OK` → Success  
- `404 Not Found` → Cart not found  

---

### **POST /carts/:cartId/items**

Add an item to the cart.

**Request Body**
```json
{
  "productId": 1234,
  "quantity": 2
}
```

**Status Codes**  
- `201 Created` → Item added  
- `400 Bad Request` → Invalid parameters  

---

### **PATCH /carts/:cartId/items/:itemId**

Modify an existing cart item.

```json
{
  "quantity": 3
}
```

---

### **PUT /carts/:cartId/items/:itemId**

Replace an existing cart item.

```json
{
  "productId": 1234,
  "quantity": 1
}
```

---

### **DELETE /carts/:cartId/items/:itemId**

Remove an item from the cart.

---

## 📦 Orders

### **GET /orders**

Returns all orders.  
⚠️ Requires **Authorization header**

---

### **GET /orders/:orderId**

Returns details of a single order.  
⚠️ Requires **Authorization header**

---

### **POST /orders**

Create a new order.

**Request Body**
```json
{
  "cartId": "ZFe4yhG5qNhmuNyrbLWa4",
  "customerName": "John Doe"
}
```

---

### **PATCH /orders/:orderId**

Update an existing order.

```json
{
  "customerName": "Jane Doe",
  "comment": "Please deliver between 5–6 PM"
}
```

---

### **DELETE /orders/:orderId**

Deletes an order.  
⚠️ Requires **Authorization header**

---

## 🔐 Authentication

Some endpoints require **Bearer Token Authentication**.

**Header Example**
```
Authorization: Bearer YOUR_TOKEN
```

---

### **POST /api-clients**

Register a new API client to receive an access token.  
The token is valid for **7 days**.

**Request Body**
```json
{
  "clientName": "Postman Demo Client",
  "clientEmail": "example@test.com"
}
```

**Status Codes**  
- `201 Created` → Client registered, token returned  
- `400 Bad Request` → Invalid request  
- `409 Conflict` → Email already registered  

