# 研究データのタイトル傾向調査

* DataCite DOIで根拠データのタイトルリストを取得したい、根拠データをどう識別するか、has-citationsとhas-referencesのどちらかを使う?  
* データの偏りがある、「HEPData」のデータが8割近く占める、「Cambridge Crystallographic Data Centre」も多い、これらを除外する
* has-citations=1、 「HEPData」「Cambridge Crystallographic Data Centre」除外、2020-2024年のデータを取得してoutputフォルダに保存

Query Params: 
* has-citations: Search the citationCount field for integer values greater than or equal to the inputted value.
* has-references: Search the referenceCount field for integer values greater than or equal to the inputted value.

Reference: 
* https://support.datacite.org/reference/get_dois
