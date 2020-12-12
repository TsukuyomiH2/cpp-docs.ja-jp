---
description: 詳細については、「コンパイラエラー C2814」を参照してください。
title: コンパイラ エラー C2814
ms.date: 11/04/2016
f1_keywords:
- C2814
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
ms.openlocfilehash: 3da888c70356abee8ae18990d521d5589a5c5069
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278390"
---
# <a name="compiler-error-c2814"></a>コンパイラ エラー C2814

'member' : ネイティブ型をマネージド型または WinRT 型の 'type' の中に入れ子にすることはできません

## <a name="example"></a>例

ネイティブ型を CLR 型または WinRT 型の中に入れ子にすることはできません。 次の例では、C2814 を生成し、その修正方法を示しています。

```cpp
// C2814.cpp
// compile with: /clr /c
ref class A {
   class B {};   // C2814
   ref class C {};   // OK
};
```
