# Redis
Redis info

Redis is an in memory database using based on key:value priciple, it is very fast, operated by cli, is used in caching to access pre-queried data for fast access.

<h1>Getting Started + Basics</h1>

<ul>
  <li>brew install redis {To install redis}</li>
  <li>redis-server {To start redis}</li>
  <li>redis-cli {run in parallel terminal to run redis commands}</li>
  <li>SET name rahul {Set key value pair}</li>
  <li>GET name {get value from key}</li>
  <li>DEL name {delete key value pair}</li>
  <li>EXISTS name {checks if K-V pair is present}</li>
  <li>KEYS * {Get all keys in redis cache}</li>
  <li>FLUSHALL {clear whole cache server}</li>
  <li>SETEX name 10 rahul {gives an expiration time to key in seconds}</li>
  <li>ttl name {Check Time to live for that key, -1 if indefinite, -2 if expired, >=0 if in countdown}</li>
  <li>expire name 10 {gives an expiration time to a key}</li>
</ul>

<h2>Storing array,set and Hashcodes based data in Redis</h2>

**By default reddis stores all values in form of Strings, but we can also store Array/lists or HashCodes/Json data in REDIS**

<ul>
  Array
  <li>lpush friends john {adds john to list of friends from left}</li>
  <li>rpush friends mike {adds mike to list of friends from right}</li>
  <li>lrange friends 0 -1 {get values in john from start to end}</li>
  <li>lpop friends {removes leftmost element}</li>
  <li>rpop friends {removes rightmost element}</li>
</ul>

<ul>
  Set
  <li>SADD hobbies "weight lifting" {adds value to the hobbies set}</li>
  <li>SMEMBERS hobbies {gets all elements}</li>
  <li>SREM hobbies "weight lifting" {Removes this value}</li>
</ul>

<ul>
  HashCode
  <li>HSET person name tom {in hashset perons => sets key name to tom}</li>
  <li>HGET person name {gets value for key name in hashset person}</li>
  <li>HSET person age 26</li>
  <li>HGETALL person {Gives all key value pairs in person}</li>
  <li>HDEL person age {removes age from hashmap}</li>
  <li>HEXISTS person name {checks if key is present}</li>
</ul>

<h1>Use in Node</h1>

```
router.get('/bomcompletionperrahul', async (req, res) => {
    const viewName = constant.viewName.BOMCompletionPercent;
    try{
        const value = await redisClient.get(viewName);
        
        if(value){
            return res.status(200).send(JSON.parse(value))
        }
        else{
            const view = db.collection(viewName);
            const result = await view.find().toArray();
            await redisClient.set(viewName, JSON.stringify(result), {
                EX: expiry,
                NX: true 
              });
            return res.status(200).send(result);
        }
    } catch (error) {
        console.error('Error:', error);
        return res.status(500).json({ error: 'Internal server error' });
    }
});
```
