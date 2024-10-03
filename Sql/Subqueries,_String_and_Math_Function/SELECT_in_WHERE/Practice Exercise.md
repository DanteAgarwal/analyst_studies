# Practice Exercise on Subqueries in WHERE Clause in SQL

## 1 - Find Books by UK Authors:
Retrieve the titles of books written by authors from the United Kingdom.

```sql
SELECT Title, AuthorID
FROM Books_list
WHERE AuthorID IN (
    SELECT AuthorID 
    FROM Authors
    WHERE Country = 'United Kingdom'
);
```

## 2 -Books Not Sold Yet: 
List the books that have not been sold.

```sql
select * from Books_list 
where Bookid not in (select product_id from sales )
```

## 3 -Books Published After All Sales: 
Retrieve the titles of books that were published after the most recent sale.

```sql
select BookID,Title,AuthorID,GenreID,Price from Books_list 
where PublishedDate > (select max(SaleDate) from Sales_lists )
```


## 4 -Genres with No Books: 
Identify genres that do not have any books listed.

```sql
select * from Genres
where GenreID not in (select GenreID from Books_list  )
```

## 5 -Books by Authors with Specific Books: 
Retrieve the titles of books written by authors who have also written 'A Game of Thrones'.

```sql
SELECT Title 
FROM Books_list 
where AuthorID = (SELECT AuthorID 
                  FROM Books_list 
                  where Title = 'A Game of Thrones');
```

## 6. Books with Less Than Average Price: 
List the titles of books that are priced less than the average book price.

```sql
select Title from Books_list 
where Price <(select avg(Price ) from Books_list)
```
