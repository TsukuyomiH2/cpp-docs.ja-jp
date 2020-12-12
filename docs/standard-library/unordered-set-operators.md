---
description: 詳細については、「 &lt; unordered_set 演算子」を参照してください。 &gt;
title: '&lt;unordered_set&gt; operators'
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::operator!=
- unordered_set/std::operator==
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
ms.openlocfilehash: 6404ea9348dedea1e8ecdd4eefbca6b7c1b8158f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153734"
---
# <a name="ltunordered_setgt-operators"></a>&lt;unordered_set&gt; operators

## <a name="operator"></a><a name="op_neq"></a> operator! =

演算子の左側にある [unordered_set](../standard-library/unordered-set-class.md) オブジェクトが、右側にある unordered_set オブジェクトと等しくないかどうかをテストします。

```cpp
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
`unordered_set` 型のオブジェクト。

*そうです*\
`unordered_set` 型のオブジェクト。

### <a name="return-value"></a>戻り値

**`true`** unordered_sets が等しくない場合は。 **`false`** 等しい場合は。

### <a name="remarks"></a>解説

unordered_set オブジェクト間の比較は、要素を任意の順序で格納することによる影響を受けません。 同じ数の要素が存在しており、一方のコンテナー内の要素がもう一方のコンテナー内の要素の並べ替えである場合、2 つの unordered_set は等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// unordered_set_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

**出力:**

`c1 != c2: true`

`c1 != c3: false`

`c2 != c3: true`

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

演算子の左側にある [unordered_set](../standard-library/unordered-set-class.md) オブジェクトが、右側にある unordered_set オブジェクトと等しいかどうかをテストします。

```cpp
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
`unordered_set` 型のオブジェクト。

*そうです*\
`unordered_set` 型のオブジェクト。

### <a name="return-value"></a>戻り値

**`true`** unordered_sets が等しい場合は。 **`false`** 等しくない場合。

### <a name="remarks"></a>解説

unordered_set オブジェクト間の比較は、要素を任意の順序で格納することによる影響を受けません。 同じ数の要素が存在しており、一方のコンテナー内の要素がもう一方のコンテナー内の要素の並べ替えである場合、2 つの unordered_set は等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// unordered_set_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```

## <a name="operator-multiset"></a><a name="op_neq_unordered_multiset"></a> operator! = (マルチセット)

演算子の左側の [unordered_multiset](../standard-library/unordered-multiset-class.md) オブジェクトが右側の unordered_multiset オブジェクトと等しくないかどうかをテストします。

```cpp
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
`unordered_multiset` 型のオブジェクト。

*そうです*\
`unordered_multiset` 型のオブジェクト。

### <a name="return-value"></a>戻り値

**`true`** unordered_multisets が等しくない場合は。 **`false`** 等しい場合は。

### <a name="remarks"></a>解説

unordered_multiset オブジェクト間の比較は、要素を任意の順序で格納することによる影響を受けません。 同じ数の要素が存在しており、一方のコンテナー内の要素がもう一方のコンテナー内の要素の並べ替えである場合、2 つの unordered_multisets は等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// unordered_multiset_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

```Output
c1 != c2: true
c1 != c3: false
c2 != c3: true
```

## <a name="operator-multiset"></a><a name="op_eq_eq_unordered_multiset"></a> operator = = (マルチセット)

演算子の左側の [unordered_multiset](../standard-library/unordered-multiset-class.md) オブジェクトが右側の unordered_multiset オブジェクトと等しいかどうかをテストします。

```cpp
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
`unordered_multiset` 型のオブジェクト。

*そうです*\
`unordered_multiset` 型のオブジェクト。

### <a name="return-value"></a>戻り値

**`true`** unordered_multisets が等しい場合は。 **`false`** 等しくない場合。

### <a name="remarks"></a>解説

unordered_multiset オブジェクト間の比較は、要素を任意の順序で格納することによる影響を受けません。 同じ数の要素が存在しており、一方のコンテナー内の要素がもう一方のコンテナー内の要素の並べ替えである場合、2 つの unordered_multisets は等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// unordered_multiset_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```
