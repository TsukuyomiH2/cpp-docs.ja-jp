---
description: '詳細情報: add_const クラス'
title: add_const クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_const
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
ms.openlocfilehash: ce1dd895a5968234feca7905d3b9f8d571336053
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319945"
---
# <a name="add_const-class"></a>add_const クラス

型から const 型を作成します。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct add_const;
```

### <a name="parameters"></a>パラメーター

*~*\
変更する型。

## <a name="remarks"></a>解説

この型修飾子のインスタンスは、 *ty* が参照、関数、または const で修飾さ *れた型である場合は*、修飾型を保持します。それ以外の場合は、を保持 `const Ty` します。

## <a name="example"></a>例

```cpp
// std__type_traits__add_const.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
{
    std::add_const<int>::type *p = (const int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_const<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_const<int> == int
```

## <a name="requirements"></a>要件

**ヘッダー:**\<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](type-traits.md)\
[remove_const クラス](remove-const-class.md)
