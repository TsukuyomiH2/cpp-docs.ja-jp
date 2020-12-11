---
description: 詳細については、「コンパイラエラー C2680」を参照してください。
title: コンパイラエラー C2680
ms.date: 11/04/2016
f1_keywords:
- C2680
helpviewer_keywords:
- C2680
ms.assetid: d6f7129e-dd17-4661-b680-18d6b925b1cc
ms.openlocfilehash: 076a7409802a786f795ebac3cac83f8d5fdf968d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155684"
---
# <a name="compiler-error-c2680"></a>コンパイラエラー C2680

' type ': 名前のターゲット型が無効です

キャスト演算子がポインターまたは参照ではない型に変換しようとしました。 [Dynamic_cast](../../cpp/dynamic-cast-operator.md)演算子は、ポインターまたは参照に対してのみ使用できます。

次の例では、C2680 が生成されます。

```cpp
// C2680.cpp
// compile with: /c
class A { virtual void f(); };
class B : public A {};

void g(B b) {
   A a;
   a = dynamic_cast<A>(b);   // C2680  target not a reference type
   a = dynamic_cast<A&>(b);   // OK
}
```

C2680 は、ターゲットが定義されていない場合にも発生する可能性があります。

```cpp
// C2680b.cpp
// compile with: /clr /c
// C2680 expected
using namespace System::Collections;

// Delete the following line to resolve.
ref class A;   // not defined

// Uncomment the following line to resolve.
// ref class A{};

public ref class B : ArrayList {
   property A^ C[int] {
      A^ get(int index) {
         return dynamic_cast<A^>(this->default::get(index));
      }
      void set(int index, A^ value) {
         this->default::set(index, value);
      }
   }
};
```
