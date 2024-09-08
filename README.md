SQL for Data Science Module 3 

Question 1
Using a subquery, find the names of all the tracks for the album "Californication".

CODE

SELECT t.Name 
From tracks t
JOIN Albums a ON t.Albumid = a.Albumid
WHERE a.Title ='Californication';

ANS Porcelain

Question 2

All of the questions in this quiz refer to the open source Chinook Database. Please familiarize yourself with the 
ER diagram
in order to familiarize yourself with the table and column names in order to write accurate queries and get the appropriate answers.
Find the total number of invoices for each customer along with the customer's full name, city and email.

CODE

SELECT c.CustomerId, c.FirstName, c.LastName, c.City, c.Email, COUNT(i.InvoiceId) 
FROM Customers c 
JOIN Invoices i ON c.CustomerId = i.CustomerId 
WHERE c.FirstName = 'František' AND c.LastName = 'Wichterlová'
GROUP BY c.CustomerId, c.FirstName, c.LastName, c.City, c.Email;

ANS: František, Wichterlová, Prague, frantisekw@jetbrains.com



Question 3

Retrieve the track name, album, artistID, and trackID for all the albums.

CODE

SELECT Tracks.Name, Tracks.TrackId, Albums.Title , Artists.Name
FROM Artists
JOIN Albums ON Artists.Artistid = Albums.Artistid
JOIN Tracks ON Albums.Albumid = Tracks.Trackid
WHERE TrackID = '12';

ANS: Breaking The Rules


Question 4

Retrieve a list with the managers last name, and the last name of the employees who report to him or her.

CODE

SELECT Mgr.LastName AS Manager, Employees.LastName AS worker
FROM Employees
LEFT JOIN Employees AS Mgr ON Employees.ReportsTo = Mgr.EmployeeId;

ANS: CALLAHAN AND KING


Question 5

Find the name and ID of the artists who do not have albums. 

CODE

SELECT Albums.Title, Artists.Name, Artists.ArtistId
FROM Artists
LEFT JOIN Albums on Artists.ArtistId = Albums.ArtistId
where Albums.Title is Null; 

ANS: Gilberto

Question 6 Use a UNION to create a list of all the employee's and customer's first names and last names ordered by the last name in descending order.

CODE

SELECT LastName 
from Employees
UNION 
SELECT LastName 
from Customers
ORDER BY LastName DESC 

ANS Taylor

Question 7 See if there are any customers who have a different city listed in their billing city versus their customer city.

CODE

SELECT Customers.CustomerId,Customers.city ,Invoices.BillingCity
FROM Customers
JOIN Invoices ON Customers.CustomerId = Invoices.CustomerId
WHERE Customers.City <> Invoices.BillingCity;

ANS No customers have a different city listed in their billing city versus customer city.

