---
description: '詳細情報: コンパイラの警告 (レベル 4) C4816'
title: コンパイラの警告 (レベル 4) C4816
ms.date: 11/04/2016
f1_keywords:
- C4816
helpviewer_keywords:
- C4816
ms.assetid: 60f730ae-d942-4db9-ab97-41d4a874d8da
ms.openlocfilehash: b48f6f0141966a75a9a15f3f172a32fd81a52354
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330491"
---
# <a name="compiler-warning-level-4-c4816"></a>コンパイラの警告 (レベル 4) C4816

'param' : パラメーターにサイズが 0 の配列があり、この配列は切り捨てられます (オブジェクトが参照によって渡される場合を除く)

サイズが 0 の配列を持つオブジェクトに対するパラメーターが、参照によって渡されませんでした。 オブジェクトが渡されるときに、配列はコピーされません。

## <a name="example"></a>例

次の例では C4816 が生成されます。

```cpp
// C4816.cpp
// compile with: /W4
#include <stdio.h>

extern "C" int printf_s(const char *, ...);

#pragma warning(disable : 4200)

struct S1
{
    int i;
    char cArr[];
};

void TestErr(S1 s1)   // C4816 param with zero-array
                      // not passed by reference
{
    printf_s("%d %c %c\n", s1.i, s1.cArr[0], s1.cArr[1]);
}

void TestOk(S1 &s1)
{
    printf_s("%d %c %c\n", s1.i, s1.cArr[0], s1.cArr[1]);
}

int main()
{
    S1 myS_1 = { 6, 'a', 'b', 'c' };
    TestErr(myS_1);
    TestOk(myS_1);
}
```
