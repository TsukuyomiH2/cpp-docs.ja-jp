---
description: 詳細については、「コンパイラエラー C2862」を参照してください。
title: コンパイラ エラー C2862
ms.date: 11/04/2016
f1_keywords:
- C2862
helpviewer_keywords:
- C2862
ms.assetid: c04d8499-b799-48a1-9fb4-7902a0b0ac8e
ms.openlocfilehash: 80b2a3d597c3289024d025bac35f5e0aeab44c58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151113"
---
# <a name="compiler-error-c2862"></a>コンパイラ エラー C2862

' interface ': インターフェイスにはパブリックメンバーのみを含めることができます

Protected メンバーと private メンバーは、他のメンバー関数からのみアクセスできます。 このようなメンバーは、そのメンバーの実装を提供しない場合があるため、インターフェイスでは使用されません。

次の例では、C2862 が生成されます。

```cpp
// C2862.cpp
// compile with: /c
#include <unknwn.h>

[object, uuid="60719E20-EF37-11D1-978D-0000F805D73B"]
__interface IMyInterface {
   HRESULT mf1(void);   // OK
protected:
   HRESULT mf2(int *b);   // C2862
private:
   HRESULT mf3(int *c);   // C2862
};
```
