# Legacy model_run_specs.json

`model_run_specs.json` used a nested structure:

```text
baseline_uuid -> children -> intervention_uuid -> time0_baseline_uuid
```

The resolved run graph replaces that structure with:

```text
run_nodes.jsonl  # flat runnable recipes
run_edges.jsonl  # relationships among recipes
```

| Legacy field | Run-graph replacement |
| --- | --- |
| `baseline_uuid` | baseline `run_id` |
| `intervention_uuid` | intervention `run_id` |
| `time0_baseline_uuid` | time-zero/static-change `run_id` |
| `baseline_parameters_hash` | baseline node `recipe_hash` |
| `parameter_hash` | intervention node `recipe_hash` |
| `time0_baseline_hash` | time-zero/static-change node `recipe_hash` |
| nested `children` | `run_edges.jsonl` relationships |
| skipped null children | `generation_report.json` skipped-direction records |

`model_run_specs.json` may still be generated as a compatibility artifact during migration, but new code should consume the resolved run graph directly.
A compatibility exporter must not introduce runnable runs that are absent from `run_nodes.jsonl`.
