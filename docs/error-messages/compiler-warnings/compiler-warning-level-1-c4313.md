---
title: コンパイラの警告 (レベル 1) C4313
ms.date: 11/04/2016
f1_keywords:
- C4313
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
ms.openlocfilehash: 14ac938d62b4c5b6f22957268721aea9c3ffef22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163051"
---
# <a name="compiler-warning-level-1-c4313"></a>コンパイラの警告 (レベル 1) C4313

'function' : 書式指定文字列内の 'format specifier' が引数 ('type' 型) と競合しています。

指定された書式と渡された値が矛盾しています。 たとえば、32 ビット整数パラメーターを想定している修飾されていない %d 書式指定子に 64 ビット パラメーターを渡しました。 この警告は、コードの 64 ビット ターゲットのコンパイル時にのみ有効です。

## <a name="example"></a>例

次のコード サンプルは、64 ビット ターゲットのコンパイル時に C4313 を生成します。

```cpp
// C4313.cpp
// Compile by using: cl /W1 C4313.cpp
#include <stdio.h>
int main() {
   int * pI = 0;
   printf("%d", pI);   // C4313 on 64-bit platform code
   // Try one of the following lines instead:
   // printf("%p\n", pI);
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information
}
```
