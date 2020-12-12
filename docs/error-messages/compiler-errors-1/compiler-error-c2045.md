---
description: 詳細については、「コンパイラエラー C2045」を参照してください。
title: コンパイラ エラー C2045
ms.date: 11/04/2016
f1_keywords:
- C2045
helpviewer_keywords:
- C2045
ms.assetid: 2fca668e-9b20-4933-987a-18c0fd0187df
ms.openlocfilehash: 878ae18a20bbaa0da7219e2a68f8772c5dd0a637
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175171"
---
# <a name="compiler-error-c2045"></a>コンパイラ エラー C2045

'identifier' : ラベルが再定義されました

このラベルは同じ関数内の複数のステートメントの前にあります。

次の例では C2045 が生成されます。

```cpp
// C2045.cpp
int main() {
   label: {
   }
   goto label;
   label: {}   // C2045
}
```
