# 附录：逐文件完整原始数据

> 下面每个 CSV 的全部行、全部列都在这里；数值列与文本列分开呈现，便于比对。

### 9B · Ornith-9B Q6_K · RTX 3060 12G + AI Max+ 395（v1.0 → v2.4 演进）

源文件：`data/benchmark-results.csv` · 10 行 · 15 列

**条件/文本列**

| version | architecture | configuration | device | model | quantization | handoff_mib | measurement | disclosure |
|---|---|---|---|---|---|---|---|---|
| v1.0 | independent-pd | ai-max-395-only | AI Max+ 395 / Radeon 8060S | 9B | Q6_K |  | server-second-run | public |
| v1.0 | independent-pd | pd-first-512 | RTX 3060 + AI Max+ 395 | 9B | Q6_K |  | server-second-run | public |
| v1.0 | independent-pd | pd-first-2048 | RTX 3060 + AI Max+ 395 | 9B | Q6_K |  | server-second-run | public |
| v1.0 | independent-pd | full-pd | RTX 3060 + AI Max+ 395 | 9B | Q6_K | 208.57 | server-second-run | public |
| v2-baseline | fused-layer | rtx-3060-only | RTX 3060 12GB | 9B | Q6_K |  | llama-bench-pp-tg | standalone-baseline |
| v2-baseline | fused-layer | ai-max-395-only | AI Max+ 395 / Radeon 8060S | 9B | Q6_K |  | llama-bench-pp-tg | standalone-baseline |
| v2.1 | fused-layer | first-fused-pipeline | RTX 3060 + AI Max+ 395 | 9B | Q6_K |  | llama-bench-pp | public-label-no-internal-… |
| v2.2 | fused-layer | overlap-refinement | RTX 3060 + AI Max+ 395 | 9B | Q6_K |  | llama-bench-pp | public-label-no-internal-… |
| v2.3 | fused-layer | balance-refinement | RTX 3060 + AI Max+ 395 | 9B | Q6_K |  | llama-bench-pp-tg | public-label-no-internal-… |
| v2.4 | fused-layer | final-calibrated-pipeline | RTX 3060 + AI Max+ 395 | 9B | Q6_K |  | llama-bench-pp-tg | public-label-no-internal-… |

**数值列**

| prompt_tokens | output_tokens | ttft_s | prefill_tok_s | decode_tok_s | handoff_tokens |
|---|---|---|---|---|---|
| 5064 | 128 | 5.879 | 861.55 | 30.24 |  |
| 5064 | 128 | 5.720 | 886.62 | 30.22 | 512 |
| 5064 | 128 | 5.077 | 999.16 | 30.18 | 2048 |
| 5064 | 128 | 3.496 | 1452.29 | 30.28 | 5063 |
| 5064 | 128 |  | 1589.00 | 43.87 |  |
| 5064 | 128 |  | 970.00 | 31.27 |  |
| 5064 | 128 |  | 1865.08 |  |  |
| 5064 | 128 |  | 1893.87 |  |  |
| 5064 | 128 |  | 1999.51 | 37.16 |  |
| 5064 | 128 |  | 2129.69 | 50.73 |  |

### 27B · Qwen3.8-27B Q4_K_M · RTX 3080 20G + DGX Spark

源文件：`data/qwen27b-spark-3080-profiles.csv` · 10 行 · 28 列

**条件/文本列**

| experiment_id | profile | evidence_tag | primary_path | control_path | model | quantization | kv_type | speculative_decode | workload | statistic | measured_date | prefill_gain_vs_3080_pct | status | notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 27B-SPARK-01 | confirmed-prefill | prefill-confirmed-8k | RTX3080+Spark | RTX3080-standalone | Qwen3.8-27B | Q4_K_M | q4_0 | none | microbench-8192in-128out | median-of-warm-repeats | 2026-09-11 | 44.03 | measured | Highest Prefill confirmed… |
| 27B-SPARK-01 | confirmed-prefill | prefill-live-8k | RTX3080+Spark | RTX3080-standalone | Qwen3.8-27B | Q4_K_M | q4_0 | none | microbench-8192in-128out-… | median-of-three-repeats | 2026-09-11 | NA | measured | Later live retest of the … |
| 27B-SPARK-01 | confirmed-decode | decode-confirmed-2k | RTX3080+Spark | RTX3080-standalone | Qwen3.8-27B | Q4_K_M | q4_0 | DFlash2 | microbench-2048in-128out | median-of-warm-repeats | 2026-09-11 | NA | measured | Highest Decode confirmed … |
| 27B-SPARK-01 | confirmed-decode | decode-confirmed-8k | RTX3080+Spark | RTX3080-standalone | Qwen3.8-27B | Q4_K_M | q4_0 | DFlash2 | microbench-8192in-128out | median-of-warm-repeats | 2026-09-11 | NA | measured | Same Decode confirmed pro… |
| 27B-SPARK-01 | balanced | balanced-c1 | RTX3080+Spark | NA | Qwen3.8-27B | Q4_K_M | q4_0 | DFlash2 | serve-8192in-256out | median-of-official-rounds | 2026-09-11 | NA | measured | Balanced six-slot serving… |
| 27B-SPARK-01 | balanced | balanced-c2 | RTX3080+Spark | NA | Qwen3.8-27B | Q4_K_M | q4_0 | DFlash2 | serve-8192in-256out | median-of-official-rounds | 2026-09-11 | NA | measured | Metric semantics as C1 row |
| 27B-SPARK-01 | balanced | balanced-c3 | RTX3080+Spark | NA | Qwen3.8-27B | Q4_K_M | q4_0 | DFlash2 | serve-8192in-256out | median-of-official-rounds | 2026-09-11 | NA | measured | Metric semantics as C1 row |
| 27B-SPARK-01 | balanced | balanced-c4 | RTX3080+Spark | NA | Qwen3.8-27B | Q4_K_M | q4_0 | DFlash2 | serve-8192in-256out | median-of-official-rounds | 2026-09-11 | NA | measured | Metric semantics as C1 row |
| 27B-SPARK-01 | balanced | balanced-c5 | RTX3080+Spark | NA | Qwen3.8-27B | Q4_K_M | q4_0 | DFlash2 | serve-8192in-256out | median-of-official-rounds | 2026-09-11 | NA | measured | Metric semantics as C1 row |
| 27B-SPARK-01 | balanced | balanced-c6 | RTX3080+Spark | NA | Qwen3.8-27B | Q4_K_M | q4_0 | DFlash2 | serve-8192in-256out | median-of-official-rounds | 2026-09-11 | NA | measured | Metric semantics as C1 ro… |

**数值列**

| input_tokens | output_tokens | concurrency | n_repeats | prefill_tok_s | decode_tok_s | prefill_control_tok_s | decode_control_tok_s | aggregate_prefill_tok_s | aggregate_decode_tok_s | e2e_output_tok_s | ttft_p95_s | batch_e2e_s |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 8192 | 128 | 1 | 3 | 1603.20 | 17.62 | 1113.13 | 33.36 | NA | NA | NA | NA | NA |
| 8192 | 128 | 1 | 3 | 1601.05 | 17.41 | 1113.13 | 33.36 | NA | NA | NA | NA | NA |
| 2048 | 128 | 1 | 3 | 1153.95 | 63.97 | 1042.97 | 60.37 | NA | NA | NA | NA | NA |
| 8192 | 128 | 1 | 3 | 1124.32 | 49.20 | 1015.15 | 58.36 | NA | NA | NA | NA | NA |
| 8192 | 256 | 1 | 3 | NA | NA | NA | NA | 1097.40 | 47.69 | 19.91 | 7.489 | 12.857 |
| 8192 | 256 | 2 | 3 | NA | NA | NA | NA | 1094.21 | 31.18 | 19.49 | 19.145 | 26.273 |
| 8192 | 256 | 3 | 3 | NA | NA | NA | NA | 1089.37 | 28.04 | 20.47 | 28.990 | 37.524 |
| 8192 | 256 | 4 | 3 | NA | NA | NA | NA | 1086.44 | 24.90 | 19.86 | 38.932 | 51.564 |
| 8192 | 256 | 5 | 3 | NA | NA | NA | NA | 1087.57 | 24.77 | 20.53 | 48.471 | 62.336 |
| 8192 | 256 | 6 | 3 | NA | NA | NA | NA | 1088.06 | 25.55 | 21.62 | 58.317 | 71.048 |

### Ornith-1.5-35B-A3B · 3080 预填 + 395 解码

源文件：`data/ornith35a3b-local-results.csv` · 14 行 · 32 列

**条件/文本列**

| experiment | revision | configuration | primary_path | control_path | model | quantization | kv_type | workload | ttft_primary_ms | ttft_control_ms | token1_to_2_ms | prefill_primary_tok_s | prefill_control_tok_s | prefill_aggregate_control_tok_s | decode_primary_tok_s | decode_control_tok_s | decode_aggregate_control_tok_s | e2e_aggregate_primary_tok_s | e2e_aggregate_control_tok_s | kv_migration_ms | acceptance_pct | ms_per_step | tokens_per_step | status | notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 35B-A3B | dual-pd-35a3b | hot-pd-matrix | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | NA | service-1000in-128out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | MoE 35B-A3B; qwen35moe 40… |
| 35B-A3B | dual-pd-35a3b | hot-pd-matrix | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | NA | service-1000in-128out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | Metric semantics as C1 ro… |
| 35B-A3B | dual-pd-35a3b | hot-pd-matrix | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | NA | service-1000in-128out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | Metric semantics as C1 ro… |
| 35B-A3B | dual-pd-35a3b | hot-pd-matrix | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | NA | service-1000in-128out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | Metric semantics as C1 ro… |
| 35B-A3B | dual-pd-35a3b | hot-pd-matrix | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | NA | service-1000in-128out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | Metric semantics as C1 ro… |
| 35B-A3B | dual-pd-35a3b | hot-pd-matrix | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | NA | service-1000in-128out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | Metric semantics as C1 ro… |
| 35B-A3B | dual-pd-35a3b | hot-pd-matrix | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | NA | service-100000in-128out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | 100K input / 128 output; … |
| 35B-A3B | dual-pd-35a3b | hot-pd-matrix | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | NA | service-100000in-128out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | 100K semantics as C1 row;… |
| 35B-A3B | dual-pd-35a3b | hot-pd-matrix | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | NA | service-100000in-128out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | 100K semantics as C1 row;… |
| 35B-A3B | dual-pd-35a3b | hot-pd-matrix | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | NA | service-100000in-128out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | 100K semantics as C1 row;… |
| 35B-A3B | dual-pd-35a3b | hot-pd-matrix | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | NA | service-100000in-128out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | 100K semantics as C1 row;… |
| 35B-A3B | dual-pd-35a3b | hot-pd-matrix | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | NA | service-100000in-128out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | 100K semantics as C1 row;… |
| 35B-A3B | fused-dflash-pd | final-optimized-recipe | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | q4_0 | service-1000in-128out | NA | NA | NA | 4173.47 | NA | NA | 114.86 | NA | NA | NA | NA | NA | 93.86 | NA | NA | measured | three-process PD; 8082 pr… |
| 35B-A3B | fused-dflash-pd | final-optimized-recipe-bi… | RTX3080-prefill+395-Vulka… | NA | Ornith-1.5-35B-A3B | IQ4_XS | q4_0 | service-1000in-128out | NA | NA | NA | 4123.15 | NA | NA | 114.42 | NA | NA | NA | NA | NA | NA | NA | NA | measured | Metric semantics as the f… |

**数值列**

| release | concurrency | input_tokens | output_tokens | prefill_aggregate_primary_tok_s | decode_aggregate_primary_tok_s |
|---|---|---|---|---|---|
| 2.11 | 1 | 1000 | 128 | 4017.46 | NA |
| 2.11 | 2 | 1000 | 128 | 3947.64 | NA |
| 2.11 | 3 | 1000 | 128 | 3924.83 | NA |
| 2.11 | 4 | 1000 | 128 | 3913.85 | NA |
| 2.11 | 5 | 1000 | 128 | 3906.09 | NA |
| 2.11 | 6 | 1000 | 128 | 3943.88 | NA |
| 2.11 | 1 | 100000 | 128 | 2895.53 | 23.33 |
| 2.11 | 2 | 100000 | 128 | 2826.07 | 53.37 |
| 2.11 | 3 | 100000 | 128 | 2796.34 | 75.20 |
| 2.11 | 4 | 100000 | 128 | 2795.28 | 103.33 |
| 2.11 | 5 | 100000 | 128 | 2793.56 | 123.09 |
| 2.11 | 6 | 100000 | 128 | 2793.24 | 148.20 |
| 2.26 | 1 | 1000 | 128 | NA | NA |
| 2.26 | 1 | 1000 | 128 | NA | NA |

### Qwen3.8-Flash Q4 · 3080(CUDA0) + 395(Vulkan) 双设备分层

源文件：`data/qwen38flash-q4-local-results.csv` · 6 行 · 32 列

**条件/文本列**

| experiment | revision | configuration | primary_path | control_path | model | quantization | kv_type | workload | ttft_primary_ms | ttft_control_ms | token1_to_2_ms | prefill_control_tok_s | prefill_aggregate_control_tok_s | decode_control_tok_s | decode_aggregate_control_tok_s | e2e_aggregate_control_tok_s | kv_migration_ms | acceptance_pct | ms_per_step | tokens_per_step | status | notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Flash-Q4 | r374-layer-split | dual-device-layer-split | RTX3080-CUDA0+395-Vulkan1 | NA | Qwen3.8-Flash | Q4 | q4_0 | service-2077in-256out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | r374 final state 2026-09-… |
| Flash-Q4 | r374-layer-split | dual-device-layer-split | RTX3080-CUDA0+395-Vulkan1 | NA | Qwen3.8-Flash | Q4 | q4_0 | service-2077in-256out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | Metric semantics as C1 ro… |
| Flash-Q4 | r374-layer-split | dual-device-layer-split | RTX3080-CUDA0+395-Vulkan1 | NA | Qwen3.8-Flash | Q4 | q4_0 | service-2077in-256out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | Metric semantics as C1 ro… |
| Flash-Q4 | r374-layer-split | dual-device-layer-split | RTX3080-CUDA0+395-Vulkan1 | NA | Qwen3.8-Flash | Q4 | q4_0 | service-2077in-256out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | Metric semantics as C1 ro… |
| Flash-Q4 | r374-layer-split | dual-device-layer-split | RTX3080-CUDA0+395-Vulkan1 | NA | Qwen3.8-Flash | Q4 | q4_0 | service-2077in-256out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | Metric semantics as C1 ro… |
| Flash-Q4 | r374-layer-split | dual-device-layer-split | RTX3080-CUDA0+395-Vulkan1 | NA | Qwen3.8-Flash | Q4 | q4_0 | service-2077in-256out | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | NA | measured | Metric semantics as C1 ro… |

**数值列**

| release | concurrency | input_tokens | output_tokens | prefill_primary_tok_s | prefill_aggregate_primary_tok_s | decode_primary_tok_s | decode_aggregate_primary_tok_s | e2e_aggregate_primary_tok_s |
|---|---|---|---|---|---|---|---|---|
| 2.14 | 1 | 2077 | 256 | 569.892 | 569.892 | 35.204 | 35.204 | 213.581 |
| 2.14 | 2 | 2076 | 256 | 330.866 | 579.215 | 26.055 | 51.877 | 273.089 |
| 2.14 | 3 | 2078 | 256 | 208.459 | 625.250 | 21.714 | 65.143 | 320.267 |
| 2.14 | 4 | 2077.75 | 256 | 159.578 | 633.685 | 17.829 | 71.185 | 338.270 |
| 2.14 | 5 | 2077.4 | 256 | 130.675 | 552.070 | 14.578 | 69.595 | 327.366 |
| 2.14 | 6 | 2076.833 | 256 | 134.886 | 554.873 | 12.317 | 67.286 | 332.790 |

### Qwen3.8-Flash · DGX Spark + RTX 6000D

源文件：`data/qwen3.8-flash-next-spark-6000d.csv` · 19 行 · 19 列

**条件/文本列**

| profile | record_type | selection |
|---|---|---|
| capacity | prefill_c1 | median_c1 |
| capacity | prefill_c1 | second_run_steady_state |
| capacity | prefill_c1 | median_c1 |
| capacity | prefill_c1 | median_c1 |
| capacity | prefill_c1 | median_c1 |
| special_pp2 | prefill_c1 | median_c1 |
| special_pp2 | prefill_c1 | median_c1 |
| capacity | serving | three_rounds_excluding_wa… |
| capacity | serving | three_rounds_excluding_wa… |
| capacity | serving | three_rounds_excluding_wa… |
| capacity | serving | three_rounds_excluding_wa… |
| capacity | serving | three_rounds_excluding_wa… |
| capacity | serving | three_rounds_excluding_wa… |
| special_pp2 | serving | three_rounds_excluding_wa… |
| special_pp2 | serving | three_rounds_excluding_wa… |
| special_pp2 | serving | three_rounds_excluding_wa… |
| special_pp2 | serving | three_rounds_excluding_wa… |
| special_pp2 | serving | three_rounds_excluding_wa… |
| special_pp2 | serving | three_rounds_excluding_wa… |

**数值列**

| target_input_tokens | actual_input_tokens | concurrency | prefill_tps | ttft_s | observed_output_tokens | output_tokens_per_request | requests | succeeded | errors | total_output_tokens | total_wall_s | aggregate_output_tps | per_request_decode_tps_mean | ttft_p50_s | ttft_p95_s |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2048 | 2023.0 | 1 | 6754.540887388295 | 0.3053949330060277 | 2 |  |  |  |  |  |  |  |  |  |  |
| 4096 | 4021 | 1 | 8016.631673792558 | 0.501582230994245 | 2 |  |  |  |  |  |  |  |  |  |  |
| 8192 | 8017.5 | 1 | 8157.735293062046 | 0.9828264170064358 | 2 |  |  |  |  |  |  |  |  |  |  |
| 16384 | 16009.0 | 1 | 8309.15291980793 | 1.9267561664892128 | 2 |  |  |  |  |  |  |  |  |  |  |
| 32768 | 31994.0 | 1 | 8218.545887693457 | 3.8929330189857865 | 2 |  |  |  |  |  |  |  |  |  |  |
| 4096 | 4021 | 1 | 7538.101946419039 | 0.533423404005589 | 2 |  |  |  |  |  |  |  |  |  |  |
| 8192 | 8017 | 1 | 8696.944968924072 | 0.9218179520103149 | 2 |  |  |  |  |  |  |  |  |  |  |
|  |  | 1 |  |  |  | 256 | 3 | 3 | 0 | 768 | 8.099296728963964 | 94.8230476917272 | 108.13344706918109 | 0.12388924899278209 | 0.6940398105769418 |
|  |  | 2 |  |  |  | 256 | 6 | 6 | 0 | 1536 | 8.895084204006707 | 172.67964695692518 | 97.0728866648463 | 0.242650598011096 | 0.24602869000227656 |
|  |  | 3 |  |  |  | 256 | 9 | 9 | 0 | 2304 | 9.914852236019215 | 232.37865226371235 | 87.76664748729769 | 0.2482441540050786 | 0.24932494818931444 |
|  |  | 4 |  |  |  | 256 | 12 | 12 | 0 | 3072 | 10.373369606997585 | 296.14292331083186 | 82.91002750597958 | 0.2496209454984637 | 0.2548883555064094 |
|  |  | 5 |  |  |  | 256 | 15 | 15 | 0 | 3840 | 12.154851630009944 | 315.9232310593707 | 79.14882216920617 | 0.2653619320190046 | 1.572433448812808 |
|  |  | 6 |  |  |  | 256 | 18 | 18 | 0 | 4608 | 11.106197700981284 | 414.90347318352366 | 76.88667824956657 | 0.2658354635059368 | 0.26771702965343136 |
|  |  | 1 |  |  |  | 256 | 3 | 3 | 0 | 768 | 9.390314413991291 | 81.78639885110798 | 85.86115564324842 | 0.141380648012273 | 0.16476688161201308 |
|  |  | 2 |  |  |  | 256 | 6 | 6 | 0 | 1536 | 11.077249666966964 | 138.66257836369311 | 73.69112042117075 | 0.14309881097869948 | 0.15294783199351514 |
|  |  | 3 |  |  |  | 256 | 9 | 9 | 0 | 2304 | 13.862375903030625 | 166.205275063728 | 61.27416978096557 | 0.2660745839821175 | 0.3601169226167258 |
|  |  | 4 |  |  |  | 256 | 12 | 12 | 0 | 3072 | 14.962471522012493 | 205.31367397963191 | 56.81239029135253 | 0.1961500275065191 | 0.3684436342853587 |
|  |  | 5 |  |  |  | 256 | 15 | 15 | 0 | 3840 | 15.277487526007462 | 251.35022977194504 | 54.66035822251629 | 0.27246882597683 | 0.3699772114021471 |
|  |  | 6 |  |  |  | 256 | 18 | 18 | 0 | 4608 | 16.193558977014618 | 284.55758283529053 | 52.140460873695474 | 0.32141565399069805 | 0.3749290249063051 |

### DeepSeek-V4.1-Flash 六卡（2×6000D + 4×Spark）主表

源文件：`data/deepseek-v4.1-flash-six-gpu-v1-v7.csv` · 17 行 · 12 列

**条件/文本列**

| dataset | source | path |
|---|---|---|
| v7-code-matrix | S1 | pd |
| v7-code-matrix | S1 | pd |
| v7-code-matrix | S1 | pd |
| v7-code-matrix | S1 | pd |
| v7-code-matrix | S1 | pd |
| v7-code-matrix | S1 | pd |
| v7-code-matrix | S1 | pd |
| v7-code-matrix | S1 | pd |
| v7-matched-controls | S2 | pd |
| v7-matched-controls | S2 | direct |
| v7-matched-controls | S2 | direct |
| v7-matched-controls | S2 | pd |
| v7-matched-controls | S2 | direct |
| v7-matched-controls | S2 | pd |
| v7-matched-controls | S2 | pd |
| v7-matched-controls | S2 | direct |
| v7-long-output-diagnostic | S2 | pd |

**数值列**

| input_tokens | output_tokens | concurrency | repeats | aggregate_input_tok_s | aggregate_decode_tok_s | wall_output_tok_s | mean_ttft_s | source_batch |
|---|---|---|---|---|---|---|---|---|
| 8192 | 512 | 1 | 2 | 5678.910873743696 | 72.96244328053432 | 60.616563204926976 | 1.4429633490071865 | mean-of-two |
| 8192 | 512 | 4 | 2 | 7184.3635761386995 | 124.31281548380325 | 114.20526513004151 | 3.074812042999838 | mean-of-two |
| 8192 | 512 | 8 | 2 | 7543.4645894874875 | 158.78122420140363 | 150.45282679417917 | 5.218310096435744 | mean-of-two |
| 8192 | 512 | 12 | 2 | 7371.074447918397 | 177.24515902201637 | 170.01602964311354 | 7.520286480081874 | mean-of-two |
| 32768 | 512 | 1 | 2 | 9757.616810556163 | 73.77389565809244 | 49.7547038670056 | 3.3669049739910406 | mean-of-two |
| 32768 | 512 | 4 | 2 | 12804.591484623652 | 103.46170034161617 | 88.9583996964263 | 6.854046036254658 | mean-of-two |
| 32768 | 512 | 8 | 2 | 13173.51493727616 | 121.70194881730413 | 110.96518258350414 | 11.713233191750078 | mean-of-two |
| 32768 | 512 | 12 | 2 | 13814.563958264122 | 135.72924543160298 | 126.58552155704498 | 16.27783773770716 | mean-of-two |
| 8192 | 512 | 8 | 1 | 7838.252759232585 | 158.91869174465666 | 150.68171904702933 | 5.103904920873902 | 1 |
| 8192 | 512 | 8 | 1 | 1723.9177535107458 | 80.85995447242561 | 73.58284126415417 | 21.440885281503142 | 2 |
| 8192 | 512 | 8 | 1 | 1717.872490557174 | 79.7750171431554 | 72.66438562631122 | 21.98133459388191 | 3 |
| 8192 | 512 | 8 | 1 | 7786.60566966096 | 161.61574971300954 | 153.05545473062924 | 5.1018013441280345 | 4 |
| 32768 | 512 | 8 | 1 | 1710.162805598616 | 27.725329348858626 | 24.649720355658904 | 85.80338760012819 | 5 |
| 32768 | 512 | 8 | 1 | 13268.225942527439 | 123.9918785078381 | 112.16697493281134 | 11.60279534025176 | 6 |
| 32768 | 512 | 8 | 1 | 13331.902510185431 | 122.51694577092763 | 111.58212708636074 | 11.589698747622606 | 7 |
| 32768 | 512 | 8 | 1 | 1689.3309576394702 | 27.703474745934383 | 24.46335364649505 | 87.27845013288243 | 8 |
| 32768 | 2048 | 12 | 1 | 13485.393455116624 | 199.39332790122936 | 194.23791170515847 | 16.241873095418367 | 9 |

### DeepSeek-V4.1-Flash 峰值对比

源文件：`data/deepseek-v4.1-flash-six-gpu-v1-v7-peaks.csv` · 5 行 · 12 列

**条件/文本列**

| hardware | engine | metric | source |
|---|---|---|---|
| 4 Spark TP4 | sglang | full_wall_input | .tmp-dsv41-chunk-restart-… |
| 2 RTX 6000Dpro + 4 Spark | vllm PD | full_wall_input | data/deepseek-v4.1-flash-… |
| 8 H20-3e TP8/EP8 | sglang | full_wall_input | sglang/core/sglang-prefil… |
| 8 H20-3e TP8/EP8 | vllm | full_wall_input | vllm/core/vllm-long-c32-r… |
| 2 RTX 6000Dpro in six-GPU… | vllm | P_stage_prefill | dsv41-pp3-6node-20260914/… |

**数值列**

| input_tokens_per_request | output_tokens_per_request | concurrency | successful | requests | total_input_tokens | seconds | tokens_per_second |
|---|---|---|---|---|---|---|---|
| 8194;8018;8019;7895 | 1 | 4 | 4 | 4 | 32126 | 6.377509385987651 | 5037.3896854759105 |
| 32768 | 512 | 12 | 12 | 12 | 393216 | 48.157598550998955 | 8165.191202040189 |
| 8192 | 128 | 32 | 64 | 64 | 524288 | 106.58817696105689 | 4918.819468988142 |
| 24576 | 128 | 32 | 64 | 64 | 1572864 | 225.51247313199565 | 6974.620863119089 |
| 32768 | 128 | 1 | 1 | 1 | 32768 | 1.9623557680024533 | 16698.297288547034 |

### DeepSeek-V4.1-Flash v8 · 并发 32 压测

源文件：`data/deepseek-v4.1-flash-six-gpu-v8-seq32.csv` · 9 行 · 16 列

**数值列**

| case | concurrency | requests | success | failed | input_tokens | output_tokens_limit | output_tokens | p_batch_wall_sampled_s | p_batch_aggregate_tokens_s | p_prefill_service_tokens_s | decode_active_span_aggregate_tokens_s | end_to_end_output_tokens_s | per_request_decode_tokens_s_median | ttft_median_s | d_running_max |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| golden_code | 16 | 16 | 16 | 0 | 576 | 1024 | 5160 | 0.5653940640040673 | 1018.7584848712816 | 274.6178345177054 | 211.2944164013785 | 208.2358170838197 | 19.544349025082838 | 6.402359881991288 | 16.0 |
| golden_code | 24 | 24 | 24 | 0 | 864 | 1024 | 7559 | 0.5641836039721966 | 1531.4163579319093 | 283.35468911592295 | 396.8663044315919 | 391.82228989530756 | 20.072834141596083 | 1.279395087476587 | 24.0 |
| golden_code | 32 | 32 | 32 | 0 | 1152 | 1024 | 10233 | 0.592961510992609 | 1942.7905161526735 | 223.12371995531353 | 442.01883396809524 | 436.4020116585628 | 16.513774867054472 | 1.657386894512456 | 32.0 |
| 8192 | 16 | 16 | 16 | 0 | 131072 | 1024 | 16384 | 8.66186439001467 | 15132.077125462594 | 10974.52586311873 | 151.418005679642 | 149.96083750026054 | 10.343847091780056 | 5.801510199991753 | 16.0 |
| 8192 | 24 | 24 | 24 | 0 | 196608 | 1024 | 24576 | 12.884120164962951 | 15259.714864710388 | 10954.664015233684 | 202.1053808779526 | 200.6016679652569 | 9.475384165894347 | 8.076923154003453 | 24.0 |
| 8192 | 32 | 32 | 32 | 0 | 262144 | 1024 | 32768 | 16.811778064991813 | 15592.877742413122 | 10905.899482391884 | 223.65246105323092 | 222.2221259766103 | 7.824507584374505 | 9.699997559015173 | 32.0 |
| 32768 | 16 | 16 | 16 | 0 | 524288 | 1024 | 16384 | 32.11363385297591 | 16326.02533865582 | 14753.095215225672 | 122.10203743655376 | 119.49711649578735 | 9.823267510838676 | 19.713723759516142 | 16.0 |
| 32768 | 24 | 24 | 24 | 0 | 786432 | 1024 | 24576 | 48.25564560003113 | 16297.201917437256 | 14703.0671275612 | 152.04942392933174 | 149.36511868932968 | 8.432370754856057 | 28.92339276248822 | 24.0 |
| 32768 | 32 | 32 | 32 | 0 | 1048576 | 1024 | 32768 | 64.33847550401697 | 16297.806122784681 | 14609.221361629237 | 152.82750426162642 | 150.8235067502584 | 6.398616506271394 | 36.902972258511 | 32.0 |

### 外部 DGX Spark 对照（作者标注不可直接比较）

源文件：`data/dgx-spark-community-controls.csv` · 4 行 · 13 列

**条件/文本列**

| control_id | device | model | quantization | context_depth | kv_type | engine | source_date | source_url | directly_comparable | reason |
|---|---|---|---|---|---|---|---|---|---|---|
| dgx-spark-9b-tq3 | DGX Spark GB10 | Qwen3.5 9B | TQ3_4S |  |  | llama.cpp-tq3 PR 53 | 2026-06-30 | https://github.com/turbo-… | false | Different quantization pr… |
| dgx-spark-qwen38-27b-nvfp… | DGX Spark GB10 | Qwen3.8-27B | NVFP4 |  | fp8_e4m3 | SGLang + DFlash2 1M-conte… | 2026-08-29 | https://github.com/hasso5… | false | Different quantization en… |
| dgx-spark-qwen38-27b-nvfp… | DGX Spark GB10 | Qwen3.8-27B | NVFP4 |  | fp8_e4m3 | SGLang + DFlash2 1M-conte… | 2026-08-29 | https://github.com/hasso5… | false | Different quantization en… |
| dgx-spark-qwen38-27b-nvfp… | DGX Spark GB10 | Qwen3.8-27B | NVFP4 |  | fp8_e4m3 | SGLang + DFlash2 1M-conte… | 2026-08-29 | https://github.com/hasso5… | false | Different quantization en… |

**数值列**

| prompt_tokens | prefill_tok_s |
|---|---|
| 2048 | 2766.28 |
| 100000 | 1170 |
| 200000 | 800 |
| 300000 | 615 |

### 实验索引（14 个实验）

源文件：`data/experiment-index.csv` · 14 行 · 12 列

**条件/文本列**

| experiment_id | legacy_labels | family | claim_type | primary_question | control | changed_factor | primary_metrics | canonical_record | machine_data | status | comparability |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 9B-PD-01 | v1.0 | 9B Q6_K | feasibility | Can CUDA Prefill hand sta… | AI Max+ 395 only | Prompt share prefetched o… | TTFT prefill decode conti… | results/v1.0-independent-… | data/benchmark-results.csv | completed | Only inside the 9B v1.0 e… |
| 9B-PIPE-01 | v2.1/v2.2/v2.3/v2.4 check… | 9B Q6_K | controlled-acceleration | Can asynchronous layered … | RTX 3060 only and AI Max+… | Pipeline scheduling check… | Prefill decode repeatabil… | results/v2.4-fused-layer-… | data/benchmark-results.csv | completed | Only against same-envelop… |
| 27B-LONG-01 | 27B-A/3060-IQ3 | Qwen3.8-27B UD-IQ3_XXS | matched-host-improvement | Can layered placement imp… | AI Max+ 395 only | Add RTX 3060 layer stage | Prompt-depth completion p… | results/qwen3.8-27b-dual-… | data/qwen27b-local-result… | completed | Not comparable with Q4 or… |
| 27B-PD-01 | 27B-B/3080-Q4-v1.0 | Qwen3.8-27B Q4_K_M | feasibility | Can 3080 Prefill hand off… | AI Max+ 395 solo | Route through two-node PD | TTFT prefill decode KV mi… | results/qwen3.8-27b-dual-… | data/qwen27b-local-result… | completed | Historical scheduler enve… |
| 27B-KV-01 | 27B-C/27B-D/remote-kv-lat… | Qwen3.8-27B Q4_K_M | capacity-envelope | What serving trade-off re… | No matched latest no-remo… | Profile C or D and concur… | Context capacity prefill … | results/qwen3.8-27b-dual-… | data/qwen27b-local-result… | partial | Profiles are not separate… |
| 27B-DRAFT-AUDIT-01 | 395-natural-audit | Qwen3.8-27B Q4_K_M | validation-audit | Do repetitive-text specul… | Historical headless value… | Natural-language workload | Completion decode accepta… | results/qwen3.8-27b-dual-… | data/qwen27b-local-result… | completed | Guardrail not architectur… |
| ORNITH-PD-01 | 35B-A3B/r337 | Ornith-1.5-35B-A3B IQ4_XS | stability-envelope | Can MoE PD keep phase att… | No matched single-node sp… | Prompt depth and concurre… | Route success KV reuse pu… | results/ornith-1.5-35b-a3… | data/ornith35a3b-local-re… | completed | Not comparable with dense… |
| FLASH-SPLIT-01 | Flash-Q4/r374-layer-split | Qwen3.8-Flash Q4 | concurrency-envelope | Can one CUDA plus Vulkan … | No standalone control | Concurrency | HTTP success aggregate pr… | results/qwen3.8-flash-q4-… | data/qwen38flash-q4-local… | completed | No causal acceleration cl… |
| EXT-DGX-01 | DGX Spark controls | External community data | external-context | What public measurements … | Not applicable | External source and workl… | Original reported metric … | results/dgx-spark-communi… | data/dgx-spark-community-… | reference | Never a matched local con… |
| ORNITH-PD-02 | 35B-A3B/r379/r382/final-o… | Ornith-1.5-35B-A3B IQ4_XS | capacity-envelope | Does adding a fused DFlas… | No matched single-node sp… | Fused draft head plus uni… | Single-stream prefill dec… | results/ornith-1.5-35b-a3… | data/ornith35a3b-local-re… | completed | Not comparable with dense… |
| 27B-SPARK-01 |  | Qwen3.8-27B Q4_K_M | working-profile-envelope | Which Prefill Decode and … | RTX 3080 standalone at ma… | Working profile after sea… | Paired prefill decode and… | results/qwen3.8-27b-spark… | data/qwen27b-spark-3080-p… | completed | Not ranked against 395-ho… |
| FLASH-SPARK-01 |  | Qwen3.8-Flash-Next NVFP4 | working-profile-envelope | How do compute and memory… | Same 6000D plus Spark und… | Resident PLE lookup versu… | C1 Prefill and C1-C6 aggr… | results/qwen3.8-flash-nex… | data/qwen3.8-flash-next-s… | completed | Separate Prefill and gene… |
| DS41-6GPU-01 | deployment-V1-to-V7 | DeepSeek-V4.1-Flash origi… | matched-path-control-and-… | Can dual 6000D Prefill ac… | Same vLLM TP4 D service w… | PD route versus direct D … | Aggregate input; batch De… | results/deepseek-v4.1-fla… | data/deepseek-v4.1-flash-… | initial-success | Matched C8 controls only;… |
| FLASH-395-01 |  | Qwen3.8-Flash-Next NVFP4 | compute-split-envelope | Can a small-VRAM RTX 3080… | AI Max 395 solo baseline … | Hot experts and the dense… | Prefill and decode throug… | qwen38-flash-395-3080/ | qwen38-flash-395-3080/evi… | initial-success | 800+ and 40+ are experime… |

### RTX 3080 相关全部原始行（34 行汇总）

源文件：`data/3080-所有原始行.csv` · 34 行 · 58 列

**条件/文本列**

| source_file | acceptance_pct | aggregate_decode_tok_s | aggregate_prefill_tok_s | batch_e2e_s | canonical_record | changed_factor | claim_type | comparability | configuration | control | control_path | decode_aggregate_control_tok_s | decode_control_tok_s | decode_primary_tok_s | decode_tok_s | e2e_aggregate_control_tok_s | e2e_aggregate_primary_tok_s | e2e_output_tok_s | evidence_tag | experiment | experiment_id | family | kv_migration_ms | kv_type | legacy_labels | machine_data | measured_date | model | ms_per_step | n_repeats | notes | prefill_aggregate_control_tok_s | prefill_control_tok_s | prefill_gain_vs_3080_pct | prefill_primary_tok_s | prefill_tok_s | primary_metrics | primary_path | primary_question | profile | quantization | revision | speculative_decode | statistic | status | token1_to_2_ms | tokens_per_step | ttft_control_ms | ttft_p95_s | ttft_primary_ms | workload |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| qwen38flash-q4-local-resu… | NA |  |  |  |  |  |  |  | dual-device-layer-split |  | NA | NA | NA | 35.204 |  | NA | 213.581 |  |  | Flash-Q4 |  |  | NA | q4_0 |  |  |  | Qwen3.8-Flash | NA |  | r374 final state 2026-09-… | NA | NA |  | 569.892 |  |  | RTX3080-CUDA0+395-Vulkan1 |  |  | Q4 | r374-layer-split |  |  | measured | NA | NA | NA |  | NA | service-2077in-256out |
| qwen38flash-q4-local-resu… | NA |  |  |  |  |  |  |  | dual-device-layer-split |  | NA | NA | NA | 26.055 |  | NA | 273.089 |  |  | Flash-Q4 |  |  | NA | q4_0 |  |  |  | Qwen3.8-Flash | NA |  | Metric semantics as C1 ro… | NA | NA |  | 330.866 |  |  | RTX3080-CUDA0+395-Vulkan1 |  |  | Q4 | r374-layer-split |  |  | measured | NA | NA | NA |  | NA | service-2077in-256out |
| qwen38flash-q4-local-resu… | NA |  |  |  |  |  |  |  | dual-device-layer-split |  | NA | NA | NA | 21.714 |  | NA | 320.267 |  |  | Flash-Q4 |  |  | NA | q4_0 |  |  |  | Qwen3.8-Flash | NA |  | Metric semantics as C1 ro… | NA | NA |  | 208.459 |  |  | RTX3080-CUDA0+395-Vulkan1 |  |  | Q4 | r374-layer-split |  |  | measured | NA | NA | NA |  | NA | service-2077in-256out |
| qwen38flash-q4-local-resu… | NA |  |  |  |  |  |  |  | dual-device-layer-split |  | NA | NA | NA | 17.829 |  | NA | 338.270 |  |  | Flash-Q4 |  |  | NA | q4_0 |  |  |  | Qwen3.8-Flash | NA |  | Metric semantics as C1 ro… | NA | NA |  | 159.578 |  |  | RTX3080-CUDA0+395-Vulkan1 |  |  | Q4 | r374-layer-split |  |  | measured | NA | NA | NA |  | NA | service-2077in-256out |
| qwen38flash-q4-local-resu… | NA |  |  |  |  |  |  |  | dual-device-layer-split |  | NA | NA | NA | 14.578 |  | NA | 327.366 |  |  | Flash-Q4 |  |  | NA | q4_0 |  |  |  | Qwen3.8-Flash | NA |  | Metric semantics as C1 ro… | NA | NA |  | 130.675 |  |  | RTX3080-CUDA0+395-Vulkan1 |  |  | Q4 | r374-layer-split |  |  | measured | NA | NA | NA |  | NA | service-2077in-256out |
| qwen38flash-q4-local-resu… | NA |  |  |  |  |  |  |  | dual-device-layer-split |  | NA | NA | NA | 12.317 |  | NA | 332.790 |  |  | Flash-Q4 |  |  | NA | q4_0 |  |  |  | Qwen3.8-Flash | NA |  | Metric semantics as C1 ro… | NA | NA |  | 134.886 |  |  | RTX3080-CUDA0+395-Vulkan1 |  |  | Q4 | r374-layer-split |  |  | measured | NA | NA | NA |  | NA | service-2077in-256out |
| qwen27b-spark-3080-profil… |  | NA | NA | NA |  |  |  |  |  |  | RTX3080-standalone |  | 33.36 |  | 17.62 |  |  | NA | prefill-confirmed-8k |  | 27B-SPARK-01 |  |  | q4_0 |  |  | 2026-09-11 | Qwen3.8-27B |  | 3 | Highest Prefill confirmed… |  | 1113.13 | 44.03 |  | 1603.20 |  | RTX3080+Spark |  | confirmed-prefill | Q4_K_M |  | none | median-of-warm-repeats | measured |  |  |  | NA |  | microbench-8192in-128out |
| qwen27b-spark-3080-profil… |  | NA | NA | NA |  |  |  |  |  |  | RTX3080-standalone |  | 33.36 |  | 17.41 |  |  | NA | prefill-live-8k |  | 27B-SPARK-01 |  |  | q4_0 |  |  | 2026-09-11 | Qwen3.8-27B |  | 3 | Later live retest of the … |  | 1113.13 | NA |  | 1601.05 |  | RTX3080+Spark |  | confirmed-prefill | Q4_K_M |  | none | median-of-three-repeats | measured |  |  |  | NA |  | microbench-8192in-128out-… |
| qwen27b-spark-3080-profil… |  | NA | NA | NA |  |  |  |  |  |  | RTX3080-standalone |  | 60.37 |  | 63.97 |  |  | NA | decode-confirmed-2k |  | 27B-SPARK-01 |  |  | q4_0 |  |  | 2026-09-11 | Qwen3.8-27B |  | 3 | Highest Decode confirmed … |  | 1042.97 | NA |  | 1153.95 |  | RTX3080+Spark |  | confirmed-decode | Q4_K_M |  | DFlash2 | median-of-warm-repeats | measured |  |  |  | NA |  | microbench-2048in-128out |
| qwen27b-spark-3080-profil… |  | NA | NA | NA |  |  |  |  |  |  | RTX3080-standalone |  | 58.36 |  | 49.20 |  |  | NA | decode-confirmed-8k |  | 27B-SPARK-01 |  |  | q4_0 |  |  | 2026-09-11 | Qwen3.8-27B |  | 3 | Same Decode confirmed pro… |  | 1015.15 | NA |  | 1124.32 |  | RTX3080+Spark |  | confirmed-decode | Q4_K_M |  | DFlash2 | median-of-warm-repeats | measured |  |  |  | NA |  | microbench-8192in-128out |
| qwen27b-spark-3080-profil… |  | 47.69 | 1097.40 | 12.857 |  |  |  |  |  |  | NA |  | NA |  | NA |  |  | 19.91 | balanced-c1 |  | 27B-SPARK-01 |  |  | q4_0 |  |  | 2026-09-11 | Qwen3.8-27B |  | 3 | Balanced six-slot serving… |  | NA | NA |  | NA |  | RTX3080+Spark |  | balanced | Q4_K_M |  | DFlash2 | median-of-official-rounds | measured |  |  |  | 7.489 |  | serve-8192in-256out |
| qwen27b-spark-3080-profil… |  | 31.18 | 1094.21 | 26.273 |  |  |  |  |  |  | NA |  | NA |  | NA |  |  | 19.49 | balanced-c2 |  | 27B-SPARK-01 |  |  | q4_0 |  |  | 2026-09-11 | Qwen3.8-27B |  | 3 | Metric semantics as C1 row |  | NA | NA |  | NA |  | RTX3080+Spark |  | balanced | Q4_K_M |  | DFlash2 | median-of-official-rounds | measured |  |  |  | 19.145 |  | serve-8192in-256out |
| qwen27b-spark-3080-profil… |  | 28.04 | 1089.37 | 37.524 |  |  |  |  |  |  | NA |  | NA |  | NA |  |  | 20.47 | balanced-c3 |  | 27B-SPARK-01 |  |  | q4_0 |  |  | 2026-09-11 | Qwen3.8-27B |  | 3 | Metric semantics as C1 row |  | NA | NA |  | NA |  | RTX3080+Spark |  | balanced | Q4_K_M |  | DFlash2 | median-of-official-rounds | measured |  |  |  | 28.990 |  | serve-8192in-256out |
| qwen27b-spark-3080-profil… |  | 24.90 | 1086.44 | 51.564 |  |  |  |  |  |  | NA |  | NA |  | NA |  |  | 19.86 | balanced-c4 |  | 27B-SPARK-01 |  |  | q4_0 |  |  | 2026-09-11 | Qwen3.8-27B |  | 3 | Metric semantics as C1 row |  | NA | NA |  | NA |  | RTX3080+Spark |  | balanced | Q4_K_M |  | DFlash2 | median-of-official-rounds | measured |  |  |  | 38.932 |  | serve-8192in-256out |
| qwen27b-spark-3080-profil… |  | 24.77 | 1087.57 | 62.336 |  |  |  |  |  |  | NA |  | NA |  | NA |  |  | 20.53 | balanced-c5 |  | 27B-SPARK-01 |  |  | q4_0 |  |  | 2026-09-11 | Qwen3.8-27B |  | 3 | Metric semantics as C1 row |  | NA | NA |  | NA |  | RTX3080+Spark |  | balanced | Q4_K_M |  | DFlash2 | median-of-official-rounds | measured |  |  |  | 48.471 |  | serve-8192in-256out |
| qwen27b-spark-3080-profil… |  | 25.55 | 1088.06 | 71.048 |  |  |  |  |  |  | NA |  | NA |  | NA |  |  | 21.62 | balanced-c6 |  | 27B-SPARK-01 |  |  | q4_0 |  |  | 2026-09-11 | Qwen3.8-27B |  | 3 | Metric semantics as C1 ro… |  | NA | NA |  | NA |  | RTX3080+Spark |  | balanced | Q4_K_M |  | DFlash2 | median-of-official-rounds | measured |  |  |  | 58.317 |  | serve-8192in-256out |
| experiment-index.csv |  |  |  |  | results/qwen3.8-27b-dual-… | Route through two-node PD | feasibility | Historical scheduler enve… |  | AI Max+ 395 solo |  |  |  |  |  |  |  |  |  |  | 27B-PD-01 | Qwen3.8-27B Q4_K_M |  |  | 27B-B/3080-Q4-v1.0 | data/qwen27b-local-result… |  |  |  |  |  |  |  |  |  |  | TTFT prefill decode KV mi… |  | Can 3080 Prefill hand off… |  |  |  |  |  | completed |  |  |  |  |  |  |
| experiment-index.csv |  |  |  |  | results/qwen3.8-27b-dual-… | Profile C or D and concur… | capacity-envelope | Profiles are not separate… |  | No matched latest no-remo… |  |  |  |  |  |  |  |  |  |  | 27B-KV-01 | Qwen3.8-27B Q4_K_M |  |  | 27B-C/27B-D/remote-kv-lat… | data/qwen27b-local-result… |  |  |  |  |  |  |  |  |  |  | Context capacity prefill … |  | What serving trade-off re… |  |  |  |  |  | partial |  |  |  |  |  |  |
| experiment-index.csv |  |  |  |  | results/qwen3.8-27b-spark… | Working profile after sea… | working-profile-envelope | Not ranked against 395-ho… |  | RTX 3080 standalone at ma… |  |  |  |  |  |  |  |  |  |  | 27B-SPARK-01 | Qwen3.8-27B Q4_K_M |  |  |  | data/qwen27b-spark-3080-p… |  |  |  |  |  |  |  |  |  |  | Paired prefill decode and… |  | Which Prefill Decode and … |  |  |  |  |  | completed |  |  |  |  |  |  |
| experiment-index.csv |  |  |  |  | qwen38-flash-395-3080/ | Hot experts and the dense… | compute-split-envelope | 800+ and 40+ are experime… |  | AI Max 395 solo baseline … |  |  |  |  |  |  |  |  |  |  | FLASH-395-01 | Qwen3.8-Flash-Next NVFP4 |  |  |  | qwen38-flash-395-3080/evi… |  |  |  |  |  |  |  |  |  |  | Prefill and decode throug… |  | Can a small-VRAM RTX 3080… |  |  |  |  |  | initial-success |  |  |  |  |  |  |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | hot-pd-matrix |  | NA | NA | NA | NA |  | NA | NA |  |  | 35B-A3B |  |  | NA | NA |  |  |  | Ornith-1.5-35B-A3B | NA |  | MoE 35B-A3B; qwen35moe 40… | NA | NA |  | NA |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | dual-pd-35a3b |  |  | measured | NA | NA | NA |  | NA | service-1000in-128out |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | hot-pd-matrix |  | NA | NA | NA | NA |  | NA | NA |  |  | 35B-A3B |  |  | NA | NA |  |  |  | Ornith-1.5-35B-A3B | NA |  | Metric semantics as C1 ro… | NA | NA |  | NA |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | dual-pd-35a3b |  |  | measured | NA | NA | NA |  | NA | service-1000in-128out |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | hot-pd-matrix |  | NA | NA | NA | NA |  | NA | NA |  |  | 35B-A3B |  |  | NA | NA |  |  |  | Ornith-1.5-35B-A3B | NA |  | Metric semantics as C1 ro… | NA | NA |  | NA |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | dual-pd-35a3b |  |  | measured | NA | NA | NA |  | NA | service-1000in-128out |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | hot-pd-matrix |  | NA | NA | NA | NA |  | NA | NA |  |  | 35B-A3B |  |  | NA | NA |  |  |  | Ornith-1.5-35B-A3B | NA |  | Metric semantics as C1 ro… | NA | NA |  | NA |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | dual-pd-35a3b |  |  | measured | NA | NA | NA |  | NA | service-1000in-128out |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | hot-pd-matrix |  | NA | NA | NA | NA |  | NA | NA |  |  | 35B-A3B |  |  | NA | NA |  |  |  | Ornith-1.5-35B-A3B | NA |  | Metric semantics as C1 ro… | NA | NA |  | NA |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | dual-pd-35a3b |  |  | measured | NA | NA | NA |  | NA | service-1000in-128out |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | hot-pd-matrix |  | NA | NA | NA | NA |  | NA | NA |  |  | 35B-A3B |  |  | NA | NA |  |  |  | Ornith-1.5-35B-A3B | NA |  | Metric semantics as C1 ro… | NA | NA |  | NA |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | dual-pd-35a3b |  |  | measured | NA | NA | NA |  | NA | service-1000in-128out |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | hot-pd-matrix |  | NA | NA | NA | NA |  | NA | NA |  |  | 35B-A3B |  |  | NA | NA |  |  |  | Ornith-1.5-35B-A3B | NA |  | 100K input / 128 output; … | NA | NA |  | NA |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | dual-pd-35a3b |  |  | measured | NA | NA | NA |  | NA | service-100000in-128out |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | hot-pd-matrix |  | NA | NA | NA | NA |  | NA | NA |  |  | 35B-A3B |  |  | NA | NA |  |  |  | Ornith-1.5-35B-A3B | NA |  | 100K semantics as C1 row;… | NA | NA |  | NA |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | dual-pd-35a3b |  |  | measured | NA | NA | NA |  | NA | service-100000in-128out |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | hot-pd-matrix |  | NA | NA | NA | NA |  | NA | NA |  |  | 35B-A3B |  |  | NA | NA |  |  |  | Ornith-1.5-35B-A3B | NA |  | 100K semantics as C1 row;… | NA | NA |  | NA |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | dual-pd-35a3b |  |  | measured | NA | NA | NA |  | NA | service-100000in-128out |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | hot-pd-matrix |  | NA | NA | NA | NA |  | NA | NA |  |  | 35B-A3B |  |  | NA | NA |  |  |  | Ornith-1.5-35B-A3B | NA |  | 100K semantics as C1 row;… | NA | NA |  | NA |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | dual-pd-35a3b |  |  | measured | NA | NA | NA |  | NA | service-100000in-128out |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | hot-pd-matrix |  | NA | NA | NA | NA |  | NA | NA |  |  | 35B-A3B |  |  | NA | NA |  |  |  | Ornith-1.5-35B-A3B | NA |  | 100K semantics as C1 row;… | NA | NA |  | NA |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | dual-pd-35a3b |  |  | measured | NA | NA | NA |  | NA | service-100000in-128out |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | hot-pd-matrix |  | NA | NA | NA | NA |  | NA | NA |  |  | 35B-A3B |  |  | NA | NA |  |  |  | Ornith-1.5-35B-A3B | NA |  | 100K semantics as C1 row;… | NA | NA |  | NA |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | dual-pd-35a3b |  |  | measured | NA | NA | NA |  | NA | service-100000in-128out |
| ornith35a3b-local-results… | 93.86 |  |  |  |  |  |  |  | final-optimized-recipe |  | NA | NA | NA | 114.86 |  | NA | NA |  |  | 35B-A3B |  |  | NA | q4_0 |  |  |  | Ornith-1.5-35B-A3B | NA |  | three-process PD; 8082 pr… | NA | NA |  | 4173.47 |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | fused-dflash-pd |  |  | measured | NA | NA | NA |  | NA | service-1000in-128out |
| ornith35a3b-local-results… | NA |  |  |  |  |  |  |  | final-optimized-recipe-bi… |  | NA | NA | NA | 114.42 |  | NA | NA |  |  | 35B-A3B |  |  | NA | q4_0 |  |  |  | Ornith-1.5-35B-A3B | NA |  | Metric semantics as the f… | NA | NA |  | 4123.15 |  |  | RTX3080-prefill+395-Vulka… |  |  | IQ4_XS | fused-dflash-pd |  |  | measured | NA | NA | NA |  | NA | service-1000in-128out |

**数值列**

| concurrency | decode_aggregate_primary_tok_s | input_tokens | output_tokens | prefill_aggregate_primary_tok_s | release |
|---|---|---|---|---|---|
| 1 | 35.204 | 2077 | 256 | 569.892 | 2.14 |
| 2 | 51.877 | 2076 | 256 | 579.215 | 2.14 |
| 3 | 65.143 | 2078 | 256 | 625.250 | 2.14 |
| 4 | 71.185 | 2077.75 | 256 | 633.685 | 2.14 |
| 5 | 69.595 | 2077.4 | 256 | 552.070 | 2.14 |
| 6 | 67.286 | 2076.833 | 256 | 554.873 | 2.14 |
| 1 |  | 8192 | 128 |  |  |
| 1 |  | 8192 | 128 |  |  |
| 1 |  | 2048 | 128 |  |  |
| 1 |  | 8192 | 128 |  |  |
| 1 |  | 8192 | 256 |  |  |
| 2 |  | 8192 | 256 |  |  |
| 3 |  | 8192 | 256 |  |  |
| 4 |  | 8192 | 256 |  |  |
| 5 |  | 8192 | 256 |  |  |
| 6 |  | 8192 | 256 |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
| 1 | NA | 1000 | 128 | 4017.46 | 2.11 |
| 2 | NA | 1000 | 128 | 3947.64 | 2.11 |
| 3 | NA | 1000 | 128 | 3924.83 | 2.11 |
| 4 | NA | 1000 | 128 | 3913.85 | 2.11 |
| 5 | NA | 1000 | 128 | 3906.09 | 2.11 |
| 6 | NA | 1000 | 128 | 3943.88 | 2.11 |
| 1 | 23.33 | 100000 | 128 | 2895.53 | 2.11 |
| 2 | 53.37 | 100000 | 128 | 2826.07 | 2.11 |
| 3 | 75.20 | 100000 | 128 | 2796.34 | 2.11 |
| 4 | 103.33 | 100000 | 128 | 2795.28 | 2.11 |
| 5 | 123.09 | 100000 | 128 | 2793.56 | 2.11 |
| 6 | 148.20 | 100000 | 128 | 2793.24 | 2.11 |
| 1 | NA | 1000 | 128 | NA | 2.26 |
| 1 | NA | 1000 | 128 | NA | 2.26 |
