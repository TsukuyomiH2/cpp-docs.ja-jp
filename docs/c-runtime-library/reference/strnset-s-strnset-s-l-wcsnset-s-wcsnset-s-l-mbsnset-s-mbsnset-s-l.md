---
title: _strnset_s、_strnset_s_l、_wcsnset_s、_wcsnset_s_l、_mbsnset_s、_mbsnset_s_l
ms.date: 4/2/2020
api_name:
- _mbsnset_s_l
- _strnset_s
- _mbsnset_s
- _strnset_s_l
- _wcsnset_s_l
- _wcsnset_s
- _o__mbsnset_s
- _o__mbsnset_s_l
- _o__strnset_s
- _o__wcsnset_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnset_s_l
- wcsnset_s
- _tcsnset_s_l
- _wcsnset_s
- _mbsnset_s
- _wcsnset_s_l
- _strnset_s_l
- strnset_s_l
- _tcsnset_s
- _strnset_s
- strnset_s
- mbsnset_s_l
- mbsnset_s
- wcsnset_s_l
helpviewer_keywords:
- tcsnset_s function
- mbsnset_s_l function
- initializing characters
- wcsnset_s function
- mbsnset_s function
- _tcsnset_s_l function
- _strnset_s_l function
- _mbsnset_s function
- strnset_s_l function
- _tcsnset_s function
- _strnset_s function
- tcsnset_s_l function
- _mbsnset_s_l function
- strnset_s function
- _wcsnset_s function
ms.assetid: 9cf1b321-b5cb-4469-b285-4c07cfbd8813
ms.openlocfilehash: 123f8c4945d98ccf3dd94a48dbbb0fef3b35a8e5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911218"
---
# <a name="_strnset_s-_strnset_s_l-_wcsnset_s-_wcsnset_s_l-_mbsnset_s-_mbsnset_s_l"></a>_strnset_s、_strnset_s_l、_wcsnset_s、_wcsnset_s_l、_mbsnset_s、_mbsnset_s_l

文字列の文字を所定の書式に初期化します。 これらの [_strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md) のバージョンは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」で説明されているように、セキュリティが強化されています。

> [!IMPORTANT]
> **_mbsnset_s**と **_mbsnset_s_l**は、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
errno_t _strnset_s(
   char *str,
   size_t numberOfElements,
   int c,
   size_t count
);
errno_t _strnset_s_l(
   char *str,
   size_t numberOfElements,
   int c,
   size_t count,
   locale_t locale
);
errno_t _wcsnset_s(
   wchar_t *str,
   size_t numberOfElements,
   wchar_t c,
   size_t count
);
errno_t _wcsnset_s_l(
   wchar_t *str,
   size_t numberOfElements,
   wchar_t c,
   size_t count,
   _locale_t locale
);
errno_t _mbsnset_s(
   unsigned char *str,
   size_t numberOfElements,
   unsigned int c,
   size_t count
);
errno_t _mbsnset_s_l(
   unsigned char *str,
   size_t numberOfElements,
   unsigned int c,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*引数*<br/>
変更対象の文字列。

*numberOfElements*<br/>
*Str*バッファーのサイズ。

*40u-c*<br/>
文字設定。

*count*<br/>
設定する文字数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

正常に終了した場合は 0 を返し、それ以外の場合はエラー コードを返します。

これらの関数は、引数を検証します。 *Str*が null で終わる有効な文字列でない場合、またはサイズ引数が0以下の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数はエラーコードを返し、 **errno**をそのエラーコードに設定します。 より具体的な値が適用されない場合、既定のエラーコードは**EINVAL**です。

## <a name="remarks"></a>解説

これらの関数は、str の最大文字*数*である*str*を*c*に設定します。 *Count*が*str*のサイズより大きい場合は、 *count*の代わりに*str*のサイズが使用されます。 *Count*が*numberofelements*よりも大きく、両方のパラメーターが*str*のサイズより大きい場合、エラーが発生します。

**_wcsnset_s**と **_mbsnset_s**は **_strnset_s**のワイド文字バージョンとマルチバイト文字バージョンです。 **_Wcsnset_s**の文字列引数はワイド文字列です。この **_mbsnset_s**は amultibyte 文字列です。 それ以外では、これらの関数の動作は同じです。

出力値は、ロケールの **LC_CTYPE** カテゴリの設定に影響されます。詳細については、「[setlocale](setlocale-wsetlocale.md)」を参照してください。 **_l** サフィックスが付いていないこれらの関数のバージョンでは、このロケールに依存する動作に現在のロケールを使用します。**_l** サフィックスが付いているバージョンは、渡されたロケール パラメーターを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

これらの関数のデバッグライブラリバージョンは、最初にバッファーを0xFE で埋めます。 この動作を無効にするには、[_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md) を使用します。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnset_s**|**_strnset_s**|**_mbsnbset_s**|**_wcsnset_s**|
|**_tcsnset_s_l**|**_strnset_s_l**|**_mbsnbset_s_l**|**_wcsnset_s_l**|

## <a name="requirements"></a>必要条件

|ルーチン|必須ヘッダー|
|-------------|---------------------|
|**_strnset_s**|\<string.h>|
|**_strnset_s_l**|\<tchar.h>|
|**_wcsnset_s**|\<string.h> または \<wchar.h>|
|**_wcsnset_s_l**|\<tchar.h>|
|**_mbsnset_s**、 **_mbsnset_s_l**|\<mbstring.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_strnset_s.c
#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 characters of string to be *'s */
   printf( "Before: %s\n", string );
   _strnset_s( string, sizeof(string), '*', 4 );
   printf( "After:  %s\n", string );
}
```

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[国](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcat、wcscat、_mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy、wcscpy、_mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
