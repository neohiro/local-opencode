# Plugin vs Config Mod

This is a **config-based mod** (not an opencode plugin). A plugin is overkill for adding a provider endpoint; opencode already supports custom providers via `opencode.jsonc`.

## Why not a plugin?
- Plugin would need to hook provider/model discovery in SDK (`plugins/` layer).
- Config-based approach (`providers.local`) achieves the same routing with zero plugin overhead and survives restarts.
- Verified: direct `/v1/chat/completions` returns assistant content using config reference (`local/huihui-qwen3.8-27b-abliterated`).

## Quick install
1. Copy snippet from README.md into `~/.config/opencode/opencode.jsonc`.
2. Set env: `[System.Environment]::SetEnvironmentVariable('LMSTUDIO_API_KEY', 'your-key', 'User')`.
3. Restart opencode server + desktop client.
4. Select model by direct ID reference if picker shows only default LM Studio entries.
