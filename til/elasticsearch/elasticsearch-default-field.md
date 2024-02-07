---
title: Default field
draft: true
tags:
  - elasticsearch
---
# Default field
Which fields should be searched if no field is provided in the query string?

You can use the setting `default_field` to provide a list of fields to use as default if no field is provided in the query.

If `default_field = *` (the default value), the list of default fields will be calculated dynamically. 

For integrations, Fleet populates the list of default fields based on the fields defined in the integration. This currently, at version 8.12, doesn't take into consideration dynamic mappings that are declared in component templates or other index template settings.

The list of default fields can get quite big, so Elasticsearch has an upper limit set by the setting `search.max_clause_count`. This value is dynamically set based on the size of the cluster. This setting is meant to replace `indices.query.bool.max_clause_count`, which is now deprecated.

## Links
- [Documentation on how to use it in query](https://www.elastic.co/guide/en/elasticsearch/reference/8.12/query-dsl-query-string-query.html#_default_field)
- [Setting index.query.default_field](https://www.elastic.co/guide/en/elasticsearch/reference/8.12/index-modules.html#index-query-default-field)
- [Setting indices.query.bool.max_clause_count](https://www.elastic.co/guide/en/elasticsearch/reference/8.12/search-settings.html)
- [Default field API](https://www.elastic.co/guide/en/kibana/current/upgrade-assistant-api-default-field.html)