# Debian 13 一键 DD/重装

这是一个只为服务器安装 Debian 13 保留的精简版本，基于 [bin456789/reinstall](https://github.com/bin456789/reinstall) 修改。

## 功能

- Debian 13 普通安装和 minimal 精简安装
- x86_64/ARM64、BIOS/UEFI
- DHCP/静态 IPv4、IPv6
- 密码或 SSH 公钥登录
- 自定义目标磁盘、SSH 端口和内核

> 警告：重装会清空目标磁盘的全部数据，请先备份。

## 使用

```bash
curl -O https://raw.githubusercontent.com/zhangx16/dd-debian13-minimal/main/reinstall.sh
bash reinstall.sh
```

Debian 13 已是唯一默认系统，也可以显式指定：

```bash
bash reinstall.sh debian 13
```

### Minimal 安装

Minimal 模式不安装 `standard` task 和 Recommends 推荐包，只额外保留 OpenSSH 和 sudo。

```bash
bash reinstall.sh --minimal
```

### 常用示例

```bash
bash reinstall.sh --minimal --password 'your-password'
bash reinstall.sh --minimal --ssh-key 'ssh-ed25519 AAAA...'
bash reinstall.sh --minimal --target-disk /dev/vda --ssh-port 2222
bash reinstall.sh --ci
```

如果没有传入用户名或密码，脚本会交互式询问。默认用户为 `root`。

## 主要参数

| 参数 | 说明 |
| --- | --- |
| `--minimal` | 安装 Debian 13 精简系统 |
| `--ci` | 使用 Debian 13 官方云镜像 |
| `--installer` | 强制使用 Debian Installer |
| `--username USER` | 设置登录用户 |
| `--password PASS` | 设置登录密码 |
| `--ssh-key KEY` | 设置 SSH 公钥或公钥文件 |
| `--ssh-port PORT` | 设置 SSH 端口 |
| `--target-disk DISK` | 设置目标磁盘 |
| `--no-cloud-kernel` | 使用 Debian 通用内核 |
| `--hold 1` | 进入安装环境后暂停 |
| `--hold 2` | 安装完成后不自动重启 |

## 系统要求

- root 权限和 Bash
- 至少 256 MB 内存
- 不支持 Secure Boot
- 目标机器可访问 Debian 镜像站和本 GitHub 仓库

## 许可证

本项目继承上游项目的 [GNU AGPLv3](LICENSE) 许可证。
