[Top](../../../../index.md)\>
[プログラミング言語](../../../pgl.md)\>
[アセンブリ（MASM32）](../../language_0001.md)\>
[アセンブリ言語の実践的活用](../MASM32_0014.md)

# インラインアセンブリ

CやC\+\+等他の高級プログラミング言語で書かれたプログラムの中に、アセンブリ言語のコードを挿入すること

## 書式

    __asm
    {
        処理
    }

上記コードが挿入されたプログラムで宣言されている変数は、上記コードの処理の中で使用できる  
ただし、オペランドのサイズには注意を払う必要あり