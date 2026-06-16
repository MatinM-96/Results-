# GIS Evaluation Results

This repository contains raw evaluation outputs from a doctoral study on language-model support for GIS workflows. The files are preserved close to their original execution format so that individual runs can be inspected, counted, and re-analysed without relying only on summary tables.

The repository is intended as a result archive, not as a polished software package. It contains prompts, query descriptions, configuration files, model outputs, execution logs, latency values, token estimates, SQL validation fields, tool-use information, and task-completion indicators.

## Repository Structure

```text
llm-gis-evaluation-results/
  prompt_comparison_evaluation/
    index.json
    <query_hash>/
      query.json
      prompt_v1/
      prompt_v2/
      prompt_v3/
      prompt_v4/
      prompt_v5/

  statistical_repeated_runs/
    index.json
    <query_hash>/
      query.json
      prompt_v5/
```

## Experiment Sets

### Prompt Comparison Evaluation

`prompt_comparison_evaluation/` contains runs used to compare five prompt formulations across the GIS benchmark tasks. The index file records 30 query entries and 6,991 runs.

The prompt variants are stored as:

```text
prompt_v1
prompt_v2
prompt_v3
prompt_v4
prompt_v5
```

Each query folder is named by a stable query hash. The associated `query.json` file contains the query identifier, query hash, and natural-language GIS task description.

### Statistical Repeated Runs

`statistical_repeated_runs/` contains repeated executions used to analyse run-to-run variability under the final prompt setting. This experiment set uses `prompt_v5` and includes 31 query entries. The index file records 11,365 runs.

These repeated runs are used to estimate stability, model-level uncertainty, task-level variation, failure modes, and differences between repeated executions of the same task and prompt setting.

## File Conventions

`index.json` gives a compact overview of each experiment set. Each entry contains the query identifier, query hash, query text, first recorded run time, total run count, and a breakdown by model and prompt configuration.

`query.json` stores the benchmark task for a single query.

`prompt.txt` stores the prompt text used for a given prompt version.

`config.json` stores the run configuration, including the prompt name and parameter settings.

`result.json` stores the main run output and evaluation fields, including model name, runtime information, final result, task-completion flags, SQL validity, latency, token estimates, tool-use counts, and recorded errors.

`logs.json` stores additional execution trace information, including planned steps, retrieval information, SQL repair counts, validation errors, and tool-related events.

## Models Represented

The result files include runs for the following model identifiers:

```text
DeepSeek-V3.2
Mistral-Large-3
functiongemma
gemma-4-31b-vllm
gpt-5-mini
gpt-oss-120b-vllm
llama-3.3-70b-fp8-vllm
mistral-nemo-12b-vllm
mistral-small-24b-vllm
qwen2.5-32b-vllm
qwen3-4b-vllm
qwen3-8b-vllm
qwen3-coder-30b-vllm
```

## Notes for Analysis

The files should be treated as raw experimental records. Some runs contain incomplete outputs, errors, retries, repaired SQL, failed validation, or failed task completion. These cases are part of the empirical material and should not be removed unless a documented exclusion rule is applied.

When reporting results from this repository, include the experiment set, query identifier or query hash, prompt version, model identifier, and repository commit hash. This makes later comparison and replication easier.

## Suggested Citation Text

This repository contains raw outputs from GIS benchmark experiments conducted as part of doctoral research on language-model support for geospatial analysis tasks. The archive includes prompt-comparison runs, repeated-run experiments, model outputs, execution logs, and evaluation metadata.
