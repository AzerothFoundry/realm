# Realm

**让 AI Bot 持续生活，让人类自由参与。**

我们希望构建一个由 AI Bot 持续参与、人类可以进入并共同冒险的 WoW 1.12.1 世界。`realm` 是这套项目的组合部署入口：定制 vMaNGOS、账号管理网页和插件套件。

当前 Bot 由服务端规则、状态机和场景协作驱动；大模型、强化学习和完整世界自治属于后续探索，尚未实现。现有基础与扩展缺口见 [AI 架构评估](docs/AI-ARCHITECTURE.md)。

## 当前状态

这是源码导入候选，尚未发布服务端镜像或完整客户端/插件体验包。不能把克隆本仓库视为已经完成一键部署。第一批发行目标为 Linux amd64/arm64 服务端镜像及 macOS ARM64、Windows x64 客户端程序包；各平台运行验收完成后才标为支持。

## 项目

源码候选在下列链接指定的分支。三个上游 fork 的默认分支保留上游内容；定制代码尚未合入默认分支或向上游提交 PR。

| 仓库 | 职责 |
| --- | --- |
| [vmangos-core](https://github.com/AzerothFoundry/vmangos-core/tree/feat/realm-integration) | 上游 vmangos/core 的正式 fork，服务端及 Bot 功能 |
| [realm-admin](https://github.com/AzerothFoundry/realm-admin) | 容器化账号注册、账号信息、密码和九项参数管理 |
| [realm-agent](https://github.com/AzerothFoundry/realm-agent) | 无界面原生客户端：状态／WS、任务控制与城市切磋首版 |
| [addons](https://github.com/AzerothFoundry/addons) | 四个自研插件及第三方插件版本清单 |
| [AutoQuest](https://github.com/AzerothFoundry/AutoQuest/tree/feat/vanilla-compat-options) | 上游 Nelkel9023/AutoQuest 的正式 fork，兼容与选项修复 |
| [benilla](https://github.com/AzerothFoundry/benilla/tree/feat/realm-client-compat) | 通用 1.12.1 客户端 fork，独立于服务端功能 |

内部环境运维信息留在私有 realm-ops。用户部署不需要克隆这些源码子项目，也不使用嵌套 submodule；正式发行通过镜像和插件 ZIP 获取组件。

## 安装与发行边界

- 当前只提供源码入口和已有组件的构建说明；统一 Compose、初始化向导及镜像发行尚待完成。
- 管理网页参考 realm-admin 的说明，依赖已有 vMaNGOS、数据库和本机 SOAP。
- 客户端参考 benilla README；玩家自行提供合法取得的 1.12.1 数据。发行包不包含 MPQ、字体、地图或其他游戏素材。
- 数据库使用上游所需的现有结构；定制功能和管理界面不新增、删除或修改表、字段、索引，也不引入额外数据库。
- 发布锁文件见 versions.json。只有验证通过的组合才进入正式发行；不依赖浮动 latest。

## 文档

- [法师九职业对战矩阵：来源、行为和未覆盖项](https://github.com/AzerothFoundry/realm-agent/blob/main/docs/MAGE-MATRIX.md)

- [无界面客户端运行与在线验证](https://github.com/AzerothFoundry/realm-agent/blob/main/docs/VALIDATION.md)

- [奥山对象数量实测：出生区样本](docs/measurements/AV-OBJECTS-2026-11-09.md)

- [AI Bot 世界：现状与架构演进建议](docs/AI-ARCHITECTURE.md)
- [可编辑决策框架：配置、离线试算与接口](https://github.com/AzerothFoundry/vmangos-core/blob/feat/realm-integration/docs/ai/DECISION-FRAMEWORK.md)
- [兼容性边界](docs/COMPATIBILITY.md)
- [发布与贡献](docs/RELEASING.md)
- [首批交付清单](docs/ROADMAP.md)
