# 研究データのタイトル傾向調査

* DataCite DOIで根拠データのタイトルリストを取得したい、根拠データをどう識別するか、has-citationsとhas-referencesのどちらかを使う?  
* データの偏りがある、「HEPData」のデータが8割近く占める、「Cambridge Crystallographic Data Centre」も多い、これらを除外する
* get_research_data_title2.ipynbでhas-citations=1、 「HEPData」「Cambridge Crystallographic Data Centre」除外、2020-2024年のデータを取得してoutputフォルダに保存
  * 合計5,410件のデータ、タイトルでソート
  * Data for ... 13件
  * Data for: ... 18件
  * Data from ... 6件
  * Data from: ... 390件 → ほぼDryadのデータ
  * Data of ... 2件
  * Data on ... 6件
  * Data: ... 4件
  * Dataset for ... 13件
  * Dataset for: ... 4件
  * Dataset from: ... 2件
  * Dataset: ... 42件
  * Supplemental data of ... 2件
  * Supplemental data: ... 1件
  * Supplementary data for ... 3件
  * Supporting data for ... 2件
  * Supporting data for: ... 5件

Query Params: 
* has-citations: Search the citationCount field for integer values greater than or equal to the inputted value.
* has-references: Search the referenceCount field for integer values greater than or equal to the inputted value.

Reference: 
* https://support.datacite.org/reference/get_dois
