---
title: コンパイラ エラー C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: fdc5de7493decf1f44617ab22a00fb5e8852116f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231976"
---
# <a name="compiler-error-c3354"></a>コンパイラ エラー C3354

'function': デリゲートを作成するための関数に、戻り値の型 'type' を指定することはできません。

次の型は、の戻り値の型として無効です **`delegate`** 。

- 関数へのポインター

- メンバーへのポインター

- メンバー関数へのポインター

- 関数への参照

- メンバー関数への参照

次の例では C3354 が生成されます。

```cpp
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
