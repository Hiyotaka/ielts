# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 用户画像

- 在职程序员（AI agent 开发 / 恶意样本分析，10:00-19:00）
- 目标：IELTS 总分 6.5（阅读 7.0→7.5，听力 6.0→6.5，写作 5.5→6.0，口语 5.5→6.0）
- 考试日期：2026-05-24
- 申博方向：AI 安全，目标香港或欧洲

## 当前备考状态

**口语**：5 组万能故事覆盖 59 题全部完成。5 篇核心回答在 `口语核心5篇.md`。练法：每天 Gemini Live 模考 1 次，早上朗读 1 篇核心回答。

**写作**：已给 Two-part 题型范文 + PEEL 模板。用户尚未交作文批改。审题 + 6 类语法自查清单已交付。

**阅读**：用户自述 passage 2&3 维持手感中，目标 7.5。

**听力**：用户用语料库听写拔高，目标 6.5。

## 8 天冲刺计划

见 5.16 对话中的 8 天拆解表。核心：80% 精力给阅读听力，口语写作保 6.0。

## 口语素材文件清单

| 文件 | 内容 | 题数 |
|------|------|------|
| `口语素材-地点组-大阪.md` | 大阪之旅 | 10 |
| `口语素材-人物组-室友.md` | CS 室友 Leo | 13 |
| `口语素材-经历组-雅思备考.md` | 在职雅思备考 | 19 |
| `口语素材-物品组-iPad.md` | 买 iPad 7 | 6（2题⚠️待替换） |
| `口语素材-志向组-纪录片.md` | AI 安全研究员 | 13 |
| `口语题库-5组万能覆盖-0515.md` | 分组索引 + Part 1 新增 | — |
| `口语核心5篇.md` | 5 篇核心回答（背诵用）| — |

## 口语素材核心技法

- 同一个万能故事换开头 + 换情绪 = 覆盖同组所有变体
- Part 2 只考一道，变体不是全部说出来，是为了"不管抽到哪张都能套"
- 素材经过用户真实经历校准：大阪是日本旅行一段（非 5 天全大阪）、用户在职非学生、iPad 7 非 Air、志向是 AI 安全非医疗 AI

## Working with the Question Bank PDF

```
pdftotext "D:\PROJECT\ielts\2026年5-8月最新雅思口语题库-0515.pdf" "/tmp/ielts_speaking.txt"
```

## API Configuration

本项目通过 DeepSeek API 代理 Anthropic 协议，配置写入 `.claude/settings.local.json` 的 `env` 字段：
- 所有主力模型 (opus/sonnet) → `deepseek-v4-pro[1m]`
- 子代理和 haiku → `deepseek-v4-flash`
- `CLAUDE_CODE_EFFORT_LEVEL=max`

## Skills System

通过 `/ielts` 入口路由到四个科目 skill：
- `/ielts-speaking` — 口语素材生成
- `/ielts-writing` — 写作批改（四维评分 + 句子标注 + 改写对比 + 审题）
- `/ielts-reading` — 阅读精读
- `/ielts-diagnose` — 成绩诊断

`env` 中的 `ANTHROPIC_AUTH_TOKEN` 是 DeepSeek API Key，不可泄露到 git。
