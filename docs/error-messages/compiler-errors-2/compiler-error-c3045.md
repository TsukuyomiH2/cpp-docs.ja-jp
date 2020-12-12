---
description: 詳細については、「コンパイラエラー C3045」を参照してください。
title: コンパイラ エラー C3045
ms.date: 11/04/2016
f1_keywords:
- C3045
helpviewer_keywords:
- C3045
ms.assetid: 9351ba3e-3d3f-455f-ac90-a810fa9fd947
ms.openlocfilehash: 0d39399d656a482d401eafb51f53c177c8c3bb2a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269849"
---
# <a name="compiler-error-c3045"></a>コンパイラ エラー C3045

OpenMP 'sections' ディレクティブの後に複合ステートメントが必要です。 '{' が必要です

中かっこで区切られたコード ブロックを [セクション](../../parallel/openmp/reference/openmp-directives.md#sections-openmp) ディレクティブの後に続ける必要があります。

次の例では C3045 が生成されます。

```cpp
// C3045.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
         ++n2;   // C3045

      #pragma omp sections   // OK
      {
         ++n3;
      }
   }
}
```
