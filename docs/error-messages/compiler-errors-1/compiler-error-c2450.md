---
title: コンパイラ エラー C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 55c7f7ba8708e1475404a474f85df7dbe37fcec0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220354"
---
# <a name="compiler-error-c2450"></a>コンパイラ エラー C2450

型 ' type ' の switch 式は無効です

**`switch`** 式が無効な型に評価されます。 整数型または整数型へのあいまいな変換を使用して、整数型またはクラス型に評価される必要があります。 ユーザー定義型に評価される場合は、変換演算子を指定する必要があります。

次の例では、C2450 が生成されます。

```cpp
// C2450.cpp
class X {
public:
   int i;
} x;

class Y {
public:
   int i;
   operator int() { return i; }   // conversion operator
} y;

int main() {
   int j = 1;
   switch ( x ) {   // C2450, x is not type int
   // try the following line instead
   // switch ( y ) {
      default:  ;
   }
}
```
