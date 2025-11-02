# 🌱 Hugo Garden Module

A Hugo module for creating and maintaining a digital garden on your Hugo site. Transform your blog into a living, growing knowledge base where ideas evolve over time.

## What is a Digital Garden?

Digital gardens are a different philosophy for publishing online:

- **Traditional blogs**: Time-ordered, finished posts that decay
- **Digital gardens**: Networked, evolving notes that grow

Garden entries have growth stages that indicate maturity:
- 🌱 **Seeds** - New ideas, just planted
- 🌿 **Sprouts** - Developing thoughts with emerging connections
- 🫚 **Rhizomes** - Mature, interconnected ideas

## Features

✨ **Beautiful Garden Interface**
- Browse by growth stage or topic
- Visual badges showing entry counts
- Smooth animations and transitions
- Fully responsive design

📊 **Growth Tracking**
- Track when ideas were "planted" (created)
- Show when they were last "tended" (updated)
- Visual indicators of maturity level

🎨 **Highly Customizable**
- Custom colors for each growth stage
- Configurable emojis and labels
- Adjustable date displays
- Override any template or style

🔗 **Connection-Focused**
- Tag-based organization
- Cross-referencing support
- Dataview-style metadata (optional)

## Quick Start

### Prerequisites

- Hugo 0.112.0 or higher
- Go 1.18+ (for module support)
- Git

### Installation

1. **Initialize Hugo modules** in your site (if not already done):

```bash
hugo mod init github.com/YOUR_USERNAME/YOUR_SITE
```

2. **Add the module** to your `config.toml`:

```toml
[module]
  [[module.imports]]
    path = "github.com/mbbroberg/hugo-garden-module"
```

3. **Add required taxonomies**:

```toml
[taxonomies]
  tag = "tags"
  state = "state"
```

4. **Download the module**:

```bash
hugo mod get -u
```

5. **Create your garden index page** at `content/garden/_index.md`:

```markdown
---
title: "🌱 My Digital Garden"
layout: garden
---

Welcome to my digital garden! This is where ideas grow.
```

6. **Add the garden to your menu** (optional):

```toml
[[menu.main]]
  name = "Digital Garden 🌱"
  url = "/garden/"
  weight = 2
```

### Creating Your First Entry

```bash
hugo new content/garden/my-first-seed.md --kind garden
```

This creates a properly formatted garden entry:

```markdown
---
title: "My First Seed"
type: garden
date: 2024-01-15
created: 2024-01-15 Mon 10:30am
updated: 2024-01-15 Mon 10:30am
state: seed
tags: []
share: true
---

Your idea goes here!
```

## Using Garden Features in Your Single Post Layout

If you want garden posts to display with state indicators and callouts in your existing single post layout, add this to your `layouts/_default/single.html`:

```html
{{ define "main" }}
<div class="post">
  <!-- Add garden state indicator at the top -->
  {{ if eq .Type "garden" }}
    {{ partial "garden-state-indicator.html" . }}
  {{ end }}

  <!-- Your post content -->
  <div class="post__content">
    {{ .Content }}
  </div>

  <!-- Add garden callout at the bottom -->
  {{ if eq .Type "garden" }}
    {{ partial "garden-callout.html" . }}
  {{ end }}
</div>

<!-- Include garden CSS -->
{{ if eq .Type "garden" }}
  {{ $gardenCSS := resources.Get "css/garden.css" }}
  {{ if $gardenCSS }}
    {{ $gardenCSS = $gardenCSS | minify }}
    <link rel="stylesheet" href="{{ $gardenCSS.RelPermalink }}">
  {{ end }}
{{ end }}
{{ end }}
```

## Configuration

Add customization options to your `config.toml`:

```toml
[params.garden]
  # Section settings
  sectionTitle = "🌱 My Digital Garden"
  showLastTended = true
  showPlantedDate = true
  enableDataviewStyler = true

  # Callout customization
  calloutText = "This is an entry in my digital garden."
  calloutLinkText = "See what else is growing here."

  # Growth stages (customize order, names, and number of stages)
  growthStages = ["seed", "sprout", "rhizome"]

  # Colors for each growth stage (RGBA format)
  [params.garden.colors]
    seed = "rgba(145, 219, 105, 1)"
    sprout = "rgba(72, 187, 120, 1)"
    rhizome = "rgba(47, 133, 90, 1)"

  # Emojis for each growth stage
  [params.garden.emojis]
    seed = "🌱"
    sprout = "🌿"
    rhizome = "🫚"

  # Labels for each growth stage
  [params.garden.labels]
    seed = "seed"
    sprout = "sprout"
    rhizome = "rhizome"
```

### Configuration Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `sectionTitle` | string | "🌱 Digital Garden" | Title for the garden index page |
| `showLastTended` | bool | true | Show "last tended" dates |
| `showPlantedDate` | bool | true | Show "planted" dates |
| `enableDataviewStyler` | bool | true | Enable Dataview-style metadata styling |
| `calloutText` | string | "This is an entry in my digital garden." | Text for the garden callout |
| `calloutLinkText` | string | "See what else is growing here." | Link text in callout |
| `growthStages` | array | ["seed", "sprout", "rhizome"] | List of growth stages |
| `colors` | map | See above | Colors for each growth stage |
| `emojis` | map | See above | Emojis for each growth stage |
| `labels` | map | See above | Labels for each growth stage |

## Front Matter Reference

Garden entries support the following front matter:

```yaml
---
title: "Your Entry Title"           # Required
type: garden                         # Required - marks as garden content
date: 2024-01-15                    # Required - planting date
created: 2024-01-15 Mon 10:30am     # Optional - detailed creation timestamp
updated: 2024-01-15 Mon 10:30am     # Optional - last update timestamp
state: seed                          # Required - growth stage
tags: ["learning", "meta"]          # Optional - topical tags
share: true                          # Optional - visibility flag
---
```

### Required Fields

- **title**: Entry title
- **type**: Must be "garden"
- **date**: Planting date (Hugo date format)
- **state**: Growth stage (must match one in your config)

### Optional Fields

- **created**: Detailed creation timestamp (format: "YYYY-MM-DD Dow H:MMam/pm")
- **updated**: Last update timestamp (same format as created)
- **tags**: List of tags for topical organization
- **share**: Boolean flag (useful for filtering)

## Customization

### Override Layouts

Create these files in your site to override defaults:

- `layouts/garden/list.html` - Garden index page
- `layouts/partials/garden-state-indicator.html` - State indicator badge
- `layouts/partials/garden-callout.html` - Bottom callout box

### Override Styles

Create `assets/css/garden-custom.css` and import it after the default styles:

```html
{{ $gardenCSS := resources.Get "css/garden.css" }}
{{ $customCSS := resources.Get "css/garden-custom.css" }}
{{ if $gardenCSS }}
  <link rel="stylesheet" href="{{ $gardenCSS.RelPermalink }}">
{{ end }}
{{ if $customCSS }}
  <link rel="stylesheet" href="{{ $customCSS.RelPermalink }}">
{{ end }}
```

### Custom Growth Stages

Want different stages? Add your own:

```toml
[params.garden]
  growthStages = ["idea", "draft", "published", "evergreen"]

  [params.garden.colors]
    idea = "rgba(255, 200, 100, 1)"
    draft = "rgba(255, 150, 50, 1)"
    published = "rgba(100, 200, 255, 1)"
    evergreen = "rgba(50, 150, 100, 1)"

  [params.garden.emojis]
    idea = "💡"
    draft = "✏️"
    published = "📚"
    evergreen = "🌲"

  [params.garden.labels]
    idea = "idea"
    draft = "draft"
    published = "published"
    evergreen = "evergreen"
```

## Advanced Features

### Dataview-Style Metadata

Add structured metadata to your entries:

```markdown
---
title: "My Entry"
---

Main content here...

## Metadata

- [category::learning]
- [confidence::high]
- [related::other-post]
```

With `enableDataviewStyler: true`, these will be styled automatically.

### Custom CSS Variables

The module uses CSS variables for theming. Override them in your custom CSS:

```css
:root {
  --garden-color-seed: rgba(255, 100, 100, 1);
  --garden-color-sprout: rgba(255, 150, 100, 1);
  --garden-color-rhizome: rgba(255, 200, 100, 1);
}
```

## Updating the Module

Keep your garden module up to date:

```bash
hugo mod get -u github.com/mbbroberg/hugo-garden-module
```

Or update all modules:

```bash
hugo mod get -u
```

## Philosophy

Digital gardens embrace:

- **Imperfection** - Seeds are welcome
- **Growth** - Ideas evolve over time
- **Connection** - Links matter more than hierarchy
- **Process** - Learning in public
- **Stewardship** - Tending over time

This module provides the tools; you provide the care and cultivation.

## Example Sites

See the `exampleSite/` directory for a complete working example.

Run the example:

```bash
cd exampleSite
hugo server
```

> **Note**: The example site is pre-configured with a `go.mod` that uses a `replace` directive to test the local module. This allows you to test changes without publishing the module first.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License - see LICENSE file for details.

## Credits

Created by [Matt Broberg](https://github.com/mbbroberg)

Inspired by the digital gardening community and the philosophy of learning in public.

## Support

- 🐛 [Report bugs](https://github.com/mbbroberg/hugo-garden-module/issues)
- 💡 [Request features](https://github.com/mbbroberg/hugo-garden-module/issues)
- 📖 [Read the docs](https://github.com/mbbroberg/hugo-garden-module)
- 🌱 [Share your garden](https://github.com/mbbroberg/hugo-garden-module/discussions)

---

Happy gardening! 🌱
