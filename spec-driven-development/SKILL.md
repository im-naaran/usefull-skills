---
name: spec-driven-development
description: 规范驱动开发编排流程，仿 Kiro 的需求、设计、任务、执行分阶段工作流。用户以"新功能"、"开发功能"、"需求开发"、"Start Feature"、"New Feature"开头，或要求先写需求规格、技术设计、任务拆解再编码时使用。
---

# 规范驱动开发编排器

## 核心流程

按以下顺序推进功能开发：

```text
需求 -> 设计 -> 任务 -> 执行
```

在需求、设计和任务拆解获得用户确认前，禁止修改生产代码。实现必须能追溯到对应需求和任务。

---

## 启动规则

当用户消息以以下关键词开头时，启动流程：

```text
新功能
开发功能
需求开发
Start Feature
New Feature
```

创建规格目录：

```text
specs/{YYYYMMDD_feature_name}/
├── project-context.md
├── requirements.md
├── design.md
├── tasks.md
└── changelog.md
```

`YYYYMMDD` 使用当前日期，`feature_name` 从用户需求提炼为小写下划线名称。

启动后输出：

```text
规范驱动开发编排器已启动

Feature: {feature_name}
Spec 目录: specs/{YYYYMMDD_feature_name}/

正在进入 Phase 0: 项目上下文分析...
```

---

## 生产代码保护

Phase 0 到 Phase 3 期间只允许修改 `specs/{YYYYMMDD_feature_name}/` 下的规格文档，禁止修改生产代码。常见生产代码目录包括：

```text
src/
app/
pages/
components/
server/
```

除非用户明确批准，禁止升级依赖、修改锁文件、调整 CI/CD、Docker、部署或基础设施配置。

---

## Phase 0: 项目上下文

阅读项目结构与已有规范，生成 `project-context.md`。优先查看：

```text
README.md
package.json
docs/
specs/
architecture/
```

记录技术栈、架构模式、关键约束、相关模块和已知风险。

---

## Phase 1: 需求

生成 `requirements.md`，包含：

- 背景与目标
- 功能需求，使用 `R-01`、`R-02` 编号
- 必要的非功能需求
- 验收标准或人工确认点
- 明确的范围外内容

展示文档后等待用户确认：

```text
Phase 1 完成。

请确认需求规格说明书。

回复 Approve 或 Proceed 进入下一阶段。
```

---

## Phase 2: 设计

用户确认需求后，生成 `design.md`，包含：

- 采用方案和选择原因
- 涉及模块与数据流
- 接口、类型或状态设计
- 主要风险与规避方式

展示文档后等待用户确认：

```text
Phase 2 完成。

请确认技术设计文档。

回复 Approve 或 Proceed 进入下一阶段。
```

---

## Phase 3: 任务

用户确认设计后，生成 `tasks.md`。任务必须足够小，能独立实现、验证和回滚。

任务格式：

```text
- [ ] task-01: [模块] 任务描述
```

每个任务应标注追踪需求、修改范围和完成标准。

---

## Phase 4: 执行

严格按 `tasks.md` 顺序执行，一次只处理一个任务：

1. 读取当前任务和对应需求、设计。
2. 实现最小代码变更。
3. 执行可用的类型检查、Lint、构建或单元测试。
4. 更新任务状态。
5. 在任务下补充人工验证关注点。
6. 向用户汇报已完成任务、校验结果和下一步。

不得声明"测试通过"、"验证通过"或"生产可用"，除非用户明确确认人工验证结果。

---

## 变更处理

实现阶段如果出现新需求、设计缺陷或任务拆分不合理，先停止编码，回到对应阶段更新 `requirements.md`、`design.md` 或 `tasks.md`，获得用户确认后再继续。

---

## 参考资料

- **文档模板**：参考 [REFERENCE.md](REFERENCE.md)
- **简短示例**：参考 [EXAMPLES.md](EXAMPLES.md)
