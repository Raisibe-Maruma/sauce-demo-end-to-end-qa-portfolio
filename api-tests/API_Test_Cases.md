# 🧪 Manual API Test Cases - Simple Grocery Store API

## Module 1: Cart Management (`/carts`)

| Test ID | Scenario | HTTP Method & Endpoint | Request Body / Parameters | Expected Status | Expected Response Body / Outcome |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-CRT-01** | Create dynamic shopping cart | `POST /carts` | None | `201 Created` | Returns JSON containing a valid string `cartId` and `created: true`. |
| **TC-CRT-02** | Add valid product to cart | `POST /carts/:cartId/items` | `{"productId": 4643, "quantity": 2}` | `201 Created` | Returns `created: true` and a unique `itemId`. |
| **TC-CRT-03** | Update item quantity in cart | `PATCH /carts/:cartId/items/:itemId` | `{"quantity": 5}` | `204 No Content` | Cart item quantity updates to 5 upon fetching `GET /carts/:cartId`. |
| **TC-CRT-04** | Add invalid product ID | `POST /carts/:cartId/items` | `{"productId": 99999}` | `400 Bad Request` | Returns error message indicating invalid product ID. |
| **TC-CRT-05** | Update quantity with negative value | `PATCH /carts/:cartId/items/:itemId` | `{"quantity": -1}` | `400 Bad Request` | Returns validation error rejecting negative quantities. |

---

## Module 2: Order Processing (`/orders`)

| Test ID | Scenario | HTTP Method & Endpoint | Headers | Expected Status | Expected Response Body / Outcome |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-ORD-01** | Submit valid order | `POST /orders` | `Authorization: Bearer <token>` | `201 Created` | Order created successfully, returns `orderId` and `created: true`. |
| **TC-ORD-02** | Submit order without Bearer Token | `POST /orders` | None | `401 Unauthorized` | Returns error message: `"Missing or invalid token"`. |
| **TC-ORD-03** | Submit order with invalid `cartId` | `POST /orders` | `Authorization: Bearer <token>` | `404 Not Found` | Returns error message indicating cart does not exist. |
