---
description: 詳細については、「コンパイラエラー C2451」を参照してください。
title: コンパイラ エラー C2451
ms.date: 11/04/2016
f1_keywords:
- C2451
helpviewer_keywords:
- C2451
ms.assetid: a64c93a5-ab8d-4d39-ae57-9ee7ef803036
ms.openlocfilehash: 9e8800cb9df233d681afb65edc9b9248e120283a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332378"
---
# <a name="compiler-error-c2451"></a>コンパイラ エラー C2451

型 ' type ' の条件式は無効です

条件式は、整数型に評価されます。

次の例では、C2451 が生成されます。

```cpp
// C2451.cpp
class B {};

int main () {
   B b1;
   int i = 0;
   if (b1)   // C2451
   // try the following line instead
   // if (i)
      ;
}
```
