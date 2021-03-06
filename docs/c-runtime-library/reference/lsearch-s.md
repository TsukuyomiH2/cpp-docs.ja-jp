---
description: '詳細については、次を参照してください: _lsearch_s'
title: _lsearch_s
ms.date: 4/2/2020
api_name:
- _lsearch_s
- _o__lsearch_s
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
- _lsearch_s
- lsearch_s
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
ms.openlocfilehash: fdc3d8011dac00cd8d19fe414c2ae1aa78120eee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299957"
---
# <a name="_lsearch_s"></a>_lsearch_s

値の線形探索を実行します。 「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [_lsearch](lsearch.md) です。

## <a name="syntax"></a>構文

```C
void *_lsearch_s(
   const void *key,
   void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
検索するオブジェクト。

*base*<br/>
検索する配列のベースへのポインター。

*number*<br/>
要素の数。

*size*<br/>
バイト単位での配列の各要素のサイズ。

*対照*<br/>
比較ルーチンへのポインター。 2 番目のパラメーターは、検索用のキーへのポインターです。 3 番目のパラメーターは、そのキーと比較する配列要素へのポインターです。

*context*<br/>
比較関数内でアクセスされることのあるオブジェクトへのポインター。

## <a name="return-value"></a>戻り値

*キー* が見つかった場合、 **_lsearch_s** は、*キー* に一致する *ベース* の配列の要素へのポインターを返します。 *キー* が見つからない場合、 **_lsearch_s** は配列の末尾に新しく追加された項目へのポインターを返します。

この関数に無効なパラメーターが渡されると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno** は **EINVAL** に設定され、関数は **NULL** を返します。 詳細については、「[errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

### <a name="error-conditions"></a>エラー条件

|*key*|*base*|*対照*|*number*|*size*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NULL**|any|any|any|any|**EINVAL**|
|any|**NULL**|any|!= 0|any|**EINVAL**|
|any|any|any|any|ゼロ|**EINVAL**|
|any|any|**NULL**|1 つ|any|**EINVAL**|

## <a name="remarks"></a>解説

**_Lsearch_s** 関数は、*数値* 要素の配列内の値 *キー* の線形検索を実行します (各 *幅* バイト)。 **Bsearch_s** とは異なり、 **_lsearch_s** では配列を並べ替える必要はありません。 *キー* が見つからない場合は、 **_lsearch_s** 配列の末尾に追加し、*数値* をインクリメントします。

*Compare* 関数は、2つの配列要素を比較し、それらの関係を指定する値を返すユーザー指定のルーチンへのポインターです。 また、 *compare* 関数は、コンテキストへのポインターを最初の引数として受け取ります。 **_lsearch_s** 呼び出しは、検索中に1回以上の繰り返しを *比較* し、各呼び出しで2つの配列要素へのポインターを渡します。 *比較* では、要素を比較し、0以外 (要素が異なる場合) または 0 (要素が同じであることを意味します) のいずれかを返す必要があります。

*コンテキスト* ポインターは、検索対象のデータ構造体がオブジェクトの一部であり、 *compare* 関数がオブジェクトのメンバーにアクセスする必要がある場合に役立ちます。 たとえば、 *compare* 関数のコードでは、void ポインターを適切なオブジェクト型にキャストし、そのオブジェクトのメンバーにアクセスできます。 *コンテキスト* ポインターを追加すると、 **_lsearch_s** のセキュリティが強化されます。これは、*比較* 関数でデータを使用できるようにするために静的変数を使用する場合に関連する再入バグを回避するためにコンテキストを追加できるためです。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[検索と並べ替え](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
