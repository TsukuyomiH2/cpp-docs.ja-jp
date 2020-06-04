---
title: コンパイラの警告 (レベル 1) C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: 31ceb972edf975055f930d4ff70a6663a5760922
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163259"
---
# <a name="compiler-warning-level-1-c4237"></a>コンパイラの警告 (レベル 1) C4237

' keyword ' キーワードはまだサポートされていませんが、将来使用するために予約されています

C++指定されたキーワードは Microsoft C++コンパイラに実装されていませんが、キーワードはユーザー定義シンボルとして使用できません。

次の例では、C4237 が生成されます。

```cpp
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```
