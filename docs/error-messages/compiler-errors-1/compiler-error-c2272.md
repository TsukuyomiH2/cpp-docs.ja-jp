---
title: コンパイラ エラー C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: e4163d68e0fbfea062279ba91e2c902855245e4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220393"
---
# <a name="compiler-error-c2272"></a>コンパイラ エラー C2272

' function ': 静的メンバー関数では、修飾子は使用できません

**`static`** メンバー関数は、 [const](../../cpp/const-cpp.md)や[volatile](../../cpp/volatile-cpp.md)などのメモリモデル指定子を使用して宣言されています。このような修飾子は、メンバー関数では使用できません **`static`** 。

次の例では、C2272 が生成されます。

```cpp
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```
