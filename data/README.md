# **📁 Data Directory**

## Dataset Information

This project uses the **Brazilian E-Commerce Public Dataset by Olist**, a real-world dataset containing 100,000+ orders from a Brazilian marketplace between September 2016 and October 2018.

### **Download the Dataset**

The dataset is publicly available on Kaggle:

**[Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)**

> The raw data files are **not included** in this repository to respect Kaggle's terms of use and keep the repo lightweight. Please download directly from Kaggle.

###  **Dataset Tables (9 CSV Files)**

| File | Description | Rows | Key Columns |
|------|-------------|------|-------------|
| `olist_orders_dataset.csv` | Central fact table — one row per order | 99,441 | order_id, customer_id, order_status, timestamps |
| `olist_order_items_dataset.csv` | Products within each order | 112,650 | order_id, product_id, seller_id, price, freight_value |
| `olist_order_payments_dataset.csv` | Payment details per order | 103,886 | order_id, payment_type, installments, payment_value |
| `olist_order_reviews_dataset.csv` | Customer review scores and comments | 99,224 | order_id, review_score, review_comment_message |
| `olist_customers_dataset.csv` | Customer demographics and location | 99,441 | customer_id, customer_unique_id, city, state |
| `olist_products_dataset.csv` | Product attributes and categories | 32,951 | product_id, category_name, dimensions, weight |
| `olist_sellers_dataset.csv` | Seller information and location | 3,095 | seller_id, seller_city, seller_state |
| `olist_geolocation_dataset.csv` | Lat/lng coordinates per zip code | 1,000,163 | zip_code_prefix, lat, lng, city, state |
| `product_category_name_translation.csv` | Portuguese → English category names | 71 | category_name, category_name_english |

###  **Table Relationships (Schema)**
```
orders.customer_id         → customers.customer_id
orders.order_id            → order_items.order_id
orders.order_id            → order_payments.order_id
orders.order_id            → order_reviews.order_id
order_items.product_id     → products.product_id
order_items.seller_id      → sellers.seller_id
products.product_category  → category_translation.product_category_name
customers.customer_zip     → geolocation.geolocation_zip_code_prefix
sellers.seller_zip         → geolocation.geolocation_zip_code_prefix
```

**Central table:** `orders` (connects to everything)
**True customer identifier:** `customers.customer_unique_id` (not `customer_id`)

### **Key Business Metrics from This Dataset**

| Metric | Value |
|--------|-------|
| Total orders | 99,441 |
| Unique customers | 96,096 |
| Unique products | 32,951 |
| Unique sellers | 3,095 |
| Product categories | 71 |
| Date range | Sep 2016 → Oct 2018 |
| Repeat purchase rate | 3.0% |
| Total revenue | R$15.4M |

### **How to Use**

**Option 1 — Kaggle (Recommended):**
Open the [notebook on Kaggle](https://www.kaggle.com/code/armandjunior/full-cycle-analysis-e-commerce-churn-prediction) where the dataset is pre-attached.

**Option 2 — Local:**
1. Download all 9 CSV files from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
2. Place them in this `data/` directory
3. Run the notebook from `notebooks/`

###  **License & Attribution**

This dataset was generously made public by [Olist](https://www.olist.com/) and is available under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

**Citation:**
> Olist, "Brazilian E-Commerce Public Dataset by Olist," Kaggle, 2018. Available at: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
