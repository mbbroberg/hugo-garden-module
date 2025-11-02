# Hugo Garden Module - Example Site

This example site demonstrates how to use the Hugo Garden Module.

## Running the Example

From the `exampleSite` directory:

```bash
hugo server
```

This will start a local server at `http://localhost:1313/` where you can see the digital garden in action.

> **Note**: The `go.mod` file in this directory uses a `replace` directive to point to the parent module directory, allowing you to test local changes without publishing the module first.

## What's Included

- Three example garden entries at different growth stages (seed, sprout, rhizome)
- Configuration examples showing all available customization options
- The garden index page with browsing interface
- Integration of the garden-state-indicator and garden-callout partials

## Creating New Garden Entries

```bash
hugo new content/garden/my-new-idea.md
```

This will use the garden archetype to create a properly formatted entry.

## Customization

See the `config/_default/config.toml` file for all available configuration options. You can customize:
- Colors for each growth stage
- Emojis and labels
- Callout text
- Date display preferences
- And more!
