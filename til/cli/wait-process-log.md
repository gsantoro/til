---
title: Wait for another to print a string into their logs
draft: true
tags: 

---
# Wait for another to print a string into their logs
I have had many occasions when a process needs to wait for another process to start.

In order to synchronize these two process we could thing of waiting for a specific string in the logs of the first process.

We can do by using grep like this

```bash
grep -m 1 "Elasticsearch and Kibana are ready for functional testing" <(tail -f {{.KIBANA_FTR_SERVER_LOG}})
```