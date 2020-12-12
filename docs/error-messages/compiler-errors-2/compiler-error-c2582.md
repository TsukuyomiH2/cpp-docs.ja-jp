---
description: 詳細については、「コンパイラエラー C2582」を参照してください。
title: コンパイラ エラー C2582
ms.date: 11/04/2016
f1_keywords:
- C2582
helpviewer_keywords:
- C2582
ms.assetid: ee1b9378-8bcd-4792-b87e-6d7a466d29ed
ms.openlocfilehash: 97020c7ea9209da6524d5a0a7c8c05aa1c76d37d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177719"
---
# <a name="compiler-error-c2582"></a>コンパイラ エラー C2582

' function ' 関数は ' type ' では使用できません

代入演算子を持たないオブジェクトにを割り当てようとしました。

次の例では、C2582 が生成されます。

```cpp
// C2582.cpp
// compile with: /clr
using namespace System;

struct N {};
ref struct O {};
ref struct R {
   property O prop;   // C2582
   property O ^ prop2;   // OK
};

int main() {
   String ^ st1 = gcnew String("");
   ^st1 = gcnew String("");   // C2582
   st1 = "xxx";   // OK
}
```
