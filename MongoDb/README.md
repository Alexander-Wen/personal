## Setting Up Mongo
Start the Mongo server by running the command `mongod`.

If the command results in an error because of a missing directory, create the directory using the [command](http://www.linfo.org/mkdir.html)
`mkdir -p /data/db`

If the command results in an error because of permission denied, change permission by using chown [command](http://linuxcommand.org/man_pages/chown1.html) `sudo chown -R $USER /data/db`

## Exporting the Mongo server onto a local server

Get the url for the mongodb server from a coworker. It should take the form of

    mongodb://{ username }:{ password }@{ host }:{ port }/{ db name }

To dump all of the contents to a .bson file, run the command in your terminal

`mongodump -h { host }:{ port } -u { username } -p { password } -d { db name } -o dump`

replacing all the fields with the corresponding fields in the url.

This should create a new folder called /dump/{ db name }. Inside of this folder will the .bson files with all the different collections that are inside of this database.

To import a collection into your local database, run the command

`mongorestore --host 127.0.0.1 --db { db name you export in ./secrets/env.sh } dump/{ db name }/{ collection name }.bson`

The database should not be running on your local machine! :D
