# ABCDisneyWebAPI
Take home test
You will have to create the SQL database/table prior to running the solution. Here's the SQL code to do that:
CREATE DATABASE Events;
GO

USE Events;
CREATE TABLE SystemEvents
(
Id int IDENTITY(1,1) PRIMARY KEY CLUSTERED,
Description varchar(255) NOT NULL
)

CREATE PROCEDURE [dbo].[GetSystemEvents] @id INT
AS
IF(@id != 0)
	BEGIN
	SELECT * FROM dbo.SystemEvents
	WHERE id = @id
	END
ELSE
	BEGIN
	SELECT * FROM dbo.SystemEvents
	END

CREATE PROCEDURE dbo.AddSystemEvent @description VARCHAR(255)
AS
BEGIN
INSERT INTO dbo.SystemEvents
(Description)
VALUES
(@description)
END

CREATE PROCEDURE [dbo].[DeleteSystemEvent] @id INT
AS
BEGIN
DELETE FROM dbo.SystemEvents
WHERE id = @id
END

CREATE PROCEDURE dbo.UpdateSystemEvent @id INT, @description VARCHAR(255)
AS
BEGIN
UPDATE dbo.SystemEvents
SET Description = @description
WHERE Id = @id
END
