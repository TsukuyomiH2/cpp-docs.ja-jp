---
description: 詳細については、「コンパイラエラー C2831」を参照してください。
title: コンパイラ エラー C2831
ms.date: 11/04/2016
f1_keywords:
- C2831
helpviewer_keywords:
- C2831
ms.assetid: c8c04288-0889-4265-a077-17f94cbcdcc9
ms.openlocfilehash: 65fece68763e38de8c5047c66327e0615865fa9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194502"
---
# <a name="compiler-error-c2831"></a>コンパイラ エラー C2831

' operator operator ' に既定のパラメーターを設定することはできません。

既定のパラメーターを持つことができるのは、3つの演算子のみです。

- [新規](../../cpp/new-operator-cpp.md)

- 割り当て =

- 左かっこ (

次の例では、C2831 が生成されます。

```cpp
// C2831.cpp
// compile with: /c
#define BINOP <=
class A {
public:
   int i;
   int operator BINOP(int x = 1) {   // C2831
   // try the following line instead
   // int operator BINOP(int x) {
      return i+x;
   }
};
```
