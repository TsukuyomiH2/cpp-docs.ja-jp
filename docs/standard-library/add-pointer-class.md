---
title: add_pointer クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_pointer
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
ms.openlocfilehash: 8adeffd0352d04fe844b286ea7456c66e907a0a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619259"
---
# <a name="add_pointer-class"></a>add_pointer クラス

指定された型から型へのポインターを作成します。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>パラメーター

*\T*\
変更する型。

## <a name="remarks"></a>Remarks

このメンバー **typedef**は `type` 、と同じ型に名前を付け `remove_reference<T>::type*` ます。 エイリアス `add_pointer_t` は、メンバー **typedef**にアクセスするためのショートカットです `type` 。

参照からポインターを作成することは無効であるため、`add_pointer` は型へのポインターを作成する前に、指定された型から参照を削除します (存在する場合)。 その結果、型が参照であるかどうかを気にすることなく、型を `add_pointer` で使用できます。

## <a name="example"></a>例

次の例では、型の `add_pointer` がその型へのポインターと同じであることを示します。

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>必要条件

**ヘッダー:**\<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](type-traits.md)\
[remove_pointer クラス](remove-pointer-class.md)
