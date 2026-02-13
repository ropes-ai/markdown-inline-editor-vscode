# markdown-inline-editor-vscode (Internal Fork) README

This is our internal fork of markdown-inline-editor-vscode.

We deploy this extension **internally** to our coder/workspace environments.

We are **not** using external marketplace distribution for this fork.

## Contributing

Want to help out with **markdown-inline-editor-vscode**? Here's how to get rolling:

### 1. What you'll need

- [Node.js](https://nodejs.org/) (v18+)
- npm
- [VS Code](https://code.visualstudio.com/)

### 2. Get set up

```sh
npm ci
```

### 3. Run locally in Extension Host

- Open this project in VS Code
- Press `F5` to launch Extension Development Host
- Open a markdown file (`.md`) in the host window

After code changes, run `Developer: Reload Window` in the Extension Development Host window.

### 4. Build it

Compile:

```sh
npm run compile
```

Build VSIX:

```sh
npm run build
```

Artifact:

- `dist/extension.vsix`

### 5. Validate

```sh
npm run validate
```

### 6. Test it

```sh
npm test
```

### 7. Try it out in VS Code

- Open project in VS Code
- Press `F5`
- In Extension Host, run `Toggle Markdown Decorations`
- Verify behavior in markdown files

### 8. Making changes

- Branch off `main`
- Keep checks green (`npm run validate`)
- Open PR with conventional commit messages

# Deploying (Internal)

Build:

```sh
npm run build
```

This generates:

- `dist/extension.vsix`

## Internal staging flow (example)

1. Copy VSIX to staging host:

```sh
scp dist/extension.vsix coder-staging:/tmp/markdown-inline-editor.vsix
```

2. On staging host, move into startup files location:

```sh
sudo chown root:root /tmp/markdown-inline-editor.vsix
sudo mv /tmp/markdown-inline-editor.vsix /startup_files/
```

3. If your infra/template references a versioned VSIX path, update that reference in the relevant template/config.

## Internal production flow

- Promote the same validated VSIX artifact to production startup files/template.
- Update template/config references if versioned filenames are used.
- Roll forward by replacing VSIX with a new validated build.

1. Copy VSIX to prod host:

```sh
scp dist/extension.vsix coder-prod:/tmp/markdown-inline-editor.vsix
```

2. On prod host, move into startup files location:

```sh
sudo chown root:root /tmp/markdown-inline-editor.vsix
sudo mv /tmp/markdown-inline-editor.vsix /startup_files/
```

## Rollback

- Repoint template/config to previous known-good VSIX, or
- Replace startup-files VSIX with the previous artifact.

---

## License / Compliance

This fork remains MIT licensed.

For internal redistribution, keep:

- `LICENSE.txt`
- Existing attribution notices already included in `LICENSE.txt`

Do not remove upstream attribution from the license file.
