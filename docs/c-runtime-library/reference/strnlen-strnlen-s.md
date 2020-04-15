---
title: strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l
ms.date: 4/2/2020
api_name:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
- _o__mbsnlen
- _o__mbsnlen_l
- _o__mbstrnlen
- _o__mbstrnlen_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
ms.openlocfilehash: db4fa65fa47dfe11d7ab56ffc5feee06f2634e2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364472"
---
# <a name="strnlen-strnlen_s-wcsnlen-wcsnlen_s-_mbsnlen-_mbsnlen_l-_mbstrnlen-_mbstrnlen_l"></a>strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l

現在のロケールまたは渡されたロケールを使用して、文字列の長さを取得します。 これらは、[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md) のセキュリティを強化したバージョンです。

> [!IMPORTANT]
> **_mbsnlen**、 **_mbsnlen_l**、 **_mbstrnlen**、および **_mbstrnlen_l**は、 Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
size_t strnlen(
   const char *str,
   size_t numberOfElements
);
size_t strnlen_s(
   const char *str,
   size_t numberOfElements
);
size_t wcsnlen(
   const wchar_t *str,
   size_t numberOfElements
);
size_t wcsnlen_s(
   const wchar_t *str,
   size_t numberOfElements
);
size_t _mbsnlen(
   const unsigned char *str,
   size_t numberOfElements
);
size_t _mbsnlen_l(
   const unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
size_t _mbstrnlen(
   const char *str,
   size_t numberOfElements
);
size_t _mbstrnlen_l(
   const char *str,
   size_t numberOfElements,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*Str*<br/>
NULL で終わる文字列。

*要素の数*<br/>
文字列バッファーのサイズ。

*ロケール*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

これらの関数は、文字列内の文字数を返します (終端の null 文字は含まれません)。 文字列の最初の*数 OfElements*バイト (または**wcsnlen**のワイド文字) に null 終端文字がない場合は、エラー状態を示すために*numberOfElements*が返されます。null で終わる文字列の長さは、*厳密には数の OfElements*より小さい長さです。

**_mbstrnlen**し、文字列に無効なマルチバイト文字が含まれている場合は -1 を返 **_mbstrnlen_l。**

## <a name="remarks"></a>解説

> [!NOTE]
> **strnlen**は**strlen**の代わりではありません。**strnlen**は、ネットワーク パケットなどの既知のサイズのバッファ内の、信頼されていない受信データのサイズを計算するためだけに使用されます。 **strnlen**は長さを計算しますが、文字列が終了していない場合はバッファーの末尾を超えません。 その他の状況では、 **strlen**を使用します。 **(wcsnlen**、 **_mbsnlen**、および **_mbstrnlen**についても同じです。

これらの関数は、終端の NULL 文字を含め *、str*内の文字数を返します。 ただし **、strnlen**と**strnlen_s**は文字列を 1 バイト文字ストリングとして解釈するため、文字列にマルチバイト文字が含まれている場合でも、戻り値は常にバイト数と等しくなります。 **wcsnlen**と**wcsnlen_s**はそれぞれ**strnlen**および**strnlen_s**のワイド文字バージョンです。**wcsnlen**と**wcsnlen_s**の引数はワイド文字ストリングであり、文字の数はワイド文字単位です。 それ以外**の場合は、wcsnlen**と**strnlen**は **、strnlen_s**と**wcsnlen_s**と同じように動作します。

**strnlen** **、wcsnlen**、**および_mbsnlen**は、パラメーターを検証しません。 *str*が**NULL**の場合、アクセス違反が発生します。

**パラメーターをstrnlen_s****してwcsnlen_s**検証します。 *str*が**NULL**の場合、関数は 0 を返します。

**_mbstrnlen**もパラメーターを検証します。 *str*が**NULL**の場合、または*numberOfElements*が**INT_MAX**より大きい場合 **、_mbstrnlen**はパラメーター[の検証](../../c-runtime-library/parameter-validation.md)の説明に従って無効なパラメーター例外を生成します。 実行を続行できる場合 **、_mbstrnlen**は**errno**を**EINVAL**に設定し、-1 を返します。

既定では、この関数のグローバル状態はアプリケーションにスコープされます。 これを変更するには[、CRT のグローバル状態を](../global-state.md)参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen**と **_mbstrnlen**は、マルチバイト文字の文字列のマルチバイト文字の数を返します。 **_mbsnlen**は、現在使用されているマルチバイト コード ページ、または渡されたロケールに従ってマルチバイト文字シーケンスを認識します。マルチバイト文字の有効性はテストされません。 **_mbstrnlenは**、マルチバイト文字の妥当性をテストし、マルチバイト文字シーケンスを認識します。 **_mbstrnlen**に渡された文字列に無効なマルチバイト文字が含まれている場合 **、errno**は**EILSEQ**に設定されます。

出力値は、ロケールの**LC_CTYPE**カテゴリ設定の設定によって影響されます。詳細については[、setlocale を参照_wsetlocale。](setlocale-wsetlocale.md) これらの関数のバージョンは同じですが **、_l**サフィックスを持たない関数は、このロケールに依存する動作に現在のロケールを使用し、**代わりに_l**サフィックスを持つバージョンが渡されるロケール パラメーターを使用します。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチン|必須ヘッダー|
|-------------|---------------------|
|**ストルンレン**, **strnlen_s**|\<string.h>|
|**wcsnlen**, **wcsnlen_s**|\<string.h> または \<wchar.h>|
|**_mbsnlen**, **_mbsnlen_l**|\<mbstring.h>|
|**_mbstrnlen**, **_mbstrnlen_l**|\<stdlib.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_strnlen.c

#include <string.h>

int main()
{
   // str1 is 82 characters long. str2 is 159 characters long

   char* str1 = "The length of a string is the number of characters\n"
               "excluding the terminating null.";
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"
                "than the maximum size specified, the maximum size is\n"
                "returned rather than the actual size of the string.";
   size_t len;
   size_t maxsize = 100;

   len = strnlen(str1, maxsize);
   printf("%s\n Length: %d \n\n", str1, len);

   len = strnlen(str2, maxsize);
   printf("%s\n Length: %d \n", str2, len);
}
```

```Output
The length of a string is the number of characters
excluding the terminating null.
Length: 82

strnlen takes a maximum size. If the string is longer
than the maximum size specified, the maximum size is
returned rather than the actual size of the string.
Length: 100
```

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字シーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[関数](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
