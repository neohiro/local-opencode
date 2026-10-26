# Plugin vs Config Mod

This is a **config-based mod** (not an opencode plugin / source patch). A plugin patch is overkill for adding a provider endpoint; opencode already supports custom providers via `opencode.jsonc`. The included `local-provider-complete.patch` is kept for backward compatibility but no longer required.

## Why config-based?
- Plugin would need to hook provider/model discovery in SDK (`plugins/` layer) and rebuild the desktop binary.
- Config-based approach (`providers.local`) achieves the same routing with zero plugin overhead.
- Verified: direct `/v1/chat/completions` returns assistant content using config reference (`local/huihui-qwen3.8-27b-abliterated`).

## Quick install
1. Copy snippet from README.md into `~/.config/opencode/opencode.jsonc`.
2. No API key needed — endpoint (`wsl-desktop.beaver-sidewinder.ts.net:1234`) runs without auth.
3. Restart opencode desktop client.
4. Select model by direct ID reference (`local/huihui-qwen3.8-27b-abliterated`) if picker shows only default LM Studio entries.
