 # 1. Sharding

### What is sharding?

Sharding is the process of breaking up a large database table into smaller, distinct chunks called `shards`. These shards can be stored on different physical servers, and as a whole they make up a single logical table.
All shards have the same columns but entirely different and unrelated data.


This practice is also referred to as `horizontal partitioning` . 

### Benefits of Sharding

* As a database grows in size, limitations in CPU power, memory, and storage capacity can cause poor performance. In a sharded architecture, since each shard is responsible for serving only a portion of the entire dataset, a network of smaller, cheaper machines can be used in place of one big expensive server.
Thus sharding facilitates `horizontal scaling`.

* Sharding can also improve query response time. As a database table grows larger, some queries will take longer to execute because of the sheer number of rows that needed to be read before a result set is ready. With a sharded database, queries are faster since each shard only ever holds a small subset of the entire table.  

* Sharding can make a system more reliable. If an unsharded database becomes unavailable, this can cause the entire system to stop working for all users. However in the case of a sharded database, if one shard is unavailable, only a subset of users would be affected.

### Sharding Architectures

* **Hash Sharding:** This involves using data from a specific column on the sharded table to generate a hash. The hash value determines which shard/partition the new row will go to. This strategy is great for evenly distributing data among shards and preventing hotspots.

* **Range Sharding:** This involves sharding the data based on the ranges of a given value. E.g, a table that stores product information can be sharded based on price ranges. Items in that cost between $1 - $9 could make up one shared, items in the range $10 - $14 could make up another shard, and so on. While Range sharding is easy to implement, it doesn't ensure that data is evenly between shards.

### Disadvantages of Sharding

* Sharding is complex and if not done correctly can lead to lost data or corrupted tables.

* Shards can become unbalanced i.e some shards can end up storing much more data than others. Unevenly distributed data between shards could mean the servers holding some shards would have a handle a disproportionate amount of work.

* It is very difficult to return a sharded database back to an unsharded state. 

* Not all database management systems support sharding. Doing it manually carries significant risk.

# 2. Transactions

A database transaction is a group of read/write operations which are treated as a single logical unit. A transaction is either commited when all operations complete successfully or rolled back if any fail.

Transactions ensure that data is left in a consistent state in the event of a failure, and provide isolation between the different processes that may attempt to access the database concurrently.

# 3. Indexes

An index is key-value data structure used to speed up database queries. 

Indexing is not advisable if the table is constantly been written to. This is because each write has to update the index, and this renders them unusable until the update is done.

**Clustered Indexes:** A clustered index will cause a table to be sorted in the same order as the index. There can be only one clustered index per table. Some database engines automatically create a clustered index using the table's primary key column. A clustered index uses the leaf nodes of a B-tree for storage of the data pages. For a table without a clustered index, data is stored in a heap, a data structure without order.


**Non-clustered Indexes:** These have a structure separate from the table data. A table can have more than one non-clustered index. These kind of indexes helps improve performance of queries involving columns which are not the primary key. This index stores a pointer to the location of the data and doesn't store data pages in the index.


# 4. Query Optimization Techniques

caching

indexes

sharding



#### References

* [Digital Ocean Tutorial | Understanding Database Sharding](https://www.digitalocean.com/community/tutorials/understanding-database-sharding)
* [YugaByteDB | How Sharding Works](https://blog.yugabyte.com/how-data-sharding-works-in-a-distributed-sql-database/)
* [ A Primer on DB Replication](https://www.brianstorti.com/replication/)
* [A Beginner's Guide to ACID and DB Transactions](https://vladmihalcea.com/a-beginners-guide-to-acid-and-database-transactions/)
* [FreeCodeCampe | A Look at Indexing](https://www.freecodecamp.org/news/database-indexing-at-a-glance-bb50809d48bd/)
* [Guru99 | Clustered vs Non-clustered Index](https://www.guru99.com/clustered-vs-non-clustered-index.html#1)
* [Clustered vs Non-clustered Indexes](https://medium.com/fintechexplained/clustered-vs-non-clustered-index-8efed55ed7b9)