---
description: '詳細情報: is_abstract クラス'
title: is_abstract クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_abstract
helpviewer_keywords:
- is_abstract class
- is_abstract
ms.assetid: 8867f660-3434-404c-ba90-c26607a5e0d2
ms.openlocfilehash: 9b2fe31d2f4e742381c4e2e76a668d4e68e76b75
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323888"
---
# <a name="is_abstract-class"></a>is_abstract クラス

型が抽象クラスであるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_abstract;
```

### <a name="parameters"></a>パラメーター

*~*\
照会する型。

## <a name="remarks"></a>解説

型 *Ty* が1つ以上の純粋仮想関数を持つクラスである場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

## <a name="example"></a>例

```cpp
// std__type_traits__is_abstract.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct abstract
    {
    virtual int val() = 0;
    };

int main()
    {
    std::cout << "is_abstract<trivial> == " << std::boolalpha
        << std::is_abstract<trivial>::value << std::endl;
    std::cout << "is_abstract<abstract> == " << std::boolalpha
        << std::is_abstract<abstract>::value << std::endl;

    return (0);
    }
```

```Output
is_abstract<trivial> == false
is_abstract<abstract> == true
```

## <a name="requirements"></a>要件

**ヘッダー:**\<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[is_polymorphic クラス](../standard-library/is-polymorphic-class.md)
