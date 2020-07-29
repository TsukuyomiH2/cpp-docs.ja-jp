---
title: コンパイラの警告 (レベル 1) C4230
ms.date: 11/04/2016
f1_keywords:
- C4230
helpviewer_keywords:
- C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
ms.openlocfilehash: 0b590eaef2094c3d1c3a83541e9d5e10415928f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223214"
---
# <a name="compiler-warning-level-1-c4230"></a>コンパイラの警告 (レベル 1) C4230

旧形式: 修飾子/修飾子が混在しています。修飾子が無視されました

などの Microsoft 修飾子の前に修飾子を使用すること **`__cdecl`** は、古い方法です。

## <a name="example"></a>例

```cpp
// C4230.cpp
// compile with: /W1 /LD
int __cdecl const function1();   // C4230 const ignored
```
