---
title: front_insert_iterator クラス
ms.date: 11/04/2016
f1_keywords:
- iterator/std::front_insert_iterator
- iterator/std::front_insert_iterator::container_type
- iterator/std::front_insert_iterator::reference
helpviewer_keywords:
- std::front_insert_iterator [C++]
- std::front_insert_iterator [C++], container_type
- std::front_insert_iterator [C++], reference
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
ms.openlocfilehash: 8f60b2e5e21b559edb630be2aee377341d4480f6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203274"
---
# <a name="front_insert_iterator-class"></a>front_insert_iterator クラス

出力反復子の要件を満たす反復子アダプターについて説明します。 シーケンスの前に要素を上書きではなく、挿入し、C++ のシーケンス コンテナーの反復子が提供する上書きセマンティクスとは異なるセマンティクスを提供します。 `front_insert_iterator` クラスはコンテナーの型でテンプレート化されます。

## <a name="syntax"></a>構文

```cpp
template <class Container>
class front_insert_iterator;
```

### <a name="parameters"></a>パラメーター

*コンテナー*\
要素が `front_insert_iterator` によって前方に挿入されるコンテナーの型。

## <a name="remarks"></a>解説

コンテナーは償却定数時間でシーケンスの先頭に要素を挿入できる、有効な前方挿入シーケンスの要件を満たしている必要があります。 [deque クラス](../standard-library/deque-class.md)と [list クラス](../standard-library/list-class.md)によって定義された、C++標準ライブラリのシーケンス コンテナーは、必要な `push_front` メンバー関数を提供し、次の要件を満たします。 一方、[vector クラス](../standard-library/vector-class.md)で定義されるシーケンス コンテナーは、以下の要件を満たさず、`front_insert_iterator` を使用するように調整することはできません。 `front_insert_iterator` は、常に、コンテナーで初期化されている必要があります。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[front_insert_iterator](#front_insert_iterator)|指定されたコンテナー オブジェクトの前に要素を挿入できる反復子を作成します。|

### <a name="typedefs"></a>Typedefs

|型名|説明|
|-|-|
|[container_type](#container_type)|前方挿入の対象となるコンテナーを表す型。|
|[reference](#reference)|関連するコンテナーによって制御されるシーケンスの要素への参照を提供する型。|

### <a name="operators"></a>オペレーター

|演算子|説明|
|-|-|
|[operator](#op_star)|\* `i`  =  `x` 前方挿入のための出力反復子式を実装するために使用される逆参照演算子。|
|[+ + 演算子](#op_add_add)|値を格納できる次の位置に `front_insert_iterator` をインクリメントします。|
|[operator =](#op_eq)|\* `i`  =  `x` 前方挿入のための出力反復子式を実装するために使用される代入演算子。|

## <a name="requirements"></a>必要条件

**ヘッダー**:\<iterator>

**名前空間:** std

## <a name="front_insert_iteratorcontainer_type"></a><a name="container_type"></a>front_insert_iterator:: container_type

前方挿入の対象となるコンテナーを表す型。

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>解説

この型は、テンプレート パラメーター *Container* のシノニムです。

### <a name="example"></a>例

```cpp
// front_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> >::container_type L2 = L1;
   front_inserter ( L2 ) = 20;
   front_inserter ( L2 ) = 10;
   front_inserter ( L2 ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 10 20 ).
*/
```

## <a name="front_insert_iteratorfront_insert_iterator"></a><a name="front_insert_iterator"></a>front_insert_iterator:: front_insert_iterator

指定されたコンテナー オブジェクトの前に要素を挿入できる反復子を作成します。

```cpp
explicit front_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>パラメーター

*_Cont*\
`front_insert_iterator` によって要素が挿入されるオブジェクト コンテナーです。

### <a name="return-value"></a>戻り値

パラメーター コンテナー オブジェクトの `front_insert_iterator`。

### <a name="example"></a>例

```cpp
// front_insert_iterator_front_insert_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   front_inserter ( L ) = 20;

   // Alternatively, one may use the template function
   front_insert_iterator< list < int> > Iter(L);
*Iter = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_star"></a>front_insert_iterator:: operator\*

アドレス指定された要素を返す挿入反復子を逆参照します。

```cpp
front_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>戻り値

このメンバー関数は、アドレス指定された要素の値を返します。

### <a name="remarks"></a>解説

出力反復子式** \* Iter**値を実装するために使用され  =  **value**ます。 `Iter`がシーケンス内の要素をアドレス指定する反復子である場合、 ** \* Iter**  =  **value**はその要素を値に置き換え、シーケンス内の要素の合計数を変更しません。

### <a name="example"></a>例

```cpp
// front_insert_iterator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   front_insert_iterator< list < int> > Iter(L);
*Iter = 20;

   // Alternatively, you may use
   front_inserter ( L ) = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_add_add"></a>front_insert_iterator:: operator + +

値を格納できる次の位置に `back_insert_iterator` をインクリメントします。

```cpp
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>戻り値

値を格納できる次の位置をアドレス指定する `front_insert_iterator`。

### <a name="remarks"></a>解説

preincrementation と postincrementation の演算子は、どちらも同じ結果を返します。

### <a name="example"></a>例

```cpp
// front_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_eq"></a>front_insert_iterator:: operator =

コンテナーの前に値を追加 (プッシュ) します。

```cpp
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>パラメーター

*val*\
コンテナーに割り当てられる値。

### <a name="return-value"></a>戻り値

コンテナーの前に挿入される最後の要素への参照。

### <a name="remarks"></a>解説

1つ目のメンバー演算子はを評価し `container.push_front( val)` 、を返し **`*this`** ます。

2 つ目のメンバー演算子は次の評価をします。

`container->push_front((typename Container::value_type&&) val)`,

その後、を返し **`*this`** ます。

### <a name="example"></a>例

```cpp
// front_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="front_insert_iteratorreference"></a><a name="reference"></a>front_insert_iterator:: reference

関連するコンテナーによって制御されるシーケンスの要素への参照を提供する型。

```cpp
typedef typename Container::reference reference;
```

### <a name="example"></a>例

```cpp
// front_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   front_insert_iterator<list<int> > fiivIter( L );
*fiivIter = 10;
*fiivIter = 20;
*fiivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++)
      cout << *LIter << " ";
   cout << ")." << endl;

   front_insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 30 20 10 ).
The first element in the list L is: 30.
*/
```

## <a name="see-also"></a>関連項目

[\<iterator>](../standard-library/iterator.md)\
[C++ 標準ライブラリのスレッドセーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリリファレンス](../standard-library/cpp-standard-library-reference.md)
