# local-opencode

Config-based mod for local LM Studio / OpenAI-compatible provider in opencode desktop and serve.

## Snippet (opencode.jsonc)

"providers": {
  "local": {
    "baseURL": "http://127.0.0.1:1234/v1",
    "apiKey": "{env:LMSTUDIO_API_KEY}",
    "timeout": 30000
  }
},
"model": "local/huihui-qwen3.8-27b-abliterated",
"small_model": "local/huihui-qwen3.8-27b-abliterated"

## Note
Direct routing verified: endpoint responds 200 and returns assistant content. Picker behavior is client-side; direct model reference works reliably.