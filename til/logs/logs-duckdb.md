---
title: Logs processing with duckdb
draft: true
tags:
  - logs
---
# Logs processing with duckdb
Let's say that I have some logs with ndjson (new line delimited JSON) format like the following:

In a sample file logs.json

```
{"key1":"value1", "key2": "value1"} 
{"key1":"value2", "key2": "value2"} 
{"key1":"value3", "key2": "value3"}
```

I can use [duckdb](https://duckdb.org/) to parse and query those JSON logs like the following
```bash
# Create a table from the file
duckdb logs.db -c "CREATE TABLE logs AS SELECT * FROM read_json_auto('logs.json');"

# output query result as CSV
duckdb logs.db -c "select * from logs" -csv
```