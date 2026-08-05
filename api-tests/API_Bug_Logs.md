# 🐛 API Bug Logs — Simple Grocery Store API

## 📌 Bug Report Overview
This document logs defects and input-validation edge cases identified during manual API execution against the **Simple Grocery Store API**.

---

## [BUG-01] Cart item quantity accepts negative integers without input validation

* **Bug ID:** `BUG-01`
* **Severity:** Medium
* **Priority:** High
* **Module:** Cart Management
* **Endpoint:** `PATCH /carts/:cartId/items/:itemId`
* **Test Case ID:** `TC-CRT-06`
* **Status:** Open

### Description
When submitting a payload to update an item's quantity in an active shopping cart using a negative integer (`-1`), the API accepts the request and returns `204 No Content` instead of rejecting the payload with an input validation error.

### Steps to Reproduce
1. Execute `POST /carts` to create a new cart and obtain a valid `cartId`.
2. Add a product to the cart via `POST /carts/:cartId/items` with payload `{"productId": 4643}` to generate an `itemId`.
3. Send a `PATCH` request to `/carts/:cartId/items/:itemId` with the following body:
   ```json
   {
     "quantity": -1
   }
