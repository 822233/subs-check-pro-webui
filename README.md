# Subs-Check PRO WebUI（中文修复维护版）

本仓库是 [Subs-Check PRO 主项目](https://github.com/822233/subs-check-pro) 配套的 WebUI 前端修复维护仓库，基于上游 WebUI 进行必要的小范围维护。

## 本仓库修复内容

### Sub-Store 公网入口与分享链接统一

部分自建部署环境中，Sub-Store 实际公网入口与前端自动探测出的地址不同，可能导致首页入口无法正确打开，或生成的订阅分享链接仍指向旧域名。

本仓库已修复相关地址选择逻辑：

- **优先使用主程序提供的公网入口配置**：读取主程序传递的 `sub-store-public-url` 配置值。
- **首页入口与分享链接保持一致**：避免首页可以访问，但分享链接仍使用错误域名。
- **保留原有链接结构**：保留配置地址中的协议、主机、端口和路径前缀，并继续拼接 Sub-Store 原有随机访问路径及订阅路径。
- **兼容未配置的部署**：未配置或配置无效时，回退原有自动探测逻辑。
- **桌面端兼容**：Wails 桌面端仍优先使用本地地址。

> WebUI 只负责读取并使用主程序提供的公网入口，不会把任何维护者的域名、IP 或端口写死在前端代码中。

## 配置与部署

公网入口在主程序侧配置，不是在本仓库单独设置。升级主程序后，在实际使用的配置文件中设置：

```yaml
sub-store-public-url: 'http://<你的公网主机>:<端口>'
```

也可以通过环境变量设置：

```bash
SUB_STORE_PUBLIC_URL=http://<你的公网主机>:<端口>
```

配置值填写可从访问 WebUI 的设备直接访问的 Sub-Store 公网基础地址，不要填写示例占位符，也不要添加查询参数或片段。若已有同名配置项，只修改原值，不要重复添加。

**完整配置步骤、版本下载、升级和验证方法：** 请查看主项目 [README 与部署说明](https://github.com/822233/subs-check-pro)。

当前配套主程序修复版本：[v3.6.6 Release](https://github.com/822233/subs-check-pro/releases/tag/v3.6.6)。

## 原项目界面预览

![登录界面](https://github.com/sinspired/subs-check-pro/raw/main/doc/images/login.png)
![WebUI 管理界面](https://github.com/sinspired/subs-check-pro/raw/main/doc/images/WebUI.png)

# Wails v3 现代化桌面客户端

如果你更喜欢原生桌面应用程序，可以使用跨平台客户端。它提供系统级适配和现代化 GUI 交互界面。

![桌面客户端](https://github.com/sinspired/subs-check-pro/raw/main/doc/images/GUI.png)

立即体验：[subs-free 仓库](https://github.com/sinspired/subs-free)

# 检测结果分析报告

`http://localhost:8199/analysis`

![分析报告](https://github.com/sinspired/subs-check-pro/raw/main/doc/images/analysis.png)

## 交流反馈

以下为上游项目交流渠道，并非本 Fork 的专属支持渠道：

- Telegram 群组：[subs-check 性能版](https://t.me/subs_check_pro)
- Telegram 频道：[关注频道](https://t.me/sinspired_ai)
