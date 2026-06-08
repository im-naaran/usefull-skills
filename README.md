# Useful Skills

通用 Agent Skills 集合，包含实用的自动化工作流。

## 📋 Skills 列表

### code-review
分析 git 代码变更并生成结构化的测试报告。

**使用场景：**
- 分析 commit 之间的代码差异
- 生成测试指导文档
- 代码变更审查

**触发示例：**
- "帮我分析这次提交的改动"
- "生成测试报告"
- "review 这些代码变更"

---

### spec-driven-development
仿 Kiro 的规范驱动开发流程，按需求、设计、任务、执行分阶段推进功能开发。

**使用场景：**
- 新功能开发前先生成规格文档
- 需要需求追踪、设计评审、任务拆解后再编码
- 需要保护生产代码，避免未确认规格时直接实现

**触发示例：**
- "新功能 用户登录支持短信验证码"
- "开发功能 支付中心增加分期还款入口"
- "Start Feature add invoice export"

---

## 🚀 安装方法

推荐使用 `npx skills` 安装：

```bash
npx skills add im-naaran/usefull-skills
```

### 手动安装

如果需要手动安装，可以将需要的 skill 目录复制到你的 Agent skills 目录中：

```bash
cp -r code-review <your-skills-dir>/
cp -r spec-driven-development <your-skills-dir>/
```

`<your-skills-dir>` 取决于你使用的 Agent 或运行环境。

---

## 📝 版本历史

- **v1.0.0** (2026-02-04) - 初始版本
  - 新增 code-review skill
- **v1.1.0** (2026-06-08) - 新增规范驱动开发流程
  - 新增 spec-driven-development skill
