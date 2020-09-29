---
title: コンパイラ エラー C3056
ms.date: 11/04/2016
f1_keywords:
- C3056
helpviewer_keywords:
- C3056
ms.assetid: 9500173d-870b-49b3-8e88-0ee93586d19a
ms.openlocfilehash: dd000e56d5fc24929e4d06e1bf0100ad9647610a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501592"
---
# <a name="compiler-error-c3056"></a>コンパイラ エラー C3056

'symbol': シンボルは、'threadprivate' ディレクティブと同じスコープに存在しません

[threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) 句で使用されるシンボルは `threadprivate` 句と同じスコープである必要があります。

次の例では C3056 が生成されます。

```cpp
// C3056.cpp
// compile with: /openmp
int x, y;
void test() {
   #pragma omp threadprivate(x, y)   // C3056
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

考えられる解決策:

```cpp
// C3056b.cpp
// compile with: /openmp /LD
int x, y;
#pragma omp threadprivate(x, y)
void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```
