---
description: 詳細については、「コンパイラエラー C2550」を参照してください。
title: コンパイラ エラー C2550
ms.date: 11/04/2016
f1_keywords:
- C2550
helpviewer_keywords:
- C2550
ms.assetid: 3293f53e-ee66-4035-920d-34e115c3a24c
ms.openlocfilehash: 046cb88be2dfdb0e73273a7c370d6d7fdd97243f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204083"
---
# <a name="compiler-error-c2550"></a>コンパイラ エラー C2550

' identifier ': コンストラクターの初期化子リストは、コンストラクターの定義でのみ使用できます

基底クラスの初期化子リストが、コンストラクターではない関数の定義で使用されています。

次の例では、C2550 が生成されます。

```cpp
// C2550.cpp
// compile with: /c
class C {
public:
   C();
};

class D : public C {
public:
   D();
   void func();
};

void D::func() : C() {}  // C2550
D::D() : C() {}   // OK
```
