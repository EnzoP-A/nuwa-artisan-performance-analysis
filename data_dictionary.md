# Nuwa Data Dictionary

## Overview

This document describes the structure of the datasets used in the Nuwa artisan business and SaaS performance analysis.

The analytical model is organized around five main tables:

- `artisans`
- `products`
- `orders`
- `order_items`
- `subscriptions`

These tables are connected through unique identifiers such as `artisan_id`, `product_id` and `order_id`.

---

## 1. Artisans

The `artisans` table contains seller-level information.

| Column | Type | Description |
|---|---|---|
| `artisan_id` | Text | Unique identifier for each artisan |
| `artisan_name` | Text | Fictional artisan or brand name |
| `category` | Text | Main artisan business category |
| `region` | Text | Geographic region of the artisan |
| `onboarding_date` | Date | Date the artisan joined Nuwa |
| `business_age_years` | Integer | Number of years the artisan business has existed |
| `business_size` | Text | Size of the artisan business |
| `acquisition_channel` | Text | Channel through which the artisan discovered Nuwa |

---

## 2. Products

The `products` table contains product-level information.

| Column | Type | Description |
|---|---|---|
| `product_id` | Text | Unique identifier for each product |
| `artisan_id` | Text | Identifier of the artisan selling the product |
| `product_name` | Text | Fictional product name |
| `category` | Text | Main product category |
| `subcategory` | Text | More detailed product category |
| `base_price` | Decimal | Standard catalogue price |
| `launch_date` | Date | Date the product was added to Nuwa |
| `product_status` | Text | Current status of the product |

---

## 3. Orders

The `orders` table contains order-level information.

| Column | Type | Description |
|---|---|---|
| `order_id` | Text | Unique identifier for each order |
| `order_date` | Date | Date the order was placed |
| `artisan_id` | Text | Artisan linked to the order |
| `customer_id` | Text | Fictional customer identifier |
| `customer_region` | Text | Geographic region of the customer |
| `order_status` | Text | Status of the order |

---

## 4. Order Items

The `order_items` table contains product-level information for each order.

| Column | Type | Description |
|---|---|---|
| `order_item_id` | Text | Unique identifier for each order line |
| `order_id` | Text | Identifier of the related order |
| `product_id` | Text | Identifier of the related product |
| `quantity` | Integer | Number of units purchased |
| `unit_price` | Decimal | Actual selling price per unit |
| `discount_rate` | Decimal | Discount applied to the item |
| `item_sales_value` | Decimal | Total sales value of the order line |

---

## 5. Subscriptions

The `subscriptions` table contains the subscription history of Nuwa artisans.

| Column | Type | Description |
|---|---|---|
| `subscription_id` | Text | Unique identifier for each subscription period |
| `artisan_id` | Text | Identifier of the related artisan |
| `plan_name` | Text | Starter, Growth or Pro |
| `start_date` | Date | Start date of the subscription period |
| `end_date` | Date | End date of the subscription period |
| `monthly_price` | Decimal | Monthly subscription price |
| `subscription_status` | Text | Current status of the subscription |
| `change_type` | Text | Subscription change such as upgrade, downgrade or churn |

---

## Relationships

The datasets follow a relational structure:

- One artisan can own multiple products.
- One artisan can receive multiple orders.
- One order can contain multiple order items.
- One product can appear in multiple order items.
- One artisan can have multiple subscription periods over time.

---

## Key Technical Terms

- **Primary Key:** a unique identifier for each row in a table.
- **Foreign Key:** a field used to connect one table to another.
- **One-to-Many Relationship:** one record in one table can be linked to multiple records in another table.
- **Data Normalization:** structuring data to reduce unnecessary duplication and improve consistency.
- **Granularity:** the level of detail represented by each row in a dataset.
