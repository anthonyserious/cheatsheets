# elk-mongodb-cheatsheet
Cheatsheet for operating Elasticsearch and the River MongoDB plugin

##  Create an index for a collection
```javascript
curl -XPUT 'http://localhost:9200/_river/mongodb/_meta' -d '{
    "type": "mongodb", 
    "mongodb": { 
      "db": "DATABASE_NAME", 
      "collection": "COLLECTION"
    }, 
    "index": { 
      "name": "ES_INDEX_NAME", 
      "type": "ES_TYPE_NAME" 
    }
  }'
```
In this example, we've pumped vmstat data from an Ubuntu server into a collection called "vmstat1" in a Mongodb database called "vmstat".  We'll specify a type called vmstat_linux in anticipation of also including vmstat data from other operating systems like Solaris.

```javascript
  curl -XPUT 'http://localhost:9200/_river/mongodb/_meta' -d '{ 
    "type": "mongodb", 
    "mongodb": { 
      "db": "vmstat", 
      "collection": "vmstat1"
    }, 
    "index": {
      "name": "mongoindex", 
      "type": "vmstat_linux" 
    }
  }'
```

## Delete an index
```bash
curl -XDELETE http://HOSTNAME:PORT/ES_INDEX_NAME
```

## List available indices
```bash
curl http://HOST:PORT/_cat/indices
```




