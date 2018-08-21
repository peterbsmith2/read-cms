+++
chapter = "Databases"
title = "Cracking The Coding Interview, 6th Edition"
subtitle = "189 Programming Questions & Solutions"
author = "Gayle Laakmann McDowell"
chapter_number = 18
amazon = "https://www.amazon.com/Cracking-Coding-Interview-Programming-Questions/dp/0984782850/ref=sr_1_1?ie=UTF8&qid=1518885012&sr=8-1&keywords=cracking+the+coding+interview" 
bn = "https://www.barnesandnoble.com/w/cracking-the-coding-interview-gayle-laakmann-mcdowell/1122334602?ean=9780984782857"
books = ["Cracking The Coding Interview, 6th Edition"]
+++

### Denormalized vs. Normalized Databases
Normalized databases are designed to minimize redundancy, while denormalized databases are designed to optimize read time.  
  
In a traditional normalized database with data like `Courses` and `Teachers`, `Courses` might contain a column called `TeacherID`, which is a foreign key to `Teacher`. One benefit of this is that information about the teacher (name, address, etc.) is only stored once in the database. The drawback is that many common queries will require expensive joins.  
  
Instead, we can denormalize the database by storing redundant data. For example, if we knew that we would have to repeat this query often, we might store the teacher's name in the `Courses` table. Denormalization is commonly used to create highly scalable systems.  