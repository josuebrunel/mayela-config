# mayela-config

Remote model-catalog config for the [Mayela](https://github.com/josuebrunel/mayela) app.

`models.json` is fetched at runtime by the app to refresh its list of
selectable AI models per provider, without requiring an app-store review
cycle. It's a published copy of `remote_config/models.json` in the main
(private) app repo, which is the source of truth — edit it there, then copy
the updated file here and push.

## Schema

```json
{
  "version": 1,
  "providers": {
    "<provider-key>": [{"id": "<model-id>", "label": "<display-label>"}, ...]
  }
}
```

`<provider-key>` matches the app's internal provider keys (`claude`,
`gemini`, `deepseek`, `openai`). A provider key omitted from an update
leaves that provider's list unchanged in the app.
