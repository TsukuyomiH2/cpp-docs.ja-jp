---
description: 詳細については、関数プラグマ
title: function プラグマ
ms.date: 08/29/2019
f1_keywords:
- function_CPP
- vc-pragma.function
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
ms.openlocfilehash: 77b215458f9ffdb6be605d0ae4b239451a1fe1bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269303"
---
# <a name="function-pragma"></a>function プラグマ

プラグマの引数リストで指定された関数をインライン展開するのではなく、その関数の呼び出しを生成するようコンパイラに指示します。

## <a name="syntax"></a>構文

> **#pragma 関数 (** *function1* [ **,** *function2* ...] **)**

## <a name="remarks"></a>解説

組み込み関数は、通常、関数呼び出しとしてではなく、インラインコードとして生成されます。 組み込みの [プラグマ](intrinsic.md) または [/Oi](../build/reference/oi-generate-intrinsic-functions.md) コンパイラオプションを使用して、組み込み関数を生成するようにコンパイラに指示した場合は、 **関数** プラグマを使用して明示的に関数呼び出しを強制することができます。 **関数** プラグマが検出されると、指定された組み込み関数を含む最初の関数定義で有効になります。 効果は、ソースファイルの末尾、または `intrinsic` 同じ組み込み関数を指定するプラグマの外観に続きます。 **関数** プラグマは、関数の外部でグローバルレベルでのみ使用できます。

組み込みフォームを持つ関数の一覧については、「 [組み込みプラグマ](intrinsic.md)」を参照してください。

## <a name="example"></a>例

```cpp
// pragma_directive_function.cpp
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// use intrinsic forms of memset and strlen
#pragma intrinsic(memset, strlen)

// Find first word break in string, and set remaining
// chars in string to specified char value.
char *set_str_after_word(char *string, char ch) {
   int i;
   int len = strlen(string);  /* NOTE: uses intrinsic for strlen */

   for(i = 0; i < len; i++) {
      if (isspace(*(string + i)))
         break;
   }

   for(; i < len; i++)
      *(string + i) = ch;

   return string;
}

// do not use strlen intrinsic
#pragma function(strlen)

// Set all chars in string to specified char value.
char *set_str(char *string, char ch) {
   // Uses intrinsic for memset, but calls strlen library function
   return (char *) memset(string, ch, strlen(string));
}

int main() {
   char *str = (char *) malloc(20 * sizeof(char));

   strcpy_s(str, sizeof("Now is the time"), "Now is the time");
   printf("str is '%s'\n", set_str_after_word(str, '*'));
   printf("str is '%s'\n", set_str(str, '!'));
}
```

```Output
str is 'Now************'
str is '!!!!!!!!!!!!!!!'
```

## <a name="see-also"></a>関連項目

[プラグマ ディレクティブと __pragma キーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
