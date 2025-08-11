USE LibraryDB;
SELECT B.Title, B.Genre, A.Name AS AuthorName
FROM Books B
INNER JOIN Authors A ON B.AuthorID = A.AuthorID;
SELECT B.Title, BR.BorrowDate, BR.ReturnDate
FROM Books B
LEFT JOIN Borrow BR ON B.BookID = BR.BookID;
SELECT BR.BorrowID, B.Title, BR.BorrowDate
FROM Borrow BR
RIGHT JOIN Books B ON BR.BookID = B.BookID;
SELECT M.MemberID, M.Name, BR.BorrowID, BR.BorrowDate
FROM Members M
LEFT JOIN Borrow BR ON M.MemberID = BR.MemberID
UNION
SELECT M.MemberID, M.Name, BR.BorrowID, BR.BorrowDate
FROM Members M
RIGHT JOIN Borrow BR ON M.MemberID = BR.MemberID;
SELECT BR.BorrowID, B.Title, M.Name AS MemberName, BR.BorrowDate, BR.ReturnDate
FROM Borrow BR
INNER JOIN Books B ON BR.BookID = B.BookID
INNER JOIN Members M ON BR.MemberID = M.MemberID;
SELECT A.Name AS AuthorName, B.Title
FROM Authors A
LEFT JOIN Books B ON A.AuthorID = B.AuthorID;
SELECT S.Name AS StaffName, BR.BorrowID
FROM Staff S
RIGHT JOIN Borrow BR ON S.StaffID = BR.BorrowID; -- Just a sample, not an actual relationship
SELECT A.Name AS AuthorName, B.Genre
FROM Authors A
CROSS JOIN (SELECT DISTINCT Genre FROM Books) B;
