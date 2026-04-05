# homebrew-monitor

用于通过 Homebrew 安装 `monitor`。

## 要求

- `macOS arm64`
- `node` 已在 `PATH` 中
- `Node.js 22.x`

## 安装

```bash
HOMEBREW_NO_AUTO_UPDATE=1 brew install ycloud-sean/monitor/monitor
```

## 升级

```bash
HOMEBREW_NO_AUTO_UPDATE=1 brew upgrade ycloud-sean/monitor/monitor
```

## 卸载

```bash
brew uninstall monitor
```

## 完全卸载

```bash
pkill -f 'monitord.js' || true
brew uninstall monitor
brew untap ycloud-sean/monitor
```

如果还想把旧 `curl` 安装残留、本地任务数据和 Cursor bridge 一并清掉，再额外执行：

```bash
rm -rf ~/.monitor/monitor-cli-task-observer
rm -f ~/.local/bin/monitor ~/.local/bin/monitord
rm -rf ~/.monitor-data
rm -rf ~/.cursor/extensions/liangxin.monitor-cursor-bridge-0.1.0
```

如果你确认 `~/.local/bin` 这一行只是 `monitor` 安装脚本加的，也可以再手动从 `~/.zshrc`、`~/.bashrc` 或 `~/.bash_profile` 里删掉：

```bash
export PATH="$HOME/.local/bin:$PATH"
```

## 说明

- tap 仓库本身只保留很小的 formula 和文档
- formula 会安装 `monitor` 和 `monitord`
- runtime 包会在安装阶段单独下载，不再随 tap 仓库一起分发
- 包内自带的是预构建运行时，不再内置 Node
- 第一次在 Cursor 中运行 `monitor codex` 或 `monitor claude` 时，会自动补装 Cursor bridge
- 如果补装时 Cursor 已经在运行，重启一次 Cursor
- 如果你之前装过旧的 `curl` 版本，`monitor 1.0.6+` 会在首次运行时自动替换旧 daemon
- 如果你不想使用 Homebrew，主仓库 README 里仍然保留 `curl` 安装脚本方式
