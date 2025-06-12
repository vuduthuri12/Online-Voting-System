# Online Voting System

This project implements a basic online voting system. It allows users to cast votes for candidates and provides functionalities to view real-time vote results and candidate-wise vote details.

## Features

- User authentication (implied, as `hasVoted` uses `userId`)
- Record votes for candidates
- View overall vote results
- Get total vote count
- View detailed candidate vote percentages

## Technologies Used

- Java
- JDBC (Java Database Connectivity)
- SQL (for database operations)
- JSP/Servlets (assumed for web interface)
- Apache Tomcat (assumed for deployment)

## Setup Instructions

1.  **Database Setup:**
    - Create a MySQL (or other compatible SQL) database.
    - Run the following SQL scripts to create necessary tables:
    ```sql
    CREATE TABLE users (
        id INT PRIMARY KEY AUTO_INCREMENT,
        username VARCHAR(50) UNIQUE NOT NULL,
        password VARCHAR(255) NOT NULL
    );

    CREATE TABLE candidates (
        id INT PRIMARY KEY AUTO_INCREMENT,
        name VARCHAR(100) NOT NULL,
        party VARCHAR(100),
        position VARCHAR(100)
    );

    CREATE TABLE votes (
        id INT PRIMARY KEY AUTO_INCREMENT,
        user_id INT NOT NULL,
        candidate_id INT NOT NULL,
        vote_timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
        FOREIGN KEY (user_id) REFERENCES users(id),
        FOREIGN KEY (candidate_id) REFERENCES candidates(id)
    );
    ```
    - Update the `DBUtil.java` file (or equivalent) with your database connection details (URL, username, password).

2.  **Project Build:**
    - Open the project in your preferred Java IDE (e.g., Eclipse, IntelliJ IDEA).
    - Ensure all necessary JDBC drivers are included in your project's build path.
    - Build the project to resolve dependencies and compile source code.

3.  **Deployment:**
    - Export the project as a WAR file.
    - Deploy the WAR file to an Apache Tomcat server or any other servlet container.

## Usage

1.  Access the application through your web browser (e.g., `http://localhost:8081/onlinevotingsystem`).
2.  Register/Login as a user.
3.  Cast your vote for a candidate.
4.  View real-time vote results and statistics on the results page.
