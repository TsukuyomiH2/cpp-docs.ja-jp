---
description: '詳細については、次を参照してください: _com_error:: WCodeToHRESULT'
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: 9925c34f14f0685cb563e37a8cae0970911f009c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295719"
---
# <a name="_com_errorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Microsoft 固有の仕様**

16ビット *Wcode* を32ビット HRESULT にマップします。

## <a name="syntax"></a>構文

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>パラメーター

*wCode*<br/>
32ビットの HRESULT にマップされる16ビットの *Wcode* 。

## <a name="return-value"></a>戻り値

16ビットの *Wcode* からマップされた32ビットの HRESULT。

## <a name="remarks"></a>解説

[Wcode](../cpp/com-error-wcode.md)メンバー関数を参照してください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error クラス](../cpp/com-error-class.md)
