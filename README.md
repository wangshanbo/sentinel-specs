# Sentinel · Public Specs

让普通人通过自然对话做出真实可上线、可演化、可运营的全栈应用。

The "AI co-founder" web product that helps non-coders ship real, deployable, evolvable, operable full-stack apps by chatting.

## 这个仓库是什么

Sentinel 产品的公开 specs。把 vision、strategy、target users、product overview 这 4 篇规格文档开源，LLM orchestration、sandbox、evolution-engine、data model 等具体实现保留。

为什么这样做：Bolt / Lovable / v0 / Replit Agent 主打的是「demo 速度」，Sentinel 想做的是「应用做完之后还能持续演化、能上线运营」。把 vision 写出来公开，比 PPT 更可信，比代码更易读。

## 4 篇公开规格

| # | 文件 | 一句话 |
|---|---|---|
| 00 | [Vision](./00-vision.md) | 一句话定位 / 5 个核心信条 / 5 年北极星 / 不是什么 |
| 01 | [Strategy](./01-strategy.md) | 战场全景 / 主要竞品分析 / 4 条差异化 / 3 道护城河 / 不打的仗 |
| 02 | [Target Users](./02-target-users.md) | 4 类目标用户画像 / 优先级 / 付费意愿 / 不服务的用户 |
| 10 | [Product Overview](./10-product-overview.md) | Create / Evolve / Operate 三大模块全景 |

## 配套作品

- [NormCode](https://github.com/wangshanbo/NormCode)——5 个月 build 出来的长程 Agent IDE（fork VS Code），10 个版本之后归档。Sentinel v2 复用了 NormCode 的领域逻辑。
- [Guard](https://github.com/wangshanbo/guard)——Rust 写的 AI 策略约束层。
- [ai-native-sop](https://github.com/wangshanbo/ai-native-sop)——中文方法论连载。完整 build / kill / pivot 故事在[《做就是最好的想》](https://github.com/wangshanbo/ai-native-sop/blob/main/00-manifesto-build-to-think.md)。

## 作者

王善波，36 岁，杭州，台满满科技研发主管和硬件采购。完整介绍在 [github.com/wangshanbo](https://github.com/wangshanbo)。

627257359@qq.com

## 反馈

- 看完觉得方向对——Star
- 看到 strategy 里的逻辑漏洞——开 Issue
- 想做 alpha 用户 / 投资 / 合伙——邮件

## License

CC BY 4.0，转载请注明作者和原文链接。
