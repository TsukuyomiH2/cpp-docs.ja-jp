---
title: コンパイラエラー C2792
ms.date: 11/04/2016
f1_keywords:
- C2792
helpviewer_keywords:
- C2792
ms.assetid: 392cf748-4f5e-4e62-a364-3118d5658408
ms.openlocfilehash: 70a1f483aa48b45847306a668a11446a6bb599e7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220224"
---
# <a name="compiler-error-c2792"></a>コンパイラエラー C2792

' super ': このキーワードの後には、':: ' を指定しなければなりません

キーワードの後に使用できるトークンはだけです **`__super`** `::` 。

次の例では、C2792 が生成されます。

```cpp
// C2792.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super.();   // C2792

      // try the following line instead
      // __super::mf();
   }
};
```
