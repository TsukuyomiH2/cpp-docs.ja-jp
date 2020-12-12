---
description: '詳細については、次を参照してください: _tell、_telli64'
title: _tell、_telli64
ms.date: 4/2/2020
api_name:
- _telli64
- _tell
- _o__tell
- _o__telli64
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- telli64
- _telli64
- _tell
helpviewer_keywords:
- tell function
- file pointers [C++], getting
- _tell function
- file pointers [C++]
- telli64 function
- _telli64 function
ms.assetid: 1500e8f9-8fec-4253-9eec-ec66125dfc9b
ms.openlocfilehash: d82b79a65edb7c88944336604ed329d67876094a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299554"
---
# <a name="_tell-_telli64"></a>_tell、_telli64

ファイル ポインターの位置を取得します。

## <a name="syntax"></a>構文

```C
long _tell(
   int handle
);
__int64 _telli64(
   int handle
);
```

### <a name="parameters"></a>パラメーター

*扱え*<br/>
開いているファイルを参照するファイル記述子。

## <a name="return-value"></a>戻り値

ファイル ポインターの現在の位置。 シーク非対応のデバイスでは、戻り値は未定義です。

戻り値-1L はエラーを示します。 *Handle* が無効なファイル記述子の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は **errno** を **EBADF** に設定し、-1l を返します。

リターンコードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 」を参照してください。

## <a name="remarks"></a>解説

**_Tell** 関数は、 *handle* 引数に関連付けられたファイルポインター (存在する場合) の現在の位置を取得します。 位置は、ファイルの先頭からのバイト数で表されます。 **_Telli64** 関数の場合、この値は64ビットの整数として表されます。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_tell**、 **_telli64**|\<io.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_tell.c
// This program uses _tell to tell the
// file pointer position after a file read.
//

#include <io.h>
#include <stdio.h>
#include <fcntl.h>
#include <share.h>
#include <string.h>

int main( void )
{
   int  fh;
   char buffer[500];

   if ( _sopen_s( &fh, "crt_tell.txt", _O_RDONLY, _SH_DENYNO, 0) )
   {
      char buff[50];
      _strerror_s( buff, sizeof(buff), NULL );
      printf( buff );
      exit( -1 );
   }

   if( _read( fh, buffer, 500 ) > 0 )
      printf( "Current file position is: %d\n", _tell( fh ) );
   _close( fh );
}
```

### <a name="input-crt_telltxt"></a>入力: crt_tell.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>出力

```Output
Current file position is: 20
```

## <a name="see-also"></a>関連項目

[低レベル i/o](../../c-runtime-library/low-level-i-o.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
