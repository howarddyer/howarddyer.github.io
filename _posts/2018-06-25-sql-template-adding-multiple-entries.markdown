---
layout: post
title:  "SQL Template For Adding Multiple Entries"
date:   2018-06-25 09:00:00
description: "A SQL schema script template for adding multiple entries to table (if not currently present)."
label: note
---

<p>Updates required on <strong>@Entries</strong> temp table and <strong>Destination</strong> table.</p>

``` sql

DECLARE @Entries TABLE
(
    Name VARCHAR(10) NOT NULL UNIQUE,
    Description VARCHAR(10)
)

INSERT INTO @Entries 
VALUES
('entry1', 'Entry 1'),
('entry2', 'Entry 2'),
('entry3', 'Entry 3'),
('entry4', 'Entry 4'),
('entry5', 'Entry 5')

WHILE (SELECT COUNT(*) FROM @Entries ) > 0
BEGIN
    DECLARE @Name VARCHAR(10)
    SET @Name = (SELECT TOP 1 Name FROM @Entries)

    IF NOT EXISTS (SELECT 1 FROM Destination WHERE Name = @Name)
    BEGIN
        DECLARE @Description VARCHAR(10)
        SET @Description = (SELECT TOP 1 Description FROM @Entries)

        INSERT INTO Destination VALUES (@Name, @Description)
    END

    DELETE FROM @Entries WHERE Name = @Name
END

```