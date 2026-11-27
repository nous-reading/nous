# 如是 · Nous · 发布仓库

本仓库是 **如是（Nous）的官方发布仓库**，只存放打包好的发行文件与更新说明。

- **不包含任何源代码。** 源码在私有仓库维护，不对外公开。
- 安装包、更新包、校验和与签名一律作为 **Release 资产** 上传，不进入 git 历史。
- `main` 分支只允许白名单文件；`guard` 工作流每次 push 都会检查，出现其他文件直接失败。

## 下载

最新版本：<https://github.com/nous-reading/nous/releases/latest>

| 平台 | 文件 |
|---|---|
| macOS（Apple Silicon） | `Nous-<版本>-aarch64.dmg` |
| Windows 10/11（64 位） | `Nous-<版本>-x64-setup.exe` |

也可以直接访问官网：<https://nous.hbut.site>

## 校验

- 每个 Release 附 `SHA256SUMS.txt`。
- 桌面端更新包另带 `.sig`（ed25519 / minisign 签名），由应用内置公钥校验，不通过就不启用。

## 维护约定

| 允许入库 | 说明 |
|---|---|
| `README.md`、`LICENSE` | 说明文件 |
| `.gitignore`、`.github/` | 仓库守卫 |
| `releases/` | 纯文本发行说明 |

- 二进制（`.dmg` / `.exe` / `.zip` / `.tar.gz` / `.sig`）**不要** `git add`，一律走 Release 资产；单文件超过 5 MB 也会被守卫拒绝。
- 仓库是公开的：任何提交都会永久留在历史里，所以宁可不提交，也不要用 `git rm` 事后补救。

### 分支保护

`main` 是受保护分支，规则不是建议而是硬拦：

- 禁止直接 push、禁止强制推送、禁止删除分支（管理员也不例外）。
- 任何改动都要走 PR，且必须通过 `allowlist` 检查才能合并。
- 发版不经过 `main`：用 `gh release create <tag>` 上传资产，tag 不受分支保护限制。

---

如是 · Nous —— 让 AI 陪你读懂，也帮你真正学会。

官网 <https://nous.hbut.site> · 组织 <https://github.com/nous-reading>
