---
description: 詳細については、「コンパイラエラー C3031」を参照してください。
title: コンパイラ エラー C3031
ms.date: 11/04/2016
f1_keywords:
- C3031
helpviewer_keywords:
- C3031
ms.assetid: 7e621e7e-eda7-45b5-8836-29599cd05255
ms.openlocfilehash: 3da80fbf39c62f3e8918f58430a6932abd93f1a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328430"
---
# <a name="compiler-error-c3031"></a>コンパイラ エラー C3031

'var': 'reduction' 句の変数には、スカラー演算型を指定しなければなりません

間違った型の変数が reduction 句に渡されました。

次の例では C3031 が生成されます。

```cpp
// C3031.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

typedef struct {
   int n;
} Incomplete;

extern Incomplete inc;
int i = 9;

int main() {
   #pragma omp parallel reduction(+: inc)   // C3031
      ;

   #pragma omp parallel reduction(+: i)     // OK
      ;
}
```
