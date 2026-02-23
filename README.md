# 🤖⚡ Ｖ Ｉ Ｂ Ｅ  Ｌ Ｏ Ｃ Ａ Ｌ ⚡🤖

```
    ██╗   ██╗██╗██████╗ ███████╗
    ██║   ██║██║██╔══██╗██╔════╝
    ██║   ██║██║██████╔╝█████╗
    ╚██╗ ██╔╝██║██╔══██╗██╔══╝
     ╚████╔╝ ██║██████╔╝███████╗
      ╚═══╝  ╚═╝╚═════╝ ╚══════╝
              ██╗      ██████╗  ██████╗ █████╗ ██╗
              ██║     ██╔═══██╗██╔════╝██╔══██╗██║
              ██║     ██║   ██║██║     ███████║██║
              ██║     ██║   ██║██║     ██╔══██║██║
              ███████╗╚██████╔╝╚██████╗██║  ██║███████╗
              ╚══════╝ ╚═════╝  ╚═════╝╚═╝  ╚═╝╚══════╝
```

> 🌴✨ **Free AI Coding Environment** ✨🌴
>
> No network. No cost. Local LLM agent coding.

**🇯🇵** オフラインのワークショップでAIエージェントを使って学習者をサポートしたり、有料プランに未加入の学生がエージェントコーディングを練習したり、ネットワークのない環境で自然言語を使ってターミナル操作を学んだり――そんな場面を想定した、非営利の研究・教育目的のユーティリティツールです。

**🌱** やさしい にほんご：これは、むりょう（おかね いらない）で、AI（えーあい）に プログラムを かいて もらう ための どうぐ です。インターネットが なくても つかえます。がっこう や ワークショップで つかう ために つくりました。

**🇺🇸** Built for offline workshops where instructors support learners with AI agents, for students without paid plans who want to practice agent coding, and for beginners learning terminal operations through natural language — a non-profit research and education utility.

**🇨🇳** 面向离线工作坊中使用AI代理辅助学习者、未订阅付费计划的学生练习代理编程、以及初学者通过自然语言学习终端操作等场景，这是一个非营利性的研究与教育实用工具。

---

## 🇯🇵 日本語 | [🌱 やさしい日本語](#-やさしい-にほんご) | [🇺🇸 English](#-english) | [🇨🇳 中文](#-中文)

### これは何？

MacやWindows、LinuxにコマンドをコピペするだけでAIがコードを書いてくれる環境。
ネットワーク不要・完全無料。Python + Ollama だけで動く完全OSSのコーディングエージェント。

**v0.9.0 (vibe-coder)**: Claude Code CLI不要。Python + Ollama だけでOK。
```
vibe-local → vibe-coder.py (OSS) → Ollama (直接通信)
```
ログイン不要・Node.js不要・プロキシプロセス不要。15個の内蔵ツール、サブエージェント、画像・PDF読み取り対応。

### インストール (3ステップ)

**1.** ターミナルを開く（Mac: Spotlight `Cmd+Space` → "ターミナル"で検索 / Windows: PowerShellを開く）

**2.** 以下をコピペしてEnter:

*Mac / Linux / Windows(WSL) の場合:*
```bash
curl -fsSL https://raw.githubusercontent.com/ochyai/vibe-local/main/install.sh | bash
```

*Windows (PowerShell) の場合:*
```powershell
Invoke-WebRequest -Uri https://raw.githubusercontent.com/ochyai/vibe-local/main/install.ps1 -UseBasicParsing | Invoke-Expression
```

**3.** 新しいターミナルを開いて起動:

```bash
vibe-local
```

### 使い方

```bash
# 対話モード（AIと会話しながらコーディング）
vibe-local

# ワンショット（1回だけ質問）
vibe-local -p "Pythonでじゃんけんゲーム作って"

# ネットワーク自動判定（ネットがあればClaude API、なければローカル）
vibe-local --auto

# モデルを手動指定
vibe-local --model qwen3:8b
```

### 対応環境

| 環境 | メモリ | メインモデル | サイドカー | 備考 |
|------|--------|-------------|-----------|------|
| Apple Silicon Mac (M1以降) | 32GB+ | qwen3-coder:30b | qwen3:8b | 🏆 **推奨** |
| Apple Silicon Mac (M1以降) | 16GB | qwen3:8b | qwen3:1.7b | ⭐ 十分実用的 |
| Apple Silicon Mac (M1以降) | 8GB | qwen3:1.7b | なし | 最低限動作 |
| Intel Mac | 16GB+ | qwen3:8b | qwen3:1.7b | 動作するが遅め |
| Windows (ネイティブ) | 16GB+ | qwen3:8b | qwen3:1.7b | NVIDIA GPU推奨 |
| Windows (WSL2) | 16GB+ | qwen3:8b | qwen3:1.7b | NVIDIA GPU推奨 |
| Linux (x86_64/arm64) | 16GB+ | qwen3:8b | qwen3:1.7b | NVIDIA GPU推奨 |

> サイドカーモデル = 権限チェックや初期化プローブなど軽量タスク用。自動選択されます。

### トラブルシューティング

<details>
<summary>💡 よくある問題と解決法</summary>

**"ollama が起動できませんでした"**
```bash
open -a Ollama        # macOS
ollama serve          # Linux / Windows
```

**"モデルが見つかりません"**
```bash
ollama pull qwen3:8b
```

**"vibe-coder.py が見つかりません"**
```bash
# 再インストール
curl -fsSL https://raw.githubusercontent.com/ochyai/vibe-local/main/install.sh | bash
```

**モデルを変更したい**
```bash
nano ~/.config/vibe-local/config
# MODEL="qwen3:8b" を変更
# SIDECAR_MODEL="qwen3:1.7b"  # 軽量タスク用（省略可・自動選択）
```

**デバッグログを確認したい**
```bash
VIBE_LOCAL_DEBUG=1 vibe-local
# ログにモデルルーティング情報（sidecar/main）が表示されます
```

</details>

---

## 🌱 やさしい にほんご

### これは なに？

Mac（まっく）や Windows（ういんどうず）で、AI（えーあい）が コードを かいて くれる どうぐ です。
インターネットが なくても つかえます。おかねも かかりません。

### いれかた（3つの ステップ）

**1.** ターミナルを ひらく（Mac: `Cmd+Space` → 「ターミナル」 / Windows: PowerShellを ひらく）

**2.** したの もじを コピーして、はりつけて、Enterを おす：

*Mac / Linux / Windows(WSL) のとき:*
```bash
curl -fsSL https://raw.githubusercontent.com/ochyai/vibe-local/main/install.sh | bash
```

*Windows (PowerShell) のとき:*
```powershell
Invoke-WebRequest -Uri https://raw.githubusercontent.com/ochyai/vibe-local/main/install.ps1 -UseBasicParsing | Invoke-Expression
```

**3.** あたらしい ターミナルを ひらいて、これを うつ：

```bash
vibe-local
```

### つかいかた

```bash
# AIと はなしながら プログラムを つくる
vibe-local

# 1かいだけ しつもんする
vibe-local -p "Pythonで じゃんけんゲームを つくって"
```

### たいわ コマンド（はなしている ときに つかえる めいれい）

| コマンド | なにを する？ |
|---|---|
| `/help` | つかえる コマンドを みる |
| `/exit` または `/quit` | おわる（セッションを ほぞんする） |
| `/clear` | かいわを けす |
| `/model <なまえ>` | モデルを かえる |
| `/status` | いまの じょうほうを みる |
| `/save` | セッションを ほぞんする |
| `/compact` | かいわを みじかくする（メモリ せつやく） |
| `/yes` | じどう きょか モード オン |
| `"""` | ながい ぶんしょうを にゅうりょく する |
| `Ctrl+C` | とめる / おわる |

### きをつけること

> **⚠️ だいじ：AIが あぶない コマンドを うつことが あります！**

AIは かんぺきでは ありません。まちがった コマンドを うつことが あります。

**きけんな サイン — こんな コマンドは ゆるさないで！**

| きけんな キーワード | なぜ あぶない？ |
|---|---|
| `sudo` で はじまる | パソコンの だいじな せっていが かわる |
| `chmod` が はいっている | ファイルの まもりが なくなる |
| いみが わからない ながい コマンド | なにが おきるか わからない！ |

**あんぜんに つかう ほうほう：**

- はじめて つかうときは、しつもんに **`n`** を おして ください（あんぜんモード）
- AIが コマンドを うつまえに、「これを うっていい？」と きいてきます
- わからない コマンドは **ぜったいに ゆるさないで ください**
- だいじな ファイルが ある フォルダでは つかわないで ください
- こまったら、`Ctrl+C` で とめられます

---

## 🇺🇸 English

### What is this?

A free AI coding environment you can set up with a single command on your Mac, Windows, or Linux.
No network required. Completely free. Python + Ollama only — a fully open-source coding agent.

**v0.9.0 (vibe-coder)**: No Claude Code CLI needed. Just Python + Ollama.
```
vibe-local → vibe-coder.py (OSS) → Ollama (direct)
```
No login. No Node.js. No proxy process. 15 built-in tools, sub-agents, image reading.

### Install (3 steps)

**1.** Open Terminal (Mac: Spotlight `Cmd+Space` → search "Terminal" / Windows: Open PowerShell)

**2.** Paste and hit Enter:

*For Mac / Linux / Windows(WSL):*
```bash
curl -fsSL https://raw.githubusercontent.com/ochyai/vibe-local/main/install.sh | bash
```

*For Windows (PowerShell natively):*
```powershell
Invoke-WebRequest -Uri https://raw.githubusercontent.com/ochyai/vibe-local/main/install.ps1 -UseBasicParsing | Invoke-Expression
```

**3.** Open a new terminal and run:

```bash
vibe-local
```

### Usage

```bash
# Interactive mode (chat with AI while coding)
vibe-local

# One-shot (ask once)
vibe-local -p "Create a snake game in Python"

# Auto-detect network (uses Claude API if online, local if offline)
vibe-local --auto

# Specify model manually
vibe-local --model qwen3:8b
```

### Supported Environments

| Environment | RAM | Main Model | Sidecar | Notes |
|-------------|-----|------------|---------|-------|
| Apple Silicon Mac (M1+) | 32GB+ | qwen3-coder:30b | qwen3:8b | 🏆 **Recommended** |
| Apple Silicon Mac (M1+) | 16GB | qwen3:8b | qwen3:1.7b | ⭐ Very capable |
| Apple Silicon Mac (M1+) | 8GB | qwen3:1.7b | none | Minimum viable |
| Intel Mac | 16GB+ | qwen3:8b | qwen3:1.7b | Works but slower |
| Windows (Native) | 16GB+ | qwen3:8b | qwen3:1.7b | NVIDIA GPU recommended |
| Windows (WSL2) | 16GB+ | qwen3:8b | qwen3:1.7b | NVIDIA GPU recommended |
| Linux (x86_64/arm64) | 16GB+ | qwen3:8b | qwen3:1.7b | NVIDIA GPU recommended |

> Sidecar model = auto-selected lighter model for permission checks, init probes, and short summaries.

### Troubleshooting

<details>
<summary>💡 Common issues and solutions</summary>

**"ollama failed to start"**
```bash
open -a Ollama        # macOS
ollama serve          # Linux / Windows
```

**"model not found"**
```bash
ollama pull qwen3:8b
```

**"vibe-coder.py not found"**
```bash
# Reinstall
curl -fsSL https://raw.githubusercontent.com/ochyai/vibe-local/main/install.sh | bash
```

**Change model**
```bash
nano ~/.config/vibe-local/config
# Change MODEL="qwen3:8b"
# SIDECAR_MODEL="qwen3:1.7b"  # For lightweight tasks (optional, auto-selected)
```

**Enable debug logging**
```bash
VIBE_LOCAL_DEBUG=1 vibe-local
# Logs show model routing info — which requests go to main vs sidecar
```

</details>

---

## 🇨🇳 中文

### 这是什么？

在Mac、Windows 或 Linux上只需复制粘贴一个命令，AI就能帮你写代码。
无需网络，完全免费。Python + Ollama 打造的完全开源编程代理。

**v0.9.0 (vibe-coder)**: 不需要 Claude Code CLI。只需 Python + Ollama。
```
vibe-local → vibe-coder.py (开源) → Ollama (直接通信)
```
无需登录、无需Node.js、无需代理进程。15个内置工具、子代理、图像/PDF读取支持。

### 安装（3步）

**1.** 打开终端（Mac: Spotlight `Cmd+Space` → 搜索"终端" / Windows: 打开 PowerShell）

**2.** 粘贴以下命令并按回车：

*Mac / Linux / Windows(WSL) 环境:*
```bash
curl -fsSL https://raw.githubusercontent.com/ochyai/vibe-local/main/install.sh | bash
```

*Windows (PowerShell) 环境:*
```powershell
Invoke-WebRequest -Uri https://raw.githubusercontent.com/ochyai/vibe-local/main/install.ps1 -UseBasicParsing | Invoke-Expression
```

**3.** 打开新终端并运行：

```bash
vibe-local
```

### 使用方法

```bash
# 交互模式（与AI对话编程）
vibe-local

# 单次执行（只问一次）
vibe-local -p "用Python写一个贪吃蛇游戏"

# 自动检测网络（有网用Claude API，没网用本地）
vibe-local --auto

# 手动指定模型
vibe-local --model qwen3:8b
```

### 支持的环境

| 环境 | 内存 | 主模型 | 边车模型 | 备注 |
|------|------|--------|---------|------|
| Apple Silicon Mac (M1及以上) | 32GB+ | qwen3-coder:30b | qwen3:8b | 🏆 **推荐** |
| Apple Silicon Mac (M1及以上) | 16GB | qwen3:8b | qwen3:1.7b | ⭐ 足够实用 |
| Apple Silicon Mac (M1及以上) | 8GB | qwen3:1.7b | 无 | 最低限运行 |
| Intel Mac | 16GB+ | qwen3:8b | qwen3:1.7b | 可运行但较慢 |
| Windows (原生) | 16GB+ | qwen3:8b | qwen3:1.7b | 推荐NVIDIA GPU |
| Windows (WSL2) | 16GB+ | qwen3:8b | qwen3:1.7b | 推荐NVIDIA GPU |
| Linux (x86_64/arm64) | 16GB+ | qwen3:8b | qwen3:1.7b | 推荐NVIDIA GPU |

> 边车模型 = 用于权限检查、初始化探测等轻量任务的自动选择的较小模型。

### 故障排除

<details>
<summary>💡 常见问题及解决方法</summary>

**"ollama 无法启动"**
```bash
open -a Ollama        # macOS
ollama serve          # Linux / Windows
```

**"未找到模型"**
```bash
ollama pull qwen3:8b
```

**"vibe-coder.py 未找到"**
```bash
# 重新安装
curl -fsSL https://raw.githubusercontent.com/ochyai/vibe-local/main/install.sh | bash
```

**更换模型**
```bash
nano ~/.config/vibe-local/config
# 修改 MODEL="qwen3:8b"
# SIDECAR_MODEL="qwen3:1.7b"  # 轻量任务用（可选，自动选择）
```

**启用调试日志**
```bash
VIBE_LOCAL_DEBUG=1 vibe-local
# 日志会显示模型路由信息（主模型/边车模型）
```

</details>

---

## 🔧 Architecture (v0.9.0 — vibe-coder)

```
┌─────────────────────────────────────────────────────────┐
│  User                                                   │
│  └─> vibe-local.sh / vibe-local.ps1 (launch script)     │
│       ├─ Ensure Ollama is running                       │
│       └─ Launch vibe-coder.py (direct, no proxy)        │
└──────────────────────┬──────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────┐
│  vibe-coder.py  (single-file, Python stdlib only)       │
│  ┌────────────────────────────────────────────────────┐ │
│  │ Agent Loop (parallel tool execution)               │ │
│  │    User input → LLM → Tool calls → Execute →      │ │
│  │    Add results → Loop until done                   │ │
│  ├────────────────────────────────────────────────────┤ │
│  │ 15 Built-in Tools                                  │ │
│  │    Bash (+ background), Read (+ images/PDF/ipynb), │ │
│  │    Write, Edit (+ rich diff), Glob, Grep,          │ │
│  │    WebFetch, WebSearch, NotebookEdit, SubAgent,    │ │
│  │    TaskCreate/List/Get/Update, AskUserQuestion     │ │
│  ├────────────────────────────────────────────────────┤ │
│  │ System Prompt + OS-Specific Hints                  │ │
│  │    macOS: brew, /Users/, system_profiler            │ │
│  │    Linux: apt, /home/                              │ │
│  │    Windows: winget, %USERPROFILE%                  │ │
│  ├────────────────────────────────────────────────────┤ │
│  │ XML Tool Call Fallback (Qwen model compat)         │ │
│  │ Permission Manager (safe/ask/deny tiers)           │ │
│  │ Session Persistence (JSONL) + Context Compaction   │ │
│  │ TUI (readline, ANSI colors, markdown rendering)    │ │
│  │ Multimodal (image base64 → Ollama vision models)  │ │
│  └────────────────────┬───────────────────────────────┘ │
└───────────────────────┼─────────────────────────────────┘
                        │  OpenAI Chat API (/v1/chat/completions)
                        ▼
┌─────────────────────────────────────────────────────────┐
│  Ollama (localhost:11434)                               │
│  Local LLM inference runtime                            │
│  qwen3-coder:30b / qwen3:8b / qwen3:1.7b               │
└─────────────────────────────────────────────────────────┘
```

### Key difference from v0.2

| | v0.2 (proxy) | v0.9.0 (vibe-coder) |
|---|---|---|
| Engine | Claude Code CLI + proxy.py | vibe-coder.py (direct) |
| Dependencies | Node.js + Python + Ollama | Python + Ollama only |
| Processes | 3 (claude + proxy + ollama) | 2 (vibe-coder + ollama) |
| Login required | Yes (Anthropic account) | No |
| Fully OSS | No (Claude Code is proprietary) | Yes |
| Tools | 9 | 15 (+ sub-agents, images, PDF, background) |
| Tests | 0 | 500 |

---

## 🖥️ CLI Reference / CLIリファレンス / CLI参考

### CLI Flags / コマンドラインフラグ

| Flag | Short | Description (EN) | 説明 (JP) | 说明 (CN) |
|------|-------|------------------|-----------|-----------|
| `--prompt` | `-p` | One-shot prompt (non-interactive) | ワンショットプロンプト（非対話モード） | 单次提示（非交互模式） |
| `--model` | `-m` | Specify Ollama model name | Ollamaモデル名を指定 | 指定Ollama模型名称 |
| `--yes` | `-y` | Auto-approve all tool calls | 全ツール呼び出しを自動許可 | 自动批准所有工具调用 |
| `--debug` | | Enable debug logging | デバッグログを有効化 | 启用调试日志 |
| `--resume` | | Resume last session | 最後のセッションを再開 | 恢复上一个会话 |
| `--session-id <id>` | | Resume a specific session by ID | 指定IDのセッションを再開 | 通过ID恢复特定会话 |
| `--list-sessions` | | List all saved sessions | 保存済みセッション一覧を表示 | 列出所有已保存的会话 |
| `--ollama-host <url>` | | Ollama API endpoint URL | Ollama APIのエンドポイントURL | Ollama API端点URL |
| `--max-tokens <n>` | | Max output tokens (default: 8192) | 最大出力トークン数（デフォルト: 8192） | 最大输出令牌数（默认: 8192） |
| `--temperature <f>` | | Sampling temperature (default: 0.7) | サンプリング温度（デフォルト: 0.7） | 采样温度（默认: 0.7） |
| `--context-window <n>` | | Context window size (default: 32768) | コンテキストウィンドウサイズ（デフォルト: 32768） | 上下文窗口大小（默认: 32768） |
| `--version` | | Show version and exit | バージョンを表示して終了 | 显示版本并退出 |
| `--dangerously-skip-permissions` | | Alias for `-y` (compatibility) | `-y`のエイリアス（互換性用） | `-y`的别名（兼容性用途） |

### Examples / 使用例 / 使用示例

```bash
# Interactive mode / 対話モード / 交互模式
vibe-local

# One-shot prompt / ワンショット / 单次执行
vibe-local -p "Create a snake game in Python"

# Specify model / モデル指定 / 指定模型
vibe-local -m qwen3:8b

# Auto-approve mode / 自動許可 / 自动批准
vibe-local -y

# Resume last session / セッション再開 / 恢复会话
vibe-local --resume

# Resume specific session / 特定セッション再開 / 恢复特定会话
vibe-local --session-id 20240101_120000_abc123

# List sessions / セッション一覧 / 列出会话
vibe-local --list-sessions

# Custom Ollama host / Ollamaホスト指定 / 自定义Ollama地址
vibe-local --ollama-host http://localhost:11434

# Debug mode / デバッグモード / 调试模式
vibe-local --debug

# Adjust generation parameters / 生成パラメータ調整 / 调整生成参数
vibe-local --max-tokens 4096 --temperature 0.5 --context-window 65536
```

---

## ⌨️ Interactive Commands / 対話コマンド / 交互命令

**🇯🇵** 対話モード中に使えるスラッシュコマンド：

**🇺🇸** Slash commands available during interactive mode:

**🇨🇳** 交互模式中可用的斜杠命令：

| Command | Description (EN) | 説明 (JP) | 说明 (CN) |
|---------|------------------|-----------|-----------|
| `/help` | Show available commands | 使えるコマンド一覧を表示 | 显示可用命令 |
| `/exit`, `/quit`, `/q` | Exit (session is auto-saved) | 終了（セッション自動保存） | 退出（会话自动保存） |
| `/clear` | Clear conversation history | 会話履歴をクリア | 清除对话历史 |
| `/model <name>` | Switch to a different model | 別のモデルに切り替え | 切换到其他模型 |
| `/status` | Show session info (tokens, model, CWD) | セッション情報を表示（トークン数、モデル、CWD） | 显示会话信息（令牌数、模型、CWD） |
| `/save` | Save current session | 現在のセッションを保存 | 保存当前会话 |
| `/compact` | Compress conversation history (reduce tokens) | 会話履歴を圧縮（トークン削減） | 压缩对话历史（减少令牌） |
| `/tokens` | Show detailed token usage | トークン使用量の詳細表示 | 显示详细令牌使用情况 |
| `/undo` | Undo last file write/edit | 最後のファイル書き込み/編集を元に戻す | 撤销上次文件写入/编辑 |
| `/config` | Show current configuration | 現在の設定を表示 | 显示当前配置 |
| `/commit` | Stage and commit with git | gitでステージ＆コミット | 使用git暂存并提交 |
| `/diff` | Show git diff | git diffを表示 | 显示git diff |
| `/git <cmd>` | Run git subcommand | gitサブコマンドを実行 | 运行git子命令 |
| `/plan` | Enter plan mode (read-only tools) | プランモード（読み取り専用ツール） | 进入计划模式（只读工具） |
| `/execute` | Exit plan mode and execute | プランモード終了＆実行 | 退出计划模式并执行 |
| `/init` | Create CLAUDE.md project file | CLAUDE.mdプロジェクトファイルを作成 | 创建CLAUDE.md项目文件 |
| `/yes` | Enable auto-approve mode for this session | このセッションの自動許可モードをON | 启用本会话自动批准模式 |
| `exit`, `quit`, `bye` | Exit (also accepts `exit;`, `quit;`, `bye;`) | 終了（`exit;`, `quit;`, `bye;`も可） | 退出（也接受`exit;`, `quit;`, `bye;`） |
| `"""` | Enter multi-line input mode | 複数行入力モード | 进入多行输入模式 |
| `Ctrl+C` | Stop current action (double-tap to exit) | 現在の操作を停止（2回で終了） | 停止当前操作（连按两次退出） |

---

## ⚙️ Configuration / 設定 / 配置

### Config File / 設定ファイル / 配置文件

```bash
~/.config/vibe-local/config       # Also read by vibe-coder.py
~/.config/vibe-coder/config       # vibe-coder.py native config (overrides above)
```

**🇯🇵** 設定ファイルは `KEY="value"` の形式です。`#` でコメント行。

**🇺🇸** Config files use `KEY="value"` format. Lines starting with `#` are comments.

**🇨🇳** 配置文件使用 `KEY="value"` 格式。以 `#` 开头的行为注释。

| Key | Default | Description (EN) | 説明 (JP) | 说明 (CN) |
|-----|---------|------------------|-----------|-----------|
| `MODEL` | auto (by RAM) | Main model name | メインモデル名 | 主模型名称 |
| `SIDECAR_MODEL` | auto (by RAM) | Sidecar model name (lighter, for permission checks etc.) | サイドカーモデル名（軽量タスク用） | 边车模型名称（轻量任务用） |
| `OLLAMA_HOST` | `http://localhost:11434` | Ollama API endpoint | Ollama APIエンドポイント | Ollama API端点 |
| `MAX_TOKENS` | `8192` | Maximum output tokens per response | レスポンスあたりの最大出力トークン数 | 每次响应的最大输出令牌数 |
| `TEMPERATURE` | `0.7` | Sampling temperature (0.0 = deterministic, 1.0+ = creative) | サンプリング温度（0.0=決定的、1.0+=創造的） | 采样温度（0.0=确定性、1.0+=创造性） |
| `CONTEXT_WINDOW` | `32768` | Context window size in tokens | コンテキストウィンドウサイズ（トークン数） | 上下文窗口大小（令牌数） |

**Example / 例 / 示例:**
```bash
# ~/.config/vibe-local/config
MODEL="qwen3:8b"
SIDECAR_MODEL="qwen3:1.7b"
OLLAMA_HOST="http://localhost:11434"
MAX_TOKENS=8192
TEMPERATURE=0.7
CONTEXT_WINDOW=32768
```

### Environment Variables / 環境変数 / 环境变量

**🇯🇵** 環境変数は設定ファイルより優先されます。CLIフラグは環境変数より優先されます。
優先順位: CLIフラグ > 環境変数 > 設定ファイル > デフォルト値

**🇺🇸** Environment variables override config file values. CLI flags override environment variables.
Priority: CLI flags > Environment variables > Config file > Defaults

**🇨🇳** 环境变量覆盖配置文件值。CLI标志覆盖环境变量。
优先级: CLI标志 > 环境变量 > 配置文件 > 默认值

| Variable | Description (EN) | 説明 (JP) | 说明 (CN) |
|----------|------------------|-----------|-----------|
| `OLLAMA_HOST` | Ollama API endpoint URL | Ollama APIエンドポイントURL | Ollama API端点URL |
| `VIBE_CODER_MODEL` | Override main model (highest priority) | メインモデル上書き（最優先） | 覆盖主模型（最高优先级） |
| `VIBE_LOCAL_MODEL` | Main model (set by launcher script) | メインモデル（ランチャーが設定） | 主模型（启动脚本设置） |
| `VIBE_CODER_SIDECAR` | Override sidecar model (highest priority) | サイドカーモデル上書き（最優先） | 覆盖边车模型（最高优先级） |
| `VIBE_LOCAL_SIDECAR_MODEL` | Sidecar model (set by launcher script) | サイドカーモデル（ランチャーが設定） | 边车模型（启动脚本设置） |
| `VIBE_CODER_DEBUG` | Set to `1` to enable debug logging | `1`でデバッグログ有効化 | 设为`1`启用调试日志 |
| `VIBE_LOCAL_DEBUG` | Set to `1` to enable debug logging (alias) | `1`でデバッグログ有効化（エイリアス） | 设为`1`启用调试日志（别名） |

**🇯🇵** `VIBE_CODER_*` はユーザーが手動で設定する用途、`VIBE_LOCAL_*` はランチャースクリプト（vibe-local.sh）が自動設定する用途です。`VIBE_CODER_*` が `VIBE_LOCAL_*` より優先されます。

**🇺🇸** `VIBE_CODER_*` variables are for manual user overrides. `VIBE_LOCAL_*` variables are set automatically by the launcher script (vibe-local.sh). `VIBE_CODER_*` takes priority over `VIBE_LOCAL_*`.

**🇨🇳** `VIBE_CODER_*` 变量用于用户手动覆盖。`VIBE_LOCAL_*` 变量由启动脚本（vibe-local.sh）自动设置。`VIBE_CODER_*` 优先于 `VIBE_LOCAL_*`。

---

## 🚨 Security / セキュリティ / 安全须知

### 🇯🇵 日本語

> **⚠️ このツールは自己責任でご利用ください。AIが実行するコマンドには注意が必要です。**

`vibe-local` は通常モード（毎回確認）と自動許可モード（`-y`）を選べます。
自動許可モードを選ぶと、AIがファイルの読み書き・コマンド実行・システム操作を **確認なしで** 実行します。

**ローカルLLMはクラウドAIより精度が低いため、意図しない危険な操作を実行するリスクがあります。**

#### こんなコマンドに注意

AIが提案するコマンドの中に以下のキーワードが含まれていたら、**内容を理解できない限り拒否してください：**

| 注意すべきキーワード | リスク |
|---|---|
| `sudo` で始まるコマンド | システム全体に影響する管理者権限での操作 |
| `chmod` / `chown` | ファイルの権限やセキュリティ設定が変わる |
| `dd` / `mkfs` / `/dev/` | ディスクやパーティションを直接操作する |
| `>` で設定ファイルを上書き | 大事な設定が消える |
| `--force` が付いたコマンド | 安全確認をスキップして強制実行する |
| 意味がわからない長いコマンド | 何が起きるかわからない＝許可してはいけない |

#### 安全に使うためのルール

1. **初回起動時は必ず `n`（通常モード）を選択する** — AIの各操作を事前に確認できます
2. **わからないコマンドは許可しない** — 少しでも不安なら `n` で拒否
3. **大事なファイルがあるフォルダでは使わない** — 新しい空フォルダで練習
4. **`sudo` を求められたら基本的に拒否** — ローカルLLMの判断でシステム操作させない
5. **困ったら `Ctrl+C` で停止**

```bash
vibe-local        # 通常モード（推奨）：毎回確認あり
vibe-local -y     # 自動許可モード（上級者向け・自己責任）
```

#### 内部セキュリティ機構

vibe-coder.py には以下のセキュリティ機構が組み込まれています：

| 機構 | 説明 |
|------|------|
| **SAFE_TOOLS / ASK_TOOLS 分離** | `Read`, `Glob`, `Grep`, `SubAgent`, `AskUserQuestion`, `TaskCreate/List/Get/Update` は安全ツール（確認不要）。`Bash`, `Write`, `Edit`, `NotebookEdit` は要確認ツール。`WebFetch`, `WebSearch` はネットワークツール（追加コンテキスト付きで確認）。 |
| **SSRF防止** | `OLLAMA_HOST` は localhost/127.0.0.1/::1 のみ許可。外部ホストを指定すると自動的にlocalhostにリセットされます。 |
| **WebFetch スキーム検証** | `file://`, `ftp://`, `data://` などの危険なURLスキームをブロック。`http://` と `https://` のみ許可。 |
| **セッションIDサニタイズ** | セッションIDから英数字・アンダースコア・ハイフン以外の文字を除去し、パストラバーサル攻撃を防止。 |
| **最大反復回数制限** | エージェントループは最大50回で安全停止。 |

### 🌱 やさしい にほんご

> **⚠️ だいじな おしらせ：AIは まちがえることが あります！**

AIが うごかそうとする コマンド（めいれい）を よく みてください。
わからない コマンドは、**ぜったいに `y`（はい）を おさないで ください。**

- さいしょに きかれたら **`n`** を おす → AIが まいかい 「これ やっていい？」と きく
- `rm`（さくじょ）や `sudo`（かんりしゃ）が はいった コマンドは きけん
- こまったら **`Ctrl+C`**（コントロール と C を いっしょに おす）で とまる
- れんしゅうは **あたらしい からの フォルダ** で やる

### 🇺🇸 English

> **⚠️ Use this tool at your own risk. Pay attention to the commands the AI executes.**

`vibe-local` offers normal mode (confirms each action) and auto-approve mode (`-y`).
In auto-approve mode, the AI can read/write files, execute commands, and modify your system **without asking**.

**Local LLMs are less accurate than cloud AI — they may attempt dangerous operations unintentionally.**

#### Watch for these keywords in commands

If a command contains any of these keywords and you don't fully understand it, **always reject:**

| Keyword to watch | Risk |
|---|---|
| Commands starting with `sudo` | Runs with admin privileges — affects entire system |
| `chmod` / `chown` | Changes file permissions and security settings |
| `dd` / `mkfs` / `/dev/` | Directly modifies disks and partitions |
| `>` overwriting config files | Important settings may be erased |
| `--force` flag | Skips safety checks and forces execution |
| Long commands you don't understand | If you can't read it, don't allow it |

#### Rules for safe usage

1. **Always choose `n` (normal mode) on first launch** — you approve each action
2. **Never allow commands you don't understand** — if unsure, reject
3. **Don't use in folders with important files** — practice in a new empty folder
4. **Reject `sudo` requests** — don't let a local LLM run system-level commands
5. **Press `Ctrl+C` to stop at any time**

```bash
vibe-local        # Normal mode (recommended): confirms each action
vibe-local -y     # Auto-approve mode (advanced users only, at your own risk)
```

#### Built-in Security Mechanisms

vibe-coder.py includes the following security mechanisms:

| Mechanism | Description |
|-----------|-------------|
| **SAFE_TOOLS vs ASK_TOOLS separation** | `Read`, `Glob`, `Grep`, `SubAgent`, `AskUserQuestion`, `TaskCreate/List/Get/Update` are safe tools (no confirmation needed). `Bash`, `Write`, `Edit`, `NotebookEdit` require user confirmation. `WebFetch`, `WebSearch` are network tools (confirmed with extra context). |
| **SSRF prevention** | `OLLAMA_HOST` is restricted to localhost/127.0.0.1/::1 only. External hosts are automatically reset to localhost. |
| **WebFetch scheme validation** | Blocks dangerous URL schemes (`file://`, `ftp://`, `data://`, etc.). Only `http://` and `https://` are permitted. |
| **Session ID sanitization** | Strips all characters except alphanumerics, underscores, and hyphens from session IDs to prevent path traversal attacks. |
| **Max iteration safety limit** | The agent loop stops after 50 iterations maximum. |

### 🇨🇳 中文

> **⚠️ 使用本工具风险自负。请注意AI执行的每一个命令。**

`vibe-local` 提供普通模式（每次操作前确认）和自动批准模式（`-y`）。
在自动批准模式下，AI可以读写文件、执行命令、修改系统，**无需确认**。

**本地LLM的精度低于云端AI，可能意外执行危险操作。**

#### 注意以下关键词

如果命令中包含以下关键词且你不完全理解其含义，**务必拒绝：**

| 需注意的关键词 | 风险 |
|---|---|
| 以 `sudo` 开头的命令 | 以管理员权限运行，影响整个系统 |
| `chmod` / `chown` | 更改文件权限和安全设置 |
| `dd` / `mkfs` / `/dev/` | 直接操作磁盘和分区 |
| 用 `>` 覆盖配置文件 | 重要设置可能被清除 |
| 带 `--force` 的命令 | 跳过安全检查强制执行 |
| 看不懂的长命令 | 看不懂 = 不能允许 |

#### 安全使用规则

1. **首次启动必须选择 `n`（普通模式）** — 每次操作前确认
2. **不理解的命令一律拒绝** — 有疑问就按 `n`
3. **不要在有重要文件的文件夹中使用** — 在新的空文件夹中练习
4. **拒绝 `sudo` 请求** — 不要让本地LLM执行系统级命令
5. **随时按 `Ctrl+C` 停止**

```bash
vibe-local        # 普通模式（推荐）：每次操作前确认
vibe-local -y     # 自动批准模式（仅限高级用户，风险自负）
```

#### 内置安全机制

vibe-coder.py 包含以下安全机制：

| 机制 | 说明 |
|------|------|
| **SAFE_TOOLS 与 ASK_TOOLS 分离** | `Read`、`Glob`、`Grep`、`SubAgent`、`AskUserQuestion`、`TaskCreate/List/Get/Update` 为安全工具（无需确认）。`Bash`、`Write`、`Edit`、`NotebookEdit` 需要用户确认。`WebFetch`、`WebSearch` 为网络工具（附加上下文确认）。 |
| **SSRF防护** | `OLLAMA_HOST` 仅允许 localhost/127.0.0.1/::1。外部主机会自动重置为localhost。 |
| **WebFetch 方案验证** | 阻止危险的URL方案（`file://`、`ftp://`、`data://` 等）。仅允许 `http://` 和 `https://`。 |
| **会话ID清理** | 从会话ID中删除除字母数字、下划线和连字符之外的所有字符，防止路径遍历攻击。 |
| **最大迭代安全限制** | 代理循环最多运行50次后自动停止。 |

---

## 🎓 Workshop Guide / ワークショップガイド / 工作坊指南

### 🇯🇵 大学・ワークショップでの利用

vibe-local は**大学の授業やワークショップ**で、AIエージェントを使ったコーディングを体験してもらうために設計されています。

#### 事前準備（講師向け）

```bash
# 1. 会場のMac/PCに事前インストール（ネットワーク接続時）
curl -fsSL https://raw.githubusercontent.com/ochyai/vibe-local/main/install.sh | bash

# 2. モデルを事前ダウンロード（オフライン対応）
ollama pull qwen3:8b          # 16GB Mac用
ollama pull qwen3-coder:30b   # 32GB Mac用（推奨）

# 3. 動作確認
vibe-local -p "Hello, World!をPythonで書いて"
```

#### 受講者向けの最初の課題例

```
1. "じゃんけんゲームをPythonで作って"         → 基本的なプログラミング
2. "このフォルダにあるファイルを一覧にして"      → ターミナル操作の学習
3. "HTMLでタイマーアプリを作ってブラウザで開いて"  → Web開発体験
4. "マインスイーパをHTMLで作って"              → ゲーム開発
5. "現在のシステム情報を調べて"                → OS操作の理解
```

#### 注意事項
- **初回は必ず通常モード（`n`）で起動** — AIの操作を1つずつ確認できます
- ローカルLLMはクラウドAIより精度が低いため、**間違った操作をすることがあります**
- **新しい空のフォルダで作業する**ことを推奨します
- 困ったら **`Ctrl+C`** でいつでも停止できます

### 🇺🇸 University & Workshop Usage

vibe-local is designed for **university classes and workshops** where participants experience AI-agent-assisted coding.

#### Pre-setup (Instructor)

```bash
# 1. Pre-install on venue computers (while online)
curl -fsSL https://raw.githubusercontent.com/ochyai/vibe-local/main/install.sh | bash

# 2. Pre-download models (for offline use)
ollama pull qwen3:8b          # For 16GB Macs
ollama pull qwen3-coder:30b   # For 32GB Macs (recommended)

# 3. Verify
vibe-local -p "Write Hello World in Python"
```

#### Starter exercises for students

```
1. "Create a rock-paper-scissors game in Python"    → Basic programming
2. "List all files in this folder"                  → Terminal operations
3. "Create a timer app in HTML and open it"         → Web development
4. "Create minesweeper in HTML"                     → Game development
5. "Check the current system information"           → OS operations
```

---

## 📡 Offline Capabilities / オフライン機能 / 离线功能

### 🇯🇵

vibe-local はオフライン環境に特化しています。以下が**オフラインで動作する**機能です：

| 機能 | オフライン | 備考 |
|------|:--------:|------|
| コード生成・実行 | ✅ | 全てローカルで処理 |
| ファイル操作 (読み書き・編集) | ✅ | |
| コマンド実行 | ✅ | |
| Git操作 (ローカル) | ✅ | push/pullはオンライン必要 |
| HTMLアプリ作成・表示 | ✅ | ブラウザで開くだけ |
| Web検索 (WebSearch) | △ | オンラインなら DuckDuckGo 経由で動作 |
| URLフェッチ (WebFetch) | △ | オンラインなら動作 |
| パッケージインストール (pip/brew/winget) | △ | オンラインなら動作 |

#### オフラインでの調べもの

Web検索が使えない場合でも、以下の方法で調査できます：
- **ローカルファイル検索**: `Grep` / `Glob` ツールでプロジェクト内を検索
- **man コマンド**: `Bash(man curl)` でコマンドのマニュアルを参照
- **事前ダウンロード**: ワークショップ前に必要な資料をローカルに保存しておく

### 🇺🇸

vibe-local is optimized for offline environments:

| Feature | Offline | Notes |
|---------|:-------:|-------|
| Code generation & execution | ✅ | All processed locally |
| File operations (read/write/edit) | ✅ | |
| Terminal command execution | ✅ | |
| Git operations (local) | ✅ | push/pull need network |
| HTML app creation & viewing | ✅ | Just opens in browser |
| Web search (WebSearch) | △ | Works online via DuckDuckGo |
| URL fetch (WebFetch) | △ | Works online |
| Package install (pip/brew/winget) | △ | Works online |

---

## ⚖️ Legal / 適法性 / 法律合规

### 🇯🇵 適法性に関する説明

本ツールの法的性質を透明に説明します：

**本ツールが行うこと（v0.9.0 vibe-coder）：**
- 自作のPythonスクリプト `vibe-coder.py` がコーディングエージェントとして動作します
- ローカルで動作するOllama（オープンソースのLLMランタイム）と直接通信します
- 外部サーバーへの通信は一切行いません（Web検索・URLフェッチは任意機能）
- Anthropic社のソフトウェアは一切使用しません

**使用するソフトウェアのライセンス：**
- **vibe-coder.py**: vibe-local に含まれる完全OSSのエージェント（MIT License）
- **Ollama**: MIT License のオープンソースソフトウェア
- **Qwen3 モデル**: Apache 2.0 License で公開されているオープンソースモデル
- **vibe-local**: MIT License

**注意すべき点：**
- 全コンポーネントがオープンソースライセンスで提供されています
- 本ツールは研究・教育目的のユーティリティであり、商用利用を想定していません
- ローカルLLMはクラウドAIより精度が低いため、意図しない操作のリスクがあります

> **v0.2 以前**: Claude Code CLI + プロキシ方式を使用していました。v0.3.0 で完全自作に移行し、v0.9.0 で500テスト・15ツール・サブエージェント・画像/PDF対応まで到達しました。

### 🇺🇸 Legal Explanation

**What this tool does (v0.9.0 vibe-coder):**
- Runs `vibe-coder.py`, a fully open-source Python coding agent
- Communicates directly with Ollama (open-source LLM runtime) running locally
- No communication with external servers (Web search/fetch are optional features)
- Does not use any Anthropic software

**Software licenses:**
- **vibe-coder.py**: Fully OSS agent included in vibe-local (MIT License)
- **Ollama**: Open-source software under MIT License
- **Qwen3 models**: Open-source models under Apache 2.0 License
- **vibe-local**: MIT License

**Points to note:**
- All components are provided under open-source licenses
- This tool is intended for research and education, not commercial use
- Local LLMs are less accurate than cloud AI, posing risk of unintended operations

> **v0.2 and earlier**: Used Claude Code CLI + proxy approach. v0.3.0 migrated to fully self-contained. v0.9.0 reached 500 tests, 15 tools, sub-agents, image/PDF support, and AskUserQuestion.

---

## ⚙️ Notes

- Local LLM accuracy is lower than cloud AI
- First model download takes time (several GB to 20GB)
- Use `vibe-local --auto` to auto-switch to Claude API when online (requires Claude CLI)
- WebSearch/WebFetch tools require network (△ online only — WebSearch uses DuckDuckGo)
- Large installs (MacTeX ~4GB, Xcode tools) take significant time

---

## 📜 Disclaimer / 免責事項 / 免责声明

### 🌱 やさしい にほんご

> **この どうぐは Anthropic（あんそろぴっく）という かいしゃとは かんけい ありません。**
> じぶんの せきにんで つかってください。
> なにか もんだいが おきても、つくった ひとは せきにんを とれません。
> **つかうまえに、せんせいや くわしいひとに そうだん してください。**

### 🇯🇵

> **本プロジェクトは Anthropic 社とは一切関係ありません。**
> 「Claude」は Anthropic, PBC の商標です。本プロジェクトは非公式のコミュニティツールです。
>
> v0.3.0 以降、本ツールはプロプライエタリソフトウェアを使用していません。
> 全コンポーネント（vibe-coder.py, Ollama, Qwen3モデル）はオープンソースライセンスです。
>
> 本ソフトウェアは現状有姿（AS IS）で提供され、明示的・暗示的を問わず、いかなる保証もありません。
> 使用によって生じたいかなる損害についても、著者は一切責任を負いません。
> **すべて自己責任でご利用ください。**

### 🇺🇸

> **This project is NOT affiliated with, endorsed by, or associated with Anthropic.**
> "Claude" is a trademark of Anthropic, PBC. This is an unofficial community tool.
>
> Since v0.3.0, this tool does not use any proprietary software.
> All components (vibe-coder.py, Ollama, Qwen3 models) are open-source licensed.
>
> Third-party dependencies (Ollama, Qwen models, Python) have their own licenses and terms.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.
> The authors are not liable for any damages arising from the use of this software.
> **Use entirely at your own risk.**

### 🇨🇳

> **本项目与 Anthropic 公司无任何关联。**
> "Claude"是 Anthropic, PBC 的商标。本项目是非官方社区工具。
>
> 自v0.3.0起，本工具不使用任何专有软件。
> 所有组件（vibe-coder.py、Ollama、Qwen3模型）均为开源许可。
>
> 第三方依赖（Ollama、Qwen模型、Python）有各自的许可证和使用条款。
>
> 本软件按"原样"提供，不提供任何明示或暗示的保证。
> 作者不对因使用本软件而产生的任何损害承担责任。
> **使用本工具风险完全自负。**

## 📄 License

MIT
