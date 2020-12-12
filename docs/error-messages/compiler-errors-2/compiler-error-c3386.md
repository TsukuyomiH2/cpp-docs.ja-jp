---
description: 詳細については、「コンパイラエラー C3386」を参照してください。
title: コンパイラ エラー C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: 5bc80abe7c43e30c4114d0f3ffd7733c8ea3e9d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115899"
---
# <a name="compiler-error-c3386"></a>コンパイラ エラー C3386

> '*type-name*': `__declspec(dllexport)` / `__declspec(dllimport)` マネージ型または WinRT 型には適用できません

[`dllimport`](../../cpp/dllexport-dllimport.md)And 修飾子は、 [`dllexport`](../../cpp/dllexport-dllimport.md) **`__declspec`** マネージ型または Windows ランタイム型では有効ではありません。

次の例では、C3386 を生成し、その修正方法を示しています。

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
