# Practical Copilot Wiki

A wiki for documenting practical, concrete steps for making effective use of Agentic Copilot.

## About

This wiki is built with [TiddlyWiki](https://tiddlywiki.com/) and hosted on GitHub Pages. Content is stored as individual tiddler files in the `wiki/tiddlers` directory, making it easy to version control and collaborate.

## Development

### Prerequisites

- Node.js 20 or later
- npm

### Local Development

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```
3. Build the wiki:
   ```bash
   npm run build
   ```
   This generates `wiki/output/index.html`

4. Run a local server (optional):
   ```bash
   npm run serve
   ```
   Then visit http://localhost:8080

### Adding Content

Create new tiddler files in the `wiki/tiddlers` directory. Tiddlers are text files with a `.tid` extension that follow this format:

```
title: Your Tiddler Title
tags: Tag1 Tag2

Your content goes here in TiddlyWiki markup format.
```

### Deployment

The wiki is automatically deployed to GitHub Pages when changes are pushed to the `main` branch via GitHub Actions.

## License

This work is licensed under the [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
