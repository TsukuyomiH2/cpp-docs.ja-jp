---
description: 詳細については、「コンパイラエラー C2658」を参照してください。
title: コンパイラエラー C2658
ms.date: 11/04/2016
f1_keywords:
- C2658
helpviewer_keywords:
- C2658
ms.assetid: 638368e8-7893-4a14-abec-13c768a9543a
ms.openlocfilehash: 6f86bb2147d13a0192cb7272e3ac2f3f580b1493
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286047"
---
# <a name="compiler-error-c2658"></a>コンパイラエラー C2658

' member ': 無名構造体または共用体で再定義される

2つの匿名構造体または共用体に、同じ識別子を持ち、型が異なるメンバー宣言が含まれています。 [/Za](../../build/reference/za-ze-disable-language-extensions.md)では、同じ識別子と型のメンバーに対してもこのエラーが発生します。

次の例では、C2658 が生成されます。

```cpp
// C2658.cpp
// compile with: /c
struct X {
   union { // can be struct too
      int i;
   };
   union {
      int i;   // Under /Za, C2658
      // int i not needed here because it is defined in the first union
   };
};

struct Z {
   union {
      char *i;
   };

   union {
      void *i;   // C2658 redefinition of 'i'
      // try the following line instead
      // void *ii;
   };
};
```
