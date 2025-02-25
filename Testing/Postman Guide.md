# RESTful APIs Master Class - Postman Guide

## Overview
This guide covers how to use **Postman** for testing and interacting with RESTful APIs.

## Installation
1. Download **Postman** from [Postman’s official website](https://www.postman.com/downloads/).
2. Install and launch the application.

## Creating a Request
1. Open **Postman** and click **New Request**.
2. Select the HTTP method (**GET, POST, PUT, DELETE**).
3. Enter the API URL in the request field.
4. Add necessary headers (e.g., `Content-Type: application/json`).
5. For **POST/PUT**, enter request **Body** in JSON format.

## Using Collections
1. Click **New Collection** → Name it appropriately.
2. Add multiple API requests within the collection.
3. Save and organize requests efficiently.

## Authentication
- **API Key:** Add in the **Headers** or as a **Query Parameter**.
- **Bearer Token:** Go to the **Authorization** tab → Select **Bearer Token**.
- **Basic Auth:** Enter **username/password** in the **Authorization** tab.

## Running Tests
1. Go to the **Tests** tab.
2. Add JavaScript snippets for automated testing.
   ```javascript
   pm.test("Status code is 200", function () {
       pm.response.to.have.status(200);
   });
   ```
3. Click **Send** to execute.

## Environments & Variables
- Create an **Environment** (e.g., `Development`, `Staging`, `Production`).
- Define variables like `{{baseUrl}}` and use them dynamically in API requests.
- Set global, environment, or collection-level variables.


## Running Collections via Newman
1. Install **Newman** (CLI tool for Postman).
   ```sh
   npm install -g newman
   ```
2. Export collection from Postman.
3. Run it in the terminal:
   ```sh
   newman run <collection-file.json>
   ```