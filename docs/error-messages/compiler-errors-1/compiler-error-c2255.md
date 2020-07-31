---
title: コンパイラ エラー C2255
ms.date: 11/04/2016
f1_keywords:
- C2255
helpviewer_keywords:
- C2255
ms.assetid: 67dc4cb0-de6b-4405-bd64-d47736367a93
ms.openlocfilehash: 2cb2fd5a673fd44e2b06f8675cfc3ae8e418c290
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87208747"
---
# <a name="compiler-error-c2255"></a>コンパイラ エラー C2255

'element' : クラス定義外では使用できません

たとえば、非メンバー関数がとして宣言されていると **`friend`** します。

次の例では、C2255 が生成されます。

```cpp
// C2255.cpp
// compile with: /c
class A {
private:
   void func1();
   friend void func2();
};

friend void func1() {}   // C2255
void func2(){}
```
