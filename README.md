# <font size="6">🚂 RAILWAY RESERVATION SYSTEM</font>

A **console-based Railway Reservation System** developed using **Java** and **MySQL**. This application provides functionalities for **train and customer management**, **ticket booking**, and **generating invoices for passengers**.

---

## <font size="5">✨ FEATURES</font>

### <font size="4">🔑 USER MANAGEMENT</font>
- **Registration**: New customers can register by providing their name, age, email, and password.
- **Login**: Existing customers can log in using their email and password.

### <font size="4">🚉 TRAIN MANAGEMENT</font>
- **Add Train Information**: Add train details such as PNR, train name, starting point, destination, ticket availability, and ticket prices.
- **Update Train Information**: Modify train details like starting point or destination.
- **Delete Train Information**: Remove train records using PNR.
- **View Trains**: Display all available trains with complete information.
- **Search Train**: Search for a specific train by PNR.

### <font size="4">🎟️ TICKET BOOKING</font>
- **Book Tickets**: Book tickets for a specific train and class (1st, 2nd, 3rd, or local).
- **Generate Invoice**: Automatically generate an invoice with train and passenger details after successful booking.

### <font size="4">🗄️ DATABASE INTEGRATION</font>
- MySQL is used to manage data for customers, trains, and transactions.

---

## <font size="5">🛠️ PREREQUISITES</font>

### <font size="4">💻 SOFTWARE REQUIREMENTS</font>
- **Java JDK** (version 8 or above)
- **MySQL** (version 5.7 or above)
- **JDBC Driver** (com.mysql.cj.jdbc.Driver)

### <font size="4">🗃️ MYSQL SETUP</font>
1. Create a database named `atharva`.
2. Set up the following tables in the database:
   - **Customer Table**:
     ```sql
     CREATE TABLE customer (
         Id INT AUTO_INCREMENT PRIMARY KEY,
         Name VARCHAR(100),
         Age INT,
         Email VARCHAR(100) UNIQUE,
         Password VARCHAR(100),
         Transaction TEXT
     );
     ```
   - **Trains Table**:
     ```sql
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
     ```
3. Add the required stored procedures:
   - **Insertion**:
     ```sql
     DELIMITER //
     CREATE PROCEDURE insertion(IN name VARCHAR(100), IN age INT, IN email VARCHAR(100), IN password VARCHAR(100))
     BEGIN
         INSERT INTO customer (Name, Age, Email, Password) VALUES (name, age, email, password);
     END //
     DELIMITER ;
     ```
   - **Deletion**:
     ```sql
     DELIMITER //
     CREATE PROCEDURE deletedata(IN pnr INT)
     BEGIN
         DELETE FROM trains WHERE PNR = pnr;
     END //
     DELIMITER ;
     ```
   - **Display Train Data**:
     ```sql
     DELIMITER //
     CREATE PROCEDURE displaydata()
     BEGIN
         SELECT * FROM trains;
     END //
     DELIMITER ;
     ```
   - **Search Trains by PNR**:
     ```sql
     DELIMITER //
     CREATE PROCEDURE displayPNR(IN pnr INT)
     BEGIN
         SELECT * FROM trains WHERE PNR = pnr;
     END //
     DELIMITER ;
     ```

---

## <font size="5">🚀 HOW TO RUN</font>

### <font size="4">💾 STEP 1: COMPILE THE CODE</font>
```bash
javac Railways.java
