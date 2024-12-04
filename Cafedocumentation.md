# Ordinary Cafe Shop
## Overview
The Ordinary Cafe Shop API allows the user to mange the menu and orders.  It provides endpoints to create, read, update, and delete menus and orders. The API follows the RESTapi principles and meets the  Richardson REST API maturity sample.


**Base URL** `https://api.ordinarycafeshop.com/v1`

## Error Handling
- `200 OK`: Request was successful
- `201 Created`: Resource was successfully created.
- `204 No Content`: Resource was successfully deleted.
- `400 Bad Request`: Request was invalid or cannot be served
- `404 Not Found`: The requested resource could not be found.
- `500 Internal Server Error`: An error occurred on the server.

## Endpoints
### Get All Menus Items
```
GET /menu-items
```
**Description:** Retrieves all menu items in the cafe.

**Headers:**
  - `Accept: application/json`, `Accept: application/xml`

**Response:**
- `200 OK`: Returns a JSON or XML data.
  
**Response(JSON)**
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
**Response(XML):**
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
### Get Menu Item by ID
```
GET /menu-items/{id}
```
**Description:**  Retrieves a single menu item by ID.

**Headers:** 
    - ` Accept: application/json`, `Accept: application/xml`

**Response:**
- `200 OK`: Returns the details of the Item.
- `400 bad`: Item not found.

**Response(JSON):**
```json
{
    "id": 1,
    "name": "Cappuccino",
    "price": 3.5,
    "category": "Beverages"
}
```
**Response(XML):**
```xml
<menu-item>
    <id>1</id>
    <name>Cappuccino</name>
    <price>3.5</price>
    <category>Beverages</category>
</menu-item>
```
### Add new menu item
```
POST /menu-items
```
**Description:** Adds a new item to the cafe's menu.

**Headers:** 
    - `Content-Type: application/json`, `Accept: application/xml`

 **Request body (JSON):**
  ```json
  {
  "name": "Mocha",
  "price": 4.0,
  "category": "Beverages"
  }
  ```
 **Request body (XML):**
  ```xml
  <menu-item>
    <name>Mocha</name>
    <price>4.0</price>
    <category>Beverages</category>
  </menu-item>
  ```

**Response:**
- `201 Created`; Returns the details of the item in JSON or XML.

**Response(JSON):**
```json
 {
  "name": "Mocha",
  "price": 4.0,
  "category": "Beverages"
}
```
**Response(XML):**
```xml
<menu-item>
    <name>Mocha</name>
    <price>4.0</price>
    <category>Beverages</category>
</menu-item>
```
### Update Menu Items
```
PUT /menu-items/{id}
```
**Description:** Updates the details of an existing menu item.

**Headers:** 
    - `Content-Type: application/json`, `Accept: application/xml`

**Request Body:**
 **Reqy (JSON):**
  ```json
  {
  "name": "Iced Cappuccino",
  "price": 4.0,
  "category": "Beverages"
  }
  ```
  **Request body (XML):**
  ```xml
    <menu-item>
      <name>Iced Cappuccino</name>
      <price>4.0</price>
      <category>Beverages</category>
    </menu-item>
  ```


**Response:**
- `200 OK`: Updates the details of the Item
- `400 Not Found`: Item not found

**Response (JSON):**
  ```json
  {
  "id": 5,
  "name": "Iced Cappuccino",
  "price": 4.0,
  "category": "Beverages"
  }
  ```
  **Response (XML):**
  ```xml
  <menu-item>
    <id>5</id>
    <name>Iced Cappuccino</name>
    <price>4.0</price>
    <category>Beverages</category>
  </menu-item>
  ```

### Delete Menu Item
```
DELETE /menu-items/{id}
```

**Description:** Deletes a menu item by its ID.

**Headers:** 
    - ` Accept: application/json`, `Accept: application/xml`

**Responses:**
- `204 No Content`: Item sucessfully deleted.
- `404 Not Found`:Item not found.

**Response(JSON):**
```json
{
  "message": "Menu item successfully deleted."
}
```

**Response(XML):**
```xml
<message>Menu item successfully deleted.</message>
```

### Get All Orders
```
GET /menu-items
```

**Description:** Retrieves all customer orders.

**Headers:** 
    - ` Accept: application/json`, `Accept: application/xml`

**Response:**
`200 OK`: Returns JSON or XML data.

**Response(JSON):**
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

**Response(XML):**
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
### Get Order by ID
```
GET /orders/{id}
```

**Description:** Places a new order.Retrieves details of a specific customer order.

**Headers:** 
    - `Accept: application/json`, `Accept: application/xml`

**Response:**
- `200 OK`: Returns the Item data to JSON or XML.
- `404 Not Found`: Item not found.

**Response(JSON):**
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
**Response(XML):**
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

### Place an order
```
POST /orders
```

**Description:** Places a new order.

**Headers:** 
    - `Content-Type: application/json`, `Accept: application/xml`

  **Request body (JSON ):**
  ```json
  {
  "customer_name": "Alice Gou",
  "items": [
    { "name": "Cappuccino", "quantity": 1 },
    { "name": "Croissant", "quantity": 2 }
  ]
  }
  ```
 **Request body (XML):**
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

**Response**
- `201 Created`: Returns the created order in JSON or XML.

**Response(JSON):**
```json
{
  "id": 3,
  "message": "Order placed successfully."
}
```
**Response(XML):**
```xml
<response>
    <id>3</id>
    <message>Order placed successfully.</message>
</response>
```
### Update order status
```
PATCH /orders/{id}/status
```

**Description:** Updates the status of an order (e.g., from "Pending" to "Completed").

**Headers:** 
    - `Content-Type: application/json`, `Accept: application/xml`

**Request:**

**Request body (JSON):**
  ```json
  {
  "status": "Completed"
  }
  ```
**Request body (XML):**
  ```xml
  <status>Completed</status>
  ```

**Response:**
`204 No Content`: Sucessfully Completed to Patch the item.

**Response(JSON):**
```json
{
  "id": 2,
  "message": "Order status updated to 'Completed'."
}
```
**Response(XML):**
```xml
<response>
    <id>2</id>
    <message>Order status updated to 'Completed'.</message>
</response>
```
#### Delete an Order
```
DELETE /orders/{id}
```
**Description:** Deletes an order.

**Headers:** 
    - `Accept: application/json`, `Accept: application/xml`

**Responses:**
- `204 No Content`: order sucessfully deleted.
- `404 Not Found`:order not found.
- 
**Response(JSON):**
```json
{
  "message": "Menu item successfully deleted."
}
```
**Response(XML):**
```xml
<message>Menu item successfully deleted.</message>
```



















  




