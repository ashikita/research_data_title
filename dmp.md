
# 研究データ管理計画（DMP）

**プロジェクト名**： 研究データタイトルリスト
**版（Version）**： v[0.1]（初版）  
**改訂日**： [YYYY-MM-DD]  
**改訂責任者**： 芦北 卓也  
**連絡先**： [メール]  
**DMP DOI/URL**： https://github.com/ashikita/research_data_title  
**ライフサイクル方針**： 本DMPは研究期間中に随時更新する「生きた文書」。主要マイルストーン（データ更新／論文投稿／受領通知／公開時）で改訂。

---

## 1. 目的・対象範囲（Scope）
- **目的**： DataCite APIから研究データのタイトルを収集し、研究者が付与するタイトルの傾向（語彙、長さ、構造）を分析するための基礎データセットを構築・公開する。
- **対象データ**：
  - 収集対象： DataCite登録メタデータの `titles.title` フィールド
  - 付加情報： `publicationYear`, `resourceType`, `subjects`, `creators`（必要に応じて）
  - 取得方法： Pythonスクリプトで DataCite REST API をクエリ
- **研究期間**： [開始〜終了（予定）]
- **想定利用者**： 機関リポジトリ担当者、研究データ管理支援担当者、メタデータ研究者、学術情報基盤担当者、研究推進部局 等

---

## 2. 役割・責任（Roles & Responsibilities）
- **PI/責任者**： [氏名] — 全体方針、DMP承認、公開判断
- **データ管理責任者（Data Steward）**： [氏名] — データ品質管理、匿名化・倫理確認、版管理
- **開発担当（Python/ETL）**： [氏名] — 収集・変換・テスト・自動化
- **公開担当**： [氏名] — リポジトリ整理、メタデータ登録、DOI付与（必要時）
- **相談窓口**： [氏名] — 問合せ対応、Issue運用

---

## 3. データ記述（Data Description）
- **データタイプ**： 構造化テキスト（CSV/JSON）、ログ、コード（.py）
- **ファイル一覧（例）**：
  - `data/raw/datacite_titles_YYYYMMDD.jsonl`（APIレスポンスの原本）
  - `data/processed/titles.csv`（正規化・重複排除後のタイトル一覧）
  - `docs/DMP.md`（本ドキュメント）
  - `src/fetch_titles.py`（収集スクリプト）
  - `analysis/notebooks/01_overview.ipynb`（探索的分析）
- **スキーマ**：
  - `titles.csv`： `id(doi)`, `title`, `language`, `resourceType`, `publicationYear`, `subject`, `source(retrieval_url)`

---

## 4. 収集・生成方法（Data Collection & Processing）
- **API仕様**： DataCite REST API（エンドポイント、クエリ、ページネーション、レート制限）  
  - ベースURL： `[https://api.datacite.org/works]`
  - 例クエリ： `?page[size]=100&query=...&resource-type-id=Dataset`
- **取得頻度**： [例：月1回／四半期ごと]（プレアワードは試行、ポストアワードで定期運用）
- **前処理**： 重複除去、言語コード正規化、空タイトル除外、サロゲートペア正規化
- **変更履歴記録**： ETLログ（`logs/`）、コミットメッセージ規約（例：Conventional Commits）
- **再現性**： 同一クエリ・同一日付での再取得手順を `README.md` に明記。Docker/Conda環境定義あり。

---

## 5. ストレージとバックアップ（Storage & Backup）
- **作業用ストレージ**： [例：大学NAS／OneDrive／ローカル暗号化ディスク]
- **公開ストレージ**： GitHub（コード・軽量データ）＋[Zenodo/OSF/Institutional Repository]（大容量版）
- **バックアップ**： [例：週次スナップショット／GitHub Actionsでアーカイブ／大学バックアップポリシー準拠]
- **暗号化**： 機微データなしを前提。API取得データは公的メタデータだが、アクセス鍵等は `.env` で秘匿。

---

## 6. アクセス権・共有範囲（Access & Sharing）
- **リポジトリ公開範囲**： GitHub（Public）  
- **権限管理**： コラボレータは[氏名/役割]、PRレビュー必須、Issueテンプレート運用
- **公開手段**： GitHub Releases／Zenodo連携で DOI 付与（必要に応じて）
- **エンバーゴ**： 基本なし。分析論文査読中のみ加工済データをリリース保留する可能性あり（期限：[YYYY-MM]）

---

## 7. ライセンス・利用条件（Licensing）
- **データ**： [CC0 1.0 / CC BY 4.0]（DataCiteメタデータ由来で再利用性重視）
- **コード**： [MIT / Apache-2.0]
- **ドキュメント**： [CC BY 4.0]（DMP、README、解析メモ）
- **引用方針**： DataCiteへの帰属表示、データセットにDOIを付与した場合は引用例を `CITATION.cff` に掲載。

---

## 8. メタデータ・識別子（Metadata & PIDs）
- **リポジトリメタデータ**： `README.md`（目的、データ説明、取得手順、スキーマ、バージョン互換性）
- **PIDs**： GitHub-Release＋Zenodo DOI（[必要時：最新版＝概念DOI、各版＝バージョンDOI]）
- **フィールド標準**： DataCite Metadata Schema準拠項目のフィールド名を保持（`title`, `resourceType`, `publicationYear`, `subjects`, `creators`）

---

## 9. 品質管理（Quality Assurance）
- **検証**： タイトル空・重複・過剰長（例：>1,000文字）チェック、文字コード（UTF-8）検証
- **監査**： 月次でサンプルレビュー、APIクエリ再現性テスト、Notebookで要約指標（平均タイトル長、最頻語など）
- **自動化**： CIで `flake8`／`pytest`、CSVスキーマ検証（`frictionless` 等の利用を想定）

---

## 10. セキュリティ・倫理（Security & Ethics）
- **個人情報**： 原則なし（公的メタデータ利用）。人物名（`creators`）は公開情報であるが、二次的利用の文脈をREADMEに明記。
- **利用規約遵守**： DataCite APIの利用規約・レート制限遵守
- **研究倫理**： タイトルの統計的傾向分析を目的とし、個人への評価・ランキング化は行わない。差別的・攻撃的分類の禁止。

---

## 11. 相互運用性・再利用（Interoperability & Reuse / FAIR）
- **Findable**： DOI付与、`README`にキーワード、`topics`設定、`CITATION.cff`
- **Accessible**： 公開リポジトリ、永続リンク、バージョンごとの差分記録
- **Interoperable**： CSV/JSON標準形式、言語コード（ISO 639-1/2）、文字コードUTF-8
- **Reusable**： ライセンス明記、データ辞書（`docs/data_dictionary.md`）、処理手順のNotebook

---

## 12. コスト・リソース（Costs & Resources）
- **ストレージ費用**： [試算]
- **人的工数**： [例：収集・整形 2人日/月、レビュー 0.5人日/月]
- **CI/CD**： GitHub Actions分の制限・実行時間枠を考慮

---

## 13. リスク管理・復旧（Risks & Contingency）
- **API変更**： エンドポイント・スキーマ変更の監視（CIに健全性チェック）
- **依存ライブラリ**： 互換性テスト、`requirements.txt` のピン留め
- **障害対応**： バックアップから復旧手順を `docs/operations.md` に記載
- **法的リスク**： 権利表記・ライセンス不一致を事前レビュー

---

## 14. 公開計画・エンバーゴ（Release & Embargo）
- **公開時期**： [YYYY-MM（初版）]
- **公開可否**： 公開（Public）  
- **エンバーゴ条件**： [必要なら具体的に]
- **公開手段**： GitHub＋Zenodo、機関リポジトリ（必要に応じて）

---

## 15. 成果物リンク（Outputs）
- **学会発表**： [学会名・開催日・URL]
- **論文投稿先**： [誌名・出版社・ポリシーURL]
- **データ引用**： `CITATION.cff` に例示、READMEにも追記

---

## 16. 助成情報（Funding）
- **財源**： [助成機関名・課題番号]
- **要件**： オープンデータ／DMP提出要件、保存年限
- **報告**： 助成機関の中間・期末報告にDMP更新履歴を添付

---

## 17. 改訂運用（Governance & Versioning）
- **更新頻度**： [例：四半期ごと／主要リリース時]
- **意思決定**： Issue → PR → レビュー → Merge（責任者承認）
- **版管理**： `vMAJOR.MINOR.PATCH`、`CHANGELOG.md` に記載
- **監査ログ**： 改訂理由・影響範囲・後方互換性の記述

---

## 付録A：再現可能な実行環境
- **環境定義**： `environment.yml` / `requirements.txt`、Python [3.11]  
- **コンテナ**： `Dockerfile`（非必須）。ランタイムとロケール設定（UTF-8）
- **シークレット**： `.env` を `.gitignore` に含め、APIキーが必要な場合のみ使用（DataCiteは通常不要）

---

