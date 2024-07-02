# Bigtable

Google Bigtable is a _NoSQL_ distributed storage system that can scale to billions of rows and thousands of columns, enabling you to store terabytes or even petabytes of data. A single value in each row is indexed; this value is known as the row key. Bigtable is ideal for storing large amounts of single-keyed data with low latency.
Bigtable tables are **sparse**, meaning if a column _is not used_ for a particular row, it _does not take up space_.


#### Advantages of using Bigtable:

- **Low latency and high throughput**: Bigtable is a key-value and wide-column store. It is ideal for applications that need high throughput and scalability for key-value data, where each value is typically no larger than 10 MB. 

- **Write and read scalability with no limits**: Bigtable decouples compute resources from data storage, which makes it possible to transparently adjust processing resources. Each additional node can process reads and writes equally well, providing effortless horizontal scalability.

- **Data model flexibility**

- **From a single zone up to eight regions at once**

- **Easy migration from NoSQL databases**


#### Disadvantages of using Bigtable:

- **Costs**: It is not free.

- **Not open source**: Users must rely on Google for support and updates.

- **Expects structures data**: While it is not a relational database, it still expects more structure than other NoSql databases, e.g. document DBs

- **Complexity**: It can be more complex to set up and manage than other database systems, which can be a concern for organizations that do not have the resources or expertise to manage a complex database system. It is not as popular as relational DBs that have lots of resources available on the internet.



#### Resources
- [Bigtable](https://cloud.google.com/bigtable/?hl=en)
- [Bigtable docs](https://cloud.google.com/bigtable/docs/overview)
- [What is Google Bigtable?](https://www.zuar.com/blog/what-is-google-bigtable/)