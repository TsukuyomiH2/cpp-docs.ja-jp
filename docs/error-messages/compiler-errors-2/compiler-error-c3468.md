---
title: コンパイラ エラー C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: f22a01c5c26a55a5908c20f3b123971fadd43544
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742815"
---
# <a name="compiler-error-c3468"></a>コンパイラ エラー C3468

'type': 型は次のアセンブリにのみ転送できます:

'`file`' はアセンブリではありません

アセンブリ内の型のみを転送することができます。

詳細については、「 [型の転送 (C++/cli)](../../extensions/type-forwarding-cpp-cli.md)」を参照してください。

## <a name="examples"></a>例

モジュールを作成する例を次に示します。

```cpp
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

次の例では C3468 が生成されます。

```cpp
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```
