---
description: 詳細については、以下を参照してください。
title: feraiseexcept
ms.date: 04/05/2018
api_name:
- feraiseexcept
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
- HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: 8e7a06006cfdc768fdaa306bc293857f1c375b90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124944"
---
# <a name="feraiseexcept"></a>feraiseexcept

指定した浮動小数点例外を発生させます。

## <a name="syntax"></a>構文

```C
int feraiseexcept(
   int excepts
);
```

### <a name="parameters"></a>パラメーター

*removed*<br/>
発生させる浮動小数点例外。

## <a name="return-value"></a>戻り値

指定したすべての例外が正常に発生した場合は、0 を返します。

## <a name="remarks"></a>解説

は、 *removed* によって指定された浮動小数点例外を発生させよう **として** います。   は、次のように定義さ **れたこれら** の例外マクロをサポートしてい \<fenv.h> ます。

|例外処理マクロ|説明|
|---------------------|-----------------|
|FE_DIVBYZERO|前の浮動小数点演算で特異点エラーまたは極エラーが発生しました。無限大の値が作成されました。|
|FE_INEXACT|前の浮動小数点演算の格納結果は強制的に丸められました。|
|FE_INVALID|前の浮動小数点演算でドメイン エラーが発生しました。|
|FE_OVERFLOW|範囲エラーが発生しました。前の浮動小数点演算結果は大きすぎて表現できませんでした。|
|FE_UNDERFLOW|前の浮動小数点演算結果は小さすぎて最大有効桁数で表現できませんでした。|
|FE_ALL_EXCEPT|すべてのサポートされる浮動小数点例外のビット演算 OR。|

*Removed* 引数には、0、例外マクロ値の1つ、またはサポートされている2つ以上の例外マクロのビットごとの or を指定できます。 指定した例外処理マクロのいずれかが FE_OVERFLOW または FE_UNDERFLOW の場合、副作用として FE_INEXACT 例外が発生する可能性があります。

この関数を使用するには、呼び出しの前に `#pragma fenv_access(on)` ディレクティブを使用してアクセスを妨げる可能性のある浮動小数点の最適化をオフにする必要があります。 詳細については、「 [fenv_access](../../preprocessor/fenv-access.md)」を参照してください。

**Microsoft 固有:***Removed* で指定された例外は、FE_INVALID、FE_DIVBYZERO、FE_OVERFLOW、FE_UNDERFLOW、FE_INEXACT の順序で発生します。 ただし、 *removed* で指定されていない場合でも、FE_OVERFLOW または FE_UNDERFLOW が発生したときに FE_INEXACT を発生させることができます。

## <a name="requirements"></a>要件

|機能|C ヘッダー|C++ ヘッダー|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h>|\<cfenv>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[アルファベット順の関数リファレンス](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
