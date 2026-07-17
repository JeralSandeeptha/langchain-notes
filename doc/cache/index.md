# Caching

`LangChain` supports model response caching to reduce API costs and speed up applications by preventing duplicate calls for identical prompts

---

## In-Memory Caching (Transient)

This stores cache data directly in your application's RAM. It is perfect for local testing and development, but the cache clears completely whenever your application restarts

```python
import langchain
from langchain_core.globals import set_llm_cache
from langchain_core.caches import InMemoryCache
from langchain_openai import ChatOpenAI

# 1. Enable global in-memory caching
set_llm_cache(InMemoryCache())

# 2. Initialize your model
model = ChatOpenAI(model="gpt-4o", temperature=0)

# First call: Sent to OpenAI API (Takes ~1.5 seconds)
response1 = model.invoke("What is the capital of France?")

# Second call: Retrieved instantly from RAM (Takes ~0.001 seconds)
response2 = model.invoke("What is the capital of France?")
```

<br/>

## Database Caching (Persistent)

For production environments, you should persist your cache in a database. This ensures your cache survives application restarts and can be shared across multiple server instances

### 1. SQLite Caching (File-Based Storage)

SQLite is an excellent, zero-configuration file database for lightweight production or long-term local persistence.

```python
from langchain_core.globals import set_llm_cache
from langchain_community.cache import SQLiteCache

# Persists cache locally inside a file named 'langchain.db'
set_llm_cache(SQLiteCache(database_path="langchain.db"))
```

<br/>

### 2. Redis Caching (High-Performance Key-Value Storage)

Redis is ideal for high-concurrency production systems requiring lightning-fast distributed caching.

```python
# Terminal requirement: pip install redis
from langchain_core.globals import set_llm_cache
from langchain_community.cache import RedisCache
from redis import Redis

# Connect to your Redis server instance
redis_client = Redis(host="localhost", port=6379, db=0)
set_llm_cache(RedisCache(redis_client))
```

<br/>

### 3. Semantic (Vector) Caching

Standard database caching requires an exact string match to return a cached item. Semantic caching uses embedding models and vector databases (like `Redis`, `Chroma`, or `Milvus`) to evaluate meaning. It returns a cached answer even if a user asks the question slightly differently.

```python
# Terminal requirement: pip install redis
from langchain_core.globals import set_llm_cache
from langchain_community.cache import RedisSemanticCache
from langchain_openai import OpenAIEmbeddings

# Cache hits trigger if user meaning matches by 95% (distance < 0.05)
set_llm_cache(RedisSemanticCache(
    redis_url="redis://localhost:6379",
    embedding=OpenAIEmbeddings(),
    score_threshold=0.05
))

# Example usage sequence:
# Prompt 1: "Tell me a joke about dogs." -> Calls API & caches response
# Prompt 2: "Give me a dog joke please." -> Cache Hit! (Semantically identical)
```

---

## Quick Selection Matrix

| Cache Type | Lifetime | Match Type | Best Use Case |
| :--- | :--- | :--- | :--- |
| **`InMemoryCache`** | Temporary (RAM) | Exact String | Prototyping & unit tests |
| **`SQLiteCache`** | Persistent (File) | Exact String | Desktop apps & low-traffic sites |
| **`RedisCache`** | Persistent (Server) | Exact String | Scalable production apps |
| **`RedisSemanticCache`** | Persistent (Server) | Meaning Match | Optimizing conversational chat costs |
