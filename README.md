# eigenhelm-models

Model registry for [eigenhelm](https://github.com/metacogdev/eigenhelm) — the structural code quality engine.

## Usage

```bash
# List available models
eh model list --remote

# Pull a model
eh model pull general-polyglot-v1

# Use a pulled model
eh evaluate src/ --model general-polyglot-v1
```

Models are cached at `~/.eigenhelm/models/` after download.

## Available Models

| Name | Languages | Training files | Components | Description |
|------|-----------|---------------|------------|-------------|
| `general-polyglot-v1` | Python, JS, TS, Go, Rust | 1,594 | 36 | Class C polyglot model. Default bundled model. |

## Registry Format

The registry manifest is at [`registry.json`](registry.json). Each entry:

```json
{
  "name": "model-name",
  "description": "...",
  "language": "multi | python | ...",
  "corpus_class": "A | B | C",
  "n_components": 36,
  "n_training_files": 1594,
  "download_url": "https://github.com/metacogdev/eigenhelm-models/releases/download/.../model.npz",
  "sha256": "<hex>",
  "size_bytes": 331796,
  "version": "1.0.0"
}
```

## Contributing Models

To contribute a trained model:
1. Train with `eh train` against a curated corpus
2. Open a PR with the `.npz` file and a new entry in `registry.json`
3. Include corpus attribution (licenses, source repos, commit SHAs)

See [eigenhelm corpus guidelines](https://github.com/metacogdev/eigenhelm/blob/main/docs/corpus-targets.md) for corpus quality requirements.

## License

Models in this registry are distributed under the terms stated in each release.
The `general-polyglot-v1` model is licensed under [AGPL-3.0](https://github.com/metacogdev/eigenhelm/blob/main/LICENSE).
