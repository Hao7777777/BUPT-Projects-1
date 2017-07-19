# Learing Node.js

> Learning Node.js Notes

## Features

- single-threaded
- non-blocking
- async

## Notes

- Module
  - `exports.myFunction = function...`
  - `var myModule = require('./myModule')`
  - `myModule.myFunction(...)`
- Response
  - `res.writeHead(200, {'Content-Type': 'text/html'})`
  - `res.write('body')`
  - `res.end()`
- Request
  - `req.url
  - `req.method`
- File System
  - `var fs = require('fs')`
  - `fs.open(filename, method, function (err, file)...)`
  - `fs.readFile(filename, function (err, data)...)`
  - `fs.writeFile(filename, content, function (err)...)`
  - `fs.appendFile(filename, content, function (err)...)`
  - `fs.unlink(filename, function (err)...)`
  - `fs.rename(old, new, fucntion(err)...)`
- URL
  - `var url = require('url')`
  - `var q = url.parse(address, true)`
- NPM
  - `npm install package`
  - `npm list`
- Event
  - `var events = require('events')`
  - `var eventEmitter = new events.EventEmitter()`
  - `eventEmitter.on(event, myEventHandler)`
  - `eventEmitter.emit(event)`
- formidable
  - `var formidable = require('formidable')`
  - `var form = new formidable.IncomingForm()`
  - `form.parse(req, function (err, fields, files)...)`
  - `var oldPath = files.upload.path`
  - `var newPath = "./recv/" + files.upload.name`
  - `fs.rename(oldPath, newPath, function (err)...)`
- MySQL
  - `var mysql = require('mysql')`
  - `var con = mysql.createConnection({...})`
  - `con.connect(function (err)...)`
  - `con.query(sql, function (err, res)...)`
  - `con.query(sql, function (err, res, fields)...)`
  - Insert/Update/Delete
    - `res.affectedRows` (multi-row)
    - `res.insertId` (only single-row insert)
  - Query
    - `res`
    - `fields`
  - `var input = mysql.escape(raw)`
  - Placeholder
    - `?` (also for multi-row)
    - `con.query(sql, [...], function (err, res)...)`
- MongoDB
  - `var mongodb = require('mongodb')`
  - `var client = mongodb.MongoClient`
  - `client.connect(url, function (err, db)...)`
  - `db.close()`
  - `db.createCollection(name, function (err, res)...)`
  - `db.dropCollection(name, function (err, ok)...)`
  - `var collection = db.collection(collection)`
  - `_id` field
  - `collection.insertOne(obj, function (err, res)...)`
  - `collection.insertMany(objArray, function (err, res)...)`
  - `var query = { field: "..." }`
  - `var query = { field: /.../ }`
  - `collection.findOne(query, function (err, res)...)`
  - `collection.find(query).toArray(function (err, res)...)`
  - `collection.find(query).sort({ field: 1 })...`
  - `collection.find(query).sort({ field: -1 })...`
  - `collection.find(query).limit(n)...`
  - `collection.find(query).skip(n)...`
  - `collection.deleteOne(query, function (err, res)...)`
  - `collection.deleteMany(query, function (err, res)...)`
  - `collection.drop(function (err, ok)...)`
  - `var val = { $set: { field: "..." } }`
  - `collection.updateOne(query, val, function (err, res)...)`
  - `collection.updateMany(query, val, function (err, res)...)`
  - `var agg = { $lookup: { ... } }`
    - `from`
    - `localField`
    - `foreignField`
    - `as`
  - `collection.aggregate([agg], function (err, res)...)`
    - `collection left join from`
    - `on from.localField = collection.foreignField`
    - => `[collection + [as]]`