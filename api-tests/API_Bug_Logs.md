# 🐛 API Bug Logs - Simple Grocery Store API

## [BUG-01] Cart item quantity update accepts negative integers

* **Severity:** Medium  
* **Priority:** High  
* **Module:** Cart Management (`PATCH /carts/:cartId/items/:itemId`)  
* **Status:** Open  

### Description
When attempting to update an item's quantity in an active cart using a negative integer (`-1`), the server accepts the request and returns `204 No Content` instead of validating input bounds.

### Steps to Reproduce
1. Execute `POST /carts` to create a new cart and obtain a `cartId`.
2. Add a product to the cart using `POST /carts/:cartId/items` with payload `{"productId": 4643}`.
3. Send a `PATCH` request to `/carts/:cartId/items/:itemId` with the following body:
   ```json
   {
     "quantity": -1
   }
