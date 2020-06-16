# Redis

Redis is Non-SQL database or sometimes we called in-memory database.

Non-SQL databases have different types: Key-Value \(Redis\), Document \(MongoDB\), Graph - \(Neo4j\).

Redis is what we call a key-value store \(similar to how we handle JS Object\)

**Characteristics:**

* In-memory database which is very fast
* Use for short lived data in our applications, like sessions or web page headcounts
* Don't have large data sets like MongoDB. Only small data which allow us to keep it in machine memory and not on disk
* Even though the data is stored in memory, it does take a snapshot occasionally to save the current data contents onto the disk which, is great to recover from, when there's unexpected shutdowns. Although we might lose the some/ latest information.
* Handle 5 data types: string, hash, list, set and sorted set.

