
# How to reproduce

example for https://github.com/wundergraph/cosmo/issues/684

1.
```shell
make run
```

2.
```shell
npm install -g wgc@latest
wgc router compose -i graph.yaml -o config.json
```

3. use config.json for run router

4. run query

```graphql
query Test {
    test(filter: {b: null})
}
```
or
```graphql
query Test($filter: TestFilter) {
    test(filter: $filter)
}

and variables

{
    "filter": {"b": null}
}
```

5. view result

```json
{
  "errors": [
    {
      "message": "Failed to fetch from Subgraph '0' at path 'query'.",
      "extensions": {
        "errors": [
          {
            "message": "could not render fetch input",
            "path": []
          }
        ]
      }
    }
  ],
  "data": null,
  "extensions": {
    "trace": {
      "info": {
        "trace_start_time": "2024-04-03T18:22:51+03:00",
        "trace_start_unix": 1712157771,
        "parse_stats": {
          "duration_nanoseconds": 344291,
          "duration_pretty": "344.291µs",
          "duration_since_start_nanoseconds": 160625,
          "duration_since_start_pretty": "160.625µs"
        },
        "normalize_stats": {
          "duration_nanoseconds": 586500,
          "duration_pretty": "586.5µs",
          "duration_since_start_nanoseconds": 526291,
          "duration_since_start_pretty": "526.291µs"
        },
        "validate_stats": {
          "duration_nanoseconds": 93541,
          "duration_pretty": "93.541µs",
          "duration_since_start_nanoseconds": 1124750,
          "duration_since_start_pretty": "1.12475ms"
        },
        "planner_stats": {
          "duration_nanoseconds": 7581916,
          "duration_pretty": "7.581916ms",
          "duration_since_start_nanoseconds": 1218875,
          "duration_since_start_pretty": "1.218875ms"
        }
      },
      "fetch": {
        "id": "7d5fe3fb-0da8-4a75-b129-b414fc2193ac",
        "type": "single",
        "data_source_id": "0",
        "datasource_load_trace": {
          "raw_input_data": {},
          "single_flight_used": false,
          "single_flight_shared_response": false,
          "load_skipped": false
        }
      },
      "node_type": "object",
      "nullable": true,
      "fields": [
        {
          "name": "test",
          "value": {
            "node_type": "integer",
            "path": [
              "test"
            ]
          },
          "parent_type_names": [
            "Query"
          ],
          "named_type": "Int",
          "data_source_ids": [
            "0"
          ]
        }
      ]
    }
  }
}
```