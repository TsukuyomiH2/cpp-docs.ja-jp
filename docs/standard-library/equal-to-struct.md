---
description: '詳細については、次を参照してください: equal_to 構造体'
title: equal_to 構造体
ms.date: 11/04/2016
f1_keywords:
- functional/std::equal_to
helpviewer_keywords:
- equal_to function
- equal_to struct
ms.assetid: 8e4f2b50-b2db-48e3-b4cc-6cc03362c2a6
ms.openlocfilehash: cae0531c31396d16d447e3b0123dc679bbfd5aa6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324437"
---
# <a name="equal_to-struct"></a>equal_to 構造体

引数に対して等値演算 (`operator==`) を実行する二項述語。

## <a name="syntax"></a>構文

```cpp
template <class Type = void>
struct equal_to : public binary_function<Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator==
template <>
struct equal_to<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
      ->  decltype(std::forward<T>(Left) == std::forward<U>(Right));
};
```

### <a name="parameters"></a>パラメーター

*型*、 *T*、 *U*\
指定または推論された型のオペランドを受け取る `operator==` をサポートする任意の型。

*左側*\
等値演算の左オペランド。 非特殊テンプレートは、type *型* の左辺値参照引数を受け取ります。 特殊化されたテンプレートは、推論された型 *T* の左辺値および右辺値参照引数の完全転送を行います。

*そうです*\
等値演算の右オペランド。 非特殊テンプレートは、type *型* の左辺値参照引数を受け取ります。 特殊化されたテンプレートは、推論された型 *U* の左辺値および右辺値参照引数の完全転送を行います。

## <a name="return-value"></a>戻り値

`Left == Right` の結果。 特殊化されたテンプレートは、結果の完全転送を行います。結果には `operator==` によって返された型が含まれます。

## <a name="remarks"></a>解説

Type *型* のオブジェクトは、等値比較可能である必要があります。 オブジェクトのセットに対して定義されている `operator==` が、等価関係の数学的性質を満たしている必要があります。 組み込みの数値型とポインター型はすべて、この要件を満たします。

## <a name="example"></a>例

```cpp
// functional_equal_to.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main( )
{
   vector <double> v1, v2, v3 ( 6 );
   vector <double>::iterator Iter1, Iter2, Iter3;

   int i;
   for ( i = 0 ; i <= 5 ; i+=2 )
   {
      v1.push_back( 2.0 *i );
      v1.push_back( 2.0 * i + 1.0 );
   }

   int j;
   for ( j = 0 ; j <= 5 ; j+=2 )
   {
      v2.push_back( - 2.0 * j );
      v2.push_back( 2.0 * j + 1.0 );
   }

   cout << "The vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "The vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Testing for the element-wise equality between v1 & v2
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),
      equal_to<double>( ) );

   cout << "The result of the element-wise equal_to comparison\n"
      << "between v1 & v2 is: ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
```

```Output
The vector v1 = ( 0 1 4 5 8 9 )
The vector v2 = ( -0 1 -4 5 -8 9 )
The result of the element-wise equal_to comparison
between v1 & v2 is: ( 1 1 0 1 0 1 )
```
