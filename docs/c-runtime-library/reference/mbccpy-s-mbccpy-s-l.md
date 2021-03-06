---
description: '詳細については、次を参照してください: _mbccpy_s、_mbccpy_s_l'
title: _mbccpy_s、_mbccpy_s_l
ms.date: 4/2/2020
api_name:
- _mbccpy_s
- _mbccpy_s_l
- _o__mbccpy_s
- _o__mbccpy_s_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
ms.openlocfilehash: 6764c100fb52b025db2d8f79a72c7c6420a64bee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303532"
---
# <a name="_mbccpy_s-_mbccpy_s_l"></a>_mbccpy_s、_mbccpy_s_l

文字列のマルチバイト文字 1 個を他の文字列にコピーします。 これらのバージョンの [_mbccpy、_mbccpy_l](mbccpy-mbccpy-l.md) は、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」で説明されているように、セキュリティが強化されています。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
errno_t _mbccpy_s(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src
);
errno_t _mbccpy_s_l(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src,
   locale_t locale
);
template <size_t size>
errno_t _mbccpy_s(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbccpy_s_l(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src,
   locale_t locale
); // C++ only
```

### <a name="parameters"></a>パラメーター

*先*<br/>
コピー先。

*buffSizeInBytes*<br/>
コピー先のバッファーのサイズ。

*pCopied*<br/>
コピーされたバイト数が格納されます (正常終了した場合は 1 または 2)。 数値が気にならない場合は、 **NULL** を渡します。

*src*<br/>
コピーするマルチバイト文字。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。 *Src* または *dest* が **NULL** の場合、または **buffSizeinBytes** バイト以上が *Dest* にコピーされる場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、関数は **einval** を返し、 **errno** は **einval** に設定されます。

## <a name="remarks"></a>解説

**_Mbccpy_s** 関数は、 *src* から *dest* に1つのマルチバイト文字をコピーします。 [_Ismbblead](ismbblead-ismbblead-l.md)への暗黙的な呼び出しによって、 *src* がマルチバイト文字の先行バイトを指していない場合、 *src* が指す1バイトがコピーされます。 *Src* が先行バイトを指していても、次のバイトが0であるため無効である場合、0は *dest* にコピーされ、 **errno** は **EILSEQ** に設定され、関数は **EILSEQ** を返します。

**_mbccpy_s** は null 終端文字を追加しません。ただし、 *src* が null 文字を指している場合、その null は *dest* にコピーされます (これは通常の1バイトのコピーにすぎません)。

「 *Pcopied* 」の値には、コピーされたバイト数が格納されます。 操作が正常に終了した場合は、1 と 2 のどちらかの値となります。 **NULL** が渡された場合、このパラメーターは無視されます。

|*src*|*dest* にコピー済み|*pCopied*|戻り値|
|-----------|----------------------|---------------|------------------|
|先行バイト以外|先行バイト以外|1|0|
|0|0|1|0|
|後続が 0 以外の先行バイト|後続が 0 以外の先行バイト|2|0|
|後続が 0 以外の先行バイト|0|1|**EILSEQ**|

2 行目は、単に 1 行目の特殊なケースです。 また、このテーブルでは *buffSizeInBytes*  >=  *pcopied* が想定されていることに注意してください。

**_mbccpy_s** は、ロケールに依存する動作に現在のロケールを使用します。 **_mbccpy_s_l** は **_mbccpy_s** と同じですが、 **_mbccpy_s_l** はロケールに依存する動作に渡されたロケールを使用する点が異なります。

C++ では、テンプレートのオーバーロードによってこれらの関数を簡単に使用できます。オーバーロードでは、バッファー長を自動的に推論できるため、サイズ引数を指定する必要がなくなります。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|マクロまたはインライン関数に割り当てる。|**_mbccpy_s**|マクロまたはインライン関数に割り当てる。|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[ロケール](../../c-runtime-library/locale.md)<br/>
[Multibyte-Character シーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
