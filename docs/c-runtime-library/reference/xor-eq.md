---
title: xor_eq
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
- std.xor_eq
- xor_eq
- std::xor_eq
helpviewer_keywords:
- xor_eq function
ms.assetid: eca4b6b4-b77a-4d44-a09a-5a7e69fdb56c
ms.openlocfilehash: 107f8b6ecccf2976086654370164d73b3fb81f3d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170112"
---
# <a name="xor_eq"></a>xor_eq

^= 演算子の代替手段。

## <a name="syntax"></a>構文

```C

#define xor_eq ^=
```

## <a name="remarks"></a>解説

マクロにより ^= 演算子が生成されます。

## <a name="example"></a>例

```cpp
// iso646_xor_eq.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 3, b = 2, result;

   result= a ^= b;
   cout << result << endl;

   a = 3;
   b = 2;

   result= a xor_eq b;
   cout << result << endl;
}
```

```Output
1
1
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<iso646 >
