---
title: コンパイラ エラー C2378
ms.date: 11/04/2016
f1_keywords:
- C2378
helpviewer_keywords:
- C2378
ms.assetid: 507a91c6-ca72-48df-b3a4-2cf931c86806
ms.openlocfilehash: c72a46bbc5778bf95ddc49426f97df0320b22a30
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218235"
---
# <a name="compiler-error-c2378"></a>コンパイラ エラー C2378

'identifier': 再定義されています。シンボルは typedef でオーバーロードできません

識別子はとして再定義されました **`typedef`** 。

次の例では C2378 が生成されます。

```cpp
// C2378.cpp
// compile with: /c
int i;
typedef int i;   // C2378
typedef int b;   // OK
```
