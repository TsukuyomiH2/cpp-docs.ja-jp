---
description: 詳細については、「コンパイラエラー C3745」を参照してください。
title: コンパイラ エラー C3745
ms.date: 11/04/2016
f1_keywords:
- C3745
helpviewer_keywords:
- C3745
ms.assetid: 1e64aec5-7e53-47e5-bc7d-3905230cfc66
ms.openlocfilehash: f34d3945761b8d0ba233f3963db9392c3dbcd7c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340217"
---
# <a name="compiler-error-c3745"></a>コンパイラ エラー C3745

' function ': イベントのみを ' 発生 ' にすることができます

[__Raise](../../cpp/raise.md)キーワードに渡すことができるのは、 [__event](../../cpp/event.md)キーワードで定義された関数だけです。

次の例では、C3745 が生成されます。

```cpp
// C3745.cpp
struct E {
   __event void func();
   void func(int) {
   }

   void func2() {
   }

   void bar() {
      __raise func();
      __raise func(1);   // C3745
      __raise func2();   // C3745
   }
};

int main() {
   E e;
   __raise e.func();
   __raise e.func(1);   // C3745
   __raise e.func2();   // C3745
}
```
