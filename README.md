# Visited Countries Tracker - Family Edition

A web application to track countries visited by users. This app uses **Node.js**, **Express**, **PostgreSQL**, and **EJS** for server-side rendering.

## Features
- Add countries to a user's visited list.
- View total visited countries.
- Switch between different users.
- Create new users with customizable colors.

---

## Project Structure

```
.
├── public/             # Static files (CSS, JS, images)
├── views/              # EJS templates
├── index.js              # Main server file
├── package.json        # Project dependencies
├── .env                # Environment variables
```

---

## Prerequisites
- **Node.js** (version 16 or higher)
- **PostgreSQL**
- Install dependencies using npm:

```bash
npm install
```

---

## Setting Up the Database

### 1. Create a PostgreSQL Database
```sql
CREATE DATABASE visited_countries_tracker;
```

### 2. Create Tables

```sql
-- Table for users
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    color VARCHAR(20) NOT NULL
);

-- Table for countries
CREATE TABLE countries (
    id SERIAL PRIMARY KEY,
    country_name VARCHAR(50) NOT NULL,
    country_code VARCHAR(5) NOT NULL UNIQUE
);

-- Table for visited countries
CREATE TABLE visited_countries (
    id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(id) ON DELETE CASCADE,
    country_code VARCHAR(5) REFERENCES countries(country_code) ON DELETE CASCADE
);
```

### 3. Seed the Countries Table

Insert sample countries (you can add more as needed):

```sql
INSERT INTO countries (country_name, country_code) VALUES
('United States', 'US'),
('India', 'IN'),
('Canada', 'CA'),
('Australia', 'AU');
```

### 4. Environment Variables

Create a `.env` file in the root directory with the following:

```
PG_USER=your_username
PG_PASSWORD=your_password
PG_HOST=localhost
PG_DATABASE=visited_countries_tracker
PG_PORT=5432
```

---

## Running the Application

1. Start the PostgreSQL server.
2. Run the following command to start the app:

```bash
node index.js
```

3. Open your browser and navigate to:

```
http://localhost:3000
```

---

## Usage

### Add a New User
1. Click on the "Add New User" button.
2. Enter the user's name and select a color.

### Add a Country to Visited List
1. Type the country's name in the input field.
2. Click "Add Country".

### Switch Users
1. Select a user from the dropdown.
2. Click "Switch User".

---

## Dependencies

- **Express**: Fast, unopinionated web framework for Node.js.
- **Body-Parser**: Middleware to parse incoming request bodies.
- **PG (node-postgres)**: PostgreSQL client for Node.js.
- **EJS**: Embedded JavaScript templates for server-side rendering.

Install all dependencies with:

```bash
npm install
```

---

## Notes

- Ensure that your PostgreSQL database is running before starting the app.
- To reset the database, drop and recreate the tables using the provided SQL commands.
- Handle database credentials securely in the `.env` file.

---

## Contributing
Feel free to fork this repository and submit pull requests. For major changes, open an issue to discuss your ideas.

---

## Author
- Created by **Kanish**.

---

Happy coding! 🎉
