[Top](../../../../index.md)\>
[プログラミング言語](../../../pgl.md)\>
[アセンブリ（MASM32）](../../language_0001.md)\>
[基本的な命令](../MASM32_0009.md)

# 実数の演算

+ [実数の表現](#実数の表現)
+ [実数の計算](#実数の計算)

## 実数の表現

### 基本的な考え方

|値の位置|表現方法|
----|----
|小数点より上|2の累乗|
|小数点以下|1/2の累乗|

### 現実の一般的な表現方法

（仮数部） × （基数）^（指数部）

上記の方法によって表現された実現値を**浮動小数点数**という

## 実数の計算

通常、FPU（Floating Point Processing Unit、浮動小数点処理ユニット又は浮動小数点コプロセッサと呼ぶ）及びFPUレジスタを使用して行う

### FPUレジスタの表記方法

+ ST(0)～ST(7)
+ ST0～ST7

ST(0)、ST0の場合は、単にSTと表記することも可能  
値をロードする場合、番号の若い順に使用される

### FPUを使用した演算方法

演算に使用する値をあらかじめFPUレジスタにロードし、その後でレジスタを使用して演算する  
多くの場合、演算結果はST0に保存される

### 主なFPU命令

|命令|機能|
----|----
|f2xm1|2^x-1の計算（Calculate 2**x-1）|
|fabs|浮動小数点数の絶対値（Floating-Point Absolute Value）の計算|
|fadd,faddp|浮動小数点数の加算（Floating-Point Addition）|
|fbld|BCD浮動小数点数のロード（BCD Floating-Point Load）|
|fbstp|BCD浮動小数点数のストア（BCD Floating-Point Store）|
|fchs|浮動小数点数の符号の変更（Floating-Point Change Sign）|
|fclex,fnclex|浮動小数点例外のクリア（Clear Floating-Point Exceptions）|
|fcom,fcomp,fcomi|浮動小数点数の比較（Floating-Point Compare）|
|fcos|コサイン（Cosine）の計算|
|fdiv,fdivp,fdivr,fdivrp|浮動小数点数の除算（Floating-Point Division）|
|ffree|浮動小数点数レジスタを未使用に設定（Flag Floating-Point Register as Unused）|
|fiadd|浮動小数点数レジスタでの整数の加算（Floating-Point/Integer Addition）|
|fiom,ficomp|浮動小数点数レジスタでの整数の比較（Floating-Point/Integer Compare）|
|fidiv,fidivr|浮動小数点数レジスタでの整数の除算（Floating-Point/Integer Division）|
|fild,fist,fistp|浮動小数点数/整数の変換（Floating-Point/Integer Conversion）|
|fimul|浮動小数点数レジスタでの整数の乗算（Floating-Point/Integer Multiplication）|
|finit,fninit|浮動小数点数ユニットの初期化（Initialize Floating-Point Unit）|
|fisub|浮動小数点数レジスタでの整数の減算（Floating-Point/Integer Substraction）|
|fld|扶桑小数点数のロード（Floating-Point Load）|
|fmul,fmulp|浮動小数点数の乗算（Floating-Point Multiplication）|
|fpatan,fptan|アークタンジェントとタンジェント（Arctangent and Tangent）|
|fprem,fprem1|浮動小数点数の剰余（Floating-Point Partial Remainder）|
|frndint|浮動賞進点数の整数への丸め（Floating-Point Round to Integer）|
|fscale|2のべき乗による浮動小数点数の乗算（Scale Floating-Point Value by Power of Two）|
|fsin,fsincos|サインとコサイン（Sine,Cosine）の計算|
|fsqrt|浮動小数点数の平方根（Floating-Point Square Root）|
|fsub,fsubp,fsubr,fsubrp|浮動小数点数の減算（Floating-Point Substraction）|
|fucom,fucomp,fucomi|浮動小数点数の順序無し比較（Floating-Point Unordered Compare）|
|fxch|浮動小数点数の交換（Floating-Point Exchange）|

### FPU命令の命名規則

+ FPU命令のニモニックはFで始まる
+ FPU命令の先頭のFを除いた部分は整数の同じ機能の命令と一致又は類似
+ 操作や演算の実行後にプッシュを伴う命令は最後にPが付く