---
description: '詳細情報: &lt; キュー &gt; オペレーター'
title: '&lt;queue&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- queue/std::operator!=
- queue/std::operator&gt;
- queue/std::operator&gt;=
- queue/std::operator&lt;
- queue/std::operator&lt;=
- queue/std::operator==
ms.assetid: 7c435b48-175c-45b0-88eb-24561044019c
helpviewer_keywords:
- std::operator!= (queue)
- std::operator&gt; (queue)
- std::operator&gt;= (queue)
- std::operator&lt; (queue)
- std::operator&lt;= (queue)
- std::operator== (queue)
ms.openlocfilehash: 6d6280ca4fe1e1277a79862a5016d55dfbecc425
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327581"
---
# <a name="ltqueuegt-operators"></a>&lt;queue&gt; 演算子

## <a name="operator"></a><a name="op_neq"></a> operator! =

演算子の左側のキュー オブジェクトが右側のキュー オブジェクトと等しくないかどうかをテストします。

```cpp
bool operator!=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>パラメーター

*左側*\
`queue` 型のオブジェクト。

*そうです*\
`queue` 型のオブジェクト。

### <a name="return-value"></a>戻り値

**`true`** キューが等しくない場合は、 **`false`** キューが等しい場合は。

### <a name="remarks"></a>解説

queue オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの queue は、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// queue_op_ne.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a> operator&lt;

演算子の左側のキュー オブジェクトが右側のキュー オブジェクトより小さいかどうかをテストします。

```cpp
bool operator<(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>パラメーター

*左側*\
`queue` 型のオブジェクト。

*そうです*\
`queue` 型のオブジェクト。

### <a name="return-value"></a>戻り値

**`true`** 演算子の左側のキューが、演算子の右側のキューの値未満であり、かつ等しくない場合は。それ以外の場合は **`false`** 。

### <a name="remarks"></a>解説

queue オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの queue オブジェクト間の小なり関係は、最初の等しくない要素のペアの比較に基づいています。

### <a name="example"></a>例

```cpp
// queue_op_lt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 < q2 )
      cout << "The queue q1 is less than the queue q2." << endl;
   else
      cout << "The queue q1 is not less than the queue q2." << endl;

   if ( q1 < q3 )
      cout << "The queue q1 is less than the queue q3." << endl;
   else
      cout << "The queue q1 is not less than the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is not less than the queue q3.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> operator&lt;=

演算子の左側のキュー オブジェクトが右側のキュー オブジェクト以下かどうかをテストします。

```cpp
bool operator<=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>パラメーター

*左側*\
`queue` 型のオブジェクト。

*そうです*\
`queue` 型のオブジェクト。

### <a name="return-value"></a>戻り値

**`true`** 演算子の左辺の queue が演算子の右辺のキューより厳密に小さい場合は、。それ以外の場合は **`false`** 。

### <a name="remarks"></a>解説

queue オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの queue オブジェクト間の "以下" 関係は、最初の等しくない要素のペアの比較に基づいています。

### <a name="example"></a>例

```cpp
// queue_op_le.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 5 );
   q1.push( 10 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 5 );
   q3.push( 10 );

   if ( q1 <= q2 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;

   if ( q1 <= q3 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is greater than the queue q2.
The queue q1 is less than or equal to the queue q3.
```

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

演算子の左側の queue オブジェクトが右側の queue オブジェクトと等しいかどうかをテストします。

```cpp
bool operator==(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>パラメーター

*左側*\
`queue` 型のオブジェクト。

*そうです*\
`queue` 型のオブジェクト。

### <a name="return-value"></a>戻り値

**`true`** キューが等しくない場合は、 **`false`** キューが等しい場合は。

### <a name="remarks"></a>解説

queue オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの queue は、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// queue_op_eq.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a> operator&gt;

演算子の左側のキュー オブジェクトが右側のキュー オブジェクトより大きいかどうかをテストします。

```cpp
bool operator>(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>パラメーター

*左側*\
`queue` 型のオブジェクト。

*そうです*\
`queue` 型のオブジェクト。

### <a name="return-value"></a>戻り値

**`true`** 演算子の左辺の queue が演算子の右辺のキューより厳密に小さい場合は、。それ以外の場合は **`false`** 。

### <a name="remarks"></a>解説

queue オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの queue オブジェクト間の大なり関係は、最初の等しくない要素のペアの比較に基づいています。

### <a name="example"></a>例

```cpp
// queue_op_gt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q1.push( 3 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 > q2 )
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q2." << endl;

   if ( q1> q3 )
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is not greater than the queue q2.
The queue q1 is greater than the queue q3.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> operator&gt;=

演算子の左側のキュー オブジェクトが右側のキュー オブジェクト以上かどうかをテストします。

```cpp
bool operator>=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>パラメーター

*左側*\
`queue` 型のオブジェクト。

*そうです*\
`queue` 型のオブジェクト。

### <a name="return-value"></a>戻り値

**`true`** 演算子の左辺の queue が演算子の右辺のキューより厳密に小さい場合は、。それ以外の場合は **`false`** 。

### <a name="remarks"></a>解説

queue オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの queue は、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// queue_op_ge.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 >= q2 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q2." << endl;

   if ( q1>= q3 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is greater than or equal to the queue q3.
```
