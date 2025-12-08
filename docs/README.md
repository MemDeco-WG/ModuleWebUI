# ModuleWebUI 页面模块管理系统

一个现代化的安卓Root通用模块管理Web界面，基于Vite构建，提供模块化的页面管理系统。

[English Version](./README.en.md)

## 快速开始

### 安装与运行

先决条件：
- Node.js >= 16（推荐 LTS：18 或 22）
- npm >= 8
- Bash / POSIX shell（用于执行 `build.sh`；在 Windows 上建议使用 WSL 或 Git Bash）

```bash
# 克隆项目
git clone https://github.com/MemDeco-WG/ModuleWebUI.git
cd ModuleWebUI

# 安装依赖（在 CI 中推荐使用：npm ci）
npm ci
# 或在本地开发时使用：
# npm install

# 启动开发服务器
npm run dev

# 生成生产构建（输出到 dist/）
./build.sh <MODID>
# 或直接使用 Vite 生产构建
npm run build:prod
```

说明：
- `build.sh` 会把 `src` 与 `index.html` 中的 `ModuleWebUI` 字符串替换为你提供的模块 ID（`MODID`），然后执行生产构建，输出到 `dist/`。
- 若在 macOS 使用 `sed -i` 出现兼容性问题，请使用 macOS 格式：  
  `find src -name "*.js" -exec sed -i '' "s/ModuleWebUI/${MODID}/g" {} \\;`  
  `sed -i '' "s/ModuleWebUI/${MODID}/g" index.html`
- GitHub Actions 自动构建默认使用仓库名称作为模块名称；你可修改 CI 配置以使用自定义的模块 ID。


## 更多文档

- [用户文档](./user.md)
- [页面模块开发指南](./page-module-development.md)
- [插件开发指南](./plugin-development.md)

## 依赖更新

为保持安全性与稳定性，本项目近期对部分依赖进行了小幅升级（以非破坏性的小/补丁版本为主）。以下为主要更新（示例）：
- `esbuild`: ^0.25.12
- `fdir`: ^6.5.0
- `glob`: ^11.1.0
- `rollup`: ^4.53.3
- `tinyglobby`: ^0.2.15

升级建议：
- 使用 `npm update` 执行安全范围内的升级（只会升级包到符合 `package.json` 的 semver 范围内）。
- 若需升级到大版本（major），请使用 `npx npm-check-updates -u` 并手动验证兼容性与行为变化。
- 在升级后执行构建与测试以确保不会出现回归或断裂行为。
- 使用 `npm audit` 与 `npm audit fix` 检查并修复安全问题。

## 详细功能介绍

### 核心功能
- 支持KernelSU的webui。
- 支持执行shell命令。

### 页面模块系统
- 每个页面都是独立的模块
- 完整的模块生命周期钩子
- 支持自定义页面创建
- 页面可以添加交互、监听事件、修改页面等

### 插件系统
- 支持自定义插件开发
- 插件可以添加按钮、监听事件、修改页面等

### 国际化系统
- 支持多语言切换
- 插件可以添加新的语言包

## 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](../LICENSE) 文件了解详情。