# SQLServer
Find the URL Reservation using
Get URL Reservation
````
netsh http show urlacl
````

It was due to SQL Reporting services having reserved the http://+:80/Reports url in http.sys.
I didn't actually have reporting services installed, but it apparently still reserved the url.

I fixed it with the following command:
````
netsh http delete urlacl url=http://+:80/Reports
````
#  create a user in Microsoft SQL Server with permissions to insert rows into a specific table only

To create a user in Microsoft SQL Server with permissions to insert rows into a specific table (e.g., Computers) but not delete or update existing rows, you would typically use a combination of GRANT and DENY statements. Below is an example of how you might achieve this:
Assuming you already have a user or need to create a new user, let's create a user named "AssetUser" and grant the necessary permissions:
```
-- Create a login for the user (if not exists)
CREATE LOGIN AssetUser WITH PASSWORD = 'YourPassword';

-- Create a user in the specific database (if not exists)
USE YourDatabase;
CREATE USER AssetUser FOR LOGIN AssetUser;

-- Grant INSERT permission on the Computers table
GRANT INSERT ON dbo.Computers TO AssetUser;

-- Deny DELETE and UPDATE permissions on the Computers table
DENY DELETE, UPDATE ON dbo.Computers TO AssetUser;

-- Grant Select to user on perticular Table
GRANT SELECT ON YourOtherTable TO YourUser;
```
