# 安装 ClawLink

## 快速安装

```bash
curl -fsSL https://github.com/reorc/clawlink/releases/latest/download/install.sh | sh
```

安装完成后按提示重启 shell 或 source rc 文件，然后：

```bash
clawlink install --server-url https://<your-controlplane>
clawlink start
```

## 配对方式

安装并启动 bridge 后，需要与 app 完成配对。支持两种方式：

### Bridge 主导（扫码）

bridge 端生成连接码，app 扫码或输入完成配对：

```bash
clawlink connect-code              # 生成二维码
clawlink connect-code --format json # 输出 JSON
```

### App 主导（join code）

app 端生成 join code，bridge 端输入完成配对：

```bash
clawlink join --join-code <code>
```

适用于用户不在 bridge 旁边、无法扫码的场景。

## 安装选项

```bash
# 安装到 /usr/local/bin（需要 sudo）
curl -fsSL .../scripts/install.sh | sh -s -- --global

# 安装指定版本
curl -fsSL .../scripts/install.sh | sh -s -- --version 0.1.0

# 自定义安装目录
curl -fsSL .../scripts/install.sh | sh -s -- --install-dir /opt/clawlink/bin
```

## 默认安装路径

| 文件 | 路径 |
|------|------|
| clawlink | `~/.clawlink/bin/clawlink` |
| bridge | `~/.clawlink/bin/bridge` |

使用 `--global` 时 clawlink 安装到 `/usr/local/bin/`，bridge 仍在 `~/.clawlink/bin/`。

## 卸载

```bash
# 只删除二进制，保留配置和状态
curl -fsSL https://github.com/reorc/clawlink/releases/latest/download/uninstall.sh | sh

# 删除所有（包括 ~/.clawlink 目录）
curl -fsSL https://github.com/reorc/clawlink/releases/latest/download/uninstall.sh | sh -s -- --all
```

## 环境变量

| 变量 | 说明 | 默认值 |
|------|------|--------|
| `CLAWLINK_DOWNLOAD_BASE_URL` | 覆盖下载地址 | GitLab Package Registry |
