# Markdown Inline Editor

WYSIWYG-style Markdown editing for VS Code using native editor decorations.

The extension renders Markdown formatting inline while keeping your source file as standard Markdown.

## Features

- Inline rendering for headings, emphasis, links, images, lists, code, and more
- Context-aware syntax visibility (rendered/raw depending on cursor and selection)
- Clickable links and image links
- Mermaid fenced block rendering support
- Diff-safe defaults for review workflows

## Building & Deployment

### Build Locally

```bash
npm run build
```

This creates a VSIX package at `dist/extension.vsix` containing:
- Compiled TypeScript
- Bundled dependencies
- Mermaid assets

### Deploy to Staging Server

1. **Transfer the VSIX file:**
   ```bash
   scp dist/extension.vsix coder-staging:/tmp/markdown-inline-editor.vsix
   ```

2. **On coder-staging, move to startup directory:**
   ```bash
   sudo chown root:root /tmp/markdown-inline-editor.vsix
   sudo mv /tmp/markdown-inline-editor.vsix /startup_files/
   ```

The extension will be installed from `/startup_files/markdown-inline-editor.vsix` on the staging server.

## License

MIT. See `LICENSE.txt`.

This project includes prior MIT-licensed work and attribution retained in `LICENSE.txt` (including `markdown-inline-preview-vscode` attribution).
