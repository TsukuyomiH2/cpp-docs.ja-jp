---
title: strtod、_strtod_l、wcstod、_wcstod_l
ms.date: 4/2/2020
api_name:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
- _o__strtod_l
- _o__wcstod_l
- _o_strtod
- _o_wcstod
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstod
- strtod
- wcstod
- _strtod_l
- _wcstod_l
- stdlib/strtod
- corecrt_wstdlib/wcstod
- stdlib/_strtod_l
- corecrt_wstdlib/_wcstod_l
helpviewer_keywords:
- wcstod_l function
- tcstod_l function
- _tcstod_l function
- strtod function
- _wcstod_l function
- wcstod function
- strtod_l function
- tcstod function
- _tcstod function
- _strtod_l function
- string conversion, to floating point values
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
ms.openlocfilehash: a688846d5db4d508327745728f8933c91bfd54e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337666"
---
# <a name="strtod-_strtod_l-wcstod-_wcstod_l"></a>strtod、_strtod_l、wcstod、_wcstod_l

文字列を倍精度値に変換します。

## <a name="syntax"></a>構文

```C
double strtod(
   const char *strSource,
   char **endptr
);
double _strtod_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *strSource,
   wchar_t **endptr
);
double wcstod_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*ストソース*<br/>
NULL で終わる変換対象の文字列。

*エンドプター*<br/>
スキャンの終了位置を示す文字へのポインター。

*ロケール*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**strtod は**浮動小数点数の値を返しますが、表現がオーバーフローを引き起こす場合を除き、関数は +/-**HUGE_VAL**を返します。 **HUGE_VAL**の符号は、表現できない値の符号と一致します。 **strtod は**、変換が実行できない場合、またはアンダーフローが発生した場合は 0 を返します。

**wcstod は** **strtod**と同様に値を返します。 どちらの関数でも、オーバーフローまたはアンダーフローが発生し、無効なパラメータ ハンドラが呼び出された場合 **、errno**は**ERANGE**[に設定](../../c-runtime-library/parameter-validation.md)されます。 リターン コードの詳細については、「[_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>解説

各関数は、入力文字列*strSource*を**double**に変換します。 **strtod**関数は *、strSource*を倍精度の値に変換します。 **strtod は**、文字列*strSource*の読み取りを、数値の一部として認識できない最初の文字で停止します。 数値として認識できない最初の文字が、終端の NULL 文字の場合もあります。 **wcstod**は **、strtod**のワイド文字バージョンです。*strSource*引数はワイド文字列です。 それ以外では、これらの関数の動作は同じです。

既定では、この関数のグローバル状態はアプリケーションにスコープされます。 これを変更するには[、CRT のグローバル状態を](../global-state.md)参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

現在のロケールの**LC_NUMERIC**カテゴリ設定によって *、strSource*の基数ポイント文字の認識が決まります。 詳細については、「[setlocale](setlocale-wsetlocale.md)」をご覧ください。 **_l**サフィックスを持たない関数は、現在のロケールを使用します。**_strtod_l**は、渡された*ロケール*を使用する点を除いて **、_strtod_l**と同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

*endptr*が**NULL**でない場合は、スキャンを停止した文字へのポインタが*endptr*が指す位置に格納されます。 変換が実行できない場合 (有効な数字が見つからなかったか、無効なベースが指定されている場合 *)、strSource*の値は*endptr*が指す場所に格納されます。

**strtod は** *strSource*が次のいずれかの形式の文字列を指すことを想定しています。

[*空白*][*記号*]{*数字*[*基数* *]*&#124;*基数* *}*[{ {**e** *hexdigits*&#124; **E**} [*記号**]*[*空白*] [ *radix* *記号*] { 0x &#124; **0X**} {*16 進数*] &#124;*基*数*16*進数 } [{**p** &#124; **P**} [*符号*] *16 進数*] [*[ ホワイトスペース*] [*記号***0x** ] [**INF** &#124; **INFINITY**} [*空白*] [*記号*] **NAN** [*シーケンス*]

オプションの先頭*の空白*文字は、スペースとタブ文字で構成され、無視されます。*符号*はプラス (+) またはマイナス (-) のいずれかです。*数字*は 1 桁以上の 10 進数です。*16 進数*は 1 桁以上の 16 進数です。*基数*は、デフォルトの "C" ロケールのピリオド (.) または現在のロケールが異なる場合やロケールが指定されている場合は *、ロケール*固有の値の基数ポイント文字です。*シーケンス*は、英数字またはアンダースコア文字のシーケンスです。 10 進数形式と 16 進数形式の両方で、基数の文字の前に数字が現れなければ、少なくとも 1 つは基数ポイント文字の後になければなりません。 10 進形式では、10 進数の後に、入門文字 ( e または**E** **E**) とオプションで符号付き整数で構成される指数が続きます。 16 進形式では、16 進数字の後に、入門文字 (**p**または**P**) と、指数を 2 の累乗として表すオプションの符号付き 16 進整数で構成される指数が続きます。 どちらの形式でも、指数部も基数点文字も出現しない場合、基数ポイント文字は文字列の最後の桁に続くものと見なされます。 INF と**NAN** **INF**の両方の形式では大文字と小文字は無視されます。 これらの形式の 1 つに収まらない最初の文字は、スキャンを停止します。

これらの関数の UCRT バージョンでは、Fortran スタイル (**d**または**D**) の指数文字の変換はサポートされていません。 この非標準の拡張機能は、CRT の以前のバージョンでサポートされており、コードの互換性に影響する変更点がある可能性があります。 UCRT バージョンは、以前のバージョンではサポートされていない 16 進数文字列と INF 値と NAN 値のラウンド トリップをサポートします。 これにより、コードの変更が破損する可能性もあります。 たとえば、文字列 "0x1a" は、以前のバージョンでは**strtod**によって 0.0 として解釈されますが、UCRT バージョンでは 26.0 として解釈されます。

## <a name="requirements"></a>必要条件

|ルーチン|必須ヘッダー|
|-------------|---------------------|
|**ストルトド**, **_strtod_l**|C: &lt;stdlib.h> C++: &lt;cstdlib> または &lt;stdlib.h> |
|**wcstod**, **_wcstod_l**|C: &lt;stdlib.h > または &lt;wchar.h > C++: &lt;cstdlib >、&lt;stdlib.h > または &lt;wchar.h > |

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_strtod.c
// This program uses strtod to convert a
// string to a double-precision value; strtol to
// convert a string to long integer values; and strtoul
// to convert a string to unsigned long-integer values.
//

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char   *string, *stopstring;
   double x;
   long   l;
   int    base;
   unsigned long ul;

   string = "3.1415926This stopped it";
   x = strtod( string, &stopstring );
   printf( "string = %s\n", string );
   printf("   strtod = %f\n", x );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "-10110134932This stopped it";
   l = strtol( string, &stopstring, 10 );
   printf( "string = %s\n", string );
   printf("   strtol = %ld\n", l );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "10110134932";
   printf( "string = %s\n", string );

   // Convert string using base 2, 4, and 8:
   for( base = 2; base <= 8; base *= 2 )
   {
      // Convert the string:
      ul = strtoul( string, &stopstring, base );
      printf( "   strtol = %ld (base %d)\n", ul, base );
      printf( "   Stopped scan at: %s\n", stopstring );
   }
}
```

```Output
string = 3.1415926This stopped it
   strtod = 3.141593
   Stopped scan at: This stopped it

string = -10110134932This stopped it
   strtol = -2147483648
   Stopped scan at: This stopped it

string = 10110134932
   strtol = 45 (base 2)
   Stopped scan at: 34932
   strtol = 4423 (base 4)
   Stopped scan at: 4932
   strtol = 2134108 (base 8)
   Stopped scan at: 932
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[マルチバイト文字シーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[文字列を数値に変換する関数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
