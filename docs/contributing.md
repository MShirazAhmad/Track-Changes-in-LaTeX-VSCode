# Contributing

Contributions, bug reports, and feature requests are welcome!

## Getting Started

```bash
git clone https://github.com/MShirazAhmad/latex-diff-from-git-timeline.git
cd latex-diff-from-git-timeline
npm install
npm run compile
code .
```

## Testing Locally

1. Open the extension folder in VS Code.
2. Press `F5` to launch the **Extension Development Host**.
3. Open a LaTeX project with a Git history in the new window.
4. Right-click a `.tex` file to test the command.

## Build & Package

```bash
npm run compile
npx vsce package
# Creates: latex-diff-from-timeline-1.0.0.vsix
```

## Code Structure

| File | Purpose |
|---|---|
| `src/extension.ts` | Main command handler |
| `package.json` | VS Code manifest, commands, and menus |
| `tsconfig.json` | TypeScript configuration |

## Extending the Extension

To add features (e.g., custom diff options, inline previews):

1. Edit `src/extension.ts`.
2. Update `package.json` commands/menus if needed.
3. Run `npm run compile`.
4. Test with `F5` launch.
5. Commit and push.

## Useful Commands

Reinstall an updated build:

```bash
code --uninstall-extension mshirazahmad.latex-diff-from-timeline
code --install-extension /path/to/latex-diff-from-timeline-1.0.0.vsix
```

Package a new VSIX from the extension folder:

```bash
npm run compile
npx vsce package
```

## Submitting Issues

Found a bug or have a feature request? Open an issue on [GitHub](https://github.com/MShirazAhmad/latex-diff-from-git-timeline/issues) with:

- VS Code version
- Extension version
- Operating system
- Steps to reproduce
- Expected vs. actual behaviour
