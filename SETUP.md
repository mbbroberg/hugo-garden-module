# Publishing Your Hugo Garden Module

This guide walks you through publishing this module to GitHub so others can use it.

## Step 1: Create GitHub Repository

1. Go to https://github.com/new
2. Repository name: `hugo-garden-module`
3. Description: "A Hugo module for creating and maintaining a digital garden"
4. Choose: Public
5. Don't initialize with README (we already have one)
6. Click "Create repository"

## Step 2: Initialize Git and Push

From the `hugo-garden-module` directory:

```bash
# Initialize git repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: Hugo Garden Module v1.0.0"

# Add remote (replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/hugo-garden-module.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## Step 3: Create a Release

1. Go to your repository on GitHub
2. Click "Releases" → "Create a new release"
3. Tag version: `v1.0.0`
4. Release title: `v1.0.0 - Initial Release`
5. Description:
   ```
   🌱 Initial release of Hugo Garden Module

   Features:
   - Complete digital garden implementation
   - Three growth stages (seed, sprout, rhizome)
   - Fully customizable colors, emojis, and labels
   - Responsive design
   - Tag-based browsing
   - Dataview-style metadata support
   - Example site included
   ```
6. Click "Publish release"

## Step 4: Test the Module

Create a test Hugo site to verify the module works:

```bash
# Create test site
mkdir test-garden-site
cd test-garden-site
hugo new site . --force

# Initialize as module
hugo mod init github.com/YOUR_USERNAME/test-garden-site

# Add the module to config.toml
cat >> hugo.toml << EOF

[module]
  [[module.imports]]
    path = "github.com/YOUR_USERNAME/hugo-garden-module"

[taxonomies]
  tag = "tags"
  state = "state"

[params.garden]
  sectionTitle = "🌱 My Garden"
EOF

# Get the module
hugo mod get -u

# Create garden index
hugo new content/garden/_index.md
# Edit this file and add layout: garden to front matter

# Create a test post
hugo new content/garden/first-seed.md --kind garden

# Test it
hugo server
```

## Step 5: Update Your Own Blog to Use It

In your mbbroberg.github.io repository:

1. Update `config.toml`:
```toml
[module]
  [[module.imports]]
    path = "github.com/mbbroberg/hugo-garden-module"
```

2. Get the module:
```bash
hugo mod get -u
```

3. Remove the old garden files (now provided by the module):
```bash
# Keep these - they're your content
# - content/garden/

# You can optionally remove these (module provides them now)
# - layouts/garden/list.html (if you want to use the module version)
# - assets/css/garden.css (module version)
# - assets/js/dataview-styler.js (module version)
```

4. Update your `layouts/_default/single.html` to use the partials:
```html
{{ if eq .Type "garden" }}
  {{ partial "garden-state-indicator.html" . }}
{{ end }}

<!-- content here -->

{{ if eq .Type "garden" }}
  {{ partial "garden-callout.html" . }}
{{ end }}
```

## Step 6: Promote Your Module

1. **Add topics to GitHub repo**:
   - Go to repository settings
   - Add topics: `hugo`, `hugo-module`, `digital-garden`, `hugo-theme`

2. **Share it**:
   - Hugo Discourse forum: https://discourse.gohugo.io/
   - Hugo themes showcase: https://themes.gohugo.io/
   - Digital gardening community
   - Your own blog post about creating it!

3. **Add to Hugo modules list**:
   - Submit to https://github.com/gohugoio/hugoThemesSiteBuilder

## Maintenance

### Updating the Module

When you make changes:

```bash
git add .
git commit -m "Description of changes"
git push

# Create a new release on GitHub
# Bump version: v1.0.1, v1.1.0, etc.
```

Users update with:
```bash
hugo mod get -u github.com/YOUR_USERNAME/hugo-garden-module
```

### Version Numbers

Follow semantic versioning:
- `v1.0.0` → `v1.0.1`: Bug fixes
- `v1.0.0` → `v1.1.0`: New features (backward compatible)
- `v1.0.0` → `v2.0.0`: Breaking changes

## Next Steps

Consider adding:
- [ ] GitHub Actions for CI/CD
- [ ] Automated testing
- [ ] More example sites
- [ ] Additional growth stage presets
- [ ] Graph visualization of connections
- [ ] Search functionality
- [ ] RSS feed for garden entries

---

Happy gardening! 🌱🌿🫚
