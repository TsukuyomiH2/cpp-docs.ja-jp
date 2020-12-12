---
description: 詳細については、「コンパイラエラー C2634」を参照してください。
title: コンパイラエラー C2634
ms.date: 11/04/2016
f1_keywords:
- C2634
helpviewer_keywords:
- C2634
ms.assetid: 58c8f2db-ac95-4a81-9355-ef3cfb0ba7b3
ms.openlocfilehash: 5e8aee2ce27fc56f1204d925147f48352bd24a15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123410"
---
# <a name="compiler-error-c2634"></a>コンパイラエラー C2634

' &class:: member ': 参照メンバーへのポインターが無効です

参照メンバーへのポインターが宣言されています。

次の例では、C2634 が生成されます。

```cpp
// C2634.cpp
int mem;
struct S {
   S() : rf(mem) { }
   int &rf;
};
int (S::*pdm) = &S::rf;   // C2634
```
