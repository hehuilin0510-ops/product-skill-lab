# Product Skill Lab

这是一个面向产品经理和活动产品工作的 Codex Skill 项目。目前公开两套可以直接安装使用的工作流：

- **活动原型生成**：把活动方案、规则、脑图和参考图整理成完整的页面与状态原型。
- **原型驱动 PRD**：根据最新原型、脑图或规则变更，生成或更新可开发、可回读的中文 PRD。

在线介绍与下载：[Product Skill Lab](https://hehuilin0510-ops.github.io/product-skill-lab/)

## 这两套 Skill 解决什么问题

复杂活动通常不是“画一张页面”或“写一段需求”就能完成。真正困难的是：

- 页面、弹窗、榜单、阶段和异常状态容易遗漏。
- 原型、脑图、旧 PRD 和最新口径之间可能互相冲突。
- 展示逻辑、交互逻辑、数据口径和后台配置容易混写。
- 没有依据的规则容易被误补成正式需求。
- 修改完成后缺少回读，旧文案、旧截图和旧版本记录可能残留。

这两套 Skill 把工作拆成一条连续交付链路：

```text
活动方案 / 规则 / 脑图 / 参考图
                ↓
      完整页面与状态原型
                ↓
       原型证据与规则核对
                ↓
       可开发、可追溯的 PRD
```

## Skill 01：活动原型生成

Skill 名称：`activity-prototype-image2-workflow`

适用于根据活动方案、脑图或参考图，生成一整套低保真活动原型，而不是只生成单张示意图。

主要能力：

1. 读取活动方案、规则、脑图和参考图。
2. 先列出完整的页面与状态蓝图。
3. 在批量生成前确认页面结构和状态范围。
4. 按页面、弹窗和状态逐张生成原型。
5. 检查画布裁切、模块缺失、中文文案和状态完整性。
6. 输出单页图片、总览大画板和可交接目录。

适合场景：

- 活动主会场与子玩法原型
- 榜单、奖励预览、规则说明和历史记录
- 未开始、进行中、已结束、已参与、未参与等状态
- 需要先用低保真原型确认结构的复杂活动

## Skill 02：原型驱动 PRD

Skill 名称：`update-prd-from-prototype`

适用于根据最新原型、Axure/Figma 导出、脑图或规则调整，创建、补充或修改中文 PRD。

主要能力：

1. 读取最新 PRD、原型和规则证据。
2. 建立内部证据映射，只写有当前依据的正式需求。
3. 保留 `需求模块 / 原型截图 / 需求描述` 三列交付结构。
4. 动态编写展示逻辑、交互逻辑和必要的数据口径。
5. 将发奖、结算与后台配置放回对应模块，避免前后台规则混写。
6. 对资格、计分、时间、奖励、库存、结算和交互归属等缺失规则执行“先询问再写”。
7. 更新后回读目标内容，检查旧口径、旧截图、版本记录和图片数量。

活动类 PRD 还会遵循以下结构：

```text
活动基础信息
活动对象
背景
思维导图
原型图
需求详情（三列表格）
```

其中活动对象、全局黑名单和版本限制属于文档级基础信息，不会重复塞进三列表格或后台配置行。

## 最新更新

### v1.2.0 · 2026-08-10

本次强化 `update-prd-from-prototype`：

- 活动对象、黑名单与版本限制独立成文档级信息。
- 新增免费权益的防刷确认门槛。
- 统一确认外部活动联动、活动进度聚合、启动页和首页 Banner 接入情况。
- 强化活动礼物全渠道计分默认和角色归属确认。
- 完整度清单仅用于内部检查，不自动生成未经确认的业务规则。
- 下载包新增活动 PRD 文档结构参考。

完整历史记录请查看：[Releases](https://github.com/hehuilin0510-ops/product-skill-lab/releases)

## 安装方式

1. 在 [Releases](https://github.com/hehuilin0510-ops/product-skill-lab/releases/latest) 下载对应 ZIP。
2. 解压后，将完整 Skill 文件夹放入：

```text
~/.codex/skills/
```

3. 重新打开 Codex，或开始一个新任务使用对应 Skill。

安装后的目录示例：

```text
~/.codex/skills/
├── activity-prototype-image2-workflow/
└── update-prd-from-prototype/
```

## 使用示例

活动原型生成：

```text
用 activity-prototype-image2-workflow，根据这份活动方案生成完整活动原型。
```

原型驱动 PRD：

```text
用 update-prd-from-prototype，根据这版原型更新 PRD，只改目标模块并输出新版本。
```

也可以直接补充限制范围：

```text
根据最新原型更新 PRD，只修改榜单奖励弹窗，不改后台配置和其他模块。
```

## 下载与在线查看

| Skill | 在线说明 | 下载 |
|---|---|---|
| 活动原型生成 | [查看 SKILL.md](./activity-prototype-image2-workflow-SKILL.md) | [下载最新版](https://github.com/hehuilin0510-ops/product-skill-lab/releases/latest) |
| 原型驱动 PRD | [查看 SKILL.md](./update-prd-from-prototype-SKILL.md) | [下载最新版](https://github.com/hehuilin0510-ops/product-skill-lab/releases/latest) |

## 使用原则

- 以用户明确确认和最新材料为准。
- 先确认页面、状态和规则边界，再批量生成或修改。
- 不用旧参考文件自动补写当前活动规则。
- 只修改明确指定的范围，保留非目标结构和内容。
- 每次交付都进行回读和结构检查。
- PRD 初稿完成后，再由使用者决定是否启动额外需求走查。

## 版本与更新

每次 Skill 更新都会同步：

- 网站上的 `NEW` 标签、版本号和更新时间
- 中文更新记录
- 仓库中的公开 `SKILL.md`
- GitHub Release 下载包
- Release 更新说明

这样使用者可以清楚知道 Skill 更新了什么，以及当前下载的是哪个版本。
