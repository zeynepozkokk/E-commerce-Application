# E-commerce-Application

-- Customers tablosu
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(100),
    Email VARCHAR(100),
    Phone VARCHAR(20),
    Address VARCHAR(200)
);

-- Products tablosu
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(100),
    Price DECIMAL(10, 2),
    StockQuantity INT,
    Category VARCHAR(50)
);

-- Orders tablosu
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    OrderDate DATE,
    CustomerID INT,
    TotalAmount DECIMAL(10, 2),
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);

-- OrderDetails tablosu
CREATE TABLE OrderDetails (
    OrderDetailID INT PRIMARY KEY,
    OrderID INT,
    ProductID INT,
    Quantity INT,
    UnitPrice DECIMAL(10, 2),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
    FOREIGN KEY (ProductID) REFERENCES Products(ProductID)
);
-- Customers tablosuna veri ekleme
INSERT INTO Customers (CustomerID, CustomerName, Email, Phone, Address) 
VALUES (1, 'Ayşe Yılmaz', 'ayse@example.com', '555-1111', '123 Elm St'), 
       (2, 'Ahmet Demir', 'ahmet@example.com', '555-2222', '456 Oak St'),
       (3, 'Fadime Kaya', 'fadime@example.com', '555-3333', '789 Pine St');

-- Products tablosuna veri ekleme
INSERT INTO Products (ProductID, ProductName, Price, StockQuantity, Category)
VALUES (1, 'Laptop', 999.99, 50, 'Electronics'), 
       (2, 'Headphones', 199.99, 150, 'Accessories'),
       (3, 'Coffee Maker', 79.99, 75, 'Appliances');

-- Orders tablosuna veri ekleme
INSERT INTO Orders (OrderID, OrderDate, CustomerID, TotalAmount) 
VALUES (1, '2024-09-09', 1, 1199.97),
       (2, '2024-09-10', 2, 79.99);

-- OrderDetails tablosuna veri ekleme
INSERT INTO OrderDetails (OrderDetailID, OrderID, ProductID, Quantity, UnitPrice)
VALUES (1, 1, 1, 1, 999.99), 
       (2, 1, 2, 1, 199.99),
       (3, 2, 3, 1, 79.99);
