# Ordinary Cafe Shop
## Overview
The Ordinary Cafe Shop API allows the user to mange the menu and orders.  It provides endpoints to create, read, update, and delete menus and orders. The API follows the RESTapi principles and meets the  Richardson REST API maturity sample.

**Authentication:** `Authorization: {sample}`

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

**Response:**
- `200 OK`: Returns a JSON or XML data.
  
**Example(JSON)**
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
**Example(XML):**
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

**Response:**
- `200 OK`: Returns the details of the Item.
- `400 bad`: Item not found.

**Example(JSON):**
```json
{
    "id": 1,
    "name": "Cappuccino",
    "price": 3.5,
    "category": "Beverages"
}
```
**Example(XML):**
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

**Request Body:**
- `name`(string): Name of the Item
- `price`(integer): Price of the Item
- `category`(string): Category of the Item

**Response:**
- `201 Created`; Returns the details of the item in JSON or XML.

**Example(JSON):**
```json
 {
  "name": "Mocha",
  "price": 4.0,
  "category": "Beverages"
}
```
**Example(XML):**
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

**Request Body:**
- `name`(string): Name of the Item
- `price`(integer): Price of the Item
- `category`(string): Category of the Item

**Response:**
- `200 OK`: Updates the details of the Item
- `400 Not Found`: Item not found

**Example(JSON):**
```json
{
  "name": "Iced Cappuccino",
  "price": 4.0,
  "category": "Beverages"
}
```
**Example(XML):**
```xml
<menu-item>
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

**Responses:**
- `204 No Content`: Item sucessfully deleted.
- `404 Not Found`:Item not found.

**Example(JSON):**
```json
{
  "message": "Menu item successfully deleted."
}
```

**Example(XML):**
```xml
<message>Menu item successfully deleted.</message>
```

### Get All Orders
```
GET /menu-items
```

**Description:** Retrieves all customer orders.

**Response:**
`200 OK`: Returns JSON or XML data.

**Example(JSON):**
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

**Example(XML):**
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

**Response:**
- `200 OK`: Returns the Item data to JSON or XML.
- `404 Not Found`: Item not found.

**Example(JSON):**
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
**Example(XML):**
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

**Request body:**
- `customer_name`: name of the customer
- `name`: the item that the customer ordered
- `quantity`: how many the customer ordered the item 

**Response**
- `201 Created`: Returns the created order in JSON or XML.

**Example(JSON):**
```json
{
  "id": 3,
  "message": "Order placed successfully."
}
```
**Example(XML):**
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

**Request body:**
- `Pending`: Updates the status of an order to Pending
- `Completed`: Updates the status of an order to Completed

**Response:**
`204 No Content`: Sucessfully Completed to Patch the item.

**Example(JSON):**
```json
{
  "id": 2,
  "message": "Order status updated to 'Completed'."
}
```
**Example(XML):**
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

**Responses:**
- `204 No Content`: order sucessfully deleted.
- `404 Not Found`:order not found.
- 
**Example(JSON):**
```json
{
  "message": "Menu item successfully deleted."
}
```
**Example(XML):**
```xml
<message>Menu item successfully deleted.</message>
```



















  




