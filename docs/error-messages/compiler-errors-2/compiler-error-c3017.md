---
title: コンパイラ エラー C3017
ms.date: 11/04/2016
f1_keywords:
- C3017
helpviewer_keywords:
- C3017
ms.assetid: 12ab2c2a-d0d2-4900-9cbf-39be0af590dd
ms.openlocfilehash: 34347abffd91246ada080d19fee88ee09c8fce99
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232067"
---
# <a name="compiler-error-c3017"></a>コンパイラ エラー C3017

OpenMP 'for' ステートメントの終了テストには、正しくない形式が含まれています

**`for`** OpenMP ステートメント内のループは、完全かつ明示的に指定されている必要があります。

次の例では C3017 が生成されます。

```cpp
// C3017.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i; ++i)   // C3017
      // Try the following line instead:
      // for (i = 0; i < 10; ++i)
         ;
   }
}
```
