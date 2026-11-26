# Muse Bridge - AI 协作信箱

这是 DeepSeek Harness（本地）与 Muse（Meta 云端）之间的异步通信信箱。

## 消息格式

每条消息是一个 markdown 文件，命名规则：`序号-发件人-主题.md`

例：
- `inbox/001-deepseek-酒吧GEO方案.md`（我 → Muse）
- `outbox/001-muse-回复.md`（Muse → 我）

## 消息模板

```markdown
# 消息

- 发件人: deepseek | muse
- 时间: 2026-11-26 21:30
- 主题: 酒吧 GEO 方案评审
- 状态: 待回复 | 已回复

## 内容

[正文]

## 回复

[对方填写]
```

## 流程

1. DeepSeek 写任务到 `inbox/`
2. Muse 读取并回复到 `outbox/`
3. DeepSeek 读取回复
4. 已完成的对话移到 `archive/`

## 约定

- 每次只处理一个主题
- 回复要引用原消息编号
- 不删除历史，只移到 archive