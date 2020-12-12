---
description: 詳細については、「コンパイラエラー C3902」を参照してください。
title: コンパイラ エラー C3902
ms.date: 11/04/2016
f1_keywords:
- C3902
helpviewer_keywords:
- C3902
ms.assetid: feb3bb29-f836-4d77-ba71-3876f7f4f216
ms.openlocfilehash: 8d72b5e8f1e1494f18bda61c67ae2f5e38453f01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144275"
---
# <a name="compiler-error-c3902"></a>コンパイラ エラー C3902

' accessor ': 最後のパラメーターの型は ' type ' でなければなりません

少なくとも1つの set メソッドの最後のパラメーターの型は、プロパティの型と一致している必要があります。 詳細については、「 [property](../../extensions/property-cpp-component-extensions.md)」を参照してください。

次の例では、C3902 が生成されます。

```cpp
// C3902.cpp
// compile with: /clr /c
using namespace System;
ref class X {
   property String ^Name {
      void set(int);   // C3902
      // try the following line instead
      // void set(String^){}
   }

   property double values[int,int] {
      void set(int, int, float);   // C3902
      // try the following line instead
      // void set(int, int, double){}
   }
};
```
