# 01 · Strategy · 竞品分析与差异化

## 战场全景

把 AI 编程产品按「目标用户 × 形态」分四象限：

```
                 桌面/IDE 形态                Web 形态
              ┌─────────────────────┬──────────────────────┐
   开发者向    │ Cursor              │ Claude.ai Artifacts  │
              │ Windsurf            │ Codeium              │
              │ Trae / Kiro         │ Continue.dev (Web)   │
              │ Claude Code (CLI)   │                      │
              ├─────────────────────┼──────────────────────┤
   普通人向    │ （没人在做，因为     │ Bolt.new             │
              │  桌面对普通人是负担）│ Lovable.dev          │
              │                     │ v0.dev               │
              │                     │ Replit Agent         │
              │                     │ ★ Sentinel ★         │
              └─────────────────────┴──────────────────────┘
```

**Sentinel 在右下象限**，与 Bolt / Lovable / v0 / Replit 同台。

## 主要竞品逐个分析

### Bolt.new (StackBlitz)

- **核心**：浏览器内 WebContainer，前端纯 React，AI 用 Claude
- **优势**：首次生成体验流畅，开源
- **天花板**：受 WebContainer 限制（不能跑原生依赖、不能跑长进程）；没有真部署管线（导出到 Netlify 后续不管）；改第二次容易崩
- **真实数据**：D7 留存 < 5%，主要用户是开发者用来快速做 prototype

### Lovable.dev

- **核心**：自家 UI + Supabase 数据库 + AI 生成
- **优势**：UI 漂亮，对 PM 友好
- **天花板**：黑盒，用户不知道发生什么；生成完不能持续演化；锁定 Supabase

### v0.dev (Vercel)

- **核心**：UI 组件生成，对话式
- **优势**：Vercel 生态，发布到 Next.js 项目一键
- **天花板**：**只是 UI 生成**，不是完整应用；强绑 Next.js + React

### Replit Agent

- **核心**：在 Replit IDE 里的 AI Agent，全栈生成
- **优势**：直接在 Replit 平台运行
- **天花板**：锁定 Replit 平台；离开 Replit 几乎不可用；对普通人 IDE 心智依然太重

### Cursor / Windsurf / Trae / Kiro / Codeium

- **核心**：IDE 内 Agent，开发者向
- **不是 Sentinel 的竞争对手**：他们目标用户和我们完全不重叠

### Claude Code / Codex CLI / Devin

- **核心**：CLI / 云端 Agent，技术人员向
- **不是 Sentinel 的竞争对手**：同上

## Sentinel 的差异化（4 条）

### 差异化 1：演化能力 ★★★★★

> Bolt 帮你做 demo，Sentinel 帮你做产品。

| 场景 | Bolt / Lovable | Sentinel |
|---|---|---|
| 第 1 次生成 | ✅ 5 分钟出 demo | ✅ 5 分钟出 demo |
| 第 5 次改动 | ⚠️ 容易把已能跑的改坏 | ✅ 基于 IntentGraph + CodeGraph 增量演化 |
| 第 50 次改动 | ❌ 应用结构混乱，AI 无法理解 | ✅ 持续记忆 + 影响面分析 + 自动 E2E 验证 |
| 应用规模 200+ 文件 | ❌ AI 完全失控 | ✅ Code Graph 索引 + 局部演化 |

**关键基建**：
- `IntentGraph`（应用的"灵魂"，跨版本持续）
- `CodeGraph`（影响面分析）
- `EpisodicMemory`（演化经验）
- `FailureTaxonomy`（避免再踩坑）

### 差异化 2：真实部署 + 真实运行 ★★★★★ 入门券

> Bolt 给你一个 sandbox URL，Sentinel 给你 yourapp.com。

| 维度 | Bolt | Sentinel |
|---|---|---|
| URL 类型 | bolt.new/~/abc123（一次性、无 SEO） | yourapp.sentinel.app（持久、可绑定自定义域名）|
| 运行环境 | 浏览器内 WebContainer | 云端 Cloudflare Workers / Pages |
| 数据库 | 没有 | Supabase / Turso 自动配 |
| 关掉浏览器后 | 应用停了 | 应用持续运行，真实用户能访问 |
| 自定义域名 | 不支持 | 一键配 SSL |

### 差异化 3：上线后运营对话 ★★★★★ 真护城河

**没有任何竞品在做**。这是 Sentinel 最独特的能力。

应用上线后：

- 自动注入轻量 Telemetry（PostHog 协议）
- Production 面板出现「运营」tab：访问数据、转化漏斗、错误日志、慢查询
- 用户对着数据对话改代码：「转化率掉了」→ AI 看数据 → 提假设 → 改 → A/B → 验证
- 用户反馈 widget 内嵌 → 反馈直接进 IntentGraph 待处理列表

这把 Sentinel 从「代码生成工具」升维到「会运营产品的 AI 合伙人」。

### 差异化 4：场景化领域知识 ★★★★

不做"模板市场"（生态做不起来），做**对话式场景识别**：

- 用户说「我想给咖啡店做网站」→ 自动追问「需要在线点单吗 / 会员卡吗 / 外卖吗」
- 内置 5-10 个核心场景的领域知识库（详见 `24-llm-orchestration.md`）
- 让 IntentNormalizationService 根据领域调取领域专属 prompt 和 spec 模板

---

## 我们的护城河（3 道）

### 护城河 1：垂直领域的应用经验数据飞轮

每个用户做的每个应用都进入 EpisodicMemory（脱敏后）。下一个用户做类似应用时：

- IntentNormalize 阶段就能给出更准的澄清问题
- 生成阶段直接复用过往成功 spec
- 演化阶段避免历史踩过的坑

**这是底模无关的资产，越用越值钱。**

### 护城河 2：完整的应用全生命周期工程基座

- v1 已积累的 25+ 服务（IntentGraph / CodeGraph / ExecutionGraph / EpisodicMemory / FailureTaxonomy / HumanGate / BudgetGovernor 等）
- 重新组合在 Web 形态下，是市面上最完整的 Agent 治理基座
- 详见 `51-asset-mapping.md`

### 护城河 3：领域知识 + 提示词工程

Phase 4 选定的 1-2 个垂直场景里，做到「肉眼可见地比 Bolt/Lovable 更对」。

这个能力是**用户感知得到的**（区别于"治理基座"用户感知不到）。

---

## 不打的仗

- **不打底模仗**：我们用 Claude / GPT / GLM / Gemini，不自训模型，**节省 90% 资本**
- **不打 IDE 仗**：不和 Cursor / Windsurf / Kiro 正面打，详见 `14-non-goals.md`
- **不打企业仗**（Phase 1-3）：不做 SAML / SSO / 私有部署，等 C 端跑出来再说
- **不打模板生态仗**：不做模板市场，靠对话生成 + 领域知识

---

## 阶段性 KPI

| 阶段 | 周期 | 北极星 | 关键 KPI |
|---|---|---|---|
| Phase 1 (Deploy First) | 3 个月 | 注册→部署成功率 | ≥ 70% |
| Phase 2 (Evolution) | 3 个月 | 第 5 次演化不破坏率 | ≥ 80% |
| Phase 3 (Operation) | 3 个月 | 上线后对话改动数/应用 | ≥ 3 次/月 |
| Phase 4 (Scenario Depth) | 3 个月 | 场景内 NPS | ≥ 50 |

详见 `30-roadmap.md`。
