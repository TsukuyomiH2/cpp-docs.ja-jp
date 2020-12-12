---
description: '詳細情報: コンパイラの警告 (レベル 1) C4441'
title: コンパイラの警告 (レベル 1) C4441
ms.date: 11/04/2016
f1_keywords:
- C4441
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
ms.openlocfilehash: f09e25696edffadaeb843d0dbb7ec47f4bcf8a49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212572"
---
# <a name="compiler-warning-level-1-c4441"></a>コンパイラの警告 (レベル 1) C4441

' cc1 ' の呼び出し規約は無視されます。代わりに ' cc2 ' が使用されています

マネージユーザー定義型およびグローバル関数ジェネリックのメンバー関数は、 [__clrcall](../../cpp/clrcall.md) の呼び出し規約を使用する必要があります。  使用されるコンパイラ `__clrcall` 。

## <a name="example"></a>例

次の例では、C4441 が生成されます。

```cpp
// C4441.cpp
// compile with: /clr /W1 /c
generic <class ItemType>
void __cdecl Test(ItemType item) {}   // C4441
// try the following line instead
// void Test(ItemType item) {}

ref struct MyStruct {
   void __cdecl Test(){}   // C4441
   void Test2(){}   // OK
};
```
