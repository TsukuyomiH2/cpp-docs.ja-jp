---
title: コンパイラエラー C2761
ms.date: 11/04/2016
f1_keywords:
- C2761
helpviewer_keywords:
- C2761
ms.assetid: 38c79a05-b56d-485b-820f-95e8c0cb926f
ms.openlocfilehash: 7493934879068109c582a85592f485c1d391e2de
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743387"
---
# <a name="compiler-error-c2761"></a>コンパイラエラー C2761

' function ': メンバー関数の再宣言は許可されていません

メンバー関数を再宣言することはできません。 これは定義できますが、再宣言することはできません。

## <a name="examples"></a>例

次の例では、C2761 が生成されます。

```cpp
// C2761.cpp
class a {
   int t;
   void test();
};

void a::a;     // C2761
void a::test;  // C2761
```

クラスまたは構造体の非静的メンバーを定義することはできません。  次の例では、C2761 が生成されます。

```cpp
// C2761_b.cpp
// compile with: /c
struct C {
   int s;
   static int t;
};

int C::s;   // C2761
int C::t;   // OK
```
