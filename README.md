<h1>Advanced Databases Project</h1>
Adilet Kabiyev, SE-2433

A fullstack internal admin dashboard for an electronics store. Focused on analytics and database operations.

<h2>Tech Stack</h2>
Frontend: HTML, CSS, JS

Backend: Node.js, Express.js, Mongo/Mongoose, JWT, bcrypt, dotenv

## Project Structure

```
AdvFinalProject/
├── config/
│   └── db.js
├── models/
│   ├── Category.js
│   ├── Customer.js
│   ├── Order.js
│   ├── Product.js
│   ├── Review.js
│   └── User.js
├── middleware/
│   ├── auth.js
│   ├── errorHandler.js
│   └── requireRole.js
├── controllers/
│   ├── authController.js
│   ├── categoryController.js
│   ├── productController.js
│   ├── orderController.js
│   ├── analyticsController.js
│   └── inventoryController.js
├── routes/
│   ├── authRoutes.js
│   ├── categoryRoutes.js
│   ├── productRoutes.js
│   ├── orderRoutes.js
│   ├── analyticsRoutes.js
│   └── inventoryRoutes.js
├── public/
│   ├── dashboard.html
│   ├── products.html
│   ├── orders.html
│   ├── inventory.html
│   ├── login.html
│   ├── signup.html
│   ├── css/style.css
│   └── js/api.js
├── utils/
│   └── AppError.js
├── server.js
├── package.json
└── .env.
```

## Collections

```

│ Categories
│   ├── _id
│   ├── name
│   ├── description
│   └── createdAt
│ Customers
│   ├── _id
│   ├── name
│   ├── email
│   ├── phone
│   ├── address
│   │   ├── street
│   │   ├── city
│   │   └── country
│   └── createdAt
│ Orders
│   ├── _id
│   ├── customerId
│   ├── products
│   │   ├── productId
│   │   └── quantity
│   ├── status
│   └── createdAt
│ Products
│   ├── _id
│   ├── name
│   ├── categoryId
│   ├── brand
│   ├── price
│   ├── stock
│   ├── specs
│   │   ├── spec1
│   │   └── spec2
│   └── createdAt
│ Users
│   ├── _id
│   ├── email
│   ├── name
│   ├── role
│   └── password
```

## NoSQL Additions & MongoDB Features

### Aggregation Pipelines
Multi-stage aggregations using $unwind, $lookup, $group, $sort, $limit

- **Sales by category** (/api/analytics/sales-by-category): $unwind orders.products, $lookup products, $lookup categories, $group by category, $sort by total quantity
- **Top products** (/api/analytics/top-products): $unwind, $lookup products , $group by product, $sort by total sold, $limit
- **Summary** (/api/analytics/summary): $group orders by status; $unwind + $lookup for total revenue; countDocuments for totals

### Update Operators
- **$set:** Update order status, product price/stock
- **$inc:** Restore stock when order is deleted; bulk restock; product stock adjustments
- **bulkWrite:** Restore stock for all line items in a deleted order, bulk restock multiple

### API Endpoints

**Auth**

POST  /api/auth/login

POST  /api/auth/signup

**Categories management**

GET  /api/categories

**Products management**

GET  /api/products

GET  /api/products/:id

DELETE  /api/products/:id

**Orders management**

GET  /api/orders

PUT  /api/orders/:id/status

DELETE  /api/orders/:id

**Analytics**

GET  /api/analytics/sales-by-category

GET  /api/analytics/top-products

GET  /api/analytics/summary

**Inventory management**

GET  /api/inventory/low-stock

PUT  /api/inventory/bulk-restock


