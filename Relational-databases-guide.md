# Relational databases (MySql)

A relational database is a type of database. It uses a structure that allows us to identify and access data in relation to another piece of data in the database. Often, data in a relational database is organized into tables. In relational databases, tables related to one another are linked and queries on the database can produce relations between these tables. Non-relational databases separate these relations into different sets of documents, which are then stored together in a flexible data format. 

| Name    | Age|
| ------  | ---|
| Maria   | 24 |
| Isabelle| 21 |
| Ana     | 30 |
| Regina  | 36 |

#### What is a Relational Database Management System (RDBMS)?

A relational database management system (RDBMS) is a program that allows you to create, update, and administer a relational database. Most relational database management systems use the SQL language to access the database.

#### What is SQL?

SQL (Structured Query Language) is a programming language used to communicate with data stored in a relational database management system. SQL syntax is similar to the English language, which makes it relatively easy to write, read, and interpret.

Many RDBMSs use SQL (and variations of SQL) to access the data in tables. For example, SQLite is a relational database management system. SQLite contains a minimal set of SQL commands (which are the same across all RDBMSs). Other RDBMSs may use other variants.

#### Advantages of using relational databases

- **Ease of Use**: Users can easily access/retrieve their required information within seconds without indulging in the complexity of the database. 

- **Accuracy**: They’re strictly defined and well-organized, so data doesn’t get duplicated.

- **Collaboration**: Multiple users can access the database to retrieve information at the same time and even if data is being updated.

- **Security**: Data is secure as Relational Database Management System allows only authorized users to directly access the data.

- **Data Integrity and Structure**: Relational databases work with structured data. They support [ACID](https://en.wikipedia.org/wiki/ACID) transactional consistency and provide a flexible way to structure data that is not possible with other database technologies. Key features of relational databases include the ability to make two tables look like one, join multiple tables together on key fields, create complex indexes that perform well and are easy to manage, and maintain data integrity for maximum data accuracy. 

- **Language Standardization**: All relational databases use SQL as their language. Non-relational databases usually use their unique language to set up, manage, and query data.

#### Disadvantages of using relational databases

- **Lack of Scalability**: While using the relational database over multiple servers, its structure changes and becomes difficult to handle, especially when the quantity of the data is large. Due to this, the data is not scalable on different physical storage servers. Ultimately, its performance is affected i.e. lack of availability of data and load time etc. As the database becomes larger or more distributed with a greater number of servers, this will have negative effects like latency and availability issues affecting overall performance.

- **Maintenance**: The maintenance of the relational database becomes difficult over time due to the increase in the data. Developers and programmers have to spend a lot of time maintaining the database.

- **Complexity in Structure**: Relational databases can only store data in tabular form which makes it difficult to represent complex relationships between objects. Unlike a relational database, NoSQL databases don't require a schema. This means that NoSQL can handle unstructured or semi-structured data in different formats.

- **Decrease in performance over time**: The relational database can become slower, not just because of its reliance on multiple tables. When there is a large number of tables and data in the system, it causes an increase in complexity. It can lead to slow response times over queries or even complete failure for them depending on how many people are logged into the server at a given time.

- **Physical Storage**: A relational database is comprised of rows and columns, which requires a lot of physical memory because each operation performed depends on separate storage. The requirements of physical memory may increase along with the increase of data.


### Popular Relational Database Management Systems

SQL syntax may differ slightly depending on which RDBMS you are using. Here is a brief description of popular RDBMSs:

#### MySQL

MySQL is the most popular open source SQL database. It is typically used for web application development, and often accessed using PHP.

The main advantages of MySQL are that it is easy to use, inexpensive, reliable (has been around since 1995), and has a large community of developers who can help answer questions.

Some of the disadvantages are that it has been known to suffer from poor performance when scaling, open source development has lagged since Oracle has taken control of MySQL, and it does not include some advanced features that developers may be used to.

#### PostgreSQL

PostgreSQL is an open source SQL database that is not controlled by any corporation. It is typically used for web application development.

PostgreSQL shares many of the same advantages of MySQL. It is easy to use, inexpensive, reliable and has a large community of developers. It also provides some additional features such as foreign key support without requiring complex configuration.

The main disadvantage of PostgreSQL is that it can be slower in performance than other databases such as MySQL. It is also slightly less popular than MySQL.

#### SQLite

SQLite is a popular open source SQL database. It can store an entire database in a single file. One of the most significant advantages this provides is that all of the data can be stored locally without having to connect your database to a server.

SQLite is a popular choice for databases in cellphones, PDAs, MP3 players, set-top boxes, and other electronic gadgets.

### Conclusion

Relational databases are traditionally used to manage data in an organization. The main benefits of using relational databases are that they can be easily queried, allow for the use of stored procedures to manipulate data, and provide a consistent database design. They also have limitations when it comes to high volume transactions or large amounts of data storage, the issue of speed can arise. Best used for applications needing complex transactions and structured data, like financial systems.

#### Resources
- [Relational Database Benefits and Limitations](https://databasetown.com/relational-database-benefits-and-limitations/)