# Useful Skills

Claude Code Agent Skills 集合，包含实用的自动化工作流。

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

## 🚀 安装方法

### 方法 1：通过 Claude Code Plugin 安装

```bash
/plugin add im-naaran/usefull-skills
```

### 方法 2：通过 npx 安装

```bash
npx skills add im-naaran/usefull-skills
```

### 方法 3：手动安装

**作为个人 Skills：**
```bash
cp -r code-review ~/.cursor/skills/
```

**作为项目 Skills：**
```bash
mkdir -p .cursor/skills
cp -r code-review .cursor/skills/
```

---

## 📝 版本历史

- **v1.0.0** (2026-02-04) - 初始版本
  - 新增 code-review skill
