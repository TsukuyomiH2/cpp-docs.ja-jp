---
title: logical_and 構造体
ms.date: 11/04/2016
f1_keywords:
- functional/std::logical_and
helpviewer_keywords:
- logical_and class
- logical_and struct
ms.assetid: 1a375cc2-0592-4d57-a553-78009c7ad610
ms.openlocfilehash: 7036ebf9fed3877a395e44d8383776002b9afcae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351690"
---
# <a name="logical_and-struct"></a>logical_and 構造体

引数に対して論理積演算 (`operator&&`) を実行する定義済みの関数オブジェクト。

## <a name="syntax"></a>構文

```cpp
template <class Type = void>
struct logical_and : public binary_function<Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator&&
template <>
struct logical_and<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) && std::forward<U>(Right));
};
```

### <a name="parameters"></a>パラメーター

*タイプ*, *T*, *U*\
指定または推論された型のオペランドを受け取る `operator&&` をサポートする任意の型。

*左*\
論理積演算の左オペランド。 特殊化されていないテンプレートは、*型 Type*の左辺値参照引数を受け取ります。 特殊なテンプレートは、推定型*T*の左辺値と右辺値参照引数を完全に転送します。

*そうです*\
論理積演算の右オペランド。 特殊化されていないテンプレートは、*型 Type*の左辺値参照引数を受け取ります。 特殊なテンプレートは、推定型*U*の左辺値と右辺値参照引数を完全に転送します。

## <a name="return-value"></a>戻り値

`Left && Right` の結果。 特殊化されたテンプレートは、結果の完全転送を行います。結果には `operator&&` によって返された型が含まれます。

## <a name="remarks"></a>解説

ユーザー定義型の場合、オペランドの評価のショートサーキットはありません。 どちらの引数も `operator&&` によって評価されます。

## <a name="example"></a>例

```cpp
// functional_logical_and.cpp
// compile with: /EHsc

#define _CRT_RAND_S
#include <stdlib.h>
#include <deque>
#include <algorithm>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   deque<bool> d1, d2, d3( 7 );
   deque<bool>::iterator iter1, iter2, iter3;

   unsigned int randomValue;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
   {
      if ( rand_s( &randomValue ) == 0 )
      {
         d1.push_back((bool)(( randomValue % 2 ) != 0));
      }

   }

   int j;
   for ( j = 0 ; j < 7 ; j++ )
   {
      if ( rand_s( &randomValue ) == 0 )
      {
         d2.push_back((bool)(( randomValue % 2 ) != 0));
      }
   }

   cout << boolalpha;    // boolalpha I/O flag on

   cout << "Original deque:\n d1 = ( " ;
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )
      cout << *iter1 << " ";
   cout << ")" << endl;

   cout << "Original deque:\n d2 = ( " ;
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )
      cout << *iter2 << " ";
   cout << ")" << endl;

   // To find element-wise conjunction of the truth values
   // of d1 & d2, use the logical_and function object
   transform( d1.begin( ), d1.end( ), d2.begin( ),
      d3.begin( ), logical_and<bool>( ) );
   cout << "The deque which is the conjunction of d1 & d2 is:\n d3 = ( " ;
   for ( iter3 = d3.begin( ) ; iter3 != d3.end( ) ; iter3++ )
      cout << *iter3 << " ";
   cout << ")" << endl;
}
```

```Output
Original deque:
d1 = ( true true true true true false false )
Original deque:
d2 = ( true false true true false true false )
The deque which is the conjunction of d1 & d2 is:
d3 = ( true false true true false false false )
```
