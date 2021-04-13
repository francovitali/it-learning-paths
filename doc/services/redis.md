# Redis

Key-Value data source (https://redis.io/)

## Install with Docker

Official DockerHub [image](https://hub.docker.com/_/redis)

```bash
$ docker run --name some-redis -d -p6739:6739 redis
```

## Usage

We can use a [supported client library](https://redis.io/clients) or the [redis-cli](https://redis.io/topics/rediscli) command line

### Libraries

* [Go](https://github.com/go-redis/redis)
* [Java](https://github.com/redis/jedis)

### redis-cli

Install with Homebrew
```bash
$ brew install redis
```

Execute redis-cli
```bash
$ redis-cli
```

Add or update a key-value entry
```bash
redis> SET mykey "my value"
```

To set a TTL (in seconds) we can use
```bash
redis> SET mykey "my value" EX 10
```

To view the remaining TTL of a key
```bash
redis> TTL mykey
```

Query entry by key
```bash
redis> GET mykey
"my value"
```

Remove entry by key
```bash
redis> DEL mykey
```

To retrieve all existing keys
```bash
redis> KEYS
```

To "clear" the data source we can use
```bash
redis> FLUSHALL
```
