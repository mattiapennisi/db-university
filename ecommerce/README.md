## Table name: 'products'

** Columns: ** 

- id BIGINT - PRIMARY_KEY - AUTO-INCREMENT - NOTNULL
- name VARCHAR(255) - NOTNULL
- brand
- category
- is_available
- price
- description
- image_url

## Table name: 'copies'

** Columns: ** 

- id BIGINT - PRIMARY_KEY - AUTO-INCREMENT - NOTNULL
- product_id - FOREIGN_KEY - VARCHAR(255) - NOTNULL
- quantity
- location
- condition

## Table name: 'customers'

** Columns: **

- id BIGINT - PRIMARY_KEY - AUTO-INCREMENT - NOTNULL
- firstname
- lastname
- date_of_registration
- is_a_member
- email
- password
- phone
- address

## Table name: 'orders'

** Columns: **

- id BIGINT - PRIMARY_KEY - AUTO-INCREMENT - NOTNULL
- customer_id - FOREIGN_KEY
- product_id - FOREIGN_KEY - VARCHAR(255) - NOTNULL
- date DATETIME()
- employee_id
- total
- shipping_address
- status

## Table name: 'employees'

** Columns: **

- id BIGINT - PRIMARY_KEY - AUTO-INCREMENT - NOTNULL
- firstname
- lastname
- date_of_hiring DATE()
- role
- email

## Table name: 'payments'

** Columns: **

- id BIGINT - PRIMARY_KEY - AUTO-INCREMENT - NOTNULL
- order_id - FOREIGN_KEY - VARCHAR(255) - NOTNULL
- method
- date DATETIME()
- status