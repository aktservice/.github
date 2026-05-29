# 🛠 **aktservice** 開発・コーディング共通ルール

本Organizationにおけるすべての開発（WEBアプリ、インフラ、各種スクリプト、マクロ等）で共通して遵守するルールです。開発言語やプラットフォームに関わらず、全員が以下の運用を徹底してください。

---

## 📦 1. リポジトリ管理とドキュメント

### 1.1 必ず README.md を設置する
* すべてのリポジトリのルート直下に必ず `README.md` を作成してください。
* 記述内容：**「このプロジェクトの目的」「ローカルでの起動・開発手順」「デプロイ方法」**

### 1.2 取扱説明書（仕様書）は `docs/` に置くことを推奨
* コードの解説、詳細な仕様、運用の手順書などは、リポジトリ内の `docs/` ディレクトリにMarkdown形式（`.md`）で配置することを推奨します。

---

## 🔒 2. セキュリティと環境設定

### 2.1 機密情報のハードコード禁止（最重要）
* APIキー、アクセストークン、パスワード、秘密URL、接続文字列などの機密情報は、**絶対にソースコードに直接記述（ハードコード）してコミットしないでください。**
* **対策:** 各プラットフォームの環境変数（`.env`、スクリプトプロパティ、GitHub Secrets、Configファイルなど）を利用し、ローカルの環境変数ファイルは `.gitignore` で必ず除外してください。

---

## 👥 3. チーム開発・運用フロー（無料プランに合わせた注意）

当Organizationは無料プランのため、プライベートリポジトリにおける厳密なブランチ保護機能（強制レビュー等）に制限があります。そのため、以下の運用を各自が徹底してください。

### 3.1 他人のリポジトリに関与する際は必ずブランチを作成する
* `main`（または `master`）ブランチへの直接コミット・直接プッシュは禁止です。
* 必ず機能ごとに新しくブランチを作成し、細心の注意を払って作業してください。

### 3.2 変更時は Pull Request を作成し、共有（レビュー）を行う
* ブランチでの作業が完了したら勝手にマージせず、必ず `main` に向けて Pull Request (PR) を作成してください。
* レビューまたはマージの可否について、チャットツール等でリポジトリの管理者に必ず確認・共有を行ってください。

---

## 🎨 4. 命名規則・コード規約

コードおよびファイルの命名規則は、**「その言語の公式・標準の推奨（Style Guide）」**に準拠します。無用な自己流の命名は避けてください。

### 各言語・環境における代表的な命名規則一覧

| 言語 / 環境 | ファイル名 | 変数・関数名 | クラス・型定義 | 定数 | 標準スタイルガイド |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Python** | スネークケース<br>`api_client.py` | スネークケース<br>`total_count`<br>`fetch_data()` | パスカルケース<br>`UserClient` | スネークケース大文字<br>`MAX_RETRY` | [PEP 8](https://peps.python.org/pep-0008/) |
| **TypeScript / JS** | ケバブケース推奨<br>`api-client.ts` | キャメルケース<br>`totalCount`<br>`fetchData()` | パスカルケース<br>`UserClient`<br>`IUserConfig` | スネークケース大文字<br>`MAX_RETRY` | [TypeScript規格](https://github.com/microsoft/TypeScript/wiki/Coding-guidelines) |
| **.NET (C# / F#)** | パスカルケース<br>`ApiClient.cs` | キャメルケース（変数）<br>`totalCount`<br>パスカルケース（関数）<br>`FetchData()` | パスカルケース<br>`UserClient`<br>`IUserConfig` | パスカルケース<br>`MaxRetry` | [.NET Coding conventions](https://learn.microsoft.com/dotnet/csharp/fundamentals/coding-style/coding-conventions) |
| **VBA (Excel等)** | (モジュール名)<br>パスカルケース<br>`M_ApiClient` | キャメルケース<br>`totalCount`<br>パスカルケース（関数）<br>`FetchData` | パスカルケース<br>`UserClient` | スネークケース大文字<br>またはパスカルケース | 各自読みやすさ優先<br>(一般慣習) |

* ※**キャメルケース (camelCase):** `myVariable` (先頭小文字、単語の区切りは大文字)
* ※**パスカルケース (PascalCase):** `MyClass` (先頭大文字、単語の区切りは大文字)
* ※**スネークケース (snake_case):** `my_variable` (すべて小文字、アンダースコア区切り)
* ※**ケバブケース (kebab-case):** `my-file-name` (すべて小文字、ハイフン区切り)

### 4.2 フォーマッタ（整形ツール）の利用
* 人によるコード書き方の癖（インデント、改行など）による無駄なコード差分を防ぐため、プロジェクトで推奨されているフォーマッタ（例: Pythonなら `Black` や `Ruff`、TSなら `Prettier`、.NETなら `dotnet format`）をコミット前に必ず実行してください。
