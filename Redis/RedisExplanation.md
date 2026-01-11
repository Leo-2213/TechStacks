
# Redis Crash Course – Complete Notes

> These notes summarize a Redis crash-course style explanation covering fundamentals, architecture, use cases, and practical concepts.

---

## 1. What is Redis?

Redis stands for **Remote Dictionary Server**.  
It is an **open-source, in-memory key–value data store** commonly used as:

- Cache
- Database
- Message broker

Redis stores data in **RAM**, which makes it extremely fast compared to disk-based databases.

---

## 2. Why Redis is Fast

Redis achieves high performance because:

- Data is stored in memory (RAM)
- Most operations are **O(1)**
- Single-threaded event loop (no thread context switching)
- Optimized internal data structures

---

## 3. Redis Use Cases

Redis is commonly used for:

- Caching frequently accessed data
- Session management
- Rate limiting
- Leaderboards
- Queues
- Real-time analytics
- Pub/Sub messaging

---

## 4. Redis as Cache vs Database

### Redis as Cache
- Stores temporary data
- Reduces database load
- Uses TTL for automatic expiration

### Redis as Database
- Supports persistence
- Can recover data after restart
- Limited querying compared to relational databases

---

## 5. Redis Architecture

- Client–Server model
- Redis runs as a standalone server
- Clients communicate using TCP
- Data primarily resides in memory

---

## 6. Redis Persistence

Even though Redis is in-memory, it supports disk persistence.

### RDB (Redis Database Snapshot)
- Takes periodic snapshots of memory
- Faster restart
- Possible data loss

### AOF (Append Only File)
- Logs every write operation
- Higher durability
- Slower than RDB

Both can be enabled together for better reliability.

---

## 7. Redis Data Types

| Data Type | Description | Use Case |
|---------|------------|---------|
| String | Key-value | Simple caching |
| Hash | Map-like | User profiles |
| List | Ordered | Queues |
| Set | Unique items | Tags |
| Sorted Set | Score-based | Leaderboards |
| Stream | Append-only log | Event streaming |
| Bitmap / HyperLogLog | Bit operations | Analytics |

---

## 8. Common Redis Commands

```bash
SET key value
GET key
DEL key
EXPIRE key 300
INCR counter
DECR counter
HSET user:1 name "John"
HGET user:1 name
```

---

## 9. Redis Caching Pattern (Cache-Aside)

1. Application checks Redis cache
2. If cache hit → return data
3. If cache miss:
    - Fetch from database
    - Store result in Redis
    - Return response

---

## 10. TTL (Time To Live)

- TTL defines how long a key lives
- After expiration, Redis removes the key automatically
- Prevents stale data

```bash
EXPIRE user:101 600
```

---

## 11. Eviction Policies

When memory is full, Redis evicts keys using policies like:

- LRU (Least Recently Used)
- LFU (Least Frequently Used)
- allkeys-lru
- volatile-lru

---

## 12. Redis for Rate Limiting

```bash
INCR api:user:1
EXPIRE api:user:1 60
```

---

## 13. Redis for Leaderboards

```bash
ZADD leaderboard 1500 user1
ZADD leaderboard 1800 user2
```

---

## 14. Redis Pub/Sub

- Publisher sends messages
- Subscribers receive messages in real time

---

## 15. Advantages of Redis

- Extremely fast
- Easy to use
- Supports multiple data structures
- Scales well with replication and clustering

---

## 16. Limitations of Redis

- RAM is expensive
- Not suitable for complex queries
- Data loss possible without proper persistence

---

## 17. Summary

Redis is a powerful in-memory data store used primarily for caching and real-time data access.

---

## Interview One-Liner

> Redis is an in-memory key–value data store used for caching and fast data access, supporting rich data structures and optional persistence.
