# Voting_System

Here's the updated `README.md` file where students can log in using their **registration number**:

## Overview

This project is a simple voting system designed specifically for campus elections, such as faculty voting. It allows students to vote for their preferred faculty members or candidates in a secure and efficient manner. The system is built using PHP, HTML, CSS, and SQL. It is an easy-to-use system intended to be deployed within a campus environment for voting purposes only.

## Features

- **Faculty Voting:** Students can vote for their preferred faculty members.
- **User Authentication:** Only authorized users (students) can vote after logging into the system using their registration number.
- **Real-time Results:** View voting results in real-time after voting has been completed.
- **Admin Panel:** Admin users can manage the voting process, including adding candidates, viewing results, and managing user access.
- **Simple UI:** The user interface is designed to be intuitive and easy for students and admins to navigate.

## Technologies Used

- **PHP:** Server-side scripting language for processing votes and managing user authentication.
- **HTML:** Markup language used to structure the voting pages.
- **CSS:** Stylesheets for creating a clean and responsive design.
- **MySQL:** Database management system to store user information, votes, and candidate data.

## Installation

1. **Download the project files** and extract them to your local server directory.

2. **Set up MySQL database:**
   - Create a new database in MySQL (e.g., `campus_voting_system`).
   - Run the provided `database.sql` file to set up the required tables and data in the database.

3. **Configure the database connection:**
   - Open the `config.php` file and update the database connection parameters (host, username, password, database name) according to your local setup.

4. **Set up the local server:**
   - Install a local server environment like XAMPP or WAMP if you haven't already.
   - Place the project folder in the `htdocs` (for XAMPP) or `www` (for WAMP) directory.

5. **Access the system:**
   - Open your browser and go to `http://localhost/[project_folder]` to access the voting system.

## Usage

1. **Login as a student:**
   - Go to the login page and enter your **student registration number** (used as your username)
   - After successful login, you will be able to vote for your preferred faculty.

2. **Admin Login:**
   - The admin user can log in using the following credentials:
     - **Username:** Nikhil
     - **Password:** admin
   - Once logged in, the admin can manage the election process, such as adding/removing candidates, viewing the voting results, and managing user access.

3. **Vote:**
   - After logging in as a student, you can select the faculty member you wish to vote for and submit your vote.

4. **Admin Panel:**
   - Admin users can log in to the admin panel and manage the election process (e.g., view results, manage users, add/remove candidates).
   - after voting login admin panel than there is option of results you can see your result of voters

## Database Schema

### Tables

1. **users**
   - `id` (INT, PRIMARY KEY) - Unique identifier for the user.
   - `reg_number` (VARCHAR) - Student's registration number used for login.
   - `password` (VARCHAR) - Student's hashed password.
   - `role` (ENUM) - Role of the user (e.g., 'student', 'admin').

2. **candidates**
   - `id` (INT, PRIMARY KEY) - Unique identifier for a candidate.
   - `name` (VARCHAR) - Name of the faculty candidate.
   - `department` (VARCHAR) - Department to which the candidate belongs.

3. **votes**
   - `id` (INT, PRIMARY KEY) - Unique identifier for each vote.
   - `user_id` (INT, FOREIGN KEY) - User ID (student) who cast the vote.
   - `candidate_id` (INT, FOREIGN KEY) - ID of the voted faculty candidate.

### Example SQL Schema

```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    reg_number VARCHAR(255) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    role ENUM('student', 'admin') NOT NULL
);

CREATE TABLE candidates (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    department VARCHAR(255) NOT NULL
);

CREATE TABLE votes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    candidate_id INT NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (candidate_id) REFERENCES candidates(id)
);
```


