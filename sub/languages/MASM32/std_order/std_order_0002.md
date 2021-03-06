[Top](../../../../index.md)\>
[プログラミング言語](../../../pgl.md)\>
[アセンブリ（MASM32）](../../language_0001.md)\>
[基本的な命令](../MASM32_0009.md)

# 演算

整数の演算は汎用レジスタと整数演算用の命令を使用して行う  
実数の演算は通常FPU命令とFPUレジスタを使用して行う  
整数が自動的に実数に変換されることはないため、高級プログラミング言語のように実数と整数の演算を混在させることはできない  
整数演算用の命令は以下の通り

+ [加算命令](#加算命令)
+ [減算命令](#減算命令)
+ [インクリメントとデクリメント](#インクリメントとデクリメント)
+ [乗算命令と除算命令](#乗算命令と除算命令)
+ [シフト命令](#シフト命令)
+ [ローテート](#ローテート)

## 加算命令

ソースオペランドの値をディスティネーションオペランドの値に加算し、その結果をディスティネーションオペランドに保存

### 書式

```add ディスティネーションオペランド,ソースオペランド```

### オペランドに指定できる値

|オペランド|指定できる値|
----|----
|ディスティネーションオペランド|・レジスタ<br>・メモリ|
|ソースオペランド|・レジスタ<br>・メモリ<br>・即値|

### 注意事項

1. 計算結果の値が、結果が保存されるレジスタORメモリのサイズより大きい場合、オーバーフローが生じる
1. 値を符号付き整数と解釈するか、符号なし整数と解釈するかは、原則的にはプログラマに任される

## 減算命令

ソースオペランドの値をディスティネーションオペランドの値から減算し、その結果をディスティネーションオペランドに保存  
実行結果が0の場合は、ZFがセットされる

### 書式

```sub ディスティネーションオペランド,ソースオペランド```

### オペランドに指定できる値

|オペランド|指定できる値|
----|----
|ディスティネーションオペランド|・レジスタ<br>・メモリ|
|ソースオペランド|・レジスタ<br>・メモリ<br>・即値|

### 注意事項

addの場合と同様

## インクリメントとデクリメント

オペランドに指定できるのは、レジスタORメモリ

### インクリメント

値を1だけ増やすこと

#### 書式

```inc ディスティネーションオペランド```

### デクリメント

値を1だけ減らすこと  
実行結果が0の場合は、ZFがセットされる→ループ処理に利用可能

#### 書式

```dec ディスティネーションオペランド```

## 乗算命令と除算命令

<!-- 乗算や除算を行う場合、mulやdivを使用せずにシフト命令を使用することもある -->

### 乗算命令

オペランドとeaxレジスタの値を掛け、結果をedx,eaxに保存  
edxはeaxがオーバーフローした場合に限り使用されるため、正しい結果を得るためには、mul実行前にedxを0に設定する

#### 書式

```mul ソースオペランド```

### 除算命令

オペランドの値でeaxレジスタの値を割り、商をeax、余りをedxに保存

#### 書式

```div ソースオペランド```

## シフト命令

シフト命令による演算は、通常の乗算・除算（mul,div）よりも高速  
そのため、2の累乗の計算の場面ではシフト命令を使用するのが効率的  
ソースオペランドに指定した量（ビット数）だけ、ディスティネーションオペランドに指定した値をシフト

### オペランドに指定できる値

|オペランド|指定できる値|備考|
----|----|----
|ディスティネーションオペランド|・レジスタ<br>・メモリ|\-|
|ソースオペランド|・CLレジスタ<br>・即値|下位5ビットのみ使用される|

### 各シフトによる挙動

|シフトの種類|1ビットシフトした場合の値の変化|シフトによって空くビット|シフトによって空いたビットを埋める値|
----|----|----|----
|算術左シフト|倍|下位ビット|0|
|論理左シフト|倍|下位ビット|0|
|算術右シフト|1/2倍（以下のいずれも満たす場合）<br><br>・余りが発生しない場合<br>・ディスティネーションオペランドの元の最上位ビットが0の場合|下位ビット|ディスティネーションオペランドの元の最上位ビットのコピー|
|論理右シフト|1/2倍（余りが発生しない場合）|下位ビット|0|

### 左シフト

算術シフト・論理シフトの結果は常に一致

#### 書式（算術シフト）

```sal ディスティネーションオペランド,ソースオペランド```

#### 書式（論理シフト）

```shl ディスティネーションオペランド,ソースオペランド```

### 右シフト

ディスティネーションオペランドの元の最上位ビットが0の場合、算術シフト・論理シフトの結果は一致

#### 書式（算術シフト）

```sar ディスティネーションオペランド,ソースオペランド```

#### 書式（論理シフト）

```shr ディスティネーションオペランド,ソースオペランド```

## ローテート

シフトによって溢れたビットを、空いたビットに埋めること  
ソースオペランドに指定した量（ビット数）だけ、ディスティネーションオペランドに指定した値をシフト

### 書式

```命令 ディスティネーションオペランド,ソースオペランド```

### オペランドに指定できる値

|オペランド|指定できる値|備考|
----|----|----
|ディスティネーションオペランド|・レジスタ<br>・メモリ|\-|
|ソースオペランド|・CLレジスタ<br>・即値|下位5ビットのみ使用される|

### 命令の種類

|命令|シフトの方向|CFを含めてローテートするか|
----|----|----
|rol|左|含めない|
|ror|左→|含めない|
|rcl|左|含める|
|rcr|左|含める|