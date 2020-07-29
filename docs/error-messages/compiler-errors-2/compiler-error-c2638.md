---
title: コンパイラエラー C2638
ms.date: 11/04/2016
f1_keywords:
- C2638
helpviewer_keywords:
- C2638
ms.assetid: 9d4275e8-406d-455e-afee-3a37799230e0
ms.openlocfilehash: 863537c60584ba836c6605f31249ada95a88a1bf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212697"
---
# <a name="compiler-error-c2638"></a>コンパイラエラー C2638

' identifier ': __based 修飾子は、メンバーへのポインターでは無効です

修飾子は、 **`__based`** メンバーへのポインターには使用できません。

次の例では、C2638 が生成されます。

```cpp
// C2638.cpp
void *a;

class C {
public:
   int i;
   int j;
   int func();
};
int __based (a) C::* cpi = &C::i;  // C2638
int (__based (a) C::* cpf)() = &C::func; // c2638
```
