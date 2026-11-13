# 认知格栅（Cognition Lattice）

静态中文认知知识库，灵感来自查理·芒格的「多元思维模型格栅」：**9 个维度、77 个分类、1975 条条目**，全部正文位于 `references/`。只提供概念定义、机制、应用场景与关联概念，不联网、不修改业务代码。

## 快速开始

检索脚本只依赖 Python 3 标准库，在仓库根目录执行：

```bash
python3 scripts/lattice.py search 损失厌恶 --limit 10   # 查术语（中英文、别名）
python3 scripts/lattice.py search 系统 反馈 --full       # 多关键词 AND + 正文检索
python3 scripts/lattice.py show EW-0015                  # 按脚本 ID 读单条正文
python3 scripts/lattice.py search 锚定 --file cognitive_biases.md --show  # 限维度直读
python3 scripts/lattice.py audit                         # 全库审计（条目/分类/数据质量）
python3 scripts/lattice.py index                         # 重新生成 scripts/index.json
```

引用格式：「术语 + `references/文件:行号`」。标题编号是历史遗留、口径不一，**不得作为引用键**，统一用脚本 `ID` 或 `文件:行号`。

## 九个维度

| 维度 | 条目数 | 文件 |
|------|--------|------|
| 认知偏差 | 239 | `references/cognitive_biases.md` |
| 心理效应 | 221 | `references/psychological_effects.md` |
| 思维模型 | 712 | `references/mental_models.md` |
| 思维框架 | 235 | `references/thinking_frameworks.md` |
| 跨学科心智工具 | 64 | `references/interdisciplinary_tools.md` |
| 东方传统智慧（含三十六计体系） | 109 | `references/eastern_wisdom.md` |
| 论证谬误 | 135 | `references/argumentation_fallacies.md` |
| 管理思维 | 135 | `references/management_thinking.md` |
| 成长思维模型 | 125 | `references/growth_thinking.md` |

另附 `references/orchestrator_integration.md`：把知识库映射到任务调度/路由/派工等决策场景的集成示例（含 8 项决策偏差自检清单与执行前守门清单），不是第十个知识维度。

## 作为 Agent Skill 安装

把本仓库放进 agent 的技能目录即可，例如：

```bash
git clone https://github.com/issac-new/cognition-lattice.git ~/.hermes/skills/cognition-lattice
# 或 Claude Code 类通道：clone 到对应 skills 目录
```

入口是 `SKILL.md`（使用流程、维度路由、条目格式与数据质量说明）。分类明细、字段模板、统计口径与版本历史见 `references/catalog.md`。

## 数据质量（如实声明）

- 全库有 188 组同名条目、228 条冗余（约 11.6%），源于多次批次合并；同一概念在不同维度保留不同视角，一次回答只引用最贴合的一个维度。
- `mental_models.md` 有 573 条来源为占位文本、322 条释义与机制重复；`thinking_frameworks.md` 有 180 条模板化批次。这些条目保留不删，但引用时优先选手写批次，不把模板句当证据。
- `python3 scripts/lattice.py audit` 可复核上述全部基线。

## 版本简史

v1.0（2026-05，501 条）→ v2.2（1969 条，九维度齐）→ v2.4（2026-11-02，三十六计体系 +6 条至 1975 条）→ v3.0（2026-11-05，检索式重构）→ v3.1（2026-11-13，恢复曾丢失的三十六计融合）→ v3.2（2026-11-13，恢复重构时误删的执行前守门清单与映射行）。完整历史见 `references/catalog.md` §版本历史。

## License

MIT（见 [LICENSE](LICENSE)）。
