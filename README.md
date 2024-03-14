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

# Bookstore Database Project

## Overview

This project is a PostgreSQL database designed to manage a bookstore's data. It includes tables to store information about books, authors, publishers, categories, and orders.

## Database Schema

### Tables and Their Structures

**Authors Table**
```sql
CREATE TABLE authors (
    author_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    bio TEXT
);

CREATE TABLE books (
    book_id SERIAL PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    author_id INTEGER NOT NULL,
    publication_date DATE,
    isbn VARCHAR(20),
    price NUMERIC(5, 2),
    FOREIGN KEY (author_id) REFERENCES authors(author_id)
);
**Categories Table**
```sql
CREATE TABLE categories (
    category_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT
);
**Publishers Table**
```sql
CREATE TABLE publishers (
    publisher_id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    address TEXT,
    phone VARCHAR(20)
);
**Orders Table**
```sql
CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    order_date DATE NOT NULL,
    status VARCHAR(50)
);
**Order Items Table**
```sql
CREATE TABLE order_items (
    order_item_id SERIAL PRIMARY KEY,
    order_id INTEGER NOT NULL,
    book_id INTEGER NOT NULL,
    quantity INTEGER NOT NULL,
    price_at_order NUMERIC(5, 2) NOT NULL,
    FOREIGN KEY (order_id) REFERENCES orders(order_id),
    FOREIGN KEY (book_id) REFERENCES books(book_id)
);
### Sample Data Inserts

**Inserting Sample Authors**
```sql
INSERT INTO authors (name, bio) VALUES
('J.K. Rowling', 'British author best known for the Harry Potter series.'),
('George Orwell', 'English novelist and critic.'),
('Virginia Woolf', 'English writer and modernist.'),
('Haruki Murakami', 'Japanese author known for his surreal fiction.');

**Inserting Books**
```sql
INSERT INTO books (title, author_id, publication_date, isbn, price) VALUES
('Harry Potter and the Philosopher''s Stone', 1, '1997-06-26', '9780747532699', 19.95),
('1984', 2, '1949-06-08', '9780451524935', 9.99),
('Mrs Dalloway', 3, '1925-05-14', '9780156628709', 7.99),
('Kafka on the Shore', 4, '2002-09-12', '9781400079278', 13.95);

**Inserting Categories**
```sql
INSERT INTO categories (name, description) VALUES
('Fiction', 'Fictional works of prose.'),
('Non-Fiction', 'Informative and factual prose.'),
('Science Fiction', 'Fiction with futuristic elements.'),
('Mystery', 'Fiction dealing with solving a crime.');

**Inserting Publishers**
```sql
INSERT INTO publishers (name, address, phone) VALUES
('Penguin Books', '80 Strand, London, WC2R 0RL, England', '+44 20 7139 3000'),
('HarperCollins', '195 Broadway, New York, NY 10007, United States', '+1 212-207-7000');

**Inserting Orders**
```sql
INSERT INTO orders (order_date, status) VALUES
('2024-03-15', 'processing'),
('2024-03-16', 'shipped');

**Inserting Order Items**
```sql INSERT INTO order_items (order_id, book_id, quantity, price_at_order) VALUES
(1, 1, 1, 19.95),
(1, 2, 2, 9.99),
(2, 3, 1, 7.99),
(2, 4, 1, 13.95);

