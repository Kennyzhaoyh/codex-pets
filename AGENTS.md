# Codex 宠物安装指南

_供能访问网络和目标电脑文件系统的 AI agent 使用。_

---

## 📋 选择宠物

按用户明确选择的 ID 安装 `dogking`、`lyman`、`piggy` 或 `yuki`。用户要求「全部」时才安装四只。若用户没有指明要安装哪只，先列出这四个选项。阅读本文件本身不授权安装。

## 📦 下载并检查

1. 从 [GitHub 仓库](https://github.com/Kennyzhaoyh/codex-pets) 获取 `main` 的同一个提交。可以浅克隆，也可以用下列模板只下载两个文件。将 `<commit>` 替换为 `main` 当前的提交 SHA，`<id>` 替换为选中的 ID。把文件放在临时目录，下载失败时停止。

   ```text
   https://raw.githubusercontent.com/Kennyzhaoyh/codex-pets/<commit>/pets/<id>/pet.json
   https://raw.githubusercontent.com/Kennyzhaoyh/codex-pets/<commit>/pets/<id>/spritesheet.webp
   ```

2. 解析 `pet.json`，确认 `id` 与所选 ID 一致、`displayName` 非空、`spriteVersionNumber` 为数字 `2`、`spritesheetPath` 为 `spritesheet.webp`。确认图集是有效的 `1536 × 2288` WebP，并用现有图像工具检查透明通道。缺少检查工具时说明限制，先不要写入安装目录。

## 🔧 导入到这台电脑

1. 在运行 Codex 桌面应用的电脑上操作。确认应用使用的 `CODEX_HOME`，默认是当前用户主目录下的 `.codex`。如果应用使用的目录不能确定，先询问用户。目标是 `<CODEX_HOME>/pets/<id>/`。
2. 如果目标或其安装路径是符号链接，停止并说明。目标不存在时，只创建所选宠物的目录，放入 `pet.json` 和 `spritesheet.webp`。目标已存在且两个文件完全一致时跳过；有差异时保留现有文件，取得用户同意并完成可恢复的备份后再替换。只处理用户指定的宠物目录和必要的临时下载目录。

## ✅ 验证安装

重新读取目标目录中的两个文件，逐字节比较或比较 SHA-256，确认它们与下载件一致。报告每只宠物的 ID、安装路径、跳过项和冲突项。请用户在 Codex 桌面应用的宠物设置中刷新并选择宠物。如果列表没有更新，提示用户自行重启应用。仅在实际检查界面后报告宠物已在列表显示。
