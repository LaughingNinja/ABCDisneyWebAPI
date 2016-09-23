# ABCDisneyWebAPI
Take home test
****POSTMAN instructions after SQL below****
-- The web.config ConnectionString will have to be pointed to a valid server on your side.

--You will have to create the SQL database/table/stored procedures prior to running the solution. Here's the SQL code to do that:
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
DECLARE @new_identity INT
BEGIN
INSERT INTO dbo.SystemEvents
(Description)
VALUES
(@description)

SELECT @new_identity = SCOPE_IDENTITY();

SELECT * FROM dbo.SystemEvents
WHERE Id = @new_identity;
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
SELECT * FROM dbo.SystemEvents
WHERE Id = @id;
END
