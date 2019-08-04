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
db.dropDatabase()

{ "dropped" : "test1", "ok" : 1 }
```


### 5. db.{collection_name}.insert()

```js
> db.posts.insert({
 title: 'Post One',
body: 'body of post one',
 category: 'News',
 likes: 4,
  tags: ['news', 'events'],
 user: {
 name: 'John Doe',
 status: 'auhor'
 },
 date: Date()
 })

  WriteResult({ "nInserted" : 1 })
 ```
 
 

### 6. db.{collection_name}.insertMany()

```js
> db.posts.insertMany([
{
 title: 'Post Two',
body: 'body of post two',
 category: 'sports',
 likes: 56,
  tags: ['sports', 'tennis'],
 user: {
 name: 'James Black',
 status: 'Journalist'
 },
 date: Date()
},

{
 title: 'Post Three',
body: 'body of post three',
 category: 'Politics',
 date: Date()
},

])

{
	"acknowledged" : true,
	"insertedIds" : [
		ObjectId("5d4716bc4e356b844de7a23b"),
		ObjectId("5d4716bc4e356b844de7a23c")
	]
}

```

### 7. db.{collection_name}.find()

``` js
> db.posts.find()
{ "_id" : ObjectId("5d4715c74e356b844de7a23a"), "title" : "Post One", "body" : "body of post one", "category" : "News", "likes" : 4, "tags" : [ "news", "events" ], "user" : { "name" : "John Doe", "status" : "auhor" }, "date" : "Sun Aug 04 2019 22:58:39 GMT+0530 (IST)" }
{ "_id" : ObjectId("5d4716bc4e356b844de7a23b"), "title" : "Post Two", "body" : "body of post two", "category" : "sports", "likes" : 56, "tags" : [ "sports", "tennis" ], "user" : { "name" : "James Black", "status" : "Journalist" }, "date" : "Sun Aug 04 2019 23:02:44 GMT+0530 (IST)" }
{ "_id" : ObjectId("5d4716bc4e356b844de7a23c"), "title" : "Post Three", "body" : "body of post three", "category" : "Politics", "date" : "Sun Aug 04 2019 23:02:44 GMT+0530 (IST)" }

```

### 8. db.{collection_name}.find().pretty()

```js
> db.posts.find().pretty();
{
	"_id" : ObjectId("5d4715c74e356b844de7a23a"),
	"title" : "Post One",
	"body" : "body of post one",
	"category" : "News",
	"likes" : 4,
	"tags" : [
		"news",
		"events"
	],
	"user" : {
		"name" : "John Doe",
		"status" : "auhor"
	},
	"date" : "Sun Aug 04 2019 22:58:39 GMT+0530 (IST)"
}
{
	"_id" : ObjectId("5d4716bc4e356b844de7a23b"),
	"title" : "Post Two",
	"body" : "body of post two",
	"category" : "sports",
	"likes" : 56,
	"tags" : [
		"sports",
		"tennis"
	],
	"user" : {
		"name" : "James Black",
		"status" : "Journalist"
	},
	"date" : "Sun Aug 04 2019 23:02:44 GMT+0530 (IST)"
}
{
	"_id" : ObjectId("5d4716bc4e356b844de7a23c"),
	"title" : "Post Three",
	"body" : "body of post three",
	"category" : "Politics",
	"date" : "Sun Aug 04 2019 23:02:44 GMT+0530 (IST)"
}
```

### 9. db.{collection_name}.find({ {key} : {value} )

```js
> db.posts.find({category: 'News'}).pretty();

{
	"_id" : ObjectId("5d4715c74e356b844de7a23a"),
	"title" : "Post One",
	"body" : "body of post one",
	"category" : "News",
	"likes" : 4,
	"tags" : [
		"news",
		"events"
	],
	"user" : {
		"name" : "John Doe",
		"status" : "auhor"
	},
	"date" : "Sun Aug 04 2019 22:58:39 GMT+0530 (IST)"
}
```

### 10. db.{collection_name}.find().sort({ key : 1}).pretty()

```js
> db.posts.find().sort({ title: 1}).pretty
function () {
    this._prettyShell = true;
    return this;
}
> db.posts.find().sort({ title: 1}).pretty();
{
	"_id" : ObjectId("5d4715c74e356b844de7a23a"),
	"title" : "Post One",
	"body" : "body of post one",
	"category" : "News",
	"likes" : 4,
	"tags" : [
		"news",
		"events"
	],
	"user" : {
		"name" : "John Doe",
		"status" : "auhor"
	},
	"date" : "Sun Aug 04 2019 22:58:39 GMT+0530 (IST)"
}
{
	"_id" : ObjectId("5d4716bc4e356b844de7a23c"),
	"title" : "Post Three",
	"body" : "body of post three",
	"category" : "Politics",
	"date" : "Sun Aug 04 2019 23:02:44 GMT+0530 (IST)"
}
{
	"_id" : ObjectId("5d4716bc4e356b844de7a23b"),
	"title" : "Post Two",
	"body" : "body of post two",
	"category" : "sports",
	"likes" : 56,
	"tags" : [
		"sports",
		"tennis"
	],
	"user" : {
		"name" : "James Black",
		"status" : "Journalist"
	},
	"date" : "Sun Aug 04 2019 23:02:44 GMT+0530 (IST)"
}

```
__Note__: Sorts in ascending order of the key specified if __1__ is used as value after sort key 

### 11. db.{collection_name}.find().sort({ key : -1}).pretty()

```js
> db.posts.find().sort({ title: -1}).pretty();
{
	"_id" : ObjectId("5d4716bc4e356b844de7a23b"),
	"title" : "Post Two",
	"body" : "body of post two",
	"category" : "sports",
	"likes" : 56,
	"tags" : [
		"sports",
		"tennis"
	],
	"user" : {
		"name" : "James Black",
		"status" : "Journalist"
	},
	"date" : "Sun Aug 04 2019 23:02:44 GMT+0530 (IST)"
}
{
	"_id" : ObjectId("5d4716bc4e356b844de7a23c"),
	"title" : "Post Three",
	"body" : "body of post three",
	"category" : "Politics",
	"date" : "Sun Aug 04 2019 23:02:44 GMT+0530 (IST)"
}
{
	"_id" : ObjectId("5d4715c74e356b844de7a23a"),
	"title" : "Post One",
	"body" : "body of post one",
	"category" : "News",
	"likes" : 4,
	"tags" : [
		"news",
		"events"
	],
	"user" : {
		"name" : "John Doe",
		"status" : "auhor"
	},
	"date" : "Sun Aug 04 2019 22:58:39 GMT+0530 (IST)"
}

```
__Note__: Sorts in descending order of the key specified if __-1__ is used as value for sort key