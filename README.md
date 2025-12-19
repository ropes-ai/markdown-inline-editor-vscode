# Markdown Inline Editor

A WYSIWYG-style VS Code extension that hides Markdown syntax and displays formatted content inline as you type. Write Markdown with the ease of a rich text editor while maintaining 100% standard Markdown files.

![Extension Icon](images/icon.png)

## ✨ Features

### Hide Syntax Markers
- **Bold** and *italic* text without visible `**` or `*` markers
- ~~Strikethrough~~ without `~~`
- `Inline code` without backticks
- Links appear styled with URLs hidden
- Images show alt text styled, URLs hidden
- Headings with automatic sizing (H1-H6)

### Rich Formatting
- **Lists**: Unordered lists with bullet points (•) instead of `-`, `*`, `+`
- **Blockquotes**: Vertical bars (│) instead of `>`
- **Horizontal Rules**: Full-width lines instead of `---`
- **Code Blocks**: Syntax highlighted with fenced markers hidden
- **Nested Formatting**: Support for ***bold italic*** and nested blockquotes

### Smart Editing
- **Toggle on/off**: Click the eye icon in the editor toolbar to show/hide formatting
- **Selection reveals syntax**: Click or select text to see the raw Markdown
- **Clickable links**: Internal document links are clickable
- **Real-time updates**: Formatting updates as you type with intelligent caching
- **Pure Markdown**: Your files remain standard `.md` format

## 📦 Installation

### From VS Code Marketplace
1. Open VS Code
2. Press `Ctrl+P` / `Cmd+P`
3. Type `ext install CodeSmith.markdown-inline-editor-vscode`
4. Press Enter

### From Source
```bash
git clone https://github.com/SeardnaSchmid/markdown-inline-editor-vscode.git
cd markdown-inline-editor-vscode
npm install
npm run build
```

Then install the `.vsix` file from the `dist/` folder.

## 🚀 Usage

1. **Open any Markdown file** (`.md`, `.markdown`, `.mdx`)
2. **Start typing** - formatting is applied automatically
3. **Toggle decorations** - Click the eye icon (👁️) in the editor toolbar
4. **Edit normally** - Select text to see/edit the raw Markdown syntax

### Supported Markdown Elements

| Element | Syntax | Displayed As |
|---------|--------|--------------|
| **Bold** | `**text**` or `__text__` | **text** |
| *Italic* | `*text*` or `_text_` | *text* |
| ***Bold Italic*** | `***text***` | ***text*** |
| ~~Strikethrough~~ | `~~text~~` | ~~text~~ |
| `Inline Code` | `` `code` `` | `code` |
| Headings | `# H1` to `###### H6` | Sized & styled |
| [Links](#) | `[text](url)` | Styled link (URL hidden) |
| ![Images](url) | `![alt](url)` | Styled alt text |
| Lists | `- item` or `* item` | • item |
| Blockquotes | `> quote` | │ quote |
| Horizontal Rule | `---` or `***` | ────────── |
| Code Blocks | ` ```lang ` | Background highlighted |

## ⚙️ Configuration

Currently, the extension works out-of-the-box with no configuration needed. Styling adapts to your VS Code theme automatically.

## 🛠️ Development

### Prerequisites
- Node.js 20+
- VS Code 1.88.0+

### Setup
```bash
npm install          # Install dependencies
npm run compile      # Compile TypeScript
npm test             # Run tests (123 tests)
npm run package      # Build .vsix extension
```

### Project Structure
```
src/
├── extension.ts        # Extension entry point
├── parser.ts           # Markdown AST parser (using remark)
├── decorator.ts        # Decoration application & caching
├── decorations.ts      # VS Code decoration type definitions
├── link-provider.ts    # Clickable link support
└── parser/__tests__/   # Comprehensive test suite
```

### Architecture
- **Parser**: Uses `remark` to parse Markdown into an AST
- **Decorator**: Applies VS Code text decorations based on parsed ranges
- **Caching**: LRU cache for parsed decorations (max 10 documents)
- **Selection handling**: Real-time reveal of raw syntax when editing

## 📝 License

MIT License - see [LICENSE.md](LICENSE.md)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### Quick Start
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes using [Conventional Commits](https://www.conventionalcommits.org/)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 🐛 Issues

Found a bug or have a feature request? Please open an issue on [GitHub](https://github.com/SeardnaSchmid/markdown-inline-editor-vscode/issues).

## 🙏 Acknowledgments

Built with:
- [remark](https://github.com/remarkjs/remark) - Markdown parser
- [unified](https://github.com/unifiedjs/unified) - Content processing ecosystem
- [VS Code Extension API](https://code.visualstudio.com/api)

---

**Note**: This extension styles your Markdown while editing. Your files remain standard Markdown and are fully compatible with all Markdown tools, renderers, and AI assistants.
