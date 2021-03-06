---
description: '詳細情報: continue ステートメント (C++)'
title: continue ステートメント (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: 6899e5cd249ab5a7a3b786e4b82c9890c08a7183
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344641"
---
# <a name="continue-statement-c"></a>continue ステートメント (C++)

制御を、外側の最小の [do](../cpp/do-while-statement-cpp.md)、 [for](../cpp/for-statement-cpp.md)、または [while](../cpp/while-statement-cpp.md) ループの制御式に強制的に転送します。

## <a name="syntax"></a>構文

```
continue;
```

## <a name="remarks"></a>解説

現在のイテレーションの残りのステートメントは実行されません。 ループの次のイテレーションは、次のように決定されます。

- **`do`** またはループでは **`while`** 、次の反復処理では、またはステートメントの制御式が再評価によって開始され **`do`** **`while`** ます。

- **`for`**(構文を使用した) ループで `for( <init-expr> ; <cond-expr> ; <loop-expr> )` `<loop-expr>` は、句が実行されます。 次に、`<cond-expr>` 句が再評価され、その結果に応じて、ループが終了するか、別のイテレーションが発生します。

次の例では、 **`continue`** ステートメントを使用して、コードのセクションをバイパスし、ループの次の反復処理を開始する方法を示します。

## <a name="example"></a>例

```cpp
// continue_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        i++;
        printf_s("before the continue\n");
        continue;
        printf("after the continue, should never print\n");
     } while (i < 3);

     printf_s("after the do loop\n");
}
```

```Output
before the continue
before the continue
before the continue
after the do loop
```

## <a name="see-also"></a>関連項目

[ジャンプ ステートメント](../cpp/jump-statements-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)
