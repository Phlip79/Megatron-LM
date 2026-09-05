# Performance tests

This directory contains performance-test infrastructure. The baseline-driven
test cases currently exercise inference and live under `inference/test_cases/`:

```text
inference/test_cases/<model>/<case>/
├── model_config.yaml
└── baseline_values.json
```

Inference case names include `_inference_perf` so that generated CI job names
identify the workload without relying on the recipe filename. The recipes in
`tests/test_utils/recipes/` pass each case to
`shell_test_utils/run_perf_test.sh`, which launches the dynamic inference
server and checks the recorded performance metrics against the baseline.

The automated training determinism benchmark remains separate and uses the
utilities under `shell_test_utils/determinism/`. If additional benchmark
classes are added, place their test cases in a workload-specific directory
alongside `inference/`.
