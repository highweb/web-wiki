```sh
# Pretty print:
db.collection.find().pretty()

# Export a collection:
mongoexport --db test --collection traffic --out traffic.json

# Export complete db:
# For lazy people like me, i use mongodump it's faster:
mongodump -d <database_name> -o <directory_backup>

# And to "restore/import" that, i used (from directory_backup/dump/):
mongorestore -d <database_name> <directory_backup>
```
