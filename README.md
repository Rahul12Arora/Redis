# Redis
Redis info

Redis is an in memory database using based on key:value priciple, it is very fast, operated by cli, is used in caching to access pre-queried data for fast access.

<h1>Getting Started + Basics</h1>

<ul>
  <li>homebrew install redis {To install redis}</li>
  <li>redis-cli {run in parallel terminal to start redis}</li>
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

<h2>Storing arrays and Hashcodes based data in Redis</h2>

**By default reddis stores all values in form of Strings, but we can also store Array/lists or HashCodes/Json data in REDIS**

<ul>
  <li>lpush friends john {adds john to list of friends}</li>
  <li>lrange friends 0 -1 {get values in john from start to end}</li>
  <li></li>
</ul>
