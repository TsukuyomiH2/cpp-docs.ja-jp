---
description: 詳細については、「コンパイラエラー C2450」を参照してください。
title: コンパイラ エラー C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 5e2d838ea03ca8d42b2addb2e52d4cf29deabfa1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332409"
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
