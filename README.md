````markdown
# Cypress Automation Project - AutomationExercise

## Description

This project includes automated end-to-end (E2E) tests using Cypress for the AutomationExercise platform. It covers UI tests for different site features, API validations using Postman, basic code coverage metrics, and an optional setup for CI with GitHub Actions.

---

### 🧾 Project Selection Justification

I chose [AutomationExercise](https://automationexercise.com) as the target application because it simulates a comprehensive e-commerce platform, including key flows such as user login, product browsing, cart management, and API endpoints. This allowed me to build realistic test cases for both **UI** and **API** layers.

The site provides a stable and predictable environment, which is ideal for implementing reliable and maintainable automated tests. It also exposes a public API, enabling backend verification and negative testing scenarios.

By testing this platform, I was able to simulate real-world interactions and validate the system both through the UI and API. This dual-layer strategy reflects a practical and scalable QA approach for real production environments.

---

## Tools & Technologies

- **Cypress**: Main E2E test automation framework using JavaScript.
- **Postman**: For manual and automated REST API validation.
- **GitHub Actions**: (optional) To execute tests automatically on every pull request.
- **nyc / cypress-coverage**: To collect basic code coverage metrics (basic config included).

---

## Folder Structure

```txt
cypress/
├── e2e/
│   ├── pages/         # Page objects for UI tests
│   ├── tests/         # Cypress E2E test files
├── fixtures/          # Test data (e.g., users)
├── support/           # Custom commands and setup
postman/
├── collections/       # Postman collections for API tests
├── environments/      # Postman environment variables
````

---

## How to Run the Tests

### Prerequisites

* Node.js installed (v16+ recommended)
* npm or yarn installed

### Steps to Run UI Tests with Cypress

1. Clone the repository:

```bash
git clone <repo-url>
cd <project-folder>
```

2. Install dependencies:

```bash
npm install
```

3. Open Cypress Test Runner (GUI mode):

```bash
npx cypress open
```

4. Run all tests in headless mode (CLI):

```bash
npx cypress run
```

### Running API Tests with Postman

* Import the Postman collection from `postman/collections/AutomationExercise_API.postman_collection.json`
* Run the requests manually or using a runner in Postman
* Each request includes test scripts validating response codes and payload structures

---

## Code Coverage

The project includes a basic configuration for `cypress-coverage` using `nyc`. Coverage reports are generated automatically and can help identify untested areas for improvement.

---

## API Coverage and Validation with Postman

| ID   | API                                | Method | URL                                                               | Expected Code | Description                                        |
| ---- | ---------------------------------- | ------ | ----------------------------------------------------------------- | ------------- | -------------------------------------------------- |
| API1 | Get All Products List              | GET    | [productsList](https://automationexercise.com/api/productsList)   | 200           | Validates that the product list is returned.       |
| API5 | POST to Search Product             | POST   | [searchProduct](https://automationexercise.com/api/searchProduct) | 200           | Validates product search with a valid parameter.   |
| API7 | POST Verify Login (valid)          | POST   | [verifyLogin](https://automationexercise.com/api/verifyLogin)     | 200           | Validates login with correct email/password.       |


---

# API Testing with Newman + HTML Report

## Prerequisites

- [Node.js](https://nodejs.org/) installed (v12+)
- Postman Collection (`NaNLabsTest.postman_collection.json`)
- Postman Environment file (`Dev.postman_environment.json`)

---

## Installation & Execution (1 step)

Install Newman, the HTML reporter, and run the tests with one command:

```bash
npm install -g newman newman-reporter-htmlextra && \
newman run NaNLabsTest.postman_collection.json \
  -e Dev.postman_environment.json \
  -r htmlextra \
  --reporter-htmlextra-title "NanLabs Test"



