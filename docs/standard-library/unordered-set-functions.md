---
description: '詳細情報: &lt; unordered_set &gt; 関数'
title: '&lt;unordered_set&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::swap (set)
- unordered_set/std::swap (unordered_multiset)
ms.assetid: 66b35671-4023-4411-ad50-83786580d8ee
ms.openlocfilehash: 852536a5c5bdfe5d944f3b70581a313a56dc8742
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153760"
---
# <a name="ltunordered_setgt-functions"></a>&lt;unordered_set&gt; 関数

## <a name="swap-unordered_set"></a><a name="swap"></a> swap (unordered_set)

2 つのコンテナーのコンテンツを交換します。

```cpp
template <class Key, class Hash, class Pred, class Alloc>
void swap(
   unordered_set <Key, Hash, Pred, Alloc>& left,
   unordered_set <Key, Hash, Pred, Alloc>& right);
```

### <a name="parameters"></a>パラメーター

*レジストリ*\
キーの型。

*ハッシュ*\
ハッシュ関数のオブジェクト型。

*Pred*\
等価比較関数のオブジェクト型。

*割り当て*\
アロケーター クラス。

*左側*\
スワップする最初のコンテナー。

*そうです*\
スワップする 2 番目のコンテナー。

### <a name="remarks"></a>解説

このテンプレート関数は `left.` [unordered_set:: swap](../standard-library/unordered-set-class.md#swap) `(right)` を実行します。

### <a name="example"></a>例

```cpp
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
Myset c1;

c1.insert('a');
c1.insert('b');
c1.insert('c');

// display contents " [c] [b] [a]"
for (Myset::const_iterator it = c1.begin();
it != c1.end(); ++it)
std::cout << " [" << *it << "]";
std::cout << std::endl;

Myset c2;

c2.insert('d');
c2.insert('e');
c2.insert('f');

c1.swap(c2);

// display contents " [f] [e] [d]"
for (Myset::const_iterator it = c1.begin();
it != c1.end(); ++it)
std::cout << " [" << *it << "]";
std::cout << std::endl;

swap(c1, c2);

// display contents " [c] [b] [a]"
for (Myset::const_iterator it = c1.begin();
it != c1.end(); ++it)
std::cout << " [" << *it << "]";
std::cout << std::endl;

return (0);
}
```

```Output
[c] [b] [a]
[f] [e] [d]
[c] [b] [a]
```

## <a name="swap-unordered_multiset"></a><a name="swap_unordered_multiset"></a> swap (unordered_multiset)

2 つのコンテナーのコンテンツを交換します。

```cpp
template <class Key, class Hash, class Pred, class Alloc>
void swap(
   unordered_multiset <Key, Hash, Pred, Alloc>& left,
   unordered_multiset <Key, Hash, Pred, Alloc>& right);
```

### <a name="parameters"></a>パラメーター

*レジストリ*\
キーの型。

*ハッシュ*\
ハッシュ関数のオブジェクト型。

*Pred*\
等価比較関数のオブジェクト型。

*割り当て*\
アロケーター クラス。

*左側*\
スワップする最初のコンテナー。

*そうです*\
スワップする 2 番目のコンテナー。

### <a name="remarks"></a>解説

このテンプレート関数は `left.` [unordered_multiset:: swap](../standard-library/unordered-multiset-class.md#swap) `(right)` を実行します。

### <a name="example"></a>例

```cpp
// std__unordered_set__u_ms_swap.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    Myset c2;

    c2.insert('d');
    c2.insert('e');
    c2.insert('f');

    c1.swap(c2);

    // display contents " [f] [e] [d]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[f] [e] [d]
[c] [b] [a]
```
