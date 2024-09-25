## How to use it

Autocomplete provides inline code suggestions as you type. To enable it, simply click the "Continue" button in the status bar at the bottom right of your IDE or ensure the "Enable Tab Autocomplete" option is checked in your IDE settings.

### Accepting a full suggestion

Accept a full suggestion by pressing `Tab`

### Rejecting a full suggestion

Reject a full suggestion with `Esc`

### Partially accepting a suggestion

For more granular control, use `cmd/ctrl + →` to accept parts of the suggestion word-by-word.

## Best overall experience

For the best Autocomplete experience, we recommend using Codestral through the [Mistral API](https://console.mistral.ai/). This model offers high-quality completions with an excellent understanding of code context:

```json title="config.json""
{
  "tabAutocompleteModel": {
    "title": "Codestral",
    "provider": "mistral",
    "model": "codestral-latest",
    "apiKey": "YOUR_API_KEY"
  }
}
```

:::tip[Codestral API Key]
The API keys for Codestral and the general Mistral APIs are different. If you are using Codestral, you probably want a Codestral API key, but if you are sharing the key as a team or otherwise want to use `api.mistral.ai`, then make sure to set `"apiBase": "https://api.mistral.ai/v1"` in your `tabAutocompleteModel`.
:::

## Local, offline / self-hosted experience

For those preferring local execution or self-hosting,`StarCoder2-3b` offers a good balance of performance and quality for most users:

```json title="config.json""
{
  "tabAutocompleteModel": {
    "title": "StarCoder2-3b",
    "model": "starcoder2:3b",
    "provider": "ollama"
  }
}
```

## Alternative experiences

- Completions too slow? Try `deepseek-coder:1.3b-base` for quicker completions on less powerful hardware
- Have more compute? Use `deepseek-coder:6.7b-base` for potentially higher-quality suggestions

:::note

For LM Studio users, navigate to the "My Models" section, find your desired model, and copy the path (e.g., second-state/StarCoder2-3B-GGUF/starcoder2-3b-Q8_0.gguf). Use this path as the `model` value in your configuration.

:::

## Other experiences

There are many more models and providers you can use with Autocomplete. Check them out [here](../customize/model-types/autocomplete.md).

Autocomplete will automatically determine context based on the current cursor position. We use the following techniques to determine what to include in the prompt:

### File prefix/suffix

We will always include the code from your file prior to and after the cursor position.

### Definitions from the Language Server Protocol

Similar to how you can use `cmd/ctrl + click` in your editor, we use the same tool (the LSP) to power "go to definition". For example, if you are typing out a function call, we will include the function definition. Or, if you are writing code inside of a method, we will include the type definitions for any parameters or the return type.

### Imported files

Because there are often many imports, we can't include all of them. Instead, we look for symbols around your cursor that have matching imports and use that as context.

### Recent files

We automatically consider recently opened or edited files and include snippets that are relevant to the current completion.
