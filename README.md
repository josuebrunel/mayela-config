# mayela-config

Remote config for the [Mayela](https://github.com/josuebrunel/mayela) app.

`config.json` is fetched at runtime by the app to refresh its list of
selectable AI models per provider and its interview-copilot system prompt,
without requiring an app-store review cycle. It's a published copy of
`remote_config/config.json` in the main (private) app repo, which is the
source of truth — edit it there, then copy the updated file here and push.

## Schema

```json
{
  "version": 1,
  "system_prompt": "<the interview-copilot system prompt>",
  "providers": {
    "<provider-key>": [{"id": "<model-id>", "label": "<display-label>"}, ...]
  }
}
```

`<provider-key>` matches the app's internal provider keys (`claude`,
`gemini`, `deepseek`, `openai`). A provider key omitted from an update
leaves that provider's list unchanged in the app.

`system_prompt` is optional and independent of `providers` — an update can
change just the prompt, just the catalog, or both. Omitting it (or an
empty/invalid value) leaves the app's current prompt unchanged.
