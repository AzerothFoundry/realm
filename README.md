# Realm

面向 WoW 1.12.1 的组合部署入口：定制 vMaNGOS、账号管理网页和插件套件。

## 当前状态

这是源码导入候选，尚未发布服务端镜像或完整客户端/插件体验包。不能把克隆本仓库视为已经完成一键部署。第一批发行目标为 Linux amd64/arm64 服务端镜像及 macOS ARM64、Windows x64 客户端程序包；各平台运行验收完成后才标为支持。

## 项目

| 仓库 | 职责 |
| --- | --- |
| vmangos-core | 上游 vmangos/core 的正式 fork，服务端及 Bot 功能 |
| realm-admin | 容器化账号注册、账号信息、密码和九项参数管理 |
| addons | 四个自研插件及第三方插件版本清单 |
| AutoQuest | 上游 Nelkel9023/AutoQuest 的正式 fork，兼容与选项修复 |
| benilla | 通用 1.12.1 客户端 fork，独立于服务端功能 |

内部环境运维信息留在私有 realm-ops。用户部署不需要克隆这些源码子项目，也不使用嵌套 submodule；正式发行通过镜像和插件 ZIP 获取组件。

## 安装与发行边界

- 当前只提供源码入口和已有组件的构建说明；统一 Compose、初始化向导及镜像发行尚待完成。
- 管理网页参考 realm-admin 的说明，依赖已有 vMaNGOS、数据库和本机 SOAP。
- 客户端参考 benilla README；玩家自行提供合法取得的 1.12.1 数据。发行包不包含 MPQ、字体、地图或其他游戏素材。
- 数据库使用上游所需的现有结构；定制功能和管理界面不新增、删除或修改表、字段、索引，也不引入额外数据库。
- 发布锁文件见 versions.json。只有验证通过的组合才进入正式发行；不依赖浮动 latest。

## 文档

- [兼容性边界](docs/COMPATIBILITY.md)
- [发布与贡献](docs/RELEASING.md)
- [首批交付清单](docs/ROADMAP.md)
