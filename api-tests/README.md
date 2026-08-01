# 🌐 API Testing Portfolio (Restful-Booker)

## 📌 Project Overview
While the main section of this GitHub portfolio utilizes the **SauceDemo** web application for frontend UI testing, SauceDemo is a frontend-only mockup and does not expose a public API backend. 

To demonstrate my backend testing capabilities, this section features a comprehensive manual API testing suite conducted against **Restful-Booker**, a live, open-source hotel booking API specifically designed for QA practice.

---

## 🛠️ Tools Used
* **Postman:** For executing and organizing API requests.
* **Markdown/Google Sheets:** For test case documentation and bug logging.

---

## 🏗️ What is Tested (Scope)
The testing suite covers the core CRUD (Create, Read, Update, Delete) operations of a hotel booking workflow, including:
1. **Authentication:** Generating auth tokens via `POST /auth` to access secure endpoints.
2. **Booking Management:** Creating, retrieving, updating, and deleting customer reservations.
3. **Data Validation:** Verifying JSON response bodies, headers, response times, and HTTP status codes.

---

## 📂 Folder Structure
* `Restful_Booker_Collection.json` - The exported Postman collection containing all test requests and basic assertions.
* `API_Test_Cases.md` - Detailed manual test cases covering positive, negative, and boundary scenarios.
* `API_Bug_Logs.md` - Simulated bug reports based on edge-case testing results.
* `Screenshots/` - Visual evidence of successful Postman test execution and response validations.

---

## 🚀 How to Review This Suite
1. Download the `Restful_Booker_Collection.json` file from this folder.
2. Open **Postman** and click **Import** in the top left corner.
3. Drag and drop the downloaded JSON file to load the collection.
4. Review the organized request folders, environment variables, and pre-written response verification snippets in the **Tests** tab.
