# 🧪 Manual API Test Cases — Simple Grocery Store API

## 📌 Project Overview
* **Target API:** Simple Grocery Store API
* **Base URL:** `https://simple-grocery-store-api.online`
* **Authentication:** Bearer Token via `POST /api-clients`
* **Author:** QA Portfolio Project

---

## 1. API Health & Product Catalog (`/status`, `/products`)

| Test ID | Scenario | HTTP Method & Endpoint | Request Parameters / Body | Expected Status | Expected Outcome |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-API-01** | Verify API health status | `GET /status` | None | `200 OK` | Returns `{"status": "UP"}`. |
| **TC-API-02** | Fetch full product catalog | `GET /products` | None | `200 OK` | Returns an array of all available products with id, category, and in-stock status. |
| **TC-API-03** | Filter products by category | `GET /products` | Query Param: `category=coffee` | `200 OK` | Returns array containing only items where `category` equals `"coffee"`. |
| **TC-API-04** | Limit result count | `GET /products` | Query Param: `limit=2` | `200 OK` | Returns array containing exactly 2 product items. |
| **TC-API-05** | Fetch single product details | `GET /products/:productId` | Path Variable: `productId=4643` | `200 OK` | Returns single product details object matching ID `4643`. |
| **TC-API-06** | Fetch non-existent product | `GET /products/:productId` | Path Variable: `productId=99999` | `404 Not Found` | Returns JSON error response: `{"error": "No product with id 99999."}`. |

---

## 2. Cart Management (`/carts`)

| Test ID | Scenario | HTTP Method & Endpoint | Request Parameters / Body | Expected Status | Expected Outcome |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-CRT-01** | Create a new cart | `POST /carts` | None | `201 Created` | Returns `{"created": true, "cartId": "<unique_string>"}`. Stores `cartId` in environment. |
| **TC-CRT-02** | Get cart contents | `GET /carts/:cartId` | Path Variable: `cartId` | `200 OK` | Returns cart item array and total cost calculation. |
| **TC-CRT-03** | Add valid product to cart | `POST /carts/:cartId/items` | Body: `{"productId": 4643}` | `201 Created` | Returns `{"created": true, "itemId": <int>}`. Stores `itemId` in environment. |
| **TC-CRT-04** | Add invalid product to cart | `POST /carts/:cartId/items` | Body: `{"productId": 0}` | `400 Bad Request` | Returns validation error: `{"error": "Invalid or missing productId."}`. |
| **TC-CRT-05** | Update item quantity in cart | `PATCH /carts/:cartId/items/:itemId` | Body: `{"quantity": 3}` | `204 No Content` | Cart item quantity updates to 3 upon re-fetching `GET /carts/:cartId`. |
| **TC-CRT-06** | Update item quantity to negative (Boundary/Edge Case) | `PATCH /carts/:cartId/items/:itemId` | Body: `{"quantity": -1}` | `400 Bad Request` | Should reject negative quantities *(Logged as BUG-01 if server returns 204)*. |
| **TC-CRT-07** | Replace/Set item quantity | `PATCH /carts/:cartId/items/:itemId` | Body: `{"quantity": 1}` | `204 No Content` | Replaces quantity for specified item. |
| **TC-CRT-08** | Delete item from cart | `DELETE /carts/:cartId/items/:itemId` | Path Variables: `cartId`, `itemId` | `204 No Content` | Item is removed from the cart; subsequent GET confirms empty item array. |

---

## 3. Client Authentication (`/api-clients`)

| Test ID | Scenario | HTTP Method & Endpoint | Request Body | Expected Status | Expected Outcome |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-ATH-01** | Register new API client | `POST /api-clients` | `{"clientName": "QA Tester", "clientEmail": "test_user_101@example.com"}` | `201 Created` | Returns `{"accessToken": "<jwt_string>"}`. Stores token as `accessToken`. |
| **TC-ATH-02** | Register with existing email | `POST /api-clients` | `{"clientName": "QA Tester", "clientEmail": "test_user_101@example.com"}` | `409 Conflict` | Returns error message: `{"error": "API client already registered."}`. |
| **TC-ATH-03** | Register with missing email field | `POST /api-clients` | `{"clientName": "QA Tester"}` | `400 Bad Request` | Returns validation error requiring email parameter. |

---

## 4. Order Processing (`/orders`)

| Test ID | Scenario | HTTP Method & Endpoint | Headers & Body | Expected Status | Expected Outcome |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-ORD-01** | Submit valid order | `POST /orders` | Header: `Bearer <token>`<br>Body: `{"cartId": "<cart_id>", "customerName": "Jane Doe"}` | `201 Created` | Order placed successfully; returns `{"created": true, "orderId": "<id>"}`. |
| **TC-ORD-02** | Submit order without Auth Header | `POST /orders` | Header: None<br>Body: `{"cartId": "<cart_id>", "customerName": "Jane Doe"}` | `401 Unauthorized` | Returns error: `{"error": "Missing or invalid token."}`. |
| **TC-ORD-03** | Submit order with empty cart (Edge Case) | `POST /orders` | Header: `Bearer <token>`<br>Body: `{"cartId": "<empty_cart_id>", "customerName": "Jane Doe"}` | `400 Bad Request` | Should reject order execution for empty carts *(Logged as BUG-02 if created)*. |
| **TC-ORD-04** | Get all client orders | `GET /orders` | Header: `Bearer <token>` | `200 OK` | Returns array of orders associated with the registered token. |
| **TC-ORD-05** | Get specific order by ID | `GET /orders/:orderId` | Header: `Bearer <token>` | `200 OK` | Returns detailed order object matching `orderId`. |
| **TC-ORD-06** | Get order with unauthorized token | `GET /orders/:orderId` | Header: `Bearer <invalid_token>` | `401 Unauthorized` | Rejects access to order data. |
| **TC-ORD-07** | Update customer details on order | `PATCH /orders/:orderId` | Header: `Bearer <token>`<br>Body: `{"customerName": "Jane Smith"}` | `204 No Content` | Customer name updated on order. |
| **TC-ORD-08** | Delete/Cancel an order | `DELETE /orders/:orderId` | Header: `Bearer <token>` | `204 No Content` | Order successfully canceled/deleted. |
