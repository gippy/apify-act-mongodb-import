# apify-act-mongodb-import
This act imports array of object to specific MongoDB colection.

## Input
You can specified import with attributes:

### mongoUrl(String) - **required**
Connection url to MongoDB, see [https://docs.mongodb.com/manual/reference/connection-string/](Connection String URI Format).

### collection(String) - **required**
Collection name, where act imports objects.

### timestampAttr(String)
When this attribute is set to a String, the act will add a timestamp attribute to each record under the specified name.

### uniqueKeys(Array)
Unique keys for object, if you specified unique keys, act try to find object with this attributes in DB and update it.

### imports(Object)

#### plainObjects(Array)
Array of object to import to DB.

#### objectsFromKvs(Object)
Defines object from Apify key-value store to import.

##### storeId(String)
Apify key-value store Id.

##### keys(Array)
List of keys in Apify key-value store.

### Input examples
- Imports list of plains objects:
```
{
  "mongoUrl": "mongodb://user:pwd@85.90.244.43:27017/db",
  "collection": "my-collection",
  "timestampAttr": "created_at",
  "uniqueKeys": ["localUniqueKey"],
  "imports": {
    "plainObjects": [
      {
        "test": "Hello"
      },
      {
        "test": "word"
      }
    ]
  }
}
```

- Imports objects from Apify key-value store:
```
{
  "mongoUrl": "mongodb://user:pwd@85.90.244.43:27017/db",
  "collection": "my-collection",
  "imports": {
    "objectsFromKvs": {
        "storeId": "a7hasd86jds",
        "keys": ["results1"]
    }
  }
}
```
