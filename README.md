# debug-architect — 调试建筑师

项目完成后扫描报错、分析根因、归档教训、生成预防规则、检测技能漏洞。

## 为什么需要

- 项目做到最后，各种报错散落在对话历史里，没人总结
- 同一个坑反复踩，因为没归档、没规则、没预警
- skill 有漏洞但没人发现——直到下一次报错

debug-architect 在项目完成后一次性扫描所有报错，把碎片变成预防体系。

## 功能

1. **扫描提取** — 从 sessions 自动搜索所有报错信号
2. **分类归类** — 语法/配置/逻辑/环境/第三方/其他
3. **根因分析** — 三层：直接原因→深层原因→预防缺口
4. **关联分析** — 因果链、同根多面、跨项目共鸣
5. **归档写入** — 按记忆 skill 融入规则写入 dev-lessons
6. **预防建议** — ≥2次同类→CLAUDE.md 规则 / ≥3次→全局规则
7. **技能漏洞** — 检测规则缺失、边界遗漏、检查缺失

## 触发

```
命令：/error-review
关键词："复盘错误"、"错误复盘"、"分析报错"、"回顾错误"、"总结错误"
```

项目完成后手动调用。

## 安装

```powershell
git clone https://github.com/2021291696/debug-architect.git
Copy-Item -Recurse debug-architect/ "$env:USERPROFILE\.claude\skills\debug-architect"
```

## 文件结构

```
debug-architect/
├── SKILL.md                     — 主指令（168行，八步流程）
├── README.md                    — 本文件
└── references/
    ├── error-patterns.md        — 常见错误模式速查
    └── skill-audit-guide.md     — 技能漏洞检测指南
```

## 与体系内其他 skill 的关系

| | debug-architect | weaver-自我迭代 | memory-keeper | file-tidy |
|------|-----------------|-----------------|---------------|----------|
| 时机 | 项目完成后 | 定期 | 实时"记住"指令 | 手动/定期 |
| 对象 | 错误报告 | 所有对话 | 单条信息 | 文件系统 |
| 产出 | 归档+预防规则+技能改进 | 知识网络+经验+自迭代 | 融入记忆 | 文件归类+清理 |
