---
title: コンパイラ エラー C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 8a040e649074e115b1b86ea56db6c9ef48f4c0d0
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520474"
---
# <a name="compiler-error-c3389"></a>コンパイラ エラー C3389

> __declspec (*キーワード*) を/clr: pure または/clr: safe と共に使用することはできません

## <a name="remarks"></a>Remarks

**`/clr:pure`** および **`/clr:safe`** コンパイラオプションは visual studio 2015 で非推奨とされており、visual studio 2017 ではサポートされていません。

[`__declspec`](../../cpp/declspec.md)使用される修飾子は、プロセスごとの状態を意味します。  [`/clr:pure`](../../build/reference/clr-common-language-runtime-compilation.md)は、状態ごとにを意味 [`appdomain`](../../cpp/appdomain.md) します。  そのため、*キーワード*修飾子を使用して変数を宣言し、を使用してコンパイルすることは **`__declspec`** **`/clr:pure`** できません。

## <a name="example"></a>例

次の例では、C3389 が生成されます。

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
