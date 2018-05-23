```
# Pretty print:
db.collection.find().pretty()
```

```sh
# How to export all collection in MongoDB?

# For lazy people like me, i use mongodump it's faster:
mongodump -d <database_name> -o <directory_backup>

# And to "restore/import" that, i used (from directory_backup/dump/):
mongorestore -d <database_name> <directory_backup>
```
