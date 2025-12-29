## 🧩 User Story: Account Microservice – Full REST API

**As a** developer on the e-commerce platform  
**I need** to extend the Account microservice REST API to support read, update, delete, and list customer accounts (in addition to the existing create endpoint)  
**So that** other microservices and internal tools can reliably manage customer data through a complete CRUD + list interface.

---

### 📋 Details and Assumptions

* The Account microservice is implemented using **Python Flask** and follows REST conventions.
* A **database model already exists**, and a **Create Customer** endpoint is already implemented and working.
* I will add endpoints for:
  * **Read** a customer by ID
  * **Update** a customer by ID
  * **Delete** a customer by ID
  * **List** customers
* The service will return **JSON** responses and appropriate **HTTP status codes**.
* Development will occur in an **online lab environment** and requires environment setup and validation.
* Customer identifiers are unique and used in the URL path.
* Validation and error handling will follow the same pattern as the existing create endpoint.

---

### ✅ Acceptance Criteria

#### 🧪 Scenario: Prepare the online lab environment for development
Given I have access to the online lab environment and the starter repository
When I install the required dependencies and start the Flask application
Then the service should run without errors and the existing "create customer" endpoint should be reachable

#### 🧪 Scenario: Read a customer account by ID
Given a customer account exists in the database with a known ID
When I send a GET request to /customers/{id}
Then the service should return HTTP 200 and the customer account details in JSON format


#### 🧪 Scenario: Read a customer account that does not exist
Given no customer account exists with ID {id}
When I send a GET request to /customers/{id}
Then the service should return HTTP 404 with an error message in JSON format

#### 🧪 Scenario: Update an existing customer account
Given a customer account exists in the database with ID {id}
When I send a PUT request to /customers/{id} with valid updated customer data
Then the service should return HTTP 200 and the updated customer account details in JSON format

#### 🧪 Scenario: Update a customer account that does not exist
Given no customer account exists with ID {id}
When I send a PUT request to /customers/{id} with valid customer data
Then the service should return HTTP 404 with an error message in JSON format


#### 🧪 Scenario: Delete an existing customer account
Given a customer account exists in the database with ID {id}
When I send a DELETE request to /customers/{id}
Then the service should return HTTP 204 and the customer account should no longer be retrievable

#### 🧪 Scenario: Delete a customer account that does not exist
Given no customer account exists with ID {id}
When I send a DELETE request to /customers/{id}
Then the service should return HTTP 404 with an error message in JSON format

#### 🧪 Scenario: List customer accounts
Given multiple customer accounts exist in the database
When I send a GET request to /customers
Then the service should return HTTP 200 and a JSON array of customer accounts
