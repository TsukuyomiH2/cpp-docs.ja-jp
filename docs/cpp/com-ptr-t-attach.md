---
description: '詳細については、「_com_ptr_t:: Attach」を参照してください。'
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 5b27a4bd6572f2f1429766328c01f377672ee11d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295654"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Microsoft 固有の仕様**

このスマート ポインターの型の生のインターフェイス ポインターをカプセル化します。

## <a name="syntax"></a>構文

```cpp
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>パラメーター

*pInterface*<br/>
生のインターフェイス ポインター。

*fAddRef*<br/>
の場合は **`true`** 、 `AddRef` が呼び出されます。 の場合 **`false`** 、オブジェクトはを呼び出さずに、 `_com_ptr_t` 生のインターフェイスポインターの所有権を取得し `AddRef` ます。

## <a name="remarks"></a>解説

- **Attach (**  *pinterface*  **)** `AddRef` が呼び出されていません。 インターフェイスの所有権は、この `_com_ptr_t` オブジェクトに渡されます。 `Release` は、以前にカプセル化されたポインターの参照カウントをデクリメントするために呼び出されます。

- **Attach (***pinterface* **,***faddref***)***Faddref* がの場合 **`true`** 、 `AddRef` は、カプセル化されたインターフェイスポインターの参照カウントをインクリメントするために呼び出されます。       *Faddref* がの場合 **`false`** 、このオブジェクトはを呼び出さずに、 `_com_ptr_t` 生のインターフェイスポインターの所有権を取得し `AddRef` ます。 `Release` は、以前にカプセル化されたポインターの参照カウントをデクリメントするために呼び出されます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_ptr_t クラス](../cpp/com-ptr-t-class.md)
