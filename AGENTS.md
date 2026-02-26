# 仓库上传规则

本仓库只允许推送以下内容：
- `README.md`
- `screenshots/` 下的图片文件
- `AGENTS.md`（本说明文件）

严格禁止以下内容进入仓库：
- 所有 `.html` / `.htm` 文件（含大小写变体）
- 其他非图片、非 `README.md` 的文件

执行前建议自检：
- `git check-ignore -v *.html *.htm` 应显示被忽略
- `git status` 不应出现任何 `.html` / `.htm` 变更项

如果在 `README.md` 中需要引用图片，默认使用 `screenshots/` 目录下资源。

协作要求（当前会话约束）：
- 每次内容修改后必须执行 `git add` 和 `git commit`，并保留提交记录。
- 本仓库设置为禁止推送到 GitHub（提交本地保留）；不执行 `git push`。
