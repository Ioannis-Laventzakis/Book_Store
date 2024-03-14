# Bookstore Database Project

## Overview
This project involves the creation of a relational database to manage a bookstore's data. The database includes tables to store information about books, authors, publishers, categories, and orders.

## Database Schema

### Tables

- `authors`: Contains information about authors.
- `books`: Stores details of books.
- `categories`: Categorizes books into various genres.
- `publishers`: Holds information about book publishers.
- `orders`: Records details of customer orders.
- `order_items`: Links orders to the books and includes quantity and price.

### Relationships

- `books` have a many-to-one relationship with `authors`.
- `books` have a many-to-one relationship with `categories`.
- `books` have a many-to-one relationship with `publishers`.
- `order_items` have a many-to-one relationship with `orders`.
- `order_items` have a many-to-one relationship with `books`.

## Setup Instructions

1. Install PostgreSQL or ensure access to a PostgreSQL database server.
2. Create the database using the provided SQL schema file.
3. Connect to the database using a PostgreSQL client such as `psql` or pgAdmin.
4. Execute the SQL scripts to create the tables in the following order:
    - `authors`
    - `categories`
    - `publishers`
    - `books`
    - `orders`
    - `order_items`
5. Insert sample data into the tables to start using the database.

## Usage

This database can be used to:

- Keep track of bookstore inventory.
- Manage book orders and sales.
- Associate books with authors and categories.
- Record publisher details.
- Maintain order histories without requiring customer information.

## Future Work

- Add a `customers` table to link customer information with orders.
- Implement features for handling stock levels and automatic reordering.
- Create views for commonly accessed queries, such as current inventory levels or pending orders.

