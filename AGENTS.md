# 仓库工作流说明

## 截图刷新

- 在仓库根目录运行 `../.tools/render_compendium_screenshots.py`，可一次生成 4 张本地截图。
- 默认输入为仓库根目录中的 4 个 HTML 文件：
  - `ChatGPT_Web_Plan_and_Model_Limits_en.html`
  - `ChatGPT_Model_Juice_Reference_en.html`
  - `ChatGPT网页版各套餐各模型限额.html`
  - `ChatGPT模型Juice值图鉴.html`
- 默认输出到 `screenshots/`，文件名依次为：
  - `usage-en.png`
  - `juice-en.png`
  - `usage-zh.png`
  - `juice-zh.png`
- 安全 dry run：`../.tools/render_compendium_screenshots.py --outdir /tmp/compendium-shots`
- 局部刷新示例：`../.tools/render_compendium_screenshots.py --only usage-en juice-en`
- 该脚本使用本地 Google Chrome 或 Chromium 配合 Playwright，截取 full-page screenshot，并将 PNG 统一规范到 `1352px` 宽。

## 仓库上传规则

- 允许提交的内容只有：
  - `README.md`
  - `AGENTS.md`
  - `screenshots/` 下的图片文件（`png`、`jpg`、`jpeg`、`webp`、`gif`）
- 严格禁止进入仓库的内容：
  - 所有 `.html` / `.htm` 文件（含大小写变体）
  - 其他非图片、非 `README.md`、非 `AGENTS.md` 的文件
- 如果在 `README.md` 中引用图片，默认使用 `screenshots/` 目录下的资源。

## 自检要求

- `git status --short --ignored | rg '\.html|\.htm'` 应显示 HTML 文件为 `!!`（已忽略）。
- `git status --short` 不应出现任何 `.html` / `.htm` 变更项。
- 如需检查某个具体 HTML 文件是否被忽略，可执行 `git check-ignore -v -- <文件名>.html`。
- 刷新截图后，确认 `screenshots/` 中只有预期图片变更，再进行提交。

## 协作要求

- 每次内容修改后执行 `git add` 和 `git commit`，保留本地提交记录。
- 本仓库不执行 `git push`；提交仅保留在本地。
