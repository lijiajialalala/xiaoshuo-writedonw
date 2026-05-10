# xiaoshuo-writedonw

小说创作、番茄平台研究、小说蒸馏和长篇写作流程仓库。

当前阶段不直接进入正文写作。P0 假设登记、P0.5 合规与相似风险边界、P1 L0 样本池已经完成初版；当前先用 P0.6 三平台够用表约束 P2 字段，再进入 P2-alpha 三本前 10 章校准批次。P2-alpha 通过后，才扩到 P2-beta 的 10-15 本正式快拆。

## 当前主线

当前不继续补抽象方法论，先按总控路线做 P0.6 够用表和 P2-alpha：

1. 先确认番茄、七猫、起点的直发/内投/签约差异。
2. 研究各平台有哪些钱可以拿、触发条件和更新成本。
3. 把平台机制字段接入 P2 证据提取协议。
4. 先从 L0 样本池中选 3 本做 P2-alpha 校准：源头/开山样本、当前热度样本、完结长线样本。
5. P2-alpha 通过后，再扩到 P2-beta 的 10-15 本前 10 章快拆。
6. 在样本证据完成前，暂停正文、完整世界观、作者级 skill 和百万字大纲。

## 入口文档

- [AGENTS.md](AGENTS.md): agent 启动级操作契约，只放长期行为规则和入口。
- [docs/README.md](docs/README.md): 文档地图和当前工作流入口。
- [docs/00_总控/00_当前总控路线图.md](docs/00_总控/00_当前总控路线图.md): 当前阶段和推进顺序。
- [docs/00_总控/05_agent工作纪律.md](docs/00_总控/05_agent工作纪律.md): 用户例子处理、反过早收缩和自问自答纪律。
- [docs/00_总控/06_编辑审稿门与大纲准备.md](docs/00_总控/06_编辑审稿门与大纲准备.md): 编辑视角、平台门禁、AI/相似风险和大纲学习接口。
- [docs/00_总控/07_模块依赖与推进顺序.md](docs/00_总控/07_模块依赖与推进顺序.md): 当前模块调度层，决定哪些现在做、哪些只留接口、哪些触发后再做。
- [docs/00_总控/04_合规与相似风险边界.md](docs/00_总控/04_合规与相似风险边界.md): 合规、洗稿、相似风险和迁移边界。
- [docs/30_平台研究/README.md](docs/30_平台研究/README.md): 番茄、七猫、起点投稿路径、收益机制和平台生产策略。
- [docs/30_平台研究/00_P0.6三平台够用表.md](docs/30_平台研究/00_P0.6三平台够用表.md): P0.6 进入 P2-alpha 前的够用表，不把平台研究做成百科。
- [docs/20_小说蒸馏方法/03_小说提取归纳总模型.md](docs/20_小说蒸馏方法/03_小说提取归纳总模型.md): 小说提取、归纳和生产运行包的总模型。
- [docs/20_小说蒸馏方法/04_P2小说证据提取器协议.md](docs/20_小说蒸馏方法/04_P2小说证据提取器协议.md): P2 前 10 章证据抽取操作手册。
- [docs/20_小说蒸馏方法/05_小说内容内核发现系统操作方案.md](docs/20_小说蒸馏方法/05_小说内容内核发现系统操作方案.md): 小说内容内核发现、颗粒度矩阵、风险循环和 clean-room 诊断路线。
- [docs/20_小说蒸馏方法/06_跨题材基础叙事逻辑库.md](docs/20_小说蒸馏方法/06_跨题材基础叙事逻辑库.md): 长篇持续可读的跨题材底层机制候选库。
- [docs/10_番茄专项/02_证据提取与归纳规格.md](docs/10_番茄专项/02_证据提取与归纳规格.md): 番茄样本提取和归纳规格。
- [research/10_番茄专项/00_P0_假设登记.md](research/10_番茄专项/00_P0_假设登记.md): 当前平台、赛道和结构假设登记表。
- [research/10_番茄专项/番茄都市高武样本拆解表_v1.md](research/10_番茄专项/番茄都市高武样本拆解表_v1.md): 第一版样本拆解主表。

## 仓库结构

```text
.agents/    后续小说写作和蒸馏 runtime skill
docs/       总控、番茄专项、小说蒸馏方法、平台研究、前期归档
data/       可入库的小样本和安全夹具，不放大体量原文
research/   样本池、榜单表、拆解表、阶段研究记录
schemas/    story bible、chapter card、validation report 等结构模板
scripts/    后续自动化抓取、清洗、校验脚本
src/        后续可执行流水线代码
tests/      后续回归测试和质量验证
```

当前可用 skill：

- [.agents/skills/critical-thinking-mode/SKILL.md](.agents/skills/critical-thinking-mode/SKILL.md): 批判性追问和反过早收缩。
- [.agents/skills/novel-editor-gate/SKILL.md](.agents/skills/novel-editor-gate/SKILL.md): 平台规则、编辑审稿、AI/相似风险和大纲准备门禁。

## 第一阶段目标

1. 已完成 P0 假设登记初版。
2. 已完成 P1 L0 样本池初版：30+ 本番茄同赛道/相邻赛道样本。
3. 已完成 P0.5：合规与相似风险边界初版。
4. 下一步执行 P0.6：三平台够用表和待验证清单分流。
5. 再进入 P2-alpha：3 本前 10 章校准批次。
6. P2-alpha 通过后，才进入 P2-beta：10-15 本前 10 章快拆。
7. 保持 clean-room 写作纪律：研究样本可以拆结构，正文创作不能搬运表达。

## 工作原则

- 不把大体量小说原文直接提交进仓库。
- 研究结论必须能回到样本证据，不接受空泛“感觉很番茄”。
- 先判断平台和读者承诺，再判断设定是否好玩。
- 先跑小样本验证，再扩成系统模型。
- 所有关键判断进入 Git，方便回滚和复盘。

## 当前执行模板

- [schemas/sample_record.yaml](schemas/sample_record.yaml): L0 样本池登记模板。
- [schemas/chapter_evidence.yaml](schemas/chapter_evidence.yaml): P2 前 10 章证据快拆模板。
- [schemas/content_kernel_card.md](schemas/content_kernel_card.md): 内容内核卡模板。
- [schemas/blind_review_report.md](schemas/blind_review_report.md): 盲审 / 追读诊断报告模板。
- [schemas/risk_loop_register.md](schemas/risk_loop_register.md): 策略漏洞循环登记模板。
