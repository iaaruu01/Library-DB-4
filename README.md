
# 📊 Task 4 – Aggregate Functions and Grouping

## 🎯 Objective

Use **aggregate functions** (`SUM`, `COUNT`, `AVG`) along with `GROUP BY` and `HAVING` clauses to analyze and summarize tabular data in a **Library Management System**.

---

## 🛠 Tools Used

- MySQL Workbench / DB Browser for SQLite
- GitHub for version control
- SQL scripts

---

##  Repository Contents

| File Name               | Description                            |
|------------------------|----------------------------------------|
| `Library-DB-Schema-1.sql` | Initial table schema setup           |
| `Library-DB-2.sql`        | Additional data insertions           |
| `Library-DB-3.sql`        | Finalized/populated sample data      |
| `task4.sql`              |  Solutions to Task 4 queries         |
| `README.md`              | This documentation                    |

---

##  Queries Overview (`task4.sql`)

### 1. Total Books per Author
```sql
SELECT AuthorID, COUNT(BookID) AS total_books 
FROM book 
GROUP BY AuthorID;
```

### 2. Total Books in Each Category
```sql
SELECT CategoryID, COUNT(BookID) AS total_books 
FROM book 
GROUP BY CategoryID;
```

### 3. Book Issued Count
```sql
SELECT BookID, COUNT(BookID) AS issued_count 
FROM loan 
GROUP BY BookID;
```

### 4. Books Borrowed per Member
```sql
SELECT MemberID, COUNT(BookID) AS books_borrowed 
FROM loan 
GROUP BY MemberID;
```

### 5. Members Who Borrowed Books by Category
```sql
SELECT category.Name, COUNT(DISTINCT loan.MemberID) AS total_members 
FROM loan 
JOIN book ON loan.BookID = book.BookID 
JOIN category ON book.CategoryID = category.CategoryID 
GROUP BY category.Name;
```

### 6. Average Number of Loans per Member
```sql
SELECT AVG(loans) 
FROM (SELECT COUNT(*) AS loans FROM loan GROUP BY MemberID) AS member_loans;
```

### 7. Staff Count by Role
```sql
SELECT Role, COUNT(*) AS staff_count 
FROM staff 
GROUP BY Role;
```

### 8. Distinct Titles per Author
```sql
SELECT AuthorID, COUNT(DISTINCT Title) AS distinct_titles 
FROM book 
GROUP BY AuthorID;
```

---

##  Author

**Aarya Gupta**  
