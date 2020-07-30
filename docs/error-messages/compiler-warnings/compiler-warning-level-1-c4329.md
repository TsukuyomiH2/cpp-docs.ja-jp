---
title: コンパイラの警告 (レベル 1) C4329
ms.date: 11/04/2016
f1_keywords:
- C4329
helpviewer_keywords:
- C4329
ms.assetid: 4316f51a-2c56-4b3f-831e-65d24b83b65c
ms.openlocfilehash: ed68b0b2bbbf4a08b4bcd1e2eea4f84346902b62
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230689"
---
# <a name="compiler-warning-level-1-c4329"></a>コンパイラの警告 (レベル 1) C4329

__declspec (align ()) は列挙型では無視されます

[__Declspec](../../cpp/declspec.md)修飾子の[align](../../cpp/align-cpp.md)キーワードの使用は、では許可されていません **`enum`** 。 次の例では、C4329 が生成されます。

```cpp
// C4329.cpp
// compile with: /W1 /LD
enum __declspec(align(256)) TestEnum {   // C4329
   TESTVAL1,
   TESTVAL2,
   TESTVAL3
};
__declspec(align(256)) enum TestEnum1;
```
