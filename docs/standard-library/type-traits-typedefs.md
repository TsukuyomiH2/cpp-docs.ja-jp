---
title: '&lt;type_traits&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::false_type
- xtr1common/std::false_type
- type_traits/std::true_type
- xtr1common/std::true_type
ms.assetid: 8ac040ca-ed2d-4570-adc9-cb5626530053
ms.openlocfilehash: 784bcfa5325e74180d3981a98cda530d839ab9f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367976"
---
# <a name="lttype_traitsgt-typedefs"></a>&lt;type_traits&gt; typedef

|||
|-|-|
|[false_type](#false_type)|[true_type](#true_type)|

## <a name="false_type-typedef"></a><a name="false_type"></a>false_type・タイプ定義

false 値を持つ整数定数を保持します。

```cpp
typedef integral_constant<bool, false> false_type;
```

### <a name="remarks"></a>解説

この型は、テンプレート `integral_constant` から特化したテンプレートのシノニムです。

### <a name="example"></a>例

```cpp
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="true_type-typedef"></a><a name="true_type"></a>true_typeタイプデフ

true 値を持つ整数定数を保持します。

```cpp
typedef integral_constant<bool, true> true_type;
```

### <a name="remarks"></a>解説

この型は、テンプレート `integral_constant` から特化したテンプレートのシノニムです。

### <a name="example"></a>例

```cpp
// std__type_traits__true_type.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
