---
title: コンパイラの警告 (レベル 1) C4224
ms.date: 11/04/2016
f1_keywords:
- C4224
helpviewer_keywords:
- C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
ms.openlocfilehash: e2e6cde3cc3c6d3032bfbf4e81959ae791a91981
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199785"
---
# <a name="compiler-warning-level-1-c4224"></a>コンパイラの警告 (レベル 1) C4224

非標準の拡張機能が使用されています: 仮パラメーター ' identifier ' は型として既に定義されています

この識別子は、以前は `typedef`として使用されていました。 これにより、ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) で警告が発生します。

## <a name="example"></a>例

```cpp
// C4224.cpp
// compile with: /Za /W1 /LD
typedef int I;
void func ( int I );  // C4224
```
