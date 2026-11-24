# Data

## Layers

| Folder | Layer | What goes in it |
|---|---|---|
| `raw/` | **raw** | The Olist CSVs exactly as downloaded. Never edit them, never write here. |
| `clean/` | **clean** | One typed, checked table per entity (orders, customers, …), saved as parquet. |
| `mart/` | **mart** | Tables ready to answer a business question, at the grain the question needs. |

Git ignores everything in these three folders. Every notebook rebuilds `clean/` and `mart/` from
`raw/`, so anyone can reproduce your numbers from a fresh clone.

Fill `raw/` with:

```bash
python scripts/download_data.py
```

## Olist Brazilian E-Commerce

Real, anonymised orders from Olist, a Brazilian marketplace that connects small shops to the
big online stores: about 99,000 orders placed between September 2016 and October 2018.

| File | Rows | One row is… |
|---|---|---|
| `olist_orders_dataset.csv` | 99,441 | an order |
| `olist_order_items_dataset.csv` | 112,650 | an item line within an order |
| `olist_order_payments_dataset.csv` | 103,886 | a payment within an order |
| `olist_order_reviews_dataset.csv` | 99,224 | a review |
| `olist_customers_dataset.csv` | 99,441 | a customer, as recorded on one order |
| `olist_products_dataset.csv` | 32,951 | a product |
| `olist_sellers_dataset.csv` | 3,095 | a seller |
| `product_category_name_translation.csv` | 71 | a product category (Portuguese → English) |

The geolocation table of the original dataset is left out: no session uses it.

### Licence and attribution

Source: Olist, *Brazilian E-Commerce Public Dataset by Olist*,
<https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce>.

The data is licensed under
[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/). You may use it for
non-commercial work, you must credit Olist, and anything you share that is built on it must use
the same licence. This repository redistributes it unchanged (minus the geolocation table) as a
release asset, under that licence.

## Map of Brazil (`geo/`)

`geo/brazil-states.geojson` holds the outline of Brazil's 27 states, for the maps in Module 7.
Each state's two-letter code (the same as `customer_state`) is in `properties.sigla`. Unlike
`raw/`, `clean/` and `mart/`, it is part of the repository: pulling gets it.

Source: `brazil-states.geojson` from the *click_that_hood* project
(<https://github.com/codeforgermany/click_that_hood>), simplified for this course (coordinates
rounded to 0.1°, only the code and the name kept). The project is under the MIT licence.
