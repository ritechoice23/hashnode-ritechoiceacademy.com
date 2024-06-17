---
title: "A quick guide to SQL Joins"
datePublished: Wed Mar 20 2024 08:34:18 GMT+0000 (Coordinated Universal Time)
cuid: cltzjrs6a000309l56k0ye8aa
slug: a-quick-guide-to-sql-joins
tags: sql-server, sql, sqltutorial

---

SQL joins is your go-to when it comes to combining data from multiple tables in a database. But with different join types, it can get confusing, my goal for this post is to clear your confusion.

So let's take a look at the different joins available.

* **Inner Join:** Returns data only when there's a match in both tables. Think of it as a matchmaker for related info.
    
* **Left Join:** Keeps all data from the left table (like a customer list) and adds matching data from the right, filling in gaps with nulls. Great for complete customer views.
    
* **Right Join:** Prioritizes the right table (products perhaps) and includes all its data, attaching any relevant info from the left table (reviews maybe). Useful for product analysis.
    
* **Full Join:** The inclusive type, including all rows from both tables with nulls for missing matches. Shows the whole picture.
    

**Need a cheat sheet?** Here's a table summarizing the joins:

| Join Type | Result Set | Use Case |
| --- | --- | --- |
| Inner Join | Matching rows only | Retrieving related data |
| Left Join | All rows from the left table matched data from the right (NULLs for non-matches) | Keeping all left table data with related info from the right |
| Right Join | All rows from the right table matched data from the left (NULLs for non-matches) | Keeping all right table data with related info from the left |
| Full Join | All rows from both tables (NULLs for non-matches) | Seeing all data, regardless of matches |

If you have any questions, you can shoot in the comment below.