# ModuleWebUI Page Module Management System

A modern Android Root universal module management web interface built with Vite, providing a modular page management system.

[中文版本](./README.md)

## Quick Start

### Prerequisites & Installation

Prerequisites:
- Node.js (LTS recommended: >= 18; CI supports Node 16, 18, and 20; some checks use Node 22)
- npm

Installation and Running:

```bash
# Clone the project
git clone https://github.com/MemDeco-WG/ModuleWebUI.git
cd ModuleWebUI

# Install dependencies
npm ci  # recommended in CI
# OR for local dev:
npm install

# Start dev server
npm run dev

# Build production artifact
npm run build:prod
# Or via helper script (replaces ModuleWebUI with <MODID>):
./build.sh <MODID>
```

Notes:
- `build.sh` expects a module ID (MODID) and replaces occurrences of `ModuleWebUI` in `src` and `index.html` with the given ID, then builds the production artifact into `dist/`.
- If using macOS `sed`, you may need to modify `build.sh` (or use `find … -exec sed -i '' "…"`) due to differences in `-i` flags.
- GitHub Actions automatic build uses the repository name as the module name by default; adjust CI if you want a custom module ID.

## More Documentation

- [User Documentation](./user-en.md)
- [Page Module Development Guide](./page-module-development.en.md)
- [Plugin Development Guide](./plugin-development.en.md)

## Dependency Updates

To keep the project secure and stable, dependencies are updated regularly. Recent (safe) updates include:
- `esbuild`: ^0.25.12
- `fdir`: ^6.5.0
- `glob`: ^11.1.0
- `rollup`: ^4.53.3
- `tinyglobby`: ^0.2.15

How to update dependencies:
- For non-breaking updates within semver range:  
  ```bash
  npm update
  ```
- For upgrading to latest versions (including major):  
  ```bash
  npx npm-check-updates -u
  npm install
  ```  
  Note: major-version upgrades may introduce breaking changes — test carefully.
- Check for vulnerabilities:
  ```bash
  npm audit
  npm audit fix
  ```

Always run a full build and CI checks after updating dependencies to verify compatibility (CI covers Node 16/18/20 in the workflow).

## Detailed Feature Introduction

### Core Features
- Supports KernelSU webui.
- Supports executing shell commands.

### Page Module System
- Each page is an independent module
- Complete module lifecycle hooks
- Supports custom page creation
- Pages can add interactions, listen to events, modify pages, etc.

### Plugin System
- Supports custom plugin development
- Plugins can add buttons, listen to events, modify pages, etc.

### Internationalization System
- Supports multi-language switching
- Plugins can add new language packs

## License

This project is licensed under the MIT License - see the [LICENSE](../LICENSE) file for details.