---
description: 詳細については、「コンパイラエラー C2064」を参照してください。
title: コンパイラエラー C2064
ms.date: 11/04/2016
f1_keywords:
- C2064
helpviewer_keywords:
- C2064
ms.assetid: 6cda05da-f437-4f50-9813-ae69538713a3
ms.openlocfilehash: dd9f0386267a81d4f92d6dd0474cd9a3292e7345
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328560"
---
# <a name="compiler-error-c2064"></a>コンパイラエラー C2064

N 引数を取り込む関数には評価されません。

式を使用して関数の呼び出しが行われています。 この式は、指定された引数値を取り込む関数へのポインターとして評価されません。

この例のコードでは、関数ではないものを関数として呼び出そうとしています。 次の例では C2064 が生成されます。

```cpp
// C2064.cpp
int i, j;
char* p;
void func() {
   j = i();    // C2064, i is not a function
   p();        // C2064, p doesn't point to a function
}
```

オブジェクト インスタンスのコンテキストから、静的でないメンバー関数へのポインターを呼び出す必要があります。 次の例では C2064 が生成され、その修正方法が示されています。

```cpp
// C2064b.cpp
struct C {
   void func1(){}
   void func2(){}
};

typedef void (C::*pFunc)();

int main() {
   C c;
   pFunc funcArray[2] = {&C::func1, &C::func2};
   (funcArray[0])();    // C2064
   (c.*funcArray[0])(); // OK - function called in instance context
}
```

クラス内で、メンバー関数ポインターは、呼び出し元のオブジェクトのコンテキストも示す必要があります。 次の例では C2064 が生成され、その修正方法が示されています。

```cpp
// C2064d.cpp
// Compile by using: cl /c /W4 C2064d.cpp
struct C {
   typedef void (C::*pFunc)();
   pFunc funcArray[2];
   void func1(){}
   void func2(){}
   C() {
      funcArray[0] = &C::func1;
      funcArray[1] = &C::func2;
   }
   void func3() {
      (funcArray[0])();   // C2064
      (this->*funcArray[0])(); // OK - called in this instance context
   }
};
```
