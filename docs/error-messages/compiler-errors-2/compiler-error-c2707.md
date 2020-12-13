---
description: 詳細については、「コンパイラエラー C2707」を参照してください。
title: コンパイラエラー C2707
ms.date: 11/04/2016
f1_keywords:
- C2707
helpviewer_keywords:
- C2707
ms.assetid: 3deaf45c-74da-4c9d-acc6-b82412720b74
ms.openlocfilehash: 1f615da7ebd2884cbaae26d7c1966725186e2883
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144834"
---
# <a name="compiler-error-c2707"></a>コンパイラエラー C2707

' identifier ': 組み込み関数のコンテキストが正しくありません

構造化例外処理の組み込みは、特定のコンテキストでは無効です。

- `_exception_code()`例外フィルターまたはブロックの外側 **`__except`**

- `_exception_info()` 例外フィルターの外側

- `_abnormal_termination()`ブロックの外側 **`__finally`**

このエラーを解決するには、例外処理の組み込みが適切なコンテキストに配置されていることを確認してください。

## <a name="example"></a>例

次の例では、C2707 が生成されます。

```cpp
// C2707.cpp
#include <windows.h>
#include <stdio.h>

LONG MyFilter(LONG excode)
{
    return (excode == EXCEPTION_ACCESS_VIOLATION ?
        EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);   // OK
}

LONG func(void)
{
    int x, y;
    return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ?  // C2707
             EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);

    __try
    {
        y = 0;
        x = 4 / y;
        return 0;
     }

    __except(MyFilter(GetExceptionCode()))
    {
        return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ? // ok
               EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);
    }
}

int main()
{
    __try
    {
        func();
    } __except(EXCEPTION_EXECUTE_HANDLER)
    {
        printf_s("Caught exception\n");
    }
}
```
