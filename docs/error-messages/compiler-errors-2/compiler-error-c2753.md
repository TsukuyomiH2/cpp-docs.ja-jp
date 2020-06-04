---
title: コンパイラエラー C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: ea2901c998ac1a44ad142779e7ce48bfffff66c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202154"
---
# <a name="compiler-error-c2753"></a>コンパイラエラー C2753

'*template*': 部分的特殊化をプライマリテンプレートの引数リストと一致させることはできません

テンプレート引数リストがパラメーターリストと一致する場合、コンパイラはそれを同じテンプレートとして扱います。 同じテンプレートを2回定義することはできません。

## <a name="example"></a>例

次の例では、C2753 を生成し、その修正方法を示しています。

```cpp
// C2753.cpp
// compile with: cl /c C2753.cpp
template<class T>
struct A {};

template<class T>
struct A<T> {};   // C2753
// try the following line instead
// struct A<int> {};

template<class T, class U, class V, class W, class X>
struct B {};
```
