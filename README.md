# AI Skills

个人 AI Skills 仓库，用于沉淀可复用的 Agent / Coding Agent 工作流规则。

这里的 Skill 主要用于把日常工作中的固定判断逻辑、文档规范、分析流程和输出格式沉淀下来，让 AI 在执行类似任务时保持一致的标准。

## Repository Structure

```text
.
├── README.md
└── skills/
    └── knowledge-base-classifier/
        └── SKILL.md
```

每个 Skill 使用独立目录管理，目录名称使用英文小写加 `-` 分隔。

原则上一个 Skill 至少包含：

```text
<skill-name>/
└── SKILL.md
```

如果 Skill 本身已经自包含，则不额外存放制度文档、说明文档或其他依赖文件。

---

## Available Skills

### knowledge-base-classifier

知识库文档分类与生成 Skill。

用于在编写研发知识库方案时，根据预先整理好的规则自动完成：

- 判断知识库分类
  - 创新攻坚
  - 优秀设计
  - 经验分享
- 判断建议等级
  - 创新攻坚：S / A / B / C
  - 优秀设计：S / A / B / C
  - 经验分享：A / B / C
- 分析当前方案与分类要求的匹配程度
- 判断缺失内容
- 给出文档补充建议
- 检查低质量方案风险
- 生成标准化知识库 Markdown
- 生成 `申报说明.txt`
- 统一管理知识库图片及相对路径

### 知识库生成目录

生成知识库方案时使用以下目录结构：

```text
<方案名称>/
├── <方案名称>.md
├── 申报说明.txt
└── img/                    # 只有存在图片时才创建
    ├── system-architecture.png
    └── problem-flow.png
```

规则：

- 一个方案只生成一个 Markdown 正文；
- Markdown 文件名与方案名称保持一致；
- 图片统一放入 `img/`；
- 没有图片时不创建空的 `img/`；
- Markdown 中所有图片均使用相对路径；
- 单独生成 `申报说明.txt`；
- 不虚构性能数据、落地结果或推广范围。

图片引用示例：

```markdown
![系统架构图](./img/system-architecture.png)
```

---

## Usage

将需要使用的 Skill 目录复制到你的 Agent / Coding Agent 所使用的 Skills 目录中即可。

例如：

```text
skills/
└── knowledge-base-classifier/
    └── SKILL.md
```

之后在对话中直接描述任务，例如：

```text
根据 knowledge-base-classifier 的规则，
帮我把这次 Cassandra 故障排查整理成知识库文档。
```

或者：

```text
帮我判断这个知识库方案属于什么分类，并给出建议等级。
```

如果 Agent 支持自动加载 Skill，也可以直接根据 `SKILL.md` 中的 `name` 和 `description` 匹配任务。

---

## Skill Design Principles

本仓库中的 Skill 尽量遵循以下原则：

1. **Self-contained**

   能写进 `SKILL.md` 的规则直接写入 Skill，不依赖额外制度文档。

2. **Deterministic**

   对分类、目录结构、文件命名、输出格式等尽量使用明确规则，减少同一任务多次执行时的差异。

3. **No fabricated data**

   不允许为了补全文档而虚构测试数据、性能指标、业务结果或落地效果。

4. **Reusable**

   Skill 应尽可能沉淀可跨项目复用的方法，而不是只适配某一次任务。

5. **Minimal dependencies**

   没有必要的附件、参考资料和中间文件不进入 Skill 目录。

---

## Adding a New Skill

新增 Skill 时建议创建：

```text
skills/
└── <skill-name>/
    └── SKILL.md
```

`SKILL.md` 顶部建议包含：

```yaml
---
name: your-skill-name
description: 简洁描述这个 Skill 在什么情况下使用，以及主要完成什么任务。
---
```

正文至少建议说明：

```text
1. Skill 的目标
2. 触发场景
3. 输入要求
4. 判断 / 执行规则
5. 输出格式
6. 边界情况
7. 禁止事项
8. 示例
```

---

## Naming Convention

推荐统一使用：

```text
knowledge-base-classifier
log-analyzer
thingsboard-troubleshooter
deployment-checker
```

约定：

- 全小写；
- 单词之间使用 `-`；
- 名称体现 Skill 的核心能力；
- 不使用空格；
- 不使用过长目录名。

---

## Roadmap

后续可以继续沉淀例如：

```text
skills/
├── knowledge-base-classifier/
├── thingsboard-troubleshooter/
├── cassandra-troubleshooter/
├── redis-cluster-checker/
├── nacos-troubleshooter/
├── nginx-config-reviewer/
└── linux-server-health-check/
```

---

## License

本仓库主要用于个人工作流和内部知识沉淀。

如需公开发布，建议根据实际使用范围补充合适的 License。
