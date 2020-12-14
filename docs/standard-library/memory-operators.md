---
description: 詳細については、「 &lt; memory operators」を参照してください。 &gt;
title: '&lt;memory&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- memory/std::operator!=
- memory/std::operator>
- memory/std::operator>=
- memory/std::operator<
- memory/std::operator<=
- memory/std::operator<<
- memory/std::operator==
ms.assetid: 257e3ba9-c4c2-4ae8-9b11-b156ba9c28de
ms.openlocfilehash: cbf52aa2af13a0eae241444d88e0eeabe7efe47b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183946"
---
# <a name="ltmemorygt-operators"></a>&lt;memory&gt; 演算子

## <a name="operator"></a><a name="op_neq"></a> operator! =

オブジェクト間の不等性をテストします。

```cpp
template <class Type, class Other>
bool operator!=(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class T, class Del1, class U, class Del2>
bool operator!=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator!=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
不等性をテストする一方のオブジェクト。

*そうです*\
不等性をテストする一方のオブジェクト。

*Ty1*\
左辺の共有ポインターによって制御される型。

*Ty2*\
右辺の共有ポインターによって制御される型。

### <a name="return-value"></a>戻り値

**`true`** オブジェクトが等しくない場合は。 **`false`** オブジェクトが等しい場合は。

### <a name="remarks"></a>解説

1 つ目のテンプレートの演算子は、false を返します。 (すべての既定のアロケーターは等価です。)

2 番目と 3 番目のテンプレート演算子は `!(left == right)` を返します。

### <a name="example"></a>例

```cpp
// memory_op_me.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<double> Alloc;
   vector <char>:: allocator_type v1Alloc;

   if ( Alloc != v1Alloc )
      cout << "The allocator objects Alloc & v1Alloc not are equal."
           << endl;
   else
      cout << "The allocator objects Alloc & v1Alloc are equal."
           << endl;
}
```

```Output
The allocator objects Alloc & v1Alloc are equal.
```

### <a name="example"></a>例

```cpp
// std__memory__operator_ne.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 != sp0 == " << std::boolalpha
        << (sp0 != sp0) << std::endl;
    std::cout << "sp0 != sp1 == " << std::boolalpha
        << (sp0 != sp1) << std::endl;

    return (0);
    }
```

```Output
sp0 != sp0 == false
sp0 != sp1 == true
```

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

オブジェクト同士が等しいかどうかをテストします。

```cpp
template <class Type, class Other>
bool operator==(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class Ty1, class Del1, class Ty2, class Del2>
bool operator==(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2, Del2>& right);

template <class Ty1, class Ty2>
bool operator==(
    const shared_ptr<Ty1>& left;,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
等しいかどうかをテストするオブジェクト。

*そうです*\
等しいかどうかをテストするオブジェクト。

*Ty1*\
左辺の共有ポインターによって制御される型。

*Ty2*\
右辺の共有ポインターによって制御される型。

### <a name="return-value"></a>戻り値

**`true`** オブジェクトが等しい場合は、 **`false`** オブジェクトが等しくない場合はです。

### <a name="remarks"></a>解説

1 つ目のテンプレート演算子は true を返します。 (すべての既定のアロケーターは等価です。)

2 番目と 3 番目のテンプレート演算子は `left.get() ==  right.get()` を返します。

### <a name="example"></a>例

```cpp
// memory_op_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<char> Alloc;
   vector <int>:: allocator_type v1Alloc;

   allocator<char> cAlloc(Alloc);
   allocator<int> cv1Alloc(v1Alloc);

   if ( cv1Alloc == v1Alloc )
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."
           << endl;

   if ( cAlloc == Alloc )
      cout << "The allocator objects cAlloc & Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cAlloc & Alloc are not equal."
           << endl;
}
```

```Output
The allocator objects cv1Alloc & v1Alloc are equal.
The allocator objects cAlloc & Alloc are equal.
```

### <a name="example"></a>例

```cpp
// std__memory__operator_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 == sp0 == " << std::boolalpha
        << (sp0 == sp0) << std::endl;
    std::cout << "sp0 == sp1 == " << std::boolalpha
        << (sp0 == sp1) << std::endl;

    return (0);
    }
```

```Output
sp0 == sp0 == true
sp0 == sp1 == false
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> operator&gt;=

1 つ目のオブジェクトが 2 つ目のオブジェクト以上であるかをテストします。

```cpp
template <class T, class Del1, class U, class Del2>
bool operator>=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U, Del2>& right);

template <class Ty1, class Ty2>
bool operator>=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
比較するオブジェクトの 1 つ。

*そうです*\
比較するオブジェクトの 1 つ。

*Ty1*\
左辺の共有ポインターによって制御される型。

*Ty2*\
右辺の共有ポインターによって制御される型。

### <a name="remarks"></a>解説

このテンプレート演算子は `left.get() >= right.get()` を返します。

## <a name="operatorlt"></a><a name="op_lt"></a> operator&lt;

1 番目のオブジェクトが 2 番目のオブジェクトより小さいかどうかをテストします。

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
比較するオブジェクトの 1 つ。

*そうです*\
比較するオブジェクトの 1 つ。

*Ty1*\
左辺のポインターによって制御される型。

*Ty2*\
右辺のポインターによって制御される型。

## <a name="operatorlt"></a><a name="op_lt_eq"></a> operator&lt;=

1 番目のオブジェクトが 2 番目のオブジェクト以下であるかどうかをテストします。

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
比較するオブジェクトの 1 つ。

*そうです*\
比較するオブジェクトの 1 つ。

*Ty1*\
左辺の共有ポインターによって制御される型。

*Ty2*\
右辺の共有ポインターによって制御される型。

### <a name="remarks"></a>解説

このテンプレート演算子は `left.get() <= right.get()` を返します。

## <a name="operatorgt"></a><a name="op_gt"></a> operator&gt;

1 番目のオブジェクトが 2 番目のオブジェクトより大きいかどうかをテストします。

```cpp
template <class Ty1, class Del1, class Ty2, class Del2>
bool operator>(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2&, Del2gt;& right);

template <class Ty1, class Ty2>
bool operator>(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
比較するオブジェクトの 1 つ。

*そうです*\
比較するオブジェクトの 1 つ。

*Ty1*\
左辺の共有ポインターによって制御される型。

*Ty2*\
右辺の共有ポインターによって制御される型。

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> operator&lt;&lt;

共有ポインターをストリームに書き込みます。

```cpp
template <class Elem, class Tr, class Ty>
std::basic_ostream<Elem, Tr>& operator<<(std::basic_ostream<Elem, Tr>& out,
    shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>パラメーター

*Elem*\
ストリーム要素の型。

*Tr*\
ストリーム要素の特性の型。

*~*\
共有ポインターによって制御される型。

*入出力*\
出力ストリーム。

*プロセッサー*\
共有ポインター。

### <a name="remarks"></a>解説

このテンプレート関数は `out << sp.get()` を返します。

### <a name="example"></a>例

```cpp
// std__memory__operator_sl.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "sp0 == " << sp0 << " (varies)" << std::endl;

    return (0);
    }
```

```Output
sp0 == 3f3040 (varies)
```
