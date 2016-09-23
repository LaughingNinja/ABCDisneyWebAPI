# ABCDisneyWebAPI
Take home test
You will have to create the SQL database/table prior to running the solution. Here's the SQL code to do that:
CREATE DATABASE Events;
USE Events;
CREATE TABLE SystemEvents
(
Id int IDENTITY(1,1) PRIMARY KEY CLUSTERED,
Description varchar(255) NOT NULL
)
