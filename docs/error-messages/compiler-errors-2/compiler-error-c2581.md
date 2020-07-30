---
title: コンパイラ エラー C2581
ms.date: 11/04/2016
f1_keywords:
- C2581
helpviewer_keywords:
- C2581
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
ms.openlocfilehash: a632d6a47afb29b8bb46761c3188391905eda842
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206875"
---
# <a name="compiler-error-c2581"></a>コンパイラ エラー C2581

' type ': 静的 ' operator = ' 関数は無効です

代入 ( `=` ) 演算子がとして正しく宣言されてい **`static`** ません。 代入演算子をにすることはできません **`static`** 。 詳細については、「[ユーザー定義の演算子 (C++/cli)](../../dotnet/user-defined-operators-cpp-cli.md)」を参照してください。

## <a name="example"></a>例

次の例では、C2581 が生成されます。

```cpp
// C2581.cpp
// compile with: /clr /c
ref struct Y {
   static Y ^ operator = (Y^ me, int i);   // C2581
   Y^ operator =(int i);   // OK
};
```
