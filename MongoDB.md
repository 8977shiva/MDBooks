





# MongoDB

## What is  MongoDB

MongoDB is a No SQL database. It is an open-source, cross-platform, document-oriented database written in C++. It  is an open-source document database that provides high performance, high availability, and automatic scaling. In simple words, you can say that - Mongo DB is a document-oriented database 

##### Sample document

```json
{
   _id: ObjectId(7df78ad8902c)
   title: 'MongoDB Overview', 
   description: 'MongoDB is no sql database',
   by: 'tutorials point',
   url: 'http://www.tutorialspoint.com',
   tags: ['mongodb', 'database', 'NoSQL'],
   likes: 100, 
   comments: [	
      {
         user:'user1',
         message: 'My first comment',
         dateCreated: new Date(2011,1,20,2,15),
         like: 0 
      },
      {
         user:'user2',
         message: 'My second comments',
         dateCreated: new Date(2011,1,25,7,45),
         like: 5
      }
   ]
}
```

|    RDBMS    |                         MongoDB                          |
| :---------: | :------------------------------------------------------: |
|  Database   |                         Database                         |
|    Table    |                        Collection                        |
|  Tuple/Row  |                         Document                         |
|   column    |                          Field                           |
| Table Join  |                    Embedded Documents                    |
| Primary Key | Primary Key (Default key _id provided by MongoDB itself) |



## Advantages over RDBMS

It  follows  document- oriented  structure. A document is a set of key-value pairs. Documents have dynamic schema. Dynamic schema means that documents in the same collection do not need to have the same set of fields or structure, and common fields in a collection's documents may hold different types of data.

- **Schema less** − MongoDB is a document database in which one collection holds different documents. Number of fields, content and size of the document can differ from one document to another.
- Structure of a single object is clear.
- No complex joins.
- Deep query-ability. MongoDB supports dynamic queries on documents using a document-based query language that's nearly as powerful as SQL.

###   when to use 

- **Document Oriented Storage** − Data is stored in the form of JSON style documents.
- Big Data
- Content Management and Delivery
- Mobile and Social Infrastructure
- User Data Management

## Installation 

To install MongoDB  first download the latest release of MongoDB from https://www.mongodb.com/download-center.

```
C:\>md data
C:\Program Files\MongoDB\Server\4.2\bin>mongod.exe --dbpath "C:\data"
C:\Program Files\MongoDB\Server\4.2\bin>mongo.exe
```

### Installation  in MAC

Folow this steps  to install in Mac os

[https://treehouse.github.io/installation-guides/mac/mongo-mac.html#:~:text=Open%20the%20Terminal%20app%20and%20type%20brew%20update%20.&text=Run%20the%20Mongo%20daemon%2C%20in,mongo%20in%20another%20terminal%20window.](https://treehouse.github.io/installation-guides/mac/mongo-mac.html#:~:text=Open the Terminal app and type brew update .&text=Run the Mongo daemon%2C in,mongo in another terminal window.)

### Creating an user(online)

after  creatiing the clustor  under  security  you will have   databaseAcess section . Here you create new  users

### connectin to online server 

After creating an account  we need to create an cluster.In clusters goto connect  us the 1st option which is conneting though shell   copy that URL  add your database name and  username

```json
C:\Program Files\MongoDB\Server\4.2\bin>mongo.exe "paste here ur account URL with database name and username "
 //example
 C:\Program Files\MongoDB\Server\4.2\bin>mongo.exe mongodb+srv://shivamongo-pmm8n.mongodb.net/test --username sagar

```

### online shell

https://docs.mongodb.com/manual/tutorial/insert-documents/

under each example you will have a shell to  try it out 

## Creating  Database

```visual basic
use DATABASE_NAME
```

To check your databases list, use the command **show dbs**  if created database  is not present in list. To display database, you need to insert at least one document into it.

```json
db.names.insert({"name":"sagar"})
show dbs
```

by default  the database is test

## Creating Collections 

Collections  are similar to that of table in relational  database. The  are  in JSON format  that is key value pair. The structure  of an document is  as  following

```json
{
		"Employeeid" : 1,
		"EmployeeName" : "Martin"
}
```

There are two was in  which we can create  Collections

### Insert method

This  is a  direct method where  we use insert  the syntax is 

```json
db.collectionName.insert({document})
//example 
db.movies.insert({
"name":"Avengers:End games",
 "release":"2019",
  "rating": "9/10"
})
```

### Create Collection

Basic syntax of **createCollection()** command is as follows 

```json
db.createCollection(name, options)
```

In the command, **name** is name of collection to be created. **Options** is a document and is used to specify configuration of collection.

Options parameter is optional, so you need to specify only the name of the collection. Following is the list of options you can use −

|    Field    |  Type   |                         Description                          |
| :---------: | :-----: | :----------------------------------------------------------: |
|   capped    | Boolean | (Optional) If true, enables a capped collection. Capped collection is a fixed size collection that automatically overwrites its oldest entries when it reaches its maximum size. **If you specify true, you need to specify size parameter also.** |
| autoIndexId | Boolean | (Optional) Specify `false` to disable the automatic creation of an index on the `_id` field. |
|    size     | number  | (Optional) Specifies a maximum size in bytes for a capped collection. **If capped is true, then you need to specify this field also.** |
|     max     | number  | (Optional) Specifies the maximum number of documents allowed in the capped collection. |

While inserting the document, MongoDB first checks size field of capped collection, then it checks max field.

```json
db.createCollection("mycol", { capped : true,  size : 6142800, max : 10000 } )
```

To see the created  collection the command is  **show collections**.

## Create a Document

MongoDB  provides three  method for inserting document into a database

1. insert()
2. insertOne()
3. insertMany()

### insert()

The insert() method inserts one or more documents into a collection. Each document is provided as a parameter. The collection name is prepended to the insert() method.

Here's the syntax for inserting a single document:

```json
db.collectionName.insert({ name: "value" })
db.movies.insert({
"name":"Avenger",
 "release":"20015",
  "rating": "9/10"
})
```

 MongoDB has creates an _id field for the documents. If you don't specify one, MongoDB will create one for you. However, you can provide this field when doing the insert if you prefer to have control over the value of the _id field.

```json
db.artists.insert({ _id: 1, artistname: "AC/DC" })
```

The _id that MongoDB provides is a 12-byte ObjectId value. It is made up of the following values;

- a 4-byte value representing the seconds since the Unix epoch,
- a 3-byte machine identifier,
- a 2-byte process id, and
- a 3-byte counter, starting with a random value.

####    Multiple Documents

You can insert multiple documents within a single insert() method.

```json
db.movies.insert({movie: "Avengers", series : [{"name":"Avenger", "year":"2012" }, { "name":"Age of ultron","year":"2015" }]})
```



### Insert one()

the insertOne() method to insert a single document into a collection

```json
 db.empDetails.insertOne(
	{
		First_Name: "Radhika",
		Last_Name: "Sharma",
		Date_Of_Birth: "1995-09-26",
		e_mail: "radhika_sharma.123@gmail.com",
		phone: "9848022338"
	})
```

### InsertMany()

we can insert multiple documents using the insertMany() method. To this method you need to pass an array of documents.

```json
db.empDetails.insertMany(
	[
		{
			First_Name: "Radhika",
			Last_Name: "Kapoor",
			Date_Of_Birth: "1995-09-30",
			e_mail: "Kapoor@gmail.com",
			phone: "9000012347"
		},
		{
			First_Name: "Rachel",
			Last_Name: "Christopher",
			Date_Of_Birth: "1990-02-16",
			e_mail: "Rachel_Christopher.123@gmail.com",
			phone: "9000054321"
		},
		{
			First_Name: "Fathima",
			Last_Name: "Sheik",
			Date_Of_Birth: "1990-02-16",
			e_mail: "Fathima_Sheik.123@gmail.com",
			phone: "9000054321"
		}
	]
)
```



## Query a Collection

The **db.collection.find()** selects documents in a collection and returns a cursor to the selected documents.

```json
db.empDetails.find()
```

###  Filtering 

we can filter the results down by providing only the criteria that you're interested in.

```json
db.empDetails.find({"First_Name":"Radhika"})
```

### format the result

The document is returned as one long line of text. You can use the **pretty()** method to format the results so that they're a bit easier to read.

```json
db.empDetails.find({"First_Name":"Radhika"}).pretty()
```

### And

we can specify that only documents containing two or more specified values should be returned.

```json
db.empDetails.find({$and:[{"First_Name":"Radhika"},{"Last_Name":"kapoor"}]}).pretty()
```

### OR

we can also specify that either one or the other value should be true. As long as one of the conditions are true, the document will be returned.

```json
db.empDetails.find({
    $or:[{"First_Name":"Radhika"},{"Last_Name":"kapoor"}]
}).pretty()
```

### Find one()

we can use the db.collection.findOne() method to return one document that satisfies the specified query criteria.

```json
db.empDetails.findOne({"First_Name":"Radhika"})
```

### Projection

A projection query is a query where you specify which fields should be returned.

```json
db.empDetails.find({"First_Name":"Radhika"},{First_Name :1})
db.empDetails.find({"First_Name":"Radhika"},{_id:0,Last_Name :1}) // output without id

```

### Limiting

In MongoDB, we can use the **limit()** method to specify a maximum number of documents for a cursor to return.

```json
db.empDetails.find({"First_Name":"Radhika"}).limit(1)
```

### Sorting

when you query a collection using the db.collection.find() method, you can append the **sort()** method to specify how the results should be sorted. The sort() method must be a JSON document that defines the sort order. It will typically contain one or more fields, each followed by either 1 or -1, depending on whether the sort should be in ascending or descending order.

```json
//Ascending order
db.empDetails.find().sort({First_Name:1})
//Desecnding order
db.empDetails.find().sort({First_Name:-1})

```

### Update

This method updates the values in the existing document

```js
db.COLLECTION_NAME.update(SELECTION_CRITERIA, UPDATED_DATA)
db.empDetails.update({"First_Name":"Radhika"},{$set:{e_mail: "Fathima_Sheik@gmail.com"}})
```

### Save

The **save()** method replaces the existing document with the new document passed in the save() method.

```json
db.COLLECTION_NAME.save({_id:ObjectId(),NEW_DATA})
  db.movies.save({
       "_id" : ObjectId("5f08aeeea11cf61d2585f789"),
      "name":"The Avengers",
 "release":"2015",
  "rating": "9/10"
       
  })

```

## Indexing

Indexes are very important in any database, and with MongoDB it's no different. With the use of Indexes, performing queries in MongoDB becomes more efficient. If you had a collection with thousands of documents with no indexes, and then you query to find certain documents, then in such case MongoDB would need to scan the entire collection to find the documents. If you had indexes, MongoDB would use these indexes to limit the number of documents that had to be searched in the collection.

Indexes are special data sets which store a partial part of the collection's data. Since the data is partial, it becomes easier to read this data. This partial set stores the value of a specific field or a set of fields ordered by the value of the field.

#### create an index 

we use createIndex() with value's 1 is for ascending order. To create index in descending order you need to use -1

```json
db.COLLECTION_NAME.createIndex({KEY:1})
db.empDetails.createIndex({"First_Name":1})
```

#### Get index

This method returns the description of all the indexes in the collection.

```json
db.COLLECTION_NAME.getIndexes()
db.empDetails.getIndexes()
```

#### drop index

we can drop a particular index using the dropIndex() method of MongoDB.

```json
db.COLLECTION_NAME.dropIndex({KEY:1})
db.movies.dropIndex({"name":1})
```

## droping collection and database

MongoDB's **db.collection.drop()** is used to drop a collection from the database.

```json
db.COLLECTION_NAME.drop()
db.empDetails.drop()
mongo "mongodb+srv://shivamongo-pmm8n.mongodb.net/<Sagar" --username sagar
```

MongoDB **db.dropDatabase()** command is used to drop a existing database.

```json
db.dropDatabase()
```

the  above syntax  will  delete the present running database.