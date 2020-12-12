---
description: 詳細については、「コンパイラエラー C2177」を参照してください。
title: コンパイラ エラー C2177
ms.date: 11/04/2016
f1_keywords:
- C2177
helpviewer_keywords:
- C2177
ms.assetid: 2a39a880-cddb-4d3e-a572-645a14c4c478
ms.openlocfilehash: d03e227b98d13c097c47843fc99f0850372286c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322137"
---
# <a name="compiler-error-c2177"></a>コンパイラ エラー C2177

定数が大きすぎます。

割り当てられている変数の型の定数値が大きすぎます。

次の例では C2177 が生成されます。

```cpp
// C2177.cpp
int main() {
   int a=18446744073709551616;   // C2177
   int b=18446744073709551615;   // OK
}
```
