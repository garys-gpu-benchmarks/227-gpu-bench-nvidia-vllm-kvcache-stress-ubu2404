# Results: 227 KV Cache Stress Test

**Main goal:** Analyze LLM KV-cache stress under long contexts  
**Tools:** Start python -m vllm.entrypoints.openai.api_server on port 8000, then run scripts/benchmark_serving.py

Reference results from the validation run on the system shown in each section (recorded 2026-11-22). Your own runs write `results/RESULTS_ACTUAL.md` in the same format.

> Smoke runs use deliberately small sizes. They check that the workload installs and runs end to end; their numbers are not performance results. Baseline and extended are.

<!-- profile:smoke -->
## smoke

- **System:** 1× NVIDIA H100 80GB HBM3 (81559 MiB) · Intel(R) Xeon(R) Platinum 8470 · Ubuntu 24.04.5 LTS · kernel 6.8.0-149-generic · driver 595.112.07
- **Run:** 2026-11-22T11:26:50Z · status **PASS** (exit 0)
- **Time (mm:ss):** setup 04:15 · benchmark 00:01 · whole run 04:30
- **Source:** run 227_20261122_112650
- **Command:** `bash run_benchmark.sh --smoke --model-name mistralai/Mistral-7B-v0.3 --dtype bfloat16 --kv-cache-dtype auto --gpu-memory-utilization 0.9 --max-model-len 128 --input-len 64 --output-len 16 --num-prompts 2 --concurrency 2 --seed 0`

| # | Metric | Result |
|---|---|---|
| 1 | Aggregate decode throughput, tokens/s (decode_throughput_tokens_sec) | 324.753206200338 |
| 2 | Time To First Token p50, ms (ttft_msec) | 44.518169001094066 |
| 3 | TPOT p50, ms (tpot_msec) | 5.922289033575604 |
| 4 | Peak KV-cache usage, GiB (kv_cache_peak_gb) | 0.023438290694407043 |
| 5 | KV-cache usage peak, pct (kv_cache_usage_peak_pct) | 0.042170368287886006 |
<!-- /profile:smoke -->
