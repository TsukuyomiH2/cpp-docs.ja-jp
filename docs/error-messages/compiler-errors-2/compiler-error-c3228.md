---
description: 詳細については、「コンパイラエラー C3228」を参照してください。
title: コンパイラ エラー C3228
ms.date: 11/04/2016
f1_keywords:
- C3228
helpviewer_keywords:
- C3228
ms.assetid: 9015adf9-17b0-4312-b4a7-c1f33e4126f4
ms.openlocfilehash: f245555674d7ce9dcd48697d7ff1fd3016750f40
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304130"
---
# <a name="compiler-error-c3228"></a>コンパイラ エラー C3228

'function' : 'param' のジェネリック型引数を 'type' にすることはできません。値型またはハンドル型にする必要があります

正しくない型がジェネリック型引数として渡されました。

次の例では C3228 が生成されます。

```cpp
// C3228.cpp
// compile with: /clr
class A {};

value class B {};

generic <class T>
void Test() {}

ref class C {
public:
   generic <class T>
   static void f() {}
};

int main() {
   C::f<A>();   // C3228
   C::f<B>();   // OK

   Test<C>();   // C3228
   Test<C ^>();   // OK
}
```
