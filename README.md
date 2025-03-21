# PySpark Data Cleaning and Preprocessing Script

This script is designed to clean and preprocess an orders dataset using PySpark. It performs various transformations and filtering operations to prepare the data for further analysis or modeling.

## Prerequisites

- Python 3.x
- PySpark (`pyspark` library)
- A Spark environment (local or cluster)

## Dataset

The dataset used in this script is stored in a Parquet file named `orders_data.parquet`. It contains the following columns:

- `order_date`: Timestamp of the order.
- `product`: Name of the product.
- `category`: Category of the product.
- `purchase_address`: Full address of the purchase.

## Script Overview

### 1. **Initialize Spark Session**

- A Spark session is initiated with the application name `cleaning_orders_dataset_with_pyspark`.

### 2. **Data Import**

- The dataset is read from the Parquet file `orders_data.parquet`.

### 3. **Data Cleaning and Preprocessing**

- **Time of Day Extraction**: A new column `time_of_day` is created based on the hour extracted from `order_date`. The values are categorized as `morning`, `afternoon`, `evening`, or `night`.
- **Filtering**: Orders with `time_of_day` as `night` are filtered out.
- **Date Casting**: The `order_date` column is cast from timestamp to date.
- **Lowercase Conversion**: The `product` and `category` columns are converted to lowercase.
- **Filtering Products**: Rows where the `product` column contains the string `"tv"` are removed.
- **State Extraction**: The `purchase_state` column is extracted from the `purchase_address` by splitting the address and taking the second-to-last element.

### 4. **Unique States Calculation**

- The number of unique states in the `purchase_state` column is calculated.

### 5. **Export Cleaned Data**

- The cleaned dataset is exported to a new Parquet file named `orders_data_clean.parquet`.

## How to Run

1. Ensure you have PySpark installed. You can install it using pip:

   ```bash
   pip install pyspark

   ```

2. Place the orders_data.parquet file in the same directory as the script.

3. Run the script using Python:

   ```bash
   python your_script_name.py

   ```

4. The cleaned dataset will be saved as `orders_data_clean.parquet` in the same directory.
