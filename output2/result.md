# 研究データタイトルの命名例集
（良い例・悪い例）

本資料は、**DataCite に登録された研究データ 773件（2024年収集）**の
タイトル分析に基づき、  
**研究データ登録時に参考となるタイトル命名例**を整理したものです。

研究者、リポジトリ担当者、研究データ管理（RDM）教育での利用を想定しています。

---

## 1. 良い研究データタイトルとは何か

良い研究データタイトルは、  
**論文本文を読まなくても、データの内容が理解できる**ことが重要です。

特に、以下の要素を意識することが推奨されます。

| 観点 | 説明 |
|---|---|
| What（何か） | 何のデータか（試料、観測値、画像、テキスト等） |
| Where（どこか） | 観測地、調査地域、資料の所在 |
| When（いつか） | 観測期間、調査年、歴史年代（必要に応じて） |
| How（どのように） | 観測方法、装置、分析・生成手法（重要な場合） |

> 研究データのタイトルは、  
> **論文タイトルよりも「メタデータとしての明確さ」**を重視します。

---

## 2. 良い研究データタイトルの例

※ 以下は、実際に DataCite に登録されていたデータタイトルからの例です。

### 例1（地球・環境科学）

**Bulk sediment geochemistry of Okhotsk Sea surface sediments**  
（オホーツク海表層堆積物のバルク地球化学データ）

- データの種類が明確
- 対象地域が具体的
- 再利用者にとって理解しやすい

---

### 例2（長期・多変量観測）

**Measurements of seawater temperature, depth, and photosynthetically active radiation (PAR)  
across seven sites at Heron Island, southern Great Barrier Reef from 2015 to 2020**

- 観測項目（温度・深度・PAR）が明示されている
- 観測場所と期間が明確
- 長いが、データ内容が一目で分かる

---

### 例3（分野特化データ）

**Age model from IODP Site 363-U1488**

- データの性質（年代モデル）が明確
- 国際的に通用するサイト識別子を使用
- 当該分野では十分に一意

---

### 例4（人文科学）

**Projet TariMa. Transcription HTR: BnF Manuscrits Arabe 4617 (XML-ALTO)**

- プロジェクトの文脈が分かる
- データ生成手法（HTR）が明示されている
- 対象資料が一意に特定可能

---

### 例5（言語・文化データ）

**A corpus of Slavic dialects in Albania**  
（アルバニアにおけるスラヴ系方言コーパス）

- データ形式（コーパス）が明確
- 対象言語と地域が分かる
- 簡潔だが十分な情報量

---

## 3. 悪い研究データタイトルの例（改善案付き）

### 悪い例1：抽象的すぎるタイトル

**Additional file 2**

**問題点**
- データ内容が全く分からない
- 論文に依存した命名
- 検索性・再利用性が低い

**改善例**
> RNA-seq differential expression results used in [論文名]

---

### 悪い例2：研究室内メモのような名称

**Testing on 26/5**

**問題点**
- 研究分野や内容が不明
- 登録者本人にしか意味が通じない

**改善例**
> Calibration test data for XXX sensor conducted on 26 May 2024

---

### 悪い例3：論文タイトルのコピー

**Data from: A conserved fungal Knr4/Smi1 protein is vital for maintaining cell wall integrity  
and host plant pathogenesis**

**問題点**
- 論文の主張を述べているだけ
- データの種類・形式が不明

**改善例**
> Microscopy images and growth assay data for Knr4/Smi1 deletion mutants

---

### 悪い例4：略語・コードのみのタイトル

**SOFOG3D_JACHERE_CNRM_FOG-MONITOR-3M-10S_L2**

**問題点**
- プロジェクト関係者以外には理解不能
- DOI の title として不親切

**改善例**
> High-resolution fog monitoring data from the SOFOG3D experiment at Jachère site (France)

---

## 4. 研究データ登録前のセルフチェックリスト

研究データを登録する前に、以下を確認しましょう。

- [ ] タイトルから「何のデータか」が分かる
- [ ] 対象地域・資料・観測点が特定できる
- [ ] 観測期間・年代が必要に応じて記載されている
- [ ] 「Additional file」「Dataset」だけのタイトルになっていない
- [ ] 研究室外の第三者にも理解できる表現になっている

---

## 5. 想定される利用用途

- 機関リポジトリの登録マニュアル
- 研究データ管理（RDM）研修教材
- DMP（データ管理計画）記載例
- 登録画面での入力支援・ヘルプ文

---

*最終更新日：2026-04-03*  
*DataCite メタデータの分析に基づく*
``
