# kovu-cn：综合去 AI 味 Skill

把 AI 味的中英双语文字改写得像人写的，不改变原意。合并 6 个开源版本，扩展中文专属模式，共 32 种检测模式 + 完整方法论。

## 这是什么

一个 Agent Skill（`SKILL.md` 格式），让 AI 写作痕迹检测和改写能力在任何支持 Agent Skills 标准的智能体中运行：Claude Code、Codex、Cursor、Windsurf、Gemini CLI 等。

核心能力：
- **检测 32 种 AI 写作模式**，覆盖中英双语
- **三种模式**：检测（只报告不改）、改写（完整重构）、编辑（原地修改文件）
- **两种方向**：生成模式（写新内容时防止 AI 味）、改写模式（清理已有文本）
- **三种剂量**：轻度（只改被点名的模式）、中度（默认）、重度（结构重排）
- **五种声音风格**：随意、专业、技术、温暖、直率
- **0-100 评分**：量化 AI 味密度

## 32 种检测模式

### A. 形式化结构（最强，单次出现即可改）
1. 排比三连堆砌 — AI 特别爱凑"三"
2. 序数词机械分段 — 第一/第二/第三、首先/其次/最后
3. 负向平行"不是X而是Y" — "It's not just X, it's Y"
4. 同义词轮换/优雅变化 — 重复惩罚导致同义词轮换
5. 段落末尾总结句重复 — "这就是…的意义"

### B. 意义膨胀
6. 空洞意义膨胀 — "为…注入新动力""marking a pivotal moment"
7. 互联网/公文黑话堆砌 — "抓手/闭环/赋能""leverage/synergy"
8. 过渡词引出 — "值得一提的是""It's worth noting"
9. "在…背景下"开场铺垫 — "In today's landscape"
10. 虚假范围 — "from X to Y"的强行跨度

### C. 语气腔调
11. 四字成语/标语堆砌 — "踔厉奋发、勇毅前行"
12. 空洞形容词堆砌 — "显著的/有力的/crucial"
13. "不仅…而且…"递进堆叠 — "Not only X but Y"
14. 句长均匀/缺乏节奏 — 节拍器式匀速节奏
15. 旁观者叙述 — "人们倾向于""one might say"
16. 虚假主体 — "数据显示""The data tells us"

### D. 格式规范
17. 加粗标签式列表 — "**用户体验：**……"
18. 分节标签 — "传播成效方面："
19. "总的来说/综上所述"收尾 — "In conclusion"
20. 标题装饰（emoji/箭头/大小写）
21. 段落可互换性 — 段落间无逻辑依赖
22. Markdown/格式泄漏 — 不该渲染 Markdown 的地方出现 Markdown

### E. 残留与读者错位
23. 写作自述/元叙述 — "本文将…""Let's dive in"
24. 对空气喊话 — "有人可能会说…""While some might argue"
25. 数字格式化装饰 — "5大亮点""3 key takeaways"
26. 占位符/模板残留 — `[Your Name]`、`[待补充]`
27. AI 引用标记泄漏 — `citeturn0search0`、`utm_source=chatgpt.com`
28. 推理链残留 — "让我想想""Step 1:"
29. 信息密度低/车轱辘话 — "换句话说""In other words"
30. 模糊列举开场 — "有几种方法可以…""There are several ways to"
31. 空洞句子 — "我们需要加强团队合作""The system is designed to be scalable"
32. 戏剧性转折开场 — "更离谱的是""The catch?""Here's the thing."

## 方法论亮点

合并了 6 个版本的最优方法论：

| 特性 | 来源 | 说明 |
|------|------|------|
| 词汇分级制 | Aboudjem | Tier 1A/1B/2/3，不是每个 AI 词都一样严重 |
| 突发性原理 | Aboudjem | 人类写作句长方差高，AI 低 |
| 困惑度原理 | Aboudjem | 选第二个想到的词，不用第一个 |
| 声音注入 11 技 | Aboudjem | 从"干净"到"像人"的 11 种技术 |
| 生成/改写双轨 | Shirhussain | 写新内容时防止 AI 味，不只是事后清理 |
| 11 项自检清单 | Shirhussain | 交付前的机械检查 |
| 8 步编辑流程 | jpeggdev | 结构→膨胀→词汇→语法→节奏→堆砌→过渡→灵魂 |
| 剂量制 | Kaos599 | 轻度/中度/重度，按需选择改动幅度 |
| 三种沟壑警告 | Kaos599 | 漂白、学术白皮书味、表演式无能 |
| 文体校准表 | Kaos599 | 9 种文体，规则不统一适用 |
| 可移植性测试 | Kaos599 | 换掉公司/人名/产品，句子还能活就是填充物 |
| 权威测试 | Kaos599 | 具体有依据的坦白是声音，笼统无依据的是 AI 味 |
| 零变更输出 | Kaos599 | 草稿已经很好时直接说没问题 |
| 虚假随意腔反模式 | jbrukh | 警惕用一种 AI 声音替换另一种 |

## 安装

### Claude Code 插件

```
/plugin marketplace add <你的用户名>/kovu-cn
/plugin install kovu@kovu-cn
```

### skills.sh CLI

```bash
npx skills add <你的用户名>/kovu-cn
```

### 手动安装

```bash
mkdir -p ~/.claude/skills/kovu
cp SKILL.md ~/.claude/skills/kovu/
```

### 在其他智能体中使用

将 `SKILL.md` 复制到智能体的 skills 目录即可。任何支持 Agent Skills 标准的智能体都能加载。

## 使用方式

用"帮我 kovu"触发，后面跟文本或文件路径：

```
帮我 kovu 这段文字：[你的文本]
```

或直接粘贴文本：

```
帮我 kovu：
[粘贴你的文本]
```

改写文件：

```
帮我 kovu docs/launch-post.md
```

指定声音风格和剂量：

```
帮我 kovu 这段文字，要专业风格、重度处理：[你的文本]
```

## 与原版 skill 的关系

本 skill 以 [blader/humanizer](https://github.com/blader/humanizer)（26 模式，维基百科 AI 写作特征指南）为基础，合并了 [Aboudjem/humanizer-skill](https://github.com/Aboudjem/humanizer-skill)（55 模式）、[Shirhussain/humanize](https://github.com/Shirhussain/humanize)（39 模式）、[jpeggdev/humanize-writing](https://github.com/jpeggdev/humanize-writing)（8 步）、[Kaos599/professional-skills](https://github.com/Kaos599/professional-skills)（anti-slop）、[jbrukh/skills](https://github.com/jbrukh/skills)（24 模式）的独特贡献，并扩展了 11 种中文专属模式。

原版英文 26 模式作为附录保留在 SKILL.md 末尾，供参考。

## 许可证

MIT

## 致谢

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) — 模式来源，WikiProject AI Cleanup 维护
- [blader/humanizer](https://github.com/blader/humanizer) — 原始基础
- [Aboudjem/humanizer-skill](https://github.com/Aboudjem/humanizer-skill) — 55 模式，词汇分级，声音注入
- [Shirhussain/humanize](https://github.com/Shirhussain/humanize) — 生成/改写双轨，自检清单
- [jpeggdev/humanize-writing](https://github.com/jpeggdev/humanize-writing) — 8 步编辑流程
- [Kaos599/professional-skills](https://github.com/Kaos599/professional-skills) — 剂量制，沟壑警告，可移植性测试
- [jbrukh/skills](https://github.com/jbrukh/skills) — 虚假随意腔反模式，边界情况
