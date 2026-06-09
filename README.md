<!-- BADGE BAR -->
[![License](https://img.shields.io/badge/license-MIT-blue)](./LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-orange)](https://claude.ai)

# debug-architect

> **调试建筑师。** 项目完成后扫描报错、分析根因、归档教训、生成预防规则、检测技能漏洞。把散落的错误碎片变成系统的免疫记忆。

[English](#english)

---

## 为什么需要 debug-architect？

- **项目做完了，各种报错散落在对话历史里，没人总结。** 下次开新项目还是踩同样的坑。
- **同一个坑反复踩，因为没归档、没规则、没预警。** 人有遗忘曲线，Agent 也有——除非我们帮它记住。
- **Skill 有漏洞但没人发现。** 直到下一次报错才知道"原来那个 Skill 少了一步校验"。

## 核心能力

- 🔍 **扫描提取** — 从会话历史自动搜索所有报错信号
- 📊 **分类归类** — 六类：语法/配置/逻辑/环境/第三方/其他
- 🎯 **三层根因分析** — 直接原因 → 深层原因 → 预防缺口
- 🔗 **关联分析** — 因果链、同根多面、跨项目共鸣
- 📈 **置信度分级** — 四象限（诊断把握 × 长期复利）分级，不同等级不同处理策略
- 📝 **归档写入** — 按等级写入项目 ERROR_LOG + memory + wiki
- 🛡️ **预防建议** — 按置信度等级决定是否写入 CLAUDE.md 规则
- 🔎 **技能漏洞检测** — 检测规则缺失、边界遗漏、检查缺失

## 四级置信度矩阵

```
              高复利                    低复利
         ┌─────────────────┬─────────────────┐
  确定   │  🟢 确定·高价值   │  🟡 确定·低价值   │
         │  沉淀：全量归档    │  仅归档 ERROR_LOG  │
         │  + 预防规则       │                  │
         ├─────────────────┼─────────────────┤
  推测   │  🔵 推测·高价值   │  ⚪ 存疑/一次性    │
         │  待验证 → 升级    │  仅记录，不出规则   │
         └─────────────────┴─────────────────┘
```

**关键洞察：频率不等于重要。** 一个发生 10 次的拼写错误和一个发生 1 次的架构缺陷——后者优先级更高。所以用"诊断把握 × 长期复利"分级，而不是按频率排序。v2 把频率从独立规则制定者降级为置信度评估的输入信号。

## 快速开始

### 触发

| 你说 | 它做什么 |
|------|---------|
| `复盘错误` / `错误复盘` | 扫描当前项目所有会话的报错 |
| `分析报错` / `回顾错误` | 同上 |
| `/error-review` | 同上 |

## 设计哲学

**错误不是 bug，是体系在说话。** 一个报错背后是一条因果链：直接原因 → 为什么会发生 → 为什么体系没拦住。停在直接原因 = 下次还会报。追到预防缺口 = 这类错误永远不再出现。

**频率不是真相。** 10 次同一个拼写错误 ≠ 10 倍重要。1 次架构级缺陷 > 100 次语法错误。v2 用置信度分级取代频率规则，就是基于这个信念。

**归档的终点不是文件，是行为改变。** ERROR_LOG 的价值不在于"记录了"，而在于下一个 Agent 打开项目时，它会先读 ERROR_LOG，然后不再犯同样的错。

## 相关项目

| 项目 | 关系 |
|------|------|
| [skill-optimizer](https://github.com/2021291696/skill-optimizer) | 下游 — 调用我获取硬证据，执行 skill 优化 |
| systematic-debugging | 兄弟 — 实时调试（报错时用）vs 事后复盘（项目完成后用） |

## License

MIT

---

## English

# debug-architect

> **Post-mortem architect for AI projects.** Scans all errors after project completion, traces root causes, grades confidence, archives lessons, and generates prevention rules.

### Why?

Errors scattered across chat history, never summarized. The same pitfalls hit again and again. debug-architect turns fragments into an immune system — every project gets an ERROR_LOG that future agents read first.

### The Four-Quadrant Model

Errors are graded by diagnostic certainty × long-term compounding value, not by frequency. An architectural flaw that happened once matters more than a typo that happened ten times.

### Design Philosophy

**Errors speak about the system, not just the moment.** Every error has a causal chain: direct cause → why it happened → why the system didn't prevent it. Stop at the direct cause = same error tomorrow. Trace to the prevention gap = that class of errors never returns.

**Archiving isn't the goal — behavior change is.** ERROR_LOG only matters if the next agent reads it and acts differently.
