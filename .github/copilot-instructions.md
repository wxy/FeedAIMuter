---
applyTo: "**"
---

# SilentFeed - Chrome Extension Project

---

## Part 1: 强制执行

**⚠️ 在开始任何工作前，必须读取并完全理解 AI 宪法与初始化协议**：
请查阅：
- `.github/AI_CONSTITUTION.md` - AI 进化宪法（核心原则）
- `.github/AI_INITIALIZATION.md` - 强制初始化协议（4 技能执行序列）

### 核心系统架构

1. **AI Constitution** (`.github/AI_CONSTITUTION.md`) - 持续进化的核心原则
   - Part 1: 持续学习与自我改进
   - Part 2: 进化触发条件
   - Part 3: 技能模块化原则
   - Part 4: 指令与技能分工

2. **Initialization Protocol** (`.github/AI_INITIALIZATION.md`) - 每次响应前必须强制执行
   - 4 个 Tier 2 系统技能的强制初始化序列
   - 带可验证的执行标记
   - 非可选的强制约束

3. **Skills System** (`AGENTS.md`) - 14 个技能的模块化体系
   - Tier 1: 2 个核心技能（进化基础设施）
   - Tier 2: 4 个必需系统技能（安全/运行时基线）
   - Tier 3: 8 个可选技能（工作流增强）

### 🎯 最高优先级

**执行前检查协议** (Part 3)：
- 每次回复前必须执行 6 步检查，这是**不可跳过的纪律**
- 特别是第 5 步"真相检验"：确认你真的做了检查，而非假装
- 第 6 步"补救"：如果发现遗漏，立即停止并重新检查

### 🔧 技能的模块化原则

**新架构亮点**：
- **技能自主声明依赖**：每个技能在其 SKILL.md 中声明触发条件和依赖关系
- **宪法不维护依赖表**：避免宪法成为"依赖中枢"，新技能可随时添加
- **Tier 2 条件强制**：当条件满足时自动触发，但在执行修改前询问用户确认
- **用户保有控制权**：对所有修改类的技能操作（Tier 2-3）都要获得用户同意

### 📖 核心参考文档

- **技能定义规范**：查阅 evoskills 仓库中的 [SKILL_DEFINITION_SPECIFICATION.md](https://github.com/wxy/evoskills/blob/main/SKILL_DEFINITION_SPECIFICATION.md)
  - 所有技能文件应遵循的格式
  - 元数据、触发条件、依赖声明、用户交互点
- **技能管理**：使用 `evoskills` CLI 命令
  - `evoskills list` - 查看所有可用技能
  - `evoskills install <skill-name>` - 安装新技能
  - `evoskills update` - 更新所有已安装的技能

## Part 2: 项目特定 - SilentFeed 工程规范

### 🏗️ 项目大图景与架构

#### MV3 Chrome Extension 结构
- **Content Script** ↔ **Popup** ↔ **Background(Service Worker)**
- 业务逻辑在 `src/core/**`，持久化在 `src/storage/**`，UI 在 `src/components/**`

#### 核心数据流
```
RSS 源发现 → Background 消息处理 → Dexie 数据库 → 定时抓取 → AI 推荐 → Popup 展示
  (rss-detector)  (chrome API)    (FeedManager)   (scheduler)  (service)  (UI)
```

#### AI 集成架构
- **AICapabilityManager**: 统筹多个 AI Provider
- **AIUsageTracker**: 成本统计与预算管理
- **Ollama 本地集成**: 通过 DNR 规则规避 CORS 限制

### 📋 项目特有约定

#### 代码结构约定
- **路径别名**: 使用 `@/` 指向 `src`，`~` 指向仓库根（见 `tsconfig.json`）
- **国际化**: 用户可见文本必须用 `translate as _` 包裹（`src/i18n/helpers.ts`）；开发日志保持中文无需 i18n
- **消息通信**: 统一使用 `chrome.runtime.sendMessage/onMessage`，所有消息类型由 Background 集中处理
  - 例如：`SAVE_PAGE_VISIT`、`RSS_DETECTED`、`ONBOARDING_STATE_CHANGED`

#### 特定功能约定
- **画像学习门控**: Onboarding 阶段（setup）跳过数据采集，状态变更需调用 `reconfigureSchedulersForState()`
- **图标/徽章**: 使用 `utils/IconManager.ts` 按优先级更新，含 AI 配置状态、未读推荐、RSS 发现提示

#### 存储与数据约定
- **数据库**: Dexie 数据库入口在 `src/storage/db/**`，事务逻辑在 `src/storage/transactions.ts`
- **类型系统**: 统一在 `src/types/**` 定义，重要类型：`ConfirmedVisit`、`Recommendation`、`DiscoveredFeed`

#### AI 与 DNR 约定
- **多厂商管理**: Provider 策略在 `src/core/ai/providers/**`
- **成本计算**: `CostCalculator.ts`、`BudgetChecker.ts` 管理预算
- **Ollama CORS**: 依赖 DeclarativeNetRequest 移除 `Origin/Referer`，须确保 `public/dnr-rules.json` 与 manifest 一致

### 🎨 代码风格

#### TypeScript 约定
- **严格模式**: 所有导出函数/对象需显式类型，避免使用 `any`
- **⚠️ 禁止动态导入**: Service Worker (background.ts) 中禁止 `import()` 或 `importScripts()`，所有导入必须在顶部静态声明
- 动态导入仅允许在测试代码中使用
- **⚠️ 禁止 HERE 文档**: 创建文件时禁止使用 `cat > file << 'EOF'` 等 HERE 文档方式，必须使用 `create_file` 工具

#### React 约定
- **仅函数组件**: 禁止 Class Component，使用 Hooks 进行状态管理
- **样式**: Tailwind CSS 进行样式，Zustand 在 `src/stores/**` 管理全局状态
- **Testing Library**: 组件测试使用 Testing Library，核心模块写集成测试

#### 文件命名约定
- 组件: `PascalCase` (如 `RecommendationCard.tsx`)
- 函数/变量: `camelCase` (如 `fetchRecommendations`)
- 常量: `UPPER_SNAKE_CASE` (如 `MAX_FEED_COUNT`)
- 文件: `kebab-case` (如 `recommendation-service.ts`)

### 🧪 测试规范（Vitest）

#### 环境配置
- **Test Runner**: Vitest，环境为 `jsdom`
- **Mocks**: `src/test/setup.ts` 中注入：
  - `chrome` 全局 Mock（Chrome API 模拟）
  - `fake-indexeddb` （Dexie 数据库模拟）
  - `react-i18next` Mock

#### 覆盖率标准
- 行覆盖率: ≥ 70%
- 函数覆盖率: ≥ 70%
- 分支覆盖率: ≥ 60%

#### 测试文件约定
- 新增代码必须同时提供 `*.test.ts(x)` 文件
- 组件测试使用 Testing Library 进行 DOM 操作
- 核心模块（service、store、utils）写集成测试
- Mock 数据参考 `_typescript-type-safety` 技能创建

### 🚀 项目工作流

#### 开发与构建命令
- **开发**: `npm run dev` - 预生成 DNR → Plasmo 开发服务
- **构建**: `npm run build` - 预生成 DNR → Plasmo 构建 → 拷贝多语言资源
- **测试**: 
  - `npm run test` - 监听模式
  - `npm run test:run` - 单次运行
  - `npm run test:coverage` - 覆盖率报告
- **推送前检查**: `npm run pre-push` - 运行完整测试、覆盖率、构建验证

#### 版本控制流程

**基本原则**：
- 在 master 不直接开发；等待用户确认再提交/推送
- 推送前必须通过 `npm run pre-push`
- PR 和 commit 都使用中文描述

**提交与 PR 说明**：
创建 PR 或提交时，**必须使用说明文件方式**，禁止在命令行使用长篇幅说明：

1. **Git 提交**: 参考 `_git-commit` 技能（`.agent/skills/_git-commit/SKILL.md`）
  - 在 `.github/COMMIT_DESCRIPTION.local.md` 中编写说明（本地文件，不入库）
  - 使用 Conventional Commits 规范
  - 执行 `git commit -F .github/COMMIT_DESCRIPTION.local.md`

2. **GitHub PR**: 使用官方 `_pr-creator` 技能（`.agent/skills/_pr-creator/SKILL.md`）
  - 在 `.github/PR_DESCRIPTION.local.md` 中编写说明（本地文件，不入库）

### ⚠️ 常见坑位

- **Background 生命周期**: 异步消息需 `sendResponse` + 返回 `true` 或使用自执行 async 包裹，否则响应丢失
- **DNR 规则生效**: 修改 DNR/manifest 后需重建并重新加载扩展；注意清理遗留动态规则
- **i18n 遗漏**: UI 文本未包裹 `_()` 会在审查时被要求修复；测试中使用英文翻译文件做断言

---

---

<!-- evoskills: auto-generated references (do not edit) -->
- **AI_CONSTITUTION.md**: Core evolution mechanism (read before every session)
- **AI_INITIALIZATION.md**: Mandatory 4-skill initialization protocol (execute before every response)
- **AGENTS.md**: Skills registry with Tier 1-3 system

<!-- evoskills: auto-generated references -->
- See EXECUTION_RULES.md for optional safety guardrails
