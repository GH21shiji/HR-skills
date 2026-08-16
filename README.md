# HR Skills

一组用于招聘筛选与飞书 HR 工作流的 Codex Skills。

## 收录内容

| 目录 | 用途 |
| --- | --- |
| `skills/boss-hiring-assistant` | BOSS 直聘的候选人筛选、沟通与约面流程 |
| `skills/liepin-candidate-screening` | 猎聘候选人筛选，包含上海期望工作地与去重规则 |
| `skills/match-fysik-candidates` | 将候选人简历与飞捷科思在招岗位进行匹配 |
| `skills/lark-offer-record-fill` | 从 Offer 审批中回填多维表格记录 |
| `skills/lark-base` | 飞书多维表格的读写、字段、视图、表单和工作流操作 |
| `skills/lark-doc` | 飞书 Docx/Wiki 文档的读取、编辑与资源处理 |

## 使用前提

- BOSS 与猎聘技能需要用户已登录对应招聘平台。
- 飞书技能依赖已完成授权的 `lark-cli`。
- 涉及候选人信息、审批和多维表格写入时，应按最小权限原则操作，并在写入后复核。

## 安全约定

仓库不包含候选人记录、个人偏好、访问令牌、真实 Base 链接或其他业务数据。`lark-offer-record-fill` 中的默认资源已替换为占位符；使用前请按自己的 Base、数据表和视图配置。

## 安装

将所需技能目录复制到 Codex Skills 目录，或按你的 Codex 环境加载对应的 `SKILL.md`。每个技能目录中都包含独立的使用说明和参考资料。

