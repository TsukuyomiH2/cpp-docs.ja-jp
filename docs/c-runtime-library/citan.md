---
title: _CItan
ms.date: 4/2/2020
api_name:
- _CItan
- _o__CItan
api_location:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CItan
- CItan
helpviewer_keywords:
- CItan intrinsic
- _CItan intrinsic
ms.assetid: d1ea3113-50a2-45a6-b6bc-680fcdcc0928
ms.openlocfilehash: 8c6cc0a51d6ef2132172164306b84f73799da729
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349362"
---
# <a name="_citan"></a>_CItan

浮動小数点スタックのトップ値のタンジェントを計算します。

## <a name="syntax"></a>構文

```C
void __cdecl _CItan();
```

## <a name="remarks"></a>解説

このバージョンの [tan](../c-runtime-library/reference/tan-tanf-tanl.md) 関数には、コンパイラで認識される特殊な呼び出し規則があります。 この関数は、コピーの生成を防ぎ、レジスタ割り当てが容易になるため、実行時間が短縮されます。

結果の値は、浮動小数点スタックのトップにプッシュされます。

既定では、この関数のグローバル状態はアプリケーションにスコープされます。 これを変更するには[、CRT のグローバル状態を](global-state.md)参照してください。

## <a name="requirements"></a>必要条件

**プラットフォーム:** x86

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[tan、tanf、tanl](../c-runtime-library/reference/tan-tanf-tanl.md)<br/>
