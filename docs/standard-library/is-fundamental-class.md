---
description: '詳細情報: is_fundamental クラス'
title: is_fundamental クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_fundamental
helpviewer_keywords:
- is_fundamental class
- is_fundamental
ms.assetid: b84eee84-2fb2-4611-beaf-b384074d8b6a
ms.openlocfilehash: 83af1491eb92f111a36e89f1511a71b48d784c73
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230953"
---
# <a name="is_fundamental-class"></a>is_fundamental クラス

型が void であるか数値型であるかを調べます。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_fundamental;
```

### <a name="parameters"></a>パラメーター

*~*\
照会する型。

## <a name="remarks"></a>解説

型 *Ty* が基本型、つまり、、 **`void`** 整数型、浮動小数点型、またはそのいずれかの形式である場合、型述語のインスタンスは true を保持し `cv-qualified` ます。それ以外の場合は、false を保持します。

## <a name="example"></a>例

```cpp
// std__type_traits__is_fundamental.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_fundamental<trivial> == " << std::boolalpha
        << std::is_fundamental<trivial>::value << std::endl;
    std::cout << "is_fundamental<int> == " << std::boolalpha
        << std::is_fundamental<int>::value << std::endl;
    std::cout << "is_fundamental<const float> == " << std::boolalpha
        << std::is_fundamental<const float>::value << std::endl;
    std::cout << "is_fundamental<void> == " << std::boolalpha
        << std::is_fundamental<void>::value << std::endl;

    return (0);
    }
```

```Output
is_fundamental<trivial> == false
is_fundamental<int> == true
is_fundamental<const float> == true
is_fundamental<void> == true
```

## <a name="requirements"></a>要件

**ヘッダー:**\<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[is_compound クラス](../standard-library/is-compound-class.md)
