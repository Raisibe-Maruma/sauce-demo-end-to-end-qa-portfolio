# Manual Test Cases (TestRail)

This directory contains the test case architecture and repository structure used for manual UI execution in **TestRail**.

--

## 🔗 Test Management & Suite Links

- **Test Suite:** `SauceDemo UI Functional & Regression Suite`
- **Test Run:** `Sprint 1 - Manual UI Regression`
- **Tool:** TestRail Enterprise

--

## 📂 Test Suite Structure

The test cases are organized into **3 core functional sections** covering 21 individual test scenarios:

### 1. Authentication & Session Management (`01-Auth`)
- Valid login (`standard_user`), invalid password handling, locked-out user restrictions (`locked_out_user`), field clearing, and session logout.

### 2. Catalog & Shopping Cart (`02-Catalog & Cart`)
-Product listing display, sorting variations (A-Z, Z-A, Price Low-High, Price High-Low), individual item detail view navigation, cart badge increment/decrement, and item removal.
* **TC65  (Defects Identified):** Image asset rendering and product title redirection under `problem_user`.

### 3. Checkout Workflow (`03-Checkout Flow`)
-Information input form validation (First Name, Last Name, Zip Code), item subtotal & tax calculation verification, order completion, and cart reset post-purchase.
* **TC64 & TC66 (Defects Identified):** Last Name field input mirroring (`problem_user`) and empty cart checkout boundary validation.
