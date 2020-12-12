---
description: 詳細については、「コンパイラエラー C2216」を参照してください。
title: コンパイラ エラー C2216
ms.date: 11/04/2016
f1_keywords:
- C2216
helpviewer_keywords:
- C2216
ms.assetid: 250f6bdc-a5e1-495f-a1e8-6e8e7021ad9d
ms.openlocfilehash: ff32949342dd4bdc9739dfbb57c4c88ece0d8949
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245552"
---
# <a name="compiler-error-c2216"></a>コンパイラ エラー C2216

'keyword1' は 'keyword2' と共に使用できません

相互に排他的である 2 つのキーワードが共に使用されました。

## <a name="examples"></a>例

次の例では C2216 が生成されます。

```cpp
// C2216.cpp
// compile with: /clr /c
ref struct Y1 {
   literal
   static int staticConst2 = 10;   // C2216
};
```

次の例では C2216 が生成されます。

```cpp
// C2216b.cpp
// compile with: /clr /c
public ref class X {
   extern property int i { int get(); }   // C2216 extern not allowed on property
   typedef property int i2;   // C2216 typedef not allowed on property
};
```

次の例では C2216 が生成されます。

```cpp
// C2216c.cpp
// compile with: /clr /c
public interface struct I {
   double f();
   double g();
   double h();
};

public ref struct R : I {
   virtual double f() new override { return 0.0; }   // C2216
   virtual double g() new { return 0.0; }   // OK
   virtual double h() override { return 0.0; }   // OK
};
```
