# b0y1 Homebrew Tap

通过 Homebrew 安装和更新 b0y1 的 macOS 工具。

```bash
brew tap b0y1/taps
```

## 先看这里：Homebrew 7 的信任机制

Homebrew 7 起，**非官方 tap 的 formula / cask 需要先被信任**才会被加载。

用完整名字安装时 Homebrew 会自动记下信任，多数情况下你不用管这一步：

```bash
brew install --cask b0y1/taps/subetter   # 自动信任，直接可用
```

但如果你想用短名字（`brew install --cask subetter`）、或者希望 `brew outdated` / `brew upgrade`
不报信任错误，就显式信任整个 tap：

```bash
brew trust --tap b0y1/taps
```

撤销信任：

```bash
brew untrust --tap b0y1/taps
```

查看当前已信任的条目：

```bash
brew trust --json v1
```

> 如果你看到这个报错：
> `Refusing to load cask b0y1/taps/subetter from untrusted tap b0y1/taps.`
> 按提示执行 `brew trust --cask b0y1/taps/subetter` 或 `brew trust --tap b0y1/taps` 即可。

## Subetter

用影片字幕与音轨学习外语的桌面应用（Tauri 构建，macOS 15 及以上，Intel 与 Apple Silicon 通用）。

```bash
brew install --cask b0y1/taps/subetter
```

Subetter 未进行 Apple 公证（ad-hoc 签名）。cask 的 `postflight` 会在安装后自动去掉隔离标记
（等价于 `xattr -dr com.apple.quarantine /Applications/Subetter.app`），不需要你手动处理。

安装、使用、升级与卸载的完整说明，见官方发布仓库 → [b0y1/subetter-release](https://github.com/b0y1/subetter-release)

## 仓库结构

```
Casks/     Cask —— 图形界面 App（.app 包）
Formula/   Formula —— 命令行工具
```

各项目的 Cask 会随官方新版本**自动更新**。安装后，用下面的命令即可升级到最新版：

```bash
brew upgrade --cask subetter
```
