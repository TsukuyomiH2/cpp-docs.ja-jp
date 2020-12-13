---
description: 詳細については、「コンパイラエラー C2258」を参照してください。
title: コンパイラ エラー C2258
ms.date: 11/04/2016
f1_keywords:
- C2258
helpviewer_keywords:
- C2258
ms.assetid: 105eaa87-befb-4ecb-9a3f-e09e14d2f5bf
ms.openlocfilehash: cb82994b582df91198fcd7455179666e66543247
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134720"
---
# <a name="compiler-error-c2258"></a>コンパイラ エラー C2258

純粋仮想関数の宣言に構文上の誤りがあります、'= 0' でなければなりません。

純粋仮想関数が正しくない構文で宣言されています。

次の例では C2258 が生成されます。

```cpp
// C2258.cpp
// compile with: /c
class A {
public:
   void virtual func1() = 1; // C2258
   void virtual func2() = 0;   // OK
};
```
