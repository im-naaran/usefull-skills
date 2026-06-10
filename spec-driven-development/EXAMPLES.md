# Spec-Driven Development - 示例

## 触发

```text
新功能 用户登录支持短信验证码
```

## 启动输出

```text
规范驱动开发编排器已启动

Feature: user_login_sms_code
Spec 目录: specs/20260608_user_login_sms_code/

正在进入 Phase 0: 项目上下文分析...
```

## requirements.md 摘要

```markdown
# 需求规格说明书

> 状态：已确认

## 背景

当前登录流程仅支持密码登录，需要增加短信验证码登录。

## 功能需求

### R-01: 发送验证码

当用户输入手机号并点击获取验证码时，系统应当调用短信验证码发送接口。

### R-02: 验证码登录

当用户输入手机号和验证码并提交时，系统应当完成登录。

## 验收标准 / 人工确认点

### AC-01

Given 用户输入合法手机号
When 点击获取验证码
Then 页面展示倒计时，且发送验证码请求参数正确

## 范围外

- 不调整密码登录流程。
```

## design.md 摘要

```markdown
# 技术设计

> 状态：已确认

## 方案概述

复用现有登录页，在登录方式区域增加短信验证码模式。

## 涉及模块

- src/api/login.ts
- src/views/login/index.vue

## 接口与类型

- sendSmsCode(params: { phone: string })
- loginBySmsCode(params: { phone: string; code: string })

## 需求追踪

| 需求 | 设计点 |
|------|--------|
| R-01 | 新增 sendSmsCode |
| R-02 | 新增 loginBySmsCode 并接入登录页 |
```

## tasks.md 摘要

```markdown
# 任务拆解

> 状态：已确认

- [ ] task-01: [API] 增加短信验证码发送与登录接口封装
- [ ] task-02: [UI] 增加短信验证码登录表单
- [ ] task-03: [State] 实现验证码倒计时状态

## task-01: [API] 增加短信验证码发送与登录接口封装

**追踪需求：** R-01, R-02
**依赖任务：** 无
**修改范围：** src/api/login.ts
**完成标准：**
- 新增 sendSmsCode API
- 新增 loginBySmsCode API
- 复用现有请求封装

**自动化验证：**
- npm run lint
- npm run build

**人工验证关注点：**
- 验证手机号参数能正确传入发送验证码接口
- 验证接口异常时展示现有错误提示
```

## 单任务汇报

```text
已完成 task-01: [API] 增加短信验证码发送与登录接口封装

本次改动：
- 新增 sendSmsCode API
- 新增 loginBySmsCode API
- 复用现有请求封装和错误处理方式

校验结果：
- lint 已执行，未发现新增问题

人工验证关注点：
- 验证手机号参数能正确传入发送验证码接口
- 验证接口异常时展示现有错误提示

准备执行 task-02。
```
