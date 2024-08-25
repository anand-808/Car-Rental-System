
---

# Car Rental System

## Overview

The Car Rental System is a comprehensive application designed to manage car rentals. This project focuses on database management and integration, providing a robust schema to handle various aspects of car rental operations, including dealers, customers, car details, and bookings. Built with Django, a high-level Python web framework, it leverages Django's ORM, admin interface, and templating system to simplify web development. 

## Features

- **User Management**: 
  - **Customer Registration/Login**: Allows users to sign up and log in.
  - **Dealer Registration/Login**: Provides functionality for dealers to manage their car listings.
  
- **Car Listings**: 
  - Dealers can add, update, and manage their cars.
  - Customers can search and view available cars.

- **Booking System**: 
  - Customers can book cars, with features for viewing and managing booking history.
  
- **Admin Interface**: 
  - A comprehensive admin panel for overseeing and managing all aspects of the car rental service.

## Installation

### Prerequisites

- Python 3.x
- MySQL database
- Virtual Environment

### Setup

1. **Clone the Repository**

   ```bash
   git clone https://github.com/yourusername/car-rental-system.git
   cd car-rental-system
   ```

2. **Set Up the Database**

   - **Create a MySQL Database:**

     Open MySQL command line or MySQL Workbench and create a new database:

     ```sql
     CREATE DATABASE car;
     ```

   - **Update `settings.py`:**

     Edit the `DATABASES` section and `SECRET_KEY` in `car_rental/settings.py` to match your database configuration:

     ```python
     import os
     from pathlib import Path

     BASE_DIR = Path(__file__).resolve().parent.parent

     SECRET_KEY = os.getenv('DJANGO_SECRET_KEY', 'default-secret-key')

     DEBUG = True

     DATABASES = {
         'default': {
             'ENGINE': 'django.db.backends.mysql',
             'NAME': os.getenv('DB_NAME', 'car'),
             'USER': os.getenv('DB_USER', 'root'),
             'PASSWORD': os.getenv('DB_PASSWORD', 'your-db-password'),
             'HOST': os.getenv('DB_HOST', 'localhost'),
             'PORT': os.getenv('DB_PORT', '3306'),
         }
     }
     ```

     **Replace placeholders**:
     - `DJANGO_SECRET_KEY`: Replace `'default-secret-key'` with a secure key.
     - `DB_NAME`: Name of your MySQL database (e.g., `car`).
     - `DB_USER`: Your MySQL username (e.g., `root`).
     - `DB_PASSWORD`: Your MySQL password.
     - `DB_HOST`: Your MySQL host (e.g., `localhost`).
     - `DB_PORT`: Your MySQL port (default is `3306`).

3. **Load Database Schema**

   - **Execute SQL Commands:**

     Use MySQL command line or MySQL Workbench to execute the contents of `sql.txt`:

     ```sql
     SOURCE path/to/sql.txt;
     ```

     This will create the necessary tables in your MySQL database.

4. **Apply Migrations**

   Run Django migrations to set up the initial database schema:

   ```bash
   python manage.py migrate
   ```

5. **Create a Superuser**

   Create an admin user to access the Django admin interface:

   ```bash
   python manage.py createsuperuser
   ```

   Follow the prompts to create the superuser.

6. **Run the Development Server**

   Start the Django development server to run the application:

   ```bash
   python manage.py runserver
   ```

   Access the application at `http://127.0.0.1:8000/`.

## Database Schema

The database schema is defined in `sql.txt`, which includes the following tables:
- **dealer**: Stores dealer information.
- **customer**: Stores customer information.
- **cdetails**: Stores car details.
- **booking**: Stores booking information.

## Project Structure

- **`car/`**: Contains the virtual environment.
- **`car_rental/`**: The main Django project folder.
- **`home/`**: Manages the homepage and application views.
- **`db.sqlite3`**: The SQLite database file (used for development).
- **`manage.py`**: Django’s command-line utility for administrative tasks.

---
