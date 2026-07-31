# Navidrome for LazyCat

[Navidrome](https://www.navidrome.org) 的 LazyCat LPK v2 打包项目，支持多实例部署。

## 应用配置

- 包名：`community.lazycat.app.navidrome`
- 运行镜像：`docker.1ms.run/deluan/navidrome:0.63.2`
- 架构：`amd64`
- 数据目录：`/lzcapp/var/data`
- 音乐目录：安装时选择懒猫个人目录下的文件夹，默认 `Music`
- Deezer 语言：安装时配置 `ND_DEEZER_LANGUAGE`，默认 `zh`

首次启动后，在 Navidrome 自带的初始化页面创建管理员账号。本项目不在安装向导中创建或设置管理员密码，也不包含密码或文件选择注入。

## 本地构建

```bash
lzc-cli project release -o dist/application.lpk
lzc-cli lpk info dist/application.lpk
```

## 自动发布

GitHub Actions 每天检查上游稳定镜像，也可以手动触发。工作流生成带版本号的 GitHub Release LPK，并且只发布到喵喵私有应用商店；不会发布到懒猫官方商店，也不会复制运行镜像到懒猫镜像仓库。

仓库需要授权以下 GitHub Secrets：

- `APPSTORE_URL`
- `APPSTORE_TOKEN`
- `APP_ID`（可选）
- `PRIVATE_STORE_GROUP_CODES`（可选）
