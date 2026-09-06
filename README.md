# HR Skills

一组用于HR全盘管理的工作宝藏，包括招聘、组织诊断、人力规划、绩效管理与飞书 HR 工作流的 Codex Skills。

## 收录内容

| 目录 | 用途 |
| --- | --- |
| `skills/boss-hiring-assistant` | BOSS 直聘的候选人筛选、沟通与约面流程 |
| `skills/liepin-candidate-screening` | 猎聘候选人筛选，包含上海期望工作地与去重规则 |
| `skills/match-fysik-candidates` | 将候选人简历与飞捷科思在招岗位进行匹配 |
| `skills/fysik-recruiting-screening` | 按 JD 全量筛选 BOSS 与猎聘候选人，输出可审计结论 |
| `skills/lark-offer-record-fill` | 从 Offer 审批中回填多维表格记录 |
| `skills/lark-base` | 飞书多维表格的读写、字段、视图、表单和工作流操作 |
| `skills/lark-doc` | 飞书 Docx/Wiki 文档的读取、编辑与资源处理 |
| `skills/hrd-cold-start` | 新任 HRD/HRBP 的组织尽调、关键风险识别与 30/60/90 天计划 |
| `skills/hrbp-business-diagnosis` | 从业务结果、流程与岗位证据中定位组织、管理和人员问题 |
| `skills/workforce-planning-and-cost` | 根据业务计划建立 HC、招聘、离职和人力成本的月度情景模型 |
| `skills/performance-cycle-calibration` | 设计和运行绩效周期、证据检查、校准会议与结果反馈 |
| `skills/ai-native-recruiting-onboarding` | 设计招聘需求到入职试用期的数据、自动检查与人工审批流程 |

## 配套文档

- [HRBP 全流程工作实践指南（公开整理版）](docs/hrbp-full-cycle-practice-guide.md)：涵盖业务诊断、年度规划、人力成本、绩效、组织与人才、招聘、入职、职级、薪酬、人才发展、员工沟通、文化和组织诊断。
- 附件：原文飞书链接：https://my.feishu.cn/docx/TbMmdmMZzoALY9xHq60cGdlonHg?from=from_copylink   密码：619z45&2

## 招聘筛选：`fysik-recruiting-screening`

适用于 BOSS 直聘沟通、新招呼、推荐牛人页面，以及猎聘搜索结果。使用时提供完整 JD、目标页面与硬筛条件；skill 会先将 JD 拆为硬条件、优先证据、可迁移条件和排除项，再输出按稳定 ID 去重的候选人结论。

- **结果**：候选人 ID、分类（高匹配 / 高迁移 / 待核验 / 淘汰）、事实依据、已审阅与去重数量，以及实际覆盖范围。
- **上海规则**：只认可候选人的 `期望城市` 或 `期望工作地=上海`；现居地或履历中出现上海不构成通过条件。
- **边界**：默认只读取、筛选与汇报；不会发消息、接受简历、约面或改变候选人状态。页面高亮仅在明确要求时使用，刷新后失效。

## 使用前提

- BOSS 与猎聘技能需要用户已登录对应招聘平台。
- 飞书技能依赖已完成授权的 `lark-cli`。
- 涉及候选人信息、审批和多维表格写入时，应按最小权限原则操作，并在写入后复核。

## 安全约定

仓库不包含候选人记录、个人偏好、访问令牌、真实 Base 链接或其他业务数据。`lark-offer-record-fill` 中的默认资源已替换为占位符；使用前请按自己的 Base、数据表和视图配置。

## 安装

将所需技能目录复制到 Codex Skills 目录，或按你的 Codex 环境加载对应的 `SKILL.md`。每个技能目录中都包含独立的使用说明和参考资料。
