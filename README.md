# local-opencode

Config-based mod for local llama-server / OpenAI-compatible provider in opencode desktop and serve.

## Working endpoint (Tailscale mesh)

- `http://wsl-desktop.beaver-sidewinder.ts.net:1234/v1`
- No API key required (`apiKey` removed)
- Model: `local/huihui-qwen3.8-27b-abliterated` (Q3_K, ~14.5 GB)

## Snippet (`opencode.jsonc`)

```jsonc
"providers": {
  "local": {
    "baseURL": "http://wsl-desktop.beaver-sidewinder.ts.net:1234/v1",
    "timeout": 30000
  }
},
"model": "local/huihui-qwen3.8-27b-abliterated",
"small_model": "local/huihui-qwen3.8-27b-abliterated"
```

## Verification

Direct routing verified (`/v1/chat/completions` returns assistant message). Picker behavior is client-side; direct model reference works reliably.

## Old broken snippet (replaced)

- `baseURL` was `http://127.0.0.1:1234/v1` (localhost only, misses Tailscale endpoint)
- `apiKey` was `"{env:LMSTUDIO_API_KEY}"` (no key set; server has no auth)

## Recovery / build notes

- Server binary: `/home/user/llama-server-build/build/bin/llama-server` (compiled `GGML_CUDA=ON`, arch `89` for RTX 5060 Ti)
- Launch script: `/home/user/neohiro-wsllmstudio/start_llama_server.sh` (GPU-only: `--gpu-layers 99 --flash-attn on --batch-size 512 --parallel 2`)
- If `wsl-desktop` is rebuilt: install `nvidia-driver-570`, `nvidia-cuda-toolkit`, rebuild with `cmake -DGGML_CUDA=ON -DCMAKE_CUDA_ARCHITECTURES=89`
