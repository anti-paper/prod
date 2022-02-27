[Top](../../../../index.md)\>
[プログラミング言語](../../../pgl.md)\>
[COBOL（OpenCOBOL）](../../language_0002.md)\>
[COBOLプログラムの構成](../COBOL_0001.md)

# 環境部（ENVIRONMENT DIVISION）

主に入出力ファイルの種類やプログラム適用先コンピュータ名など、「実行環境や使用する資源の概略」の定義

## 宣言

### 書式

```environment division.```

### 一般規則

先頭は必ずA領域スタート  
他の部の宣言文が現れるまでが環境部となる  
environmentとdivisionの間の空白数や改行の有無は自由（ピリオドはdivisionの後ろに1か所だけ記述）

### 環境部に含まれる節

|節名|節名（日本語）|省略可否|
----|----|----
|[configuration section](SECTION/SECTION_0001.md)|構成節|可|
|[input-output section](SECTION/SECTION_0002.md)|入出力節|可|