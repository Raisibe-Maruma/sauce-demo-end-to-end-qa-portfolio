# Test Plan: SauceDemo E-Commerce Web Application

## 1. Introduction & Objectives
The purpose of this testing project is to perform end-to-end functional manual testing and REST API testing on the Swag Labs (SauceDemo) web application. The primary goal is to ensure core user flows—such as authentication, product browsing, cart management, and checkout—function as expected without critical defects.

## 2. Scope of Testing

### In-Scope (What We ARE Testing)
* **User Authentication:** Valid login, invalid credentials, locked-out users, and session logout.
* **Product Catalog:** Product listing display, sorting options (A-Z, Z-A, Low-High, High-Low), and individual product details.
* **Shopping Cart:** Adding items, removing items, cart count badge updates, and cart persistence across pages.
* **Checkout Workflow:** Form input validation (First Name, Last Name, Zip Code), item total calculations, and order completion.
* **REST API:** Basic HTTP responses, endpoint availability, and status code verification.

### Out-of-Scope (What We Are NOT Testing)
* Payment gateway processing (mocked in AUT).
* Social media footer links (external third-party links).
* Performance/Load testing under high traffic.
* Security testing.

## 3. Test Types & Design Techniques
* **Smoke Testing:** Verifying core critical paths before deep testing.
* **Functional Testing:** Ensuring features behave according to business logic.
* **Equivalence Partitioning (EP):** Grouping inputs to test valid vs. invalid data ranges.
* **Boundary Value Analysis (BVA):** Testing boundary limits on form fields (e.g., Zip Code length).
* **Exploratory Testing:** Uncovering unexpected edge-case bugs using special user personas (e.g., `problem_user`, `glitch_user`).

## 4. Environment & Tools
* **Application Under Test (AUT):** https://www.saucedemo.com/
* **Test Management Tool:** TestRail
* **API Testing Tool:** Postman
* **Defect Tracking & Version Control:** GitHub Issues & GitHub Repository
* **Browsers:** Google Chrome, Safari (Latest Versions)

## 5. Entry & Exit Criteria
* **Entry Criteria:** 
  * AUT URL is publicly accessible.
  * TestRail project and sections are set up.
* **Exit Criteria:**
 * 100% of planned test cases executed in TestRail.
  * All discovered bugs logged with steps to reproduce and synced to GitHub Issues.
  * Test Run execution summary report generated.
  * 100% of planned test cases executed in TestRail.
  * All discovered bugs logged with steps to reproduce and synced to GitHub Issues.
  * Test Run execution summary report generated.
