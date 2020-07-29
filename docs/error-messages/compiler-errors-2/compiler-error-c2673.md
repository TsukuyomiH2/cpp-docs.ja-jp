---
title: コンパイラエラー C2673
ms.date: 11/04/2016
f1_keywords:
- C2673
helpviewer_keywords:
- C2673
ms.assetid: 780230c0-619b-4a78-b01d-ff5886306741
ms.openlocfilehash: 1a27b41c11905a509889d46da655900b69070445
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216116"
---
# <a name="compiler-error-c2673"></a>コンパイラエラー C2673

' function ': グローバル関数に ' this ' ポインターがありません。

グローバル関数がにアクセスしようとしました **`this`** 。

次の例では、C2673 が生成されます。

```cpp
// C2673.cpp
int main() {
   this = 0;   // C2673
}
```
