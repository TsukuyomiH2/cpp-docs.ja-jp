---
title: コンパイラの警告 (レベル 1) C4997
ms.date: 11/04/2016
f1_keywords:
- C4997
helpviewer_keywords:
- C4997
ms.assetid: d39678fd-0c1a-4104-8a45-9e3f20de0407
ms.openlocfilehash: 15f96c6ab65eb5d9728e31e1cc9b31d0bc8aa9b2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499669"
---
# <a name="compiler-warning-level-1-c4997"></a>コンパイラの警告 (レベル 1) C4997

'class': コクラスは COM インターフェイスまたは擬似インターフェイスを実装しません

[coclass](../../windows/attributes/coclass.md) 属性でマークされているクラスがインターフェイスを実装しませんでした。

次の例では C4997 が生成されます。

```cpp
// C4997.cpp
// compile with: /WX
// to resolve this C4997, uncomment all code
#include <objbase.h>

[ object ]
__interface I {
   HRESULT func();
};

[ coclass ]
struct C /*: I*/ {
   /*
   HRESULT func() {
      return S_OK;
   }
   */
};   // C4997
```
