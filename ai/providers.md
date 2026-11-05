# Provider paths

Four wire styles are supported by the design. Each is the same request and the same response - only the envelope differs.

| Provider | Endpoint | Auth header | Body shape |
|---|---|---|---|
| OpenAI-style | `{BASE_URL}/chat/completions` | `Authorization: Bearer <key>` | `messages: [{role, content}]` |
| Anthropic-style | `{BASE_URL}/v1/messages` | `x-api-key: <key>` plus `anthropic-version: 2023-06-01` | `messages`, `max_tokens`, `system` |
| Meta Model API | `https://api.meta.ai/v1/messages` | `Authorization: Bearer <key>` | Anthropic-style message array |
| OpenCode Go | `https://opencode.ai/zen/go` - both `/v1/messages` and `/v1/chat/completions` | `x-api-key: <key>` on the messages route, `Bearer` on the chat route | either |

## Notes

- **One base URL per session.** A client that talks to a single base URL cannot switch between providers that speak different dialects unless something in the middle translates. That is the whole reason a bridge exists rather than a single hardcoded call.
- **Model names are not portable.** `deepseek-v4.1-flash` means nothing to Anthropic. The bridge keeps the model name in configuration, not in code.
- **Status codes worth handling:** 401 means the key is wrong, 402 means the account has a billing problem, 429 means slow down, 5xx means retry once with backoff. Never retry a 401 or a 402.
- **Cost.** A gesture request is a few hundred bytes in and a two-line JSON out. Even a generous per-request price is negligible at human gesture rates, which is why this is a good use of a hosted model rather than a local one.

## What is not built

There is no live call in this repository. `gesture-bridge.example.js` shows where the adapter plugs in; the rules recogniser remains the only working path today.
