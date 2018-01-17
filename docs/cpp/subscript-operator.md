---
title: "添字演算子: |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '[]'
dev_langs: C++
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fbcb3657af276cdfc9aa05d461c090b76f6de0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="subscript-operator"></a>添字演算子:
## <a name="syntax"></a>構文  
  
```  
  
postfix-expression [ expression ]  
```  
  
## <a name="remarks"></a>コメント  
 (どの基本式もかまいません)、添字演算子が続く後置式**[]**配列のインデックスを指定します。  
  
 マネージ配列については、次を参照してください。[配列](../windows/arrays-cpp-component-extensions.md)です。  
  
 によって表される値では通常、*後置式*、配列識別子など、ポインター値と*式*(列挙型を含む)、整数値です。 ただし、構文上必要なのは、一方の式がポインター型で、もう一方が整数型であることです。 したがって、整数値の可能性があります、*後置式*位置と、ポインター値可能性があります。 角かっこ内、*式*または添字の位置。 次のコードがあるとします。  
  
```  
int nArray[5] = { 0, 1, 2, 3, 4 };  
cout << nArray[2] << endl;            // prints "2"  
cout << 2[nArray] << endl;            // prints "2"  
```  
  
 上の例では、式 `nArray[2]` は `2[nArray]` と同じです。 理由添字式の結果は*e1***[** *e2* **]**によって得られます。  
  
 **\*((** *e2* **)**  *+*  **(***e1***))**  
  
 式から得られるアドレスが*e2*アドレスからのバイト*e1*です。 配列内の次のオブジェクトを生成するアドレスのスケールではなく、 *e2*です。 例:  
  
```  
double aDbl[2];  
```  
  
 アドレスは、`aDb[0]`と`aDb[1]`は 8 バイトの間隔: 型のオブジェクトのサイズ**二重**です。 オブジェクトの種類基づくこのスケーリングは C++ 言語によって自動的に行われで定義された[加法演算子](../cpp/additive-operators-plus-and.md)ポインター型のオペランドの加算と減算が説明されています。  
  
 添字式には、次のように複数の添字がある場合があります。  
  
 *expression1* **[***expression2***] [***expression3***]**しています.  
  
 添字式は、左から右へ関連付けられます。 左端の添字式、*expression1***[***expression2***]** が最初に評価されます。 *expression1* と *expression2* を加算した結果として得られるアドレスからポインター式が形成され、次にこのポインター式に *expression3* が加算されて新しいポインター式が形成されます。このようにして、最後の添字式が加算されるまで処理が行われます。 間接演算子 (**\***)、最終的なポインター値が配列型のアドレスしない限り、最後の添字式が評価された後に適用します。  
  
 複数の添字を持つ式は、多次元配列の要素を参照します。 多次元配列は、要素が配列である配列です。 たとえば、3 次元配列の最初の要素は 2 次元配列です。 次の例では、文字の単純な 2 次元配列を宣言して初期化しています。  
  
```  
// expre_Subscript_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
#define MAX_ROWS 2  
#define MAX_COLS 2  
  
int main() {  
   char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };  
   for ( int i = 0; i < MAX_ROWS; i++ )  
      for ( int j = 0; j < MAX_COLS; j++ )  
         cout << c[ i ][ j ] << endl;  
}  
```  
  
## <a name="positive-and-negative-subscripts"></a>正と負の添字  
 配列の最初要素は要素 0 です。 C++ 配列の範囲は*配列*[0] に*配列*[*サイズ*- 1] です。 ただし、C++ は、正の数の添字と負の数の添字をサポートします。 負の添字は配列の範囲内になる必要があり、そうでない場合、結果は予測不能となります。 次のコードは正および負の配列添字を示します。  
  
```  
#include <iostream>  
using namespace std;  
  
int main() {  
    int intArray[1024];  
    for (int i = 0, j = 0; i < 1024; i++)  
    {  
        intArray[i] = j++;  
    }  
  
    cout << intArray[512] << endl;// 512  
  
    int *midArray = &intArray[512];  // pointer to the middle of the array  
  
    cout << midArray[-256] << endl;   // 256  
  
    cout << intArray[-256] << endl; // unpredictable  
}  
```  
  
 最後の行の負の添字は、配列の元よりもメモリ内で 256 バイト低いアドレスを生成するので、実行時エラーが生成されることがあります。 ポインター `midArray` は `intArray` の中央に初期化されます。したがって正と負、両方の配列インデックスを使用することができます。 配列添字のエラーは、コンパイル時のエラーを生成しませんが、予測できない結果になります。  
  
 添字演算子は可換です。 そのため、式は、*配列*[*インデックス*] と*配列*[*配列*]、添字限り等価であることが保証されます演算子のオーバー ロードされていない (を参照してください[オーバー ロードされた演算子](../cpp/operator-overloading.md))。 最初の形式は、共通のコーディングの推奨事項ですが、どちらの方法でも動作します。  
  
## <a name="see-also"></a>参照  
 [後置式](../cpp/postfix-expressions.md)   
 [C++ 組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [配列](../cpp/arrays-cpp.md)   
 [1 次元配列](../c-language/one-dimensional-arrays.md)   
 [多次元配列](../c-language/multidimensional-arrays-c.md)