# Analyzed DVD rental data with SQL #
## Introduction ##
I recently completed some training in Data Foundation facilitated by Bertelsmann’s School of Data Science (in partnership with Udacity). For a personal project, I decided to analyze the database for a DVD rental company we will call Rent A Film. Let’s take a look at a case study detailing my process and output.

## Data-set ##
I began by taking a look at the database. The database DvdRental has 15 tables. Below are the different tables and a brief description of them.

actor — contains actors data including first name and last name.
film — contains films data such as title, release year, length, rating, etc.
film_actor — contains the relationships between films and actors.
category — contains film’s categories data.
film_category — containing the relationships between films and categories.
store — contains the store data including manager staff and address.
inventory — stores inventory data.
rental — stores rental data.
payment — stores customer’s payments.
staff — stores staff data.
customer — stores customer’s data.
address — stores address data for staff and customers
city — stores the city names.
country — stores the country names.

## Objective & Goals ##
In this project, I’ll aim to answer the following questions:

1. Select all the data from the film table
2. Select the film id, rental rate, and title from the film table
3. Provide first name, last name, customer id, and store id from the data.
4. SELECT first_name, last_name, customer_id, store_id
5. Provide all the data from the payment table
6. Retrieve the address and district names of employees.
7. Provide the film id and title of the movies with a runtime of less than 60
8. Select the film names of those who have a rating of PG-13 or G
9. Get the Customer_id, store_id, and email of the customer name Nancy Thomas
10. Get the customer_id, first_name, last_name of for customer_id 1 to 10
11. Provide a list of films (their titles, film IDs, and ratings) that are NOT rated NC-17.
12. Get the addresses and postal codes of customers who live in the Michigan district.
13. Your manager asks for  the  list of  payment transactions between  2007-02-18	 00:00:00  and	 2007-02-20 00:00:00. Retrieve  the  payment ID, customer ID, amount and payment dates
14. Retrieve all available information for customers whose last names are either Williams, Taylor, or Andrews.
15. The manager	asks	for the	rental	ID and	customer ID	of transactions that	have a rental	date starting May 26, 2005 and return date before May	29, 2005
16. Get the film_id, title, and description from the film table which has rated G, PG-13, NC-17
17. Provide the list of drama films that have. Get the title, description, and rental_rate of the film.

Before getting started with analyses, I first tried understanding the ERM (Entity Relationship Model) of this database also known as Schema. Here is the Schema below:

![Re5gkP7yWnJhl7p84eVLeVRxixkh9Po284s0](https://github.com/SwetaMallick01/DVD-Rental/assets/132562651/8a751bf5-d982-439d-a99e-6db406409a65)


## Analysis ##
DVD rental DATABASE: 

### 1. Select all the data from the film table
SELECT*
FROM film

### 2. Select the film id, rental rate, and title from the film table
SELECT film_id, title, rental_rate
FROM film

### 3. Provide first name, last name, customer id, and store id from the data.

SELECT first_name, last_name, customer_id, store_id
FROM customer

### 4. Provide all the data from the payment table

SELECT*
FROM payment

### 5. Retrieve the address and district names of employees.

SELECT address, district
FROM address

### 6. Provide the film id and title of the movies with a runtime of less than 60

SELECT film_id, title, film.length
FROM film
WHERE film.length < 60

### 7. Select the film names of those who have a rating of PG-13 or G

SELECT title, rating
FROM film
WHERE rating = 'PG-13' OR rating = 'G'

### 8. Get the Customer_id, store_id, and email of the customer name Nancy Thomas 

SELECT customer_id, store_id, email
FROM customer
WHERE first_name = 'Nancy' AND last_name = 'Thomas'


### 9. Get the customer_id, first_name, last_name of for customer_id 1 to 10

SELECT customer_id, first_name, last_name
FROM customer
WHERE customer_id BETWEEN 1 AND 10

### 10. Provide a list of films (their titles, film IDs, and ratings) that are NOT rated NC-17.

SELECT title, film_id, rating
FROM film
WHERE rating != 'NC-17'

### 11. Get the addresses and postal codes of customers who live in the Michigan district.

SELECT address, postal_code
FROM address
WHERE district = 'Michigan'

### 12. Your manager asks for  the  list of  payment transactions between  2007-02-18	 00:00:00  and	 2007-02-20 00:00:00. Retrieve  the  payment ID, customer ID, amount and payment dates

SELECT payment_id, customer_id, amount, payment_date
FROM payment
WHERE payment_date BETWEEN '2007-02-18 00:00:00' AND '2007-02-20 00:00:00'

### 13. Retrieve all available information for customers whose last names are either Williams, Taylor, or Andrews. 

SELECT*
FROM customer
WHERE last_name IN ( 'Williams', 'Taylor', 'Andrews' )

### 14. The manager	asks	for the	rental	ID and	customer ID	of transactions that	have a rental	date starting May 26, 2005 and return date before May	29, 2005

SELECT rental_id, customer_id 
FROM rental 
WHERE rental_date>= '2005-05-26'	AND	return_date < '2005-05-29'

### 15. Get the film_id, title, and description from the film table which has rated G, PG-13, NC-17

SELECT film_id, title, description
FROM film
WHERE rating IN ('G', 'PG-13', 'NC-17')


### 16. Provide the list of drama films that have. Get the title, description, and rental_rate of the film.

SELECT title, description, rental_rate. 
FROM film
WHERE description LIKE '%Drama%'

