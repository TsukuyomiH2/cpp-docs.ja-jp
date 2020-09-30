---
title: コンパイラ エラー C3039
ms.date: 11/04/2016
f1_keywords:
- C3039
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
ms.openlocfilehash: ea6efbfa95992b04ade5496e8c7253ee87319a93
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508372"
---
# <a name="compiler-error-c3039"></a>コンパイラ エラー C3039

'var' : OpenMP 'for' ステートメントのインデックス変数を減少変数にすることはできません

インデックス変数は暗黙的にプライベートであるため、囲む [parallel](../../parallel/openmp/reference/openmp-clauses.md#reduction) ディレクティブ内の [reduction](../../parallel/openmp/reference/openmp-directives.md#parallel) 句で、変数を使用することはできません。

## <a name="example"></a>例

次の例では C3039 が生成されます。

```cpp
// C3039.cpp
// compile with: /openmp /c
int g_i;

int main() {
   int i;

   #pragma omp parallel reduction(+: i)
   {
      #pragma omp for
      for (i = 0; i < 10; ++i)   // C3039
         g_i += i;
   }
}
```
