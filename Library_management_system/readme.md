# Library Management System

## Overview
The **Library Management System** is a relational database designed to manage book borrowing, reservations, fine payments, and staff roles efficiently. This project is implemented using **MySQL** and follows a structured database schema to maintain smooth operations in a library.

## Features
- **User Management**: Supports members, staff, and admin roles.
- **Book Management**: Stores details about books including availability status.
- **Borrow & Return System**: Tracks books borrowed by users with due dates.
- **Fine Management**: Calculates and tracks fines for overdue books.
- **Reservations**: Allows users to reserve books that are unavailable.
- **Book Recommendations**: Suggests books based on users' past readings.

## Database Schema

### Users Table
```sql
CREATE TABLE Users (
    UserID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(255) NOT NULL,
    Email VARCHAR(255) UNIQUE NOT NULL,
    Phone VARCHAR(15),
    UserType ENUM('Member', 'Staff', 'Admin') NOT NULL
);
```
### Books Table
```sql
CREATE TABLE Books (
    BookID INT PRIMARY KEY AUTO_INCREMENT,
    Title VARCHAR(255) NOT NULL,
    Author VARCHAR(255) NOT NULL,
    ISBN VARCHAR(20) UNIQUE NOT NULL,
    Category VARCHAR(100),
    Availability BOOLEAN DEFAULT TRUE
);
```
### Transactions Table
```sql
CREATE TABLE Transactions (
    TransactionID INT PRIMARY KEY AUTO_INCREMENT,
    UserID INT,
    BookID INT,
    IssueDate DATE NOT NULL,
    DueDate DATE NOT NULL,
    ReturnDate DATE,
    FineAmount DECIMAL(5,2) DEFAULT 0.00,
    FOREIGN KEY (UserID) REFERENCES Users(UserID),
    FOREIGN KEY (BookID) REFERENCES Books(BookID)
);
```
### Reservations Table
```sql
CREATE TABLE Reservations (
    ReservationID INT PRIMARY KEY AUTO_INCREMENT,
    UserID INT,
    BookID INT,
    ReservationDate DATE NOT NULL,
    Status ENUM('Pending', 'Completed', 'Cancelled') DEFAULT 'Pending',
    FOREIGN KEY (UserID) REFERENCES Users(UserID),
    FOREIGN KEY (BookID) REFERENCES Books(BookID)
);
```
### Fines Table
```sql
CREATE TABLE Fines (
    FineID INT PRIMARY KEY AUTO_INCREMENT,
    UserID INT,
    Amount DECIMAL(5,2) NOT NULL,
    PaidStatus BOOLEAN DEFAULT FALSE,
    PaymentDate DATE,
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);
```
### Book Recommendations Table
```sql
CREATE TABLE BookRecommendations (
    RecommendationID INT PRIMARY KEY AUTO_INCREMENT,
    UserID INT,
    BookID INT,
    RecommendedBookID INT,
    FOREIGN KEY (UserID) REFERENCES Users(UserID),
    FOREIGN KEY (BookID) REFERENCES Books(BookID),
    FOREIGN KEY (RecommendedBookID) REFERENCES Books(BookID)
);
```
## Sample Queries

### Insert Sample Users
```sql
INSERT INTO Users (Name, Email, Phone, UserType) VALUES
('Alice Johnson', 'alice@example.com', '9876543210', 'Member'),
('Bob Smith', 'bob@example.com', '9876543211', 'Staff');
```
### Insert Sample Books
```sql
INSERT INTO Books (Title, Author, ISBN, Category) VALUES
('The Java Handbook', 'Patrick Naughton', '9780743273565', 'Technology'),
('1984', 'George Orwell', '9780451524935', 'Dystopian');
```
### Borrow a Book
```sql
INSERT INTO Transactions (UserID, BookID, IssueDate, DueDate) VALUES (1, 1, CURDATE(), DATE_ADD(CURDATE(), INTERVAL 14 DAY));
UPDATE Books SET Availability = FALSE WHERE BookID = 1;
```
### Return a Book
```sql
UPDATE Transactions SET ReturnDate = CURDATE() WHERE TransactionID = 1;
UPDATE Books SET Availability = TRUE WHERE BookID = 1;
```
### Check Overdue Books
```sql
SELECT * FROM Transactions WHERE DueDate < CURDATE() AND ReturnDate IS NULL;
```
### Apply a Fine for Overdue Books
```sql
UPDATE Transactions SET FineAmount = 50 WHERE DueDate < CURDATE() AND ReturnDate IS NULL;
```
### Reserve a Book (Only if Unavailable)
```sql
INSERT INTO Reservations (UserID, BookID, ReservationDate)
SELECT 1, 2, CURDATE() FROM Books WHERE BookID = 2 AND Availability = FALSE;
```
### Pay Fine
```sql
UPDATE Fines SET PaidStatus = TRUE, PaymentDate = CURDATE() WHERE FineID = 1;
```
### Assign Staff and Admin Roles
```sql
UPDATE Users SET UserType = 'Admin' WHERE Email = 'bob@example.com';
```
### Book Recommendation Query
```sql
INSERT INTO BookRecommendations (UserID, BookID, RecommendedBookID)
SELECT t.UserID, t.BookID, b.BookID 
FROM Transactions t
JOIN Books b ON t.BookID != b.BookID
WHERE t.UserID = 1 LIMIT 5;
```
[![Library Management System Demo](https://img.youtube.com/vi/OBT4NmcsBng/maxresdefault.jpg)](https://youtu.be/OBT4NmcsBng)

🔗 [Watch here](https://youtu.be/OBT4NmcsBng)


