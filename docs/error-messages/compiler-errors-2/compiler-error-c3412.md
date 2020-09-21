---
title: コンパイラ エラー C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: 6918e3be0a0288bab50d63a188bc33df87fe7754
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742893"
---
# <a name="compiler-error-c3412"></a>コンパイラ エラー C3412

' template ': 現在のスコープでテンプレートを特殊化できません

テンプレートはクラススコープで特殊化できません。グローバルまたは名前空間スコープでのみ使用できます。

## <a name="examples"></a>例

次の例では、C3412 が生成されます。

```cpp
// C3412.cpp
template <class T>
struct S {
   template <>
   struct S<int> {};   // C3412 in a class
};
```

次の例は、考えられる解決方法を示しています。

```cpp
// C3412b.cpp
// compile with: /c
template <class T>
struct S {};

template <>
struct S<int> {};
```
