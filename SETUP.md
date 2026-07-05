# 環境構築ガイド

チェックアウト後、以下の手順で環境をセットアップしてください。

## 前提条件

- Python 3.14 以上がインストールされていること
- [uv](https://docs.astral.sh/uv/) がインストールされていること（[公式インストール手順](https://docs.astral.sh/uv/getting-started/installation/)を参照）

  ```powershell
  # Windows (PowerShell)
  powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
  ```

## セットアップ手順

### 1. 仮想環境の作成とパッケージのインストール

```bash
uv sync
```

これで自動的に `.venv` が作成され、`pyproject.toml` で指定されたすべてのパッケージがインストールされます。

### 2. 環境変数の設定

`.env.example` を参考にして `.env` ファイルを作成してください。

```powershell
# Windows (PowerShell)
copy .env.example .env
```

その後、`.env` を編集して必要な値を設定します（特に Anthropic API キー）。

```env
ANTHROPIC_API_KEY=your-api-key-here
```

## 利用方法

### Jupyter Notebook の実行

```bash
uv run jupyter notebook
```

### Python スクリプトの実行

```bash
uv run python main.py
```

## VS Code の推奨拡張機能

以下の拡張機能をインストールすることで、開発体験が向上します。

- **Python** (ms-python.python)
- **Jupyter** (ms-toolsai.jupyter)
- **Pylance** (ms-python.vscode-pylance)
- **Black Formatter** (ms-python.black-formatter)
- **Ruff** (charliermarsh.ruff)

`.vscode/extensions.json` に設定済みのため、VS Code でこのフォルダを開くと自動的に拡張機能のインストールが推奨されます。

## トラブルシューティング

### Python バージョンエラー

プロジェクトで Python 3.14 以上が必要です。現在のバージョンは `python --version` で確認できます。

`.python-version` ファイルで指定されたバージョンを使用することをお勧めします。

### uv のインストール

```powershell
# Windows (PowerShell)
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### 仮想環境の再構築

```bash
uv sync --refresh
```
