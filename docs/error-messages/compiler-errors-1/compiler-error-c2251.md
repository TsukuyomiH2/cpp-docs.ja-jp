---
description: 詳細については、「コンパイラエラー C2251」を参照してください。
title: コンパイラ エラー C2251
ms.date: 11/04/2016
f1_keywords:
- C2251
helpviewer_keywords:
- C2251
ms.assetid: fefe050c-f8d3-4316-b237-8007dbcdd3bf
ms.openlocfilehash: 029d6fc807757da14cf004b4bf1d8ae253f17ec7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134811"
---
# <a name="compiler-error-c2251"></a>コンパイラ エラー C2251

名前空間 'namespace' にはメンバー 'member' がありません。'member' は正しいですか。

コンパイラは、指定された名前空間で識別子を見つけられませんでした。

次の例では C2251 が生成されます。

```cpp
// C2251.cpp
// compile with: /c
namespace A {
   namespace B {
      void f1();
   }

   using namespace B;
}

void A::f1() {}   // C2251
void A::B::f1() {}   // OK
```
