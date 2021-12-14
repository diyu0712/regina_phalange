# regina_phalange
#Basic Sql Database for a Taxi Management System
CREATE TABLE DRIVER (
   Driver_id VARCHAR(10),
   F_name VARCHAR(10),
   L_name VARCHAR(20),
   Conatct_no bigint,
   PRIMARY KEY (Driver_id)
);
CREATE TABLE TAXI (
   Taxi_id VARCHAR(10),
   Taxi_type VARCHAR(20),
   Status_ VARCHAR(10),
   Driver_id VARCHAR(10),
   PRIMARY KEY(Taxi_id),
   FOREIGN KEY(Driver_id) REFERENCES DRIVER(Driver_id)
);


CREATE TABLE  USER_TBL (
   Usr_id VARCHAR(10) NOT NULL,
   Name_ VARCHAR(20),
   Contat_no VARCHAR(20),
   Taxi_id VARCHAR(10),
   PRIMARY KEY (Usr_id),
   FOREIGN KEY (Taxi_id) REFERENCES TAXI(Taxi_id)
);
CREATE TABLE  TRIP_DETAILS (
   Trip_id VARCHAR(10),
   Trip_date DATE,
   Driver_id VARCHAR(10),
   Usr_id VARCHAR(10),
   Taxi_id VARCHAR(10),
   PRIMARY KEY (Trip_id),
   FOREIGN KEY (Driver_id) REFERENCES DRIVER(Driver_id), 
   FOREIGN KEY (Usr_id) REFERENCES USER_TBL(Usr_id),
   FOREIGN KEY (Taxi_id) REFERENCES TAXI(Taxi_id)
);

CREATE TABLE BILL_DETAILS (
   Bill_no VARCHAR(10) ,
   Total_amt decimal(10,2),
   Usr_id VARCHAR(10),
   Trip_id VARCHAR(10),
   PRIMARY KEY (Bill_no),
   FOREIGN KEY (Usr_id) REFERENCES USER_TBL(Usr_id),
   FOREIGN KEY (Trip_id) REFERENCES TRIP_DETAILS(Trip_id)
);
INSERT INTO DRIVER VALUES ('7a','Ramesh','S',5321);
INSERT INTO DRIVER VALUES('7b','Suresh','S',2121);
INSERT INTO DRIVER VALUES('7c','Mahesh','S',41624);
INSERT INTO TAXI VALUES('9a','Mini','Booked','7a');
INSERT INTO TAXI VALUES('9b','Mini','Booked','7a');
INSERT INTO TAXI VALUES('9c','Micro','Booked','7b');
INSERT INTO TAXI VALUES('9d','Suv','Booked','7c');
INSERT INTO TAXI VALUES('9e','Suv','Booked','7a');
INSERT INTO USER_TBL VALUES('5a','Yudishtir',66589,'9a');
INSERT INTO USER_TBL VALUES('5b','Bheem',01207,'9b');
INSERT INTO USER_TBL VALUES('5c','Arjun',35641,'9c');
INSERT INTO USER_TBL VALUES('5d','Nakul',54483,'9d');
INSERT INTO USER_TBL VALUES('5e','Sahadev',84077,'9e');
INSERT INTO TRIP_DETAILS VALUES('4a','2021-03-15','7a','5a','9a');
INSERT INTO TRIP_DETAILS VALUES('4b','2021-04-3','7a','5b','9b');
INSERT INTO TRIP_DETAILS VALUES('4c','2021-07-21','7b','5c','9c');
INSERT INTO TRIP_DETAILS VALUES('4d','2021-06-16','7c','5d','9d');
INSERT INTO TRIP_DETAILS VALUES('4e','2021-06-08','7a','5e','9e');
INSERT INTO BILL_DETAILS VALUES('1a',620.23,'5a','4a');
INSERT INTO BILL_DETAILS VALUES('1b',170.54,'5b','4b');
INSERT INTO BILL_DETAILS VALUES('1c',620.00,'5c','4c');
INSERT INTO BILL_DETAILS VALUES('1d',520.87,'5d','4d');
INSERT INTO BILL_DETAILS VALUES('1e',470.73,'5d','4d');
select * from driver;
select * from taxi;
select * from USER_TBL;
select * from TRIP_DETAILS;
select * from BILL_DETAILS;
