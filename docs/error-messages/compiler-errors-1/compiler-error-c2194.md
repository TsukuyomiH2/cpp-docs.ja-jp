---
description: 詳細については、「コンパイラエラー C2194」を参照してください。
title: コンパイラ エラー C2194
ms.date: 11/04/2016
f1_keywords:
- C2194
helpviewer_keywords:
- C2194
ms.assetid: df6e631c-0062-4844-9088-4cc7a0ff879f
ms.openlocfilehash: fefdfbc434dce1347ff4a46a56040219f64feb47
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337647"
---
# <a name="compiler-error-c2194"></a>コンパイラ エラー C2194

' identifier ': テキストセグメントです

`data_seg`プラグマは、で使用されるセグメント名を使用 `code_seg` します。

次の例では、C2194 が生成されます。

```cpp
// C2194.cpp
// compile with: /c
#pragma code_seg("MYCODE")
#pragma data_seg("MYCODE")   // C2194
#pragma data_seg("MYCODE2")   // OK
```
