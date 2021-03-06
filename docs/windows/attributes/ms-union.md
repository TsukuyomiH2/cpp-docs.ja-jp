---
description: '詳細については、次を参照してください: ms_union'
title: ms_union (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ms_union
helpviewer_keywords:
- ms_union attribute
ms.assetid: bb548689-6962-457e-af56-8ffdf68987eb
ms.openlocfilehash: a2083fd4f1acb3715edd0e194c64e03e98db9b7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329779"
---
# <a name="ms_union"></a>ms_union

カプセル化されていない共用体のネットワークデータ表現の配置を制御します。

## <a name="syntax"></a>構文

```cpp
[ms_union]
```

## <a name="remarks"></a>解説

**Ms_union** C++ 属性には、 [ms_union](/windows/win32/Midl/ms-union-attrib) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

次のコードは、 **ms_union** の配置を示しています。

```cpp
// cpp_attr_ref_ms_union.cpp
// compile with: /LD
#include <unknwn.h>
[object, ms_union, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl {
   HRESULT DisplayString([in, string] char * p1);
};

[export, switch_type(short)] union _WILLIE_UNION_TYPE  {
   [case(24)]
      float fMays;
   [case(25)]
      double dMcCovey;
   [default]
      int x;
};

[public] typedef _WILLIE_UNION_TYPE WILLIE_UNION_TYPE;

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>要件

| 属性コンテキスト | 値 |
|-|-|
|**適用対象**|カプセル化されていない共用体|
|**Repeatable**|いいえ|
|**必須属性**|なし|
|**無効な属性**|`dispinterface`|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 属性](typedef-enum-union-and-struct-attributes.md)
