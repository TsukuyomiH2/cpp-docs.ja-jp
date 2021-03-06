---
description: '詳細情報: allocator_chunklist クラス'
title: allocator_chunklist クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
ms.openlocfilehash: 91213b97059f135e0800ae81dd3f6b4966b24c7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163614"
---
# <a name="allocator_chunklist-class"></a>allocator_chunklist クラス

[cache_chunklist](cache-chunklist-class.md) 型のキャッシュを使用して、オブジェクトに対してストレージの割り当てと解放を管理するオブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
template <class Type>
class allocator_chunklist;
```

### <a name="parameters"></a>パラメーター

*各種*\
アロケーターによって割り当てられた要素の型。

## <a name="remarks"></a>解説

[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)マクロは、次のステートメントでこのクラスを *name* パラメーターとして渡します。`ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>要件

**ヘッダー:**\<allocators>

**名前空間:** stdext

## <a name="see-also"></a>関連項目

[\<allocators>](allocators-header.md)
