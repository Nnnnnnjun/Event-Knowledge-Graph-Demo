# 截图说明

这里的图片来自作者本地 Neo4j Browser 的真实运行结果，不是手绘示意图，也不是 AI 生成图。

| 文件 | 查询 | 说明 |
|---|---|---|
| `xuanwumen_v3_full.png` | `MATCH p=()-[r]->() RETURN p` | 玄武门 V3 全图：26 个节点、114 条关系 |
| `covid_v1_timeline.png` | `MATCH p=()-[r]->() RETURN p LIMIT 50` | 新冠纯时序图：51 个节点、50 条 `FOLLOWED_BY`（**这是 `LIMIT 50` 的展示子图，不是全量**） |
| `covid_v2_isolated.png` | `MATCH p=()-[r]->() RETURN p LIMIT 50` | 新冠 V2 的失败现场：节点碎成孤立小段 |
| `covid_v3_hallucination.png` | `MATCH p=()-[r]->() RETURN p LIMIT 50` | 新冠 V3 的失败现场：`15家医` 成为放射中心，61 条 `CAUSED_BY`、58 条 `REQUIRES` |

## 重要口径

- `covid_v1_timeline.png` 右侧显示 `51 nodes, 50 relationships`，是因为查询带了 `LIMIT 50`；
  全量数据是 **195 个节点、194 条 `FOLLOWED_BY`**。
- `covid_v1_timeline.png` 是原始 V1 运行的截图；当时 `P16` 被当成“前序指针”，
  当前 Notebook 已按“`P16` = 后续”修正方向。边数不变，仍为 194，但 20 条跨天边和
  119 条同日边的箭头方向更符合字段语义。
- `xuanwumen_v3_full.png` 右侧显示 `26 nodes, 114 relationships`，是全量查询结果。
- 截图中的节点颜色来自 Neo4j Browser 的自动配色，不是项目代码设置的主题。

## 替换截图

如果你在自己的环境重跑，建议保留以下命名，README 就不用改：

```text
screenshots/
├── xuanwumen_v3_full.png
├── covid_v1_timeline.png
├── covid_v2_isolated.png
└── covid_v3_hallucination.png
```

截图前建议：

1. 在 Neo4j Browser 里执行对应查询；
2. 等布局稳定后再截图；
3. 不要截入浏览器地址栏、书签、账号信息；
4. 如果图中包含真实个人信息或未公开数据，请先脱敏。
