---
description: '詳細情報: コンパイラの警告 (レベル 1) C4163'
title: コンパイラの警告 (レベル 1) C4163
ms.date: 11/04/2016
f1_keywords:
- C4163
helpviewer_keywords:
- C4163
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
ms.openlocfilehash: 6906b8c7926371a57ddcd6677d0c34ef57bbb383
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267119"
---
# <a name="compiler-warning-level-1-c4163"></a>コンパイラの警告 (レベル 1) C4163

'identifier': 組み込み関数として使用できません。

指定された関数は [組み込み](../../preprocessor/intrinsic.md) 関数として使用できません。 コンパイラは正しくない関数名を無視します。

次の例では C4163 が生成されます。

```cpp
// C4163.cpp
// compile with: /W1 /LD
#include <math.h>
#pragma intrinsic(mysin)   // C4163
// try the following line instead
// #pragma intrinsic(sin)
```
