---
title: _rotl、_rotl64、_rotr、_rotr64
description: _Rotl、_rotl64、_rotr、および _rotr64 の API リファレンスビットを左 (_rotl) または右 (_rotr) に回転させます。
ms.date: 04/05/2018
api_name:
- _rotr64
- _rotl
- _rotr
- _rotl64
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _rotr64
- rotl64
- _rotl64
- rotr64
- rotr
- _rotr
- _rotl
- rotl
helpviewer_keywords:
- rotl64 function
- _rotl function
- rotr function
- rotr64 function
- _rotr function
- rotl function
- _rotl64 function
- rotating bits
- _rotr64 function
- bits, rotating
ms.assetid: cfce439b-366f-4584-8ab1-d527b13fcfc6
ms.openlocfilehash: d2fb6b2674ed7d50cff63ae45f22af63b0120597
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556594"
---
# <a name="_rotl-_rotl64-_rotr-_rotr64"></a>_rotl、_rotl64、_rotr、_rotr64

ビットを左 (**_rotl**) または右 (**_rotr**) に回転させます。

## <a name="syntax"></a>構文

```C

unsigned int _rotl(
   unsigned int value,
   int shift
);
unsigned __int64 _rotl64(
   unsigned __int64 value,
   int shift
);
unsigned int _rotr(
   unsigned int value,
   int shift
);
unsigned __int64 _rotr64(
   unsigned __int64 value,
   int shift
);
```

### <a name="parameters"></a>パラメーター

*value*<br/>
回転させる値。

*shift*<br/>
シフトするビット数。

## <a name="return-value"></a>戻り値

回転後の値。 エラーの戻り値はありません。

## <a name="remarks"></a>解説

**_Rotl**関数と **_rotr**関数は、符号なしの*値*を*シフト*ビットで回転させます。 **_rotl** 値を左に回転します。 **_rotr** 値を右に回転します。 どちらの関数でも、回転により *value* の一端から溢れたビットは他端に折り返されます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_rotl**、 **_rotl64**|\<stdlib.h>|
|**_rotr**、 **_rotr64**|\<stdlib.h>|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_rot.c
/* This program shifts values to rotate an integer.
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   unsigned val = 0x0fd93;
   __int64 val2 = 0x0101010101010101;

   printf( "0x%4.4x rotated left three times is 0x%4.4x\n",
           val, _rotl( val, 3 ) );
   printf( "0x%4.4x rotated right four times is 0x%4.4x\n",
           val, _rotr( val, 4 ) );

   printf( "%I64x rotated left three times is %I64x\n",
           val2, _rotl64( val2, 3 ) );
   printf( "%I64x rotated right four times is %I64x\n",
           val2, _rotr64( val2, 4 ) );
}
```

### <a name="output"></a>出力

```Output
0xfd93 rotated left three times is 0x7ec98
0xfd93 rotated right four times is 0x30000fd9
101010101010101 rotated left three times is 808080808080808
101010101010101 rotated right four times is 1010101010101010
```

## <a name="see-also"></a>関連項目

[浮動小数点のサポート](../../c-runtime-library/floating-point-support.md)<br/>
[_lrotl、_lrotr](lrotl-lrotr.md)<br/>
