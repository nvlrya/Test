# Test

``query
CREATE DATABASE CourseNet

USE CourseNet

CREATE TABLE Customer(
CustomerID CHAR(5) PRIMARY KEY,
CustomerName VARCHAR(100) NOT NULL, 
CustomerGender VARCHAR(10) CONSTRAINT GenderCust CHECK(CustomerGender LIKE 'Female' OR CustomerGender LIKE 'Male'),
CustomerPhone VARCHAR(13) NOT NULL,
CustomerAddress VARCHAR(50) NOT NULL,
CustomerAge INT,
)

CREATE TABLE SellTransaction(
TransactionID INT IDENTITY(1,1)	PRIMARY KEY,			
CustomerID CHAR(5) REFERENCES Customer(CustomerID) ON UPDATE CASCADE ON DELETE CASCADE,
StaffID CHAR(5) REFERENCES Staff(StaffID) ON UPDATE CASCADE ON DELETE CASCADE,
TransactionDate DATE,
PaymentType VARCHAR(10),
)

SELECT * FROM Customer

ALTER TABLE Customer
ADD CONSTRAINT CekCustomer CHECK(CustomerID LIKE 'CU[0-9][0-9][0-9]')
