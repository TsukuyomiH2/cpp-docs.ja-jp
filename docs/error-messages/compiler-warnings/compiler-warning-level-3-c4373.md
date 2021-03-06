---
description: '詳細情報: コンパイラの警告 (レベル 3) C4373'
title: コンパイラの警告 (レベル 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: a0688f8ed0af1c2854a4449a2fcba31d412a9e4f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160455"
---
# <a name="compiler-warning-level-3-c4373"></a>コンパイラの警告 (レベル 3) C4373

> '*function*': 仮想関数は '*base_function*' をオーバーライドします。以前のバージョンのコンパイラは、パラメーターの違いが const/volatile 修飾子に限られている場合はオーバーライドしませんでした

## <a name="remarks"></a>解説

アプリケーションには、基底クラスの仮想メソッドをオーバーライドする派生クラスのメソッドが含まれ、オーバーライドする側のメソッドのパラメーターは、 [const](../../cpp/const-cpp.md) または [volatile](../../cpp/volatile-cpp.md) 修飾子についてのみ、仮想メソッドのパラメーターと異なります。 つまり、コンパイラでは、基底クラスまたは派生クラスのいずれかにおけるメソッドに、関数参照をバインドする必要があります。

Visual Studio 2008 より前のバージョンのコンパイラでは、関数が基底クラスのメソッドにバインドされ、警告メッセージが発行されます。 後続のバージョンのコンパイラで **`const`** は、またはの **`volatile`** 修飾子を無視し、派生クラスのメソッドに関数をバインドしてから、警告 **C4373** を発行します。 この後者の動作は、C++ 標準に準拠しています。

## <a name="example"></a>例

次のコード例では、警告 C4373 が生成されます。 この問題を解決するには、オーバーライドで基本メンバー関数と同じ CV 修飾子を使用するか、オーバーライドを作成しない場合は、派生クラスの関数に別の名前を付けることができます。

```cpp
// c4373.cpp
// compile with: /c /W3
#include <stdio.h>
struct Base
{
    virtual void f(int i) {
        printf("base\n");
    }
};

struct Derived : Base
{
    void f(const int i) {  // C4373
        printf("derived\n");
    }
};

int main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```
