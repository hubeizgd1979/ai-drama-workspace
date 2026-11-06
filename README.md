# AI 短剧生产工作区

把两套 AI 短剧工具链合并到一个仓库，开箱即用。

## 目录结构

| 目录 | 来源 | 作用 |
|---|---|---|
| `jellyfish/` | [Forget-C/Jellyfish](https://github.com/Forget-C/Jellyfish) | 端到端生产工作区：剧本输入 → 结构化分镜 → 一致性管理 → 镜头准备 → 视频生成 → 导出。Python 后端 + React 前端 + 站点 |
| `shuohao-skills/` | [eternityspring/shuohao-skills](https://github.com/eternityspring/shuohao-skills) | Agent Skills 集合：拆角色、排大纲、出场景与道具设定、写剧本、切分镜。可在 Claude Code / Codex 中运行 |

## 怎么用

### Jellyfish（生产流水线）
```
cd jellyfish
# 后端
cd backend && pip install -r requirements.txt   # 或 uv sync
# 前端
cd ../front && pnpm install && pnpm dev
```
详细部署见 `jellyfish/README.md` 与 `jellyfish/deploy/`。

### shuohao-skills（创作 Skill）
```
cd shuohao-skills
cat README.zh.md          # 中文说明
bash scripts/install.sh   # 安装到 Claude Code / Codex
```

## 两条链怎么配合

1. 用 `shuohao-skills` 做前期创作：角色圣经 → 改编大纲 → 美术设定 → 剧本 → 分镜。
2. 把产出的剧本/分镜喂给 `jellyfish`，进入镜头准备、一致性管理与视频生成、导出。

## 同步说明

两个子目录是上游仓库的完整快照。上游更新后可用各自仓库的 `Sync upstream` 工作流拉取，再把变更同步到本工作区。
