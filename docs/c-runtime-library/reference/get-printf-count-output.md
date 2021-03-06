---
description: '詳細については、次を参照してください: _get_printf_count_output'
title: _get_printf_count_output
ms.date: 11/04/2016
api_name:
- _get_printf_count_output
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
ms.openlocfilehash: fe5ee728b7bc8400cd93ec4e93131496d59334c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339007"
---
# <a name="_get_printf_count_output"></a>_get_printf_count_output

[Printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)ファミリの各関数が **% n** 形式をサポートするかどうかを示します。

## <a name="syntax"></a>構文

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>戻り値

**% N** がサポートされている場合は0以外、 **% n** がサポートされていない場合は0です。

## <a name="remarks"></a>解説

**% N** がサポートされていない場合 (既定)、いずれかの **printf** 関数の書式指定文字列で **% n** を検出すると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 **% N** サポートが有効になっている場合 ( [_set_printf_count_output](set-printf-count-output.md)を参照)、 **% n** は [書式指定構文: printf 関数と wprintf 関数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)の説明に従って動作します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

例については「[_set_printf_count_output](set-printf-count-output.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[_set_printf_count_output](set-printf-count-output.md)<br/>
