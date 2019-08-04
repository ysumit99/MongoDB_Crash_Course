### Basic Mongo shell commands


### 1. show dbs

``` js
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
test1   0.000GB
```

### 2. use {db_name}
``` js
> use test1
switched to db test1
```

### 3. show collections
```js
> show collections
products
```

### 4. db.dropDatabase()

```js
{ "dropped" : "test1", "ok" : 1 }
```

