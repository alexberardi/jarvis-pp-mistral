# Mistral Prompt Providers

Prompt providers for [Mistral 7B Instruct v0.3](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.3) and [Mixtral 8x7B](https://huggingface.co/mistralai/Mixtral-8x7B-Instruct-v0.1) models.

## Included Providers

| Provider | Description |
|----------|-------------|
| `Mistral7bMediumUntrained` | Base provider for Mistral 7B Q4_K_M GGUF. Handles both `<tool_call>` XML and native `[TOOL_CALLS]` formats. |
| `MixtralLargeUntrained` | Compressed prompt for Mixtral 8x7B MoE (~47B params). Minimal rules, the model's capacity needs less instruction. |

## Install

Via Jarvis admin or API:

```
POST /api/v0/prompt-providers/install
{"github_repo_url": "https://github.com/alexberardi/jarvis-pp-mistral"}
```

## Configuration

After install, set the active provider via settings:

```
llm.interface = Mistral7bMediumUntrained
```

## Model Details

- **Mistral 7B**: Dense 7B model, chatml chat format (mistral-instruct drops system messages)
- **Mixtral 8x7B**: Mixture-of-Experts (~47B params, ~13B active), compressed prompt variant
- **Format**: GGUF (Q4_K_M recommended)
- **Tool calling**: Text-based `<tool_call>` XML tags with `[TOOL_CALLS]` fallback parsing
- **Size tier**: Medium (Mistral 7B) / Large (Mixtral 8x7B)
