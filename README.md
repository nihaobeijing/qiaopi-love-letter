# 💌 侨批情书 — 《给阿嬷的情书》文风技能

> 质朴粗粝、烟火气浓、隐忍克制。一句话进去，一封侨批出来。

## 这是什么

一个 Hermes Agent / Claude Code 的 Skill，模仿电影《给阿嬷的情书》原生南洋侨批文风，把现代口语转化为民国潮汕百姓手写家书。

```
输入：我马上回来

输出：
吾爱，展信安康。
手头诸事已然了结。
即刻踏路而行。
路上顺路买了你爱吃的。
片刻便到，勿念。
```

## 特色

- **极短散句，一句一行**，还原手写侨批排版
- **藏情于烟火日常**，绝不直白说"想你爱你"
- **10条失败模式检查**，防文艺腔/成语堆砌/过度许诺
- **4个检查点**，输出前逐项校验
- **7条反例黑名单**，明确"不要做什么"
- **28组词汇替换库**，现代口语→侨批用语
- **小事推导规则**，7种场景自动匹配感官细节

## 安装

### Hermes Agent

```bash
git clone https://github.com/nihaobeijing/qiaopi-love-letter.git \
  ~/.hermes/skills/creative/qiaopi-love-letter
```

### Claude Code

```bash
git clone https://github.com/nihaobeijing/qiaopi-love-letter.git \
  ~/.claude/skills/qiaopi-love-letter
```

## 使用

直接告诉 AI 你想说的话，它会输出侨批：

| 输入 | 输出 |
|------|------|
| 下班了，在回家路上 | 吾爱，展信安康。俗事已毕。已在归途。片刻便到，勿念。 |
| 加班，晚点回 | 吾爱，展信安康。诸事缠身。归期稍缓。你不必等我，先歇息。忙完便回，勿念。 |
| 晚安 | 吾爱，展信安康。夜深了。灶火已熄，家中安稳。你早些歇息。勿念。 |
| 想你了 | 吾爱，展信安康。夜深了，船靠岸歇息。岸上人家在煮粥，烟火气飘过来。想起你也爱喝那口。勿念。 |

## 称谓匹配

| 关系 | 开头 |
|------|------|
| 伴侣/恋人 | 吾爱，展信安康。 |
| 平辈/同事/友人 | 吾兄，展信安康。 |
| 家人/长辈 | 吾亲，展信安康。 |
| 普通往来 | 见字如晤，展信安康。 |

## 进化记录

本 skill 使用 **darwin-skill + skill-evolver** 自进化系统优化，三轮迭代：

| 轮次 | 分数 | 主要改动 |
|------|------|---------|
| 基线 | 72.8 | 初始版本 |
| Round 1 | 89.1 | +失败模式(10条) +检查点(4个) +反例(7条) +词汇库翻倍 |
| Round 2 | 88.7 | +端到端流水线 +小事推导规则 +修复文艺腔 |
| Round 3 | 88.7 | 编号修复，棘轮锁定 |

## 文件结构

```
qiaopi-love-letter/
├── SKILL.md                        # 主文件
├── README.md                       # 本文件
└── references/
    ├── full-20-letters.md          # 电影20封侨批原文
    ├── original-20-letters.md      # 原始版本
    └── iteration-lessons.md        # 迭代踩坑教训
```

## 设计灵感

- 电影《给阿嬷的情书》— 木生与淑柔的跨洋家书
- Karpathy autoresearch — 自主实验循环
- SkillLens (arXiv 2605.23899) — 9维评估体系
- SkillEvolver — 角色分离，闭环进化

## 许可

MIT License

---

*Train your Skills like you train your models.* 🧬
