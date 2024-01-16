---
title: Print the stack trace from a request to Elasticsearch
draft: false
tags:
  - elasticsearch
---
# Print the stack trace from a request to Elasticsearch
If you have a request to Elasticsearch that fails with an error like the following

```
curl -X POST "localhost:9200/my-index-000001/_search?size=surprise_me&pretty"
```

You only get a basic description of the error, like:

```
{
  "error" : {
    "root_cause" : [
      {
        "type" : "illegal_argument_exception",
        "reason" : "Failed to parse int parameter [size] with value [surprise_me]"
      }
    ],
    "type" : "illegal_argument_exception",
    "reason" : "Failed to parse int parameter [size] with value [surprise_me]",
    "caused_by" : {
      "type" : "number_format_exception",
      "reason" : "For input string: \"surprise_me\""
    }
  },
  "status" : 400
}
```

If you want to print the error stack trace, you add a query parameter to the original request, like

```
curl -X POST "localhost:9200/my-index-000001/_search?size=surprise_me&error_trace=true&pretty"
```

this will return the full stack trace.
```
{
  "error": {
    "root_cause": [
      {
        "type": "illegal_argument_exception",
        "reason": "Failed to parse int parameter [size] with value [surprise_me]",
        "stack_trace": "Failed to parse int parameter [size] with value [surprise_me]]; nested: IllegalArgumentException..."
      }
    ],
    "type": "illegal_argument_exception",
    "reason": "Failed to parse int parameter [size] with value [surprise_me]",
    "stack_trace": "java.lang.IllegalArgumentException: Failed to parse int parameter [size] with value [surprise_me]\n    at org.elasticsearch.rest.RestRequest.paramAsInt(RestRequest.java:175)...",
    "caused_by": {
      "type": "number_format_exception",
      "reason": "For input string: \"surprise_me\"",
      "stack_trace": "java.lang.NumberFormatException: For input string: \"surprise_me\"\n    at java.lang.NumberFormatException.forInputString(NumberFormatException.java:65)..."
    }
  },
  "status": 400
}
```

More info at the [official Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/common-options.html#common-options-error-options)