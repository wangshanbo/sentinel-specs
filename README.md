# Sentinel · Public Specs

> **The "AI co-founder" web product that helps non-coders ship real, deployable, evolvable, operable full-stack apps — by chatting.**
>
> 让普通人通过自然对话做出真实可上线、可演化、可运营的全栈应用的 AI 合伙人。

[![License](https://img.shields.io/badge/Specs-CC--BY--4.0-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-v2%20in%20progress-D97757)]()
[![Author](https://img.shields.io/badge/Author-@wangshanbo-181717?logo=github)](https://github.com/wangshanbo)

---

## 这个仓库是什么

**这是 Sentinel 产品的「公开 specs」**：把 Sentinel 的 vision、strategy、target users、product overview 这 4 篇核心规格文档**完整开源**，而保持 LLM orchestration / sandbox / evolution-engine / data model 等核心实现 specs 闭源。

简单说：**vision 公开，弹药库保密。**

为什么这样做：

1. **Bolt / Lovable / v0 / Replit Agent 卷的是「demo 速度」**。Sentinel 卷的是「应用做完之后还能持续演化、能上线运营」。把 vision 公开，让世界知道这个赛道**还有人在认真思考**而不是抄 Bolt 的 UI。
2. **Vision 抄不走，build/kill/pivot 经验抄不走**。具体见配套作品 [NormCode](https://github.com/wangshanbo/NormCode)（v1 已 sunset，但跑通了 Anthropic 式长程 Agent Harness）。
3. **公开 specs 是「我思考有多深」的证明**。比 PPT 更可信，比代码更易读。

---

## 4 篇公开规格

| # | 文件 | 一句话讲什么 |
|---|---|---|
| 00 | [Vision](./00-vision.md) | 一句话定位 / 5 个核心信条 / 5 年北极星指标 / 不是什么（防漂移） |
| 01 | [Strategy](./01-strategy.md) | 战场全景 / 主要竞品逐个分析 / 4 条差异化 / 3 道护城河 / 不打的仗 |
| 02 | [Target Users](./02-target-users.md) | 4 类目标用户画像 / 优先级 / 付费意愿 / 不服务的用户 |
| 10 | [Product Overview](./10-product-overview.md) | Create / Evolve / Operate 三大模块全景 |

---

## 配套开源作品

Sentinel 不是孤立的产品，它是 **Build-to-Think 三部曲** 的一环：

- 🛡️ **[NormCode](https://github.com/wangshanbo/NormCode)** · v1 sunset —— 5 个月 build 出来的长程 Agent IDE（fork VS Code），10 个版本 / 13+ 核心服务上线。然后我亲手砍了 vscode fork 这个形态。砍掉的代价 = Sentinel v2 的方法论源头。
- 🚀 **Sentinel** · v2 in progress —— 这个 repo 描述的产品。Web App 形态，复用 NormCode 25+ 服务的领域逻辑。
- 🦀 **[Guard](https://github.com/wangshanbo/guard)** —— Rust 写的 AI 开发策略约束层。MCP 让 AI 有手脚，Skills 让 AI 有经验，Guard 让 AI 不做错事。

完整 build / kill / pivot 故事见 [《做就是最好的想 — 5 个月 build 了 3 个 AI 产品，砍了 1 个》](https://github.com/wangshanbo/ai-native-sop/blob/main/00-manifesto-build-to-think.md)。

---

## 关于作者

王善波 · Wang Shanbo · 36 岁 · 杭州

- 🏢 **Engineering Lead + Hardware Sourcing @ 台满满科技 (Tai Man Man)**，5+ 年跟随创始人
- 📊 服务的真实业务：**500+ 球房 / ¥3B 平台 GMV / 10 人研发部**
- 🧠 业余月烧 **\$2,000 / 6 亿 tokens** 在 Claude Opus 等顶级模型上
- 🛠️ 跨端全栈：Vue · React · **Flutter** · TypeScript · Java（存量）· Rust
- 🔌 **国内 OEM 供应链直达**：灯控 / 存杆柜 / 点单机（串口充电）/ 电视 / 一体机 6 类硬件，6 家工厂老板直达

---

## 反馈与协作

- ⭐ **看完觉得方向对 → Star 一下**，让我知道这个方向有人在等
- 🐛 **看到 strategy 里的逻辑漏洞 → 开 Issue 拍砖**，越狠越好
- ✍️ **想英文翻译 → 发 PR**
- 🤝 **想做 alpha 用户 / 投资 / 合伙 / 工程合作 → 邮件 [627257359@qq.com](mailto:627257359@qq.com)**

---

## License

文档采用 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 协议，转载请注明作者王善波 + 原文链接。

---

<sub>Sentinel 是当前进行中的产品。本仓库只代表 v2 的当前快照，未来会持续更新。如果你看到了这个 repo，恭喜你站在了一个正在被 build 的产品的最前线。</sub>
