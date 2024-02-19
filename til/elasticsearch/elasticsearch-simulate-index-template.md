---
title: Elasticsearch - simulate index template
draft: true
tags: 

---
# Elasticsearch - simulate index template
If an index template is composed of multiple component templates and other settings/mappings, and you want to know what it the output index template you can use

```
POST /_index_template/_simulate
{
  "index_patterns": ["my*"],
  "template": {
    "settings" : {
        "index.number_of_shards" : 3
    }
  },
  "composed_of": ["ct1", "ct2"]
}
```

More info at [Simulate multi-component templates](https://www.elastic.co/guide/en/elasticsearch/reference/current/simulate-multi-component-templates.html)