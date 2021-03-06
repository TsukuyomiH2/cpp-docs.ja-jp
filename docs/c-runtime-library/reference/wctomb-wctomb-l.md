---
description: 詳細については、wctomb、_wctomb_l を参照してください。
title: wctomb、_wctomb_l
ms.date: 4/2/2020
api_name:
- _wctomb_l
- wctomb
- _o__wctomb_l
- _o_wctomb
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb
helpviewer_keywords:
- string conversion, wide characters
- wide characters, converting
- _wctomb_l function
- wctomb function
- wctomb_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
ms.openlocfilehash: f49915d062aa602ab361084cbcc7a9a034599de2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136813"
---
# <a name="wctomb-_wctomb_l"></a>wctomb、_wctomb_l

ワイド文字を対応するマルチバイト文字に変換します。 これらの関数のセキュリティを強化したバージョンを使用できます。「[wctomb_s、_wctomb_s_l](wctomb-s-wctomb-s-l.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int wctomb(
   char *mbchar,
   wchar_t wchar
);
int _wctomb_l(
   char *mbchar,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*mbchar*<br/>
マルチバイト文字のアドレス。

*wchar*<br/>
ワイド文字。

## <a name="return-value"></a>戻り値

**Wctomb** がワイド文字をマルチバイト文字に変換する場合は、ワイド文字のバイト数 ( **MB_CUR_MAX** を超えない) を返します。 *Wchar* がワイド文字の null 文字 (L ' \ 0 ') の場合、 **wctomb** は1を返します。 ターゲットポインター *mbchar* が **NULL** の場合、 **wctomb** は0を返します。 現在のロケールで変換できない場合、 **wctomb** は-1 を返し、 **errno** は **EILSEQ** に設定されます。

## <a name="remarks"></a>解説

**Wctomb** 関数は、 *wchar* 引数を対応するマルチバイト文字に変換し、その結果を *mbchar* に格納します。 任意のプログラムの任意のポイントからこの関数を呼び出すことができます。 **wctomb** は、ロケールに依存する動作に現在のロケールを使用します。 **_wctomb_l** は、渡されたロケールを代わりに使用する点を除いて、 **wctomb** と同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

**wctomb** は、そのパラメーターを検証します。 *Mbchar* が **NULL** の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno** は **EINVAL** に設定され、この関数は-1 を返します。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**wctomb**|\<stdlib.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

このプログラムは、wctomb 関数の動作を示しています。

```cpp
// crt_wctomb.cpp
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int i;
   wchar_t wc = L'a';
   char *pmb = (char *)malloc( MB_CUR_MAX );

   printf( "Convert a wide character:\n" );
   i = wctomb( pmb, wc ); // C4996
   // Note: wctomb is deprecated; consider using wctomb_s
   printf( "   Characters converted: %u\n", i );
   printf( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
