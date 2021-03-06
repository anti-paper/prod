[Top](../../../../index.md)\>
[プログラミング言語](../../../pgl.md)\>
[アセンブリ（MASM32）](../../language_0001.md)\>
[基本的な命令](../MASM32_0009.md)

# 論理演算

+ [論理積](#論理積)
+ [論理和](#論理和)
+ [排他的論理和](#排他的論理和)
+ [ビットの反転](#ビットの反転)
+ [符号反転命令](#符号反転命令)

## 論理積

2つの値を2進数で表現し、いずれのビットも1である2進数を求める  
演算結果はディスティネーションオペランドに保存される

### 書式

```and ディスティネーションオペランド,ソースオペランド```

### オペランドに指定できる値

|オペランド|指定できる値|
----|----
|ディスティネーションオペランド|・レジスタ<br>・メモリ|
|ソースオペランド|・レジスタ<br>・メモリ<br>・即値|

## 論理和

2つの値を2進数で表現し、いずれかのビットが1（いずれも1である場合を含む）である2進数を求める  
演算結果はディスティネーションオペランドに保存される

### 書式

```or ディスティネーションオペランド,ソースオペランド```

### オペランドに指定できる値

|オペランド|指定できる値|
----|----
|ディスティネーションオペランド|・レジスタ<br>・メモリ|
|ソースオペランド|・レジスタ<br>・メモリ<br>・即値|

## 排他的論理和

2つの値を2進数で表現し、いずれか一方のビットのみが1（いずれも1である場合は含まない）である2進数を求める  
演算結果はディスティネーションオペランドに保存される  
ある値をxorしてから再度同一の値でxorすると、元の値を復元できる

### 書式

```xor ディスティネーションオペランド,ソースオペランド```

### オペランドに指定できる値

|オペランド|指定できる値|
----|----
|ディスティネーションオペランド|・レジスタ<br>・メモリ|
|ソースオペランド|・レジスタ<br>・メモリ<br>・即値|

## ビットの反転

指定したオペランドのビットを全て反転させる（0→1、1→0）  
オペランドを1の補数で置き換えることと同義  
オペランドに指定できる値は、レジスタ又はメモリ

### 書式

```not ディスティネーションオペランド```

## 符号反転命令

指定したオペランドの符号を反転させる  
オペランドを2の補数で置き換えることと同義  
オペランドに指定できる値は、レジスタ又はメモリ

### 書式

```neg ディスティネーションオペランド```

### 2の補数の求め方

1. ビット反転
1. 1を加える