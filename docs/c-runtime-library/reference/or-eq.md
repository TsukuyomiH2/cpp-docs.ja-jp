---
description: '詳細については、次を参照してください: or_eq'
title: or_eq
ms.date: 11/04/2016
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- std::or_eq
- or_eq
- std.or_eq
helpviewer_keywords:
- or_eq function
ms.assetid: 1eb92464-ed58-40d8-a30e-f0a6aa2f4318
ms.openlocfilehash: 94181c0f233da3c80023149e19082dadd0aeb211
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195581"
---
# <a name="or_eq"></a>or_eq

&#124;= 演算子の代替手段。

## <a name="syntax"></a>構文

```C

#define or_eq |=
```

## <a name="remarks"></a>解説

マクロにより &#124;= 演算子が生成されます。

## <a name="example"></a>例

```cpp
// iso646_oreq.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 3, b = 2, result;

   result= a |= b;
   cout << result << endl;

   result= a or_eq b;
   cout << result << endl;
}
```

```Output
3
3
```

## <a name="requirements"></a>要件

**ヘッダー:**\<iso646.h>
