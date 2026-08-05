# 🌐 API Testing Portfolio (Simple Grocery Store API)

## 📌 Project Overview
While the main section of this GitHub portfolio utilizes the **SauceDemo** web application for frontend UI testing, SauceDemo is a frontend-only mockup and does not expose a public API backend. 

To demonstrate my backend testing capabilities, this section features a comprehensive manual API testing suite conducted against the **Simple Grocery Store API**, a live, open-source e-commerce API specifically designed for QA practice.

---

## 🛠️ Tools Used
* **Postman:** For executing, organizing, and chaining API requests using environment variables.
* **Markdown:** For test case documentation and bug logging.

---

## 🏗️ What is Tested (Scope)
The testing suite covers the core end-to-end e-commerce user flow across public and authenticated endpoints:
1. **Product Catalog:** Browsing products, querying specific product details, and filtering by category.
2. **Cart Management (CRUD):** Creating dynamic shopping carts, adding/retrieving items, updating quantities, and removing items.
3. **Authentication:** Registering an API client via `POST /api-clients` to generate a Bearer Token.
4. **Order Processing (CRUD):** Placing orders using active cart IDs, updating delivery details, retrieving order statuses, and canceling orders.
5. **Data & Schema Validation:** Verifying JSON response bodies, header configurations, error handlings (400, 404, 401), and HTTP status codes.

---

## 📂 Folder Structure
* `Simple_Grocery_Store_Collection.json` - The exported Postman collection containing all test requests and workflow sequences.
* `Grocery_Store_Environment.json` - Postman environment variables (`baseUrl`, `accessToken`, `cartId`, `orderId`, `itemId`).
* `API_Test_Cases.md` - Detailed manual test cases covering positive, negative, and boundary scenarios.
* `API_Bug_Logs.md` - Bug reports based on edge-case testing results (e.g., handling negative item quantities).
* `Screenshots/` - Visual evidence of successful Postman test execution and response validations.

---

## 🚀 How to Review This Suite
1. Download `Simple_Grocery_Store_Collection.json` and `Grocery_Store_Environment.json` from this folder.
2. Open **Postman** and click **Import** in the top left corner.
3. Drag and drop both JSON files to load the collection and environment settings.
4. Select the **Simple Grocery Store Environment** from the top-right environment dropdown.
5. Review the organized request folders, dynamic environment variables, and response verification snippets in the **Tests** tab.
