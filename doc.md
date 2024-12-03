# API Documentation


## Endpoints

### Menus

#### Get all Menus

- **URL:** `/menu-items`
- **Method:** `GET`
- **Description:** Retrieves all menu items available in the cafe.
- **Headers:**
  - `Accept: application/json`, `Accept: application/xml`
- **Response (JSON):** 
    ```json
    [
    {
        "id": 1,
        "name": "Cappuccino",
        "price": 3.5,
        "category": "Beverages"
    },
    {
        "id": 2,
        "name": "Croissant",
        "price": 2.0,
        "category": "Pastries"
    },
    {
        "id": 3,
        "name": "Baguette",
        "price": 1.5,
        "category": "Pastries"
    },
    {
        "id": 4,
        "name": "Americano",
        "price": 2.0,
        "category": "Beverages"
    }
    ]
    ```
- **Response Example (XML):**
    ```xml
    <menu-items>
        <menu-item>
            <id>1</id>
            <name>Cappuccino</name>
            <price>3.5</price>
            <category>Beverages</category>
        </menu-item>
        <menu-item>
            <id>2</id>
            <name>Croissant</name>
            <price>2.0</price>
            <category>Pastries</category>
        </menu-item>
        <menu-item>
            <id>3</id>
            <name>Baguette</name>
            <price>1.5</price>
            <category>Pastries</category>
        </menu-item>
        <menu-item>
            <id>4</id>
            <name>Americano</name>
            <price>2.0</price>
            <category>Beverages</category>
        </menu-item>
    </menu-items>
    ```

#### Get Menu by ID
- **URL:** `/menu-items/{id}`
- **Method:** `GET`
- **Description:** Retrieves a single menu item by its unique ID.
- **Headers:** 
    - ` Accept: application/json`, `Accept: application/xml`
- **Response (JSON):**
    ```json
    {
    "id": 1,
    "name": "Cappuccino",
    "price": 3.5,
    "category": "Beverages"
    }
    ```
- **Response (XML):**
    ```xml
    <menu-item>
    <id>1</id>
    <name>Cappuccino</name>
    <price>3.5</price>
    <category>Beverages</category>
    </menu-item>
    ```
#### Add a new Menu item
- **URL:** `/menu-items`
- **Method:** `POST`
- **Description:** Adds a new item to the cafe's menu.
- **Headers:** 
    - `Content-Type: application/json`, `Accept: application/xml`
- **Request body (JSON):**
  ```json
  {
  "name": "Mocha",
  "price": 4.0,
  "category": "Beverages"
  }
  ```
- **Request body (XML):**
  ```xml
  <menu-item>
    <name>Mocha</name>
    <price>4.0</price>
    <category>Beverages</category>
  </menu-item>
  ```
- **Response (JSON):**
    ```json
    {
    "id": 5,
    "name": "Mocha",
    "price": 4.0,
    "category": "Beverages"
    }
    ```
- **Response (XML):**
    ```xml
    <menu-item>
      <id>3</id>
      <name>Mocha</name>
      <price>4.0</price>
      <category>Beverages</category>
    </menu-item>
    ```
#### Update Menu Items
- **URL:** `/menu-items/{id}`
- **Method:** `PUT`
- **Description:** Updates the details of an existing menu item.
- **Headers:** 
    - `Content-Type: application/json`, `Accept: application/xml`
- **Request body (JSON):**
  ```json
  {
  "name": "Iced Cappuccino",
  "price": 4.0,
  "category": "Beverages"
  }
  ```
- **Request body (XML):**
    ```xml
    <menu-item>
      <name>Iced Cappuccino</name>
      <price>4.0</price>
      <category>Beverages</category>
    </menu-item>
    ```
- **Response (JSON):**
  ```json
  {
  "id": 5,
  "name": "Iced Cappuccino",
  "price": 4.0,
  "category": "Beverages"
  }
  ```
- **Response (XML):**
  ```xml
  <menu-item>
    <id>5</id>
    <name>Iced Cappuccino</name>
    <price>4.0</price>
    <category>Beverages</category>
  </menu-item>
  ```
#### Delete Menu Item
- **URL:** `/menu-items/{id}`
- **Method:** `DELETE`
- **Description:** Deletes a menu item by its ID.
- **Response (JSON):**
  ```json
  {
  "message": "Menu item successfully deleted."
  }
  ```
- **Response (XML):**
  ```xml
  <message>Menu item successfully deleted.</message>
  ```
#### Get All Orders
- **URL:** `/orders`
- **Method:** `GET`
- **Description:**  Retrieves all customer orders.
- **Headers:** 
    - ` Accept: application/json`, `Accept: application/xml`
- **Response (JSON):**
  ```json
  [
  {
    "id": 1,
    "customer_name": "Feona",
    "items": [
      { "name": "Cappuccino", "quantity": 2 },
      { "name": "Croissant", "quantity": 1 }
    ],
    "total_price": 8.5,
    "status": "Completed"
  },
  {
    "id": 2,
    "customer_name": "Ron Vincent Cada",
    "items": [
      { "name": "Americano", "quantity": 3 }
    ],
    "total_price": 6.0,
    "status": "Pending"
  },
  {
    "id": 3,
    "customer_name": "Miks",
    "items": [
      { "name": "Cappuccino", "quantity": 1 }
      { "name": "Croissant", "quantity": 2 }
      { "name": "Baguette", "quantity": 1 }
    ],
    "total_price": 9.0,
    "status": "Pending"
  }
  ]
  ```
- **Response (XML):**
  ```xml
  <orders>
    <order>
      <id>1</id>
      <customer_name>Feona</customer_name>
      <items>
        <item>
          <name>Cappuccino</name>
          <quantity>2</quantity>
        </item>
        <item>
          <name>Croissant</name>
          <quantity>1</quantity>
        </item>
      </items>
      <total_price>8.5</total_price>
      <status>Completed</status>
    </order>
    <order>
      <id>2</id>
      <customer_name>Ron Vincent Cada</customer_name>
      <items>
          <item>
          <name>Cappuccino</name>
          <quantity>3</quantity>
          </item>
      </items>
      <total_price>6.0</total_price>
      <status>Pending</status>
    </order>
    <order>
      <id>3</id>
      <customer_name>Miks</customer_name>
        <items>
            <item>
              <name>Cappuccino</name>
              <quantity>1</quantity>
            </item>
            <item>
              <name>Croissant</name>
              <quantity>2</quantity>
            </item>
            <item>
              <name>Baguette</name>
              <quantity>1</quantity>
            </item>
        </items>
        <total_price>9.0</total_price>
        <status>Pending</status>
    </order>
  </orders>
  ```
#### Get order by ID
- **URL:** `/orders/{id}`
- **Method:** `GET`
- **Description:**  Places a new order.Retrieves details of a specific customer order.
- **Headers:** 
    - `Accept: application/json`, `Accept: application/xml`
- **Response (JSON):**
  ```json
  {
  "id": 1,
  "customer_name": "Feona",
  "items": [
    { "name": "Cappuccino", "quantity": 2 },
    { "name": "Croissant", "quantity": 1 }
  ],
  "total_price": 8.5,
  "status": "Completed"
  }
  ```
- **Response (XML)**
  ```xml
  <order>
    <id>1</id>
    <customer_name>Feona</customer_name>
    <items>
        <item>
          <name>Cappuccino</name>
          <quantity>2</quantity>  
        </item>
        <item>
          <name>Croissant</name>
          <quantity>1</quantity>
        </item>
    </items>
    <total_price>8.5</total_price>
    <status>Completed</status>
  </order>
  ```
#### Place an order
- **URL:** `/orders`
- **Method:** `POST`
- **Description:**  Places a new order.
- **Headers:** 
    - `Content-Type: application/json`, `Accept: application/xml`
- **Request body (JSON):**
  ```json
  {
  "customer_name": "Alice Gou",
  "items": [
    { "name": "Cappuccino", "quantity": 1 },
    { "name": "Croissant", "quantity": 2 }
  ]
  }
  ```
- **Request body (XML):**
  ```xml
  <order>
  <customer_name>Alice Gou</customer_name>
  <items>
    <item>
      <name>Cappuccino</name>
      <quantity>1</quantity>
    </item>
    <item>
      <name>Croissant</name>
      <quantity>2</quantity>
    </item>
  </items>
  </order>
  ```

- **Response (JSON):**
  ```json
  {
  "id": 3,
  "message": "Order placed successfully."
  }
  ```
- **Response (XML):**
  ```xml
  <response>
    <id>3</id>
    <message>Order placed successfully.</message>
  </response>
  ```
#### Update order status
- **URL:** `/orders/{id}/status`
- **Method:** `PATCH`
- **Description:**  Updates the status of an order (e.g., from "Pending" to "Completed").
- **Headers:** 
    - `Content-Type: application/json`, `Accept: application/xml`
- **Request body (JSON):**
  ```json
  {
  "status": "Completed"
  }
  ```
- **Request body (XML):**
  ```xml
  <status>Completed</status>
  ```
- **Response (JSON):**
  ```json
  {
  "id": 2,
  "message": "Order status updated to 'Completed'."
  }
  ```
- **Response (XML):**
  ```xml
  <response>
    <id>2</id>
    <message>Order status updated to 'Completed'.</message>
  </response>
  ```
#### Get all Categories
- **URL:** `/orders`
- **Method:** `GET`
- **Description:**  Retrieves all available menu categories.
- **Headers:** 
    - `Accept: application/json`, `Accept: application/xml`
- **Response (JSON):**
  ```json
  [
    { "id": 1, "name": "Beverages" },
    { "id": 2, "name": "Pastries" },
    { "id": 3, "name": "Snacks" }
  ]
  ```
- **Response (XML):**
  ```xml
  <categories>
    <category>
        <id>1</id>
        <name>Beverages</name>
    </category>
    <category>
        <id>2</id>
        <name>Pastries</name>
    </category>
    <category>
        <id>3</id>
        <name>Snacks</name>
    </category>
  </categories>
  ```
  