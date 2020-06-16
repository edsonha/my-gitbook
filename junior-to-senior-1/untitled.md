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

```yaml
// Examples of simple redis command:

SET name "String"
GET name 
EXISTS name
DEL name
EXPIRE name ${num}
SET counter 1000
INCRBY counter 55 // 1055
DECR counter //1054
MSET a 2 b 5 //Multiple Set
MGET a b //Multiple Get
```

**Hash:**

```yaml
// Similar to JS object

HMSET user id 45 name "John"
HGET user id
HGET user name
HGETALL user //id, 45, name, John
```

**List:**

*  Insertion is really really fast. Useful when you have long list and you need to add element quickly.
* Take a bit of time when searching. Use sorted list which is better for searching.

```yaml
// Similar to linked list

LPUSH mylist 10
RPUSH mylist hello
LPUSH mylist there
LRANGE mylist 0 2 // there, 10, hello
LPOP mylist // there
```

**Set and Sorted Set:**

Set is unordered collection of string and sorted set is ordered. In set, there is no duplicate value.

The difference between set and sorted set is in sorted set, for every member of a sorted set is associated with a score and this score allows it to be ordered from smallest to greatest.

```yaml
SADD myset 1 2 3 4 5
SMEMBERS myset // 1 2 3 4 5
SADD myset 1 2 4 6 // 1 2 3 4 5 6
SISMEMBER myset 5 // 1 or yes


ZADD team 50 "Alice"
ZADD team 40 "Bob"
ZADD team 1 "Charlie"
ZRANGE team 0 2 // Charlie Bob Alice
ZRANK team "Bob" // 1
```

