---
description: '詳細については、次を参照してください: _RTC_SetErrorFunc'
title: _RTC_SetErrorFunc
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorFunc
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- RTC_SetErrorFunc
- _RTC_SetErrorFunc
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
ms.openlocfilehash: 454fd54e0960e8ce52c94b4e4a1e0a93ea99d3eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268939"
---
# <a name="_rtc_seterrorfunc"></a>_RTC_SetErrorFunc

実行時エラー チェック (RTC) を報告するためのハンドラーとして関数を指定します。 この関数は非推奨とされます。代わりに **_RTC_SetErrorFuncW** を使用してください。

## <a name="syntax"></a>構文

```C
_RTC_error_fn _RTC_SetErrorFunc(
   _RTC_error_fn function
);
```

### <a name="parameters"></a>パラメーター

*function*<br/>
実行時エラー チェックを処理する関数のアドレス。

## <a name="return-value"></a>戻り値

以前に定義されたエラーの関数。 以前に定義された関数がない場合、は **NULL** を返します。

## <a name="remarks"></a>解説

この関数は使用しないでください。代わりに、 **_RTC_SetErrorFuncW** を使用します。 これは下位互換性のためだけに残されています。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_RTC_SetErrorFunc**|\<rtcapi.h>|

詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>関連項目

[_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[ランタイム エラー チェック](../../c-runtime-library/run-time-error-checking.md)<br/>
