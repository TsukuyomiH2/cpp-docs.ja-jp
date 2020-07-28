---
title: コンパイラエラー C2779
ms.date: 11/04/2016
f1_keywords:
- C2779
helpviewer_keywords:
- C2779
ms.assetid: 4a00e492-855a-41f3-8a18-5f60ee20c2f2
ms.openlocfilehash: cf2a59726e87f5cd2cdb82129db2677bf6a69d29
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220237"
---
# <a name="compiler-error-c2779"></a>コンパイラエラー C2779

' 宣言 ': プロパティメソッドは、非静的データメンバーにのみ関連付けることができます

**`property`** 拡張属性が静的データメンバーに不適切に適用されています。

次の例では、C2779 が生成されます。

```cpp
// C2779.cpp
struct A {
   static __declspec(property(put=PutProp))
   // try the following line instead
   __declspec(property(put=PutProp))
      int prop;   // C2779
   int PutProp(void);
};
```
