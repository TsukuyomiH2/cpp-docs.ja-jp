---
description: 詳細については、「コンパイラエラー C2540」を参照してください。
title: コンパイラ エラー C2540
ms.date: 11/04/2016
f1_keywords:
- C2540
helpviewer_keywords:
- C2540
ms.assetid: 92c805a3-2dd9-46ca-a63d-3845c18ecc95
ms.openlocfilehash: 488d18e37080d6bca5c8479a5f3d71b807b39b46
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341790"
---
# <a name="compiler-error-c2540"></a>コンパイラ エラー C2540

配列バインドとしての非定数式

配列には定数がバインドされている必要があります。

次の例では、C2540 が生成されます。

```cpp
// C2540.cpp
void func(int n, int pC[]) {
   int i = ((int [n])pC)[1];   // C2540
}

void func2(int n, int pC[]) {
   int i = (pC)[1];   // OK
}

int main() {
   int pC[100];
   func(100, pC);
   func2(100, pC);
}
```
