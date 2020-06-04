---
title: コンパイラの警告 (レベル 1) C4085
ms.date: 11/04/2016
f1_keywords:
- C4085
helpviewer_keywords:
- C4085
ms.assetid: 2bc6eb25-058f-4597-b351-fd69587b5170
ms.openlocfilehash: 8fc8ddc900299f372f0592b660b132188128c3d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200201"
---
# <a name="compiler-warning-level-1-c4085"></a>コンパイラの警告 (レベル 1) C4085

プラグマに、'on' か 'off' のパラメーターが必要です。

プラグマには、 **on** または **off** パラメーターが必要です。 このプラグマは無視されます。

次の例では C4085 が生成されます。

```cpp
// C4085.cpp
// compile with: /W1 /LD
#pragma optimize( "t", maybe )  // C4085
```
