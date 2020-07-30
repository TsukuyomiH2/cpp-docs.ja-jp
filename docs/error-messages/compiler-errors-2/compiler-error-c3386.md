---
title: コンパイラ エラー C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: 0cb6235f1b6bc868655cc6a6ba301be1308402cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221082"
---
# <a name="compiler-error-c3386"></a>コンパイラ エラー C3386

' type ': __declspec (dllexport)/ \_ _declspec (dllimport) をマネージまたは WinRTtype に適用することはできません

`dllimport`および[dllexport](../../cpp/dllexport-dllimport.md) **`__declspec`** c ' * * 修飾子は、マネージ型または Windows ランタイム型では無効です。

次の例では、C3386 を生成し、その修正方法を示しています。

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
