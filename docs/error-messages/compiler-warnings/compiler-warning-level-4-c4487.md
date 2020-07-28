---
title: コンパイラの警告(レベル 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: 33a2a4e36a2c1d3a3900b9f2f8261df7bbce9b00
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214348"
---
# <a name="compiler-warning-level-4-c4487"></a>コンパイラの警告(レベル 4) C4487

' derived_class_function ': 継承された仮想でないメソッド ' base_class_function ' と一致しますが、' new ' として明示的に設定されていません

派生クラスの関数は、非仮想基底クラスの関数と同じシグネチャを持っています。 C4487 は、派生クラスの関数が基底クラスの関数をオーバーライドしないことを通知します。 この警告を解決するには、派生クラスの関数を明示的にとしてマークし **`new`** ます。

詳細については、「 [new (vtable の新しいスロット)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>例

次の例では、C4487 が生成されます。

```cpp
// C4487.cpp
// compile with: /W4 /clr
using namespace System;
public ref struct B {
   void f() { Console::WriteLine("in B::f"); }
   void g() { Console::WriteLine("in B::g"); }
};

public ref struct D : B {
   void f() { Console::WriteLine("in D::f"); }   // C4487
   void g() new { Console::WriteLine("in D::g"); }   // OK
};

int main() {
   B ^ a = gcnew D;
   // will call base class functions
   a->f();
   a->g();
}
```
