---
title: コンパイラの警告 (レベル 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: d5bee2eb874b965ff99e3dc0038d63d65b346318
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164353"
---
# <a name="compiler-warning-level-1-c4033"></a>コンパイラの警告 (レベル 1) C4033

'function': 値を返さなければいけません

この関数は値を返しません。 定義されていない値が返されます。

戻り値のない `return` を使用する関数は、型 `void`として宣言する必要があります。

このエラーは、C 言語コード用です。

次の例では C4033 が生成されます。

```c
// C4033.c
// compile with: /W1 /LD
int test_1(int x)   // C4033 expected
{
   if (x)
   {
      return;   // C4033
   }
}
```
