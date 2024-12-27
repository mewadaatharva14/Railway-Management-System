Railway Reservation System

This project is a console-based Railway Reservation System developed using Java and MySQL. The application provides functionalities for train and customer management, ticket booking, and generating invoices for passengers.

Features

User Management

Registration: New customers can register by providing their name, age, email, and password.

Login: Existing customers can log in using their email and password.

Train Management

Add Train Information: Add details about trains, such as PNR, train name, starting point, destination, available tickets for different classes, and ticket prices.

Update Train Information: Modify train details, including starting point and destination.

Delete Train Information: Remove train records using PNR.

View Trains: Display all available trains with complete information.

Search Train: Search for a specific train by PNR.

Ticket Booking

Book Tickets: Book tickets for a specific train and class (1st, 2nd, 3rd, or local).

Generate Invoice: Automatically generate an invoice with train and passenger details after successful booking.

Database Integration

MySQL is used to manage data for customers, trains, and transactions.

Prerequisites

Software Requirements

Java JDK (version 8 or above)

MySQL (version 5.7 or above)

JDBC Driver (com.mysql.cj.jdbc.Driver)

MySQL Setup

Create a database named atharva.

Set up the following tables in the database:

customer:

CREATE TABLE customer (
    Id INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(100),
    Age INT,
    Email VARCHAR(100) UNIQUE,
    Password VARCHAR(100),
    Transaction TEXT
);

trains:

CREATE TABLE trains (
    PNR INT PRIMARY KEY,
    Name_of_Train VARCHAR(100),
    Starting_point VARCHAR(100),
    Destination VARCHAR(100),
    Ticket_1 INT,
    Ticket_2 INT,
    Ticket_3 INT,
    Ticket_l INT,
    Price_1 INT,
    Price_2 INT,
    Price_3 INT,
    Price_l INT,
    Time TIME
);

Add required stored procedures:

For insertion:

DELIMITER //
CREATE PROCEDURE insertion(IN name VARCHAR(100), IN age INT, IN email VARCHAR(100), IN password VARCHAR(100))
BEGIN
    INSERT INTO customer (Name, Age, Email, Password) VALUES (name, age, email, password);
END //
DELIMITER ;

For deletion:

DELIMITER //
CREATE PROCEDURE deletedata(IN pnr INT)
BEGIN
    DELETE FROM trains WHERE PNR = pnr;
END //
DELIMITER ;

For displaying train data:

DELIMITER //
CREATE PROCEDURE displaydata()
BEGIN
    SELECT * FROM trains;
END //
DELIMITER ;

For searching trains by PNR:

DELIMITER //
CREATE PROCEDURE displayPNR(IN pnr INT)
BEGIN
    SELECT * FROM trains WHERE PNR = pnr;
END //
DELIMITER ;

How to Run

Step 1: Compile the Code

javac Railways.java

Step 2: Execute the Program

java Railways

Code Structure

Railways.java: Main entry point of the application.

Classes:

Railways: Handles the main program logic and menu system.

Series: Manages customer registration and deletion.

Train1: Handles train management (add, update, delete, display, search).

Ticket_Booking: Manages ticket booking, updates ticket availability, and generates invoices.

Usage Instructions

Run the program and choose options from the menu.

Use option 1 for registration and option 2 for login.

Admin functionalities such as adding, updating, or deleting train records are available through options 4, 5, and 6.

View available trains using option 7 and search specific trains with option 8.

Exit the program using option 9.

Limitations

Basic console-based user interface.

No encryption for user passwords.

Limited exception handling for user inputs.

Future Enhancements

Add GUI for better user experience.

Enhance security by encrypting passwords.

Implement a role-based system for admin and user functionalities.

Add email notifications for ticket bookings.

Author

Atharva Mewada
