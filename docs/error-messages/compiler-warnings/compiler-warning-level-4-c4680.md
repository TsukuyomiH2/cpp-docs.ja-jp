---
title: コンパイラの警告 (レベル 4) C4680
ms.date: 11/04/2016
f1_keywords:
- C4680
helpviewer_keywords:
- C4680
ms.assetid: 6e043f4c-c601-4b77-8130-920cff1d912e
ms.openlocfilehash: ea9eb681d1696c77184a9999a94367a0bce8c454
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510047"
---
# <a name="compiler-warning-level-4-c4680"></a>コンパイラの警告 (レベル 4) C4680

' class ': コクラスは既定のインターフェイスを指定していません

[コクラス](../../windows/attributes/coclass.md)属性でマークされたクラスの[既定](../../windows/attributes/default-cpp.md)のインターフェイスが指定されませんでした。 オブジェクトを使用するためには、インターフェイスを実装する必要があります。

次の例では、C4680 が生成されます。

```cpp
// C4680.cpp
// compile with: /W4
#include <windows.h>
[module(name="MyModule")];

[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface1
{
   HRESULT f1();
};

[ object, uuid(37331a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface2
{
   HRESULT f1();
};

// to resolve C4680, specify a source interface also
// for example, default(IMyIface1, IMyface2)
[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f), default(IMyIface1), source(IMyIface1) ]
class CMyClass : public IMyIface1
{   // C4680
};

int main()
{
}
```
