---
description: '詳細については、次を参照してください: _swab'
title: _swab
ms.date: 4/2/2020
api_name:
- _swab
- stdlib/_swab
- _o__swab
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
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: 178189ede5330d467e8ec263a4558bb55108f354
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326253"
---
# <a name="_swab"></a>_swab

バイトを交換します。

## <a name="syntax"></a>構文

```C
void _swab(
   char *src,
   char *dest,
   int n
);
```

## <a name="parameters"></a>パラメーター

*src*<br/>
コピーおよび交換されるデータ。

*先*<br/>
交換したデータの格納場所。

*n*<br/>
コピーおよび交換対象のバイト数。

## <a name="return-value"></a>戻り値

**Swab** 関数は値を返しません。 関数は、 *src* ポインターまたは *dest* ポインターが null であるか、 *n* が0未満の場合に **errno** を **EINVAL** に設定し、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。

リターン コードの詳細については、「[_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>解説

*N* が偶数の場合、 **_swab** 関数は *src* から *n* バイトをコピーし、隣接するバイトの各ペアをスワップして、結果を *dest* に格納します。 *N* が奇数の場合は、 **_swab** *src* の最初の *n*-1 バイトをコピーしてスワップします。最後のバイトはコピーされません。 **_Swab** 関数は、通常、別のバイト順を使用するマシンに転送するためにバイナリデータを準備するために使用されます。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_swab**|C: \<stdlib.h> C++: \<cstdlib> または \<stdlib.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_swab.c

#include <stdlib.h>
#include <stdio.h>

char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";
char to[] =   "...........................";

int main()
{
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);
    _swab(from, to, sizeof(from));
    printf("After:  %s\n        %s\n\n", from, to);
}
```

```Output
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes
        ...........................

After:  BADCFEHGJILKNMPORQTSVUXWZY
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.
```

## <a name="see-also"></a>関連項目

[バッファー操作](../../c-runtime-library/buffer-manipulation.md)<br/>
