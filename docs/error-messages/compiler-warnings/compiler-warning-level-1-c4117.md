---
title: コンパイラの警告 (レベル 1) C4117
ms.date: 11/04/2016
f1_keywords:
- C4117
helpviewer_keywords:
- C4117
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
ms.openlocfilehash: 2474645a555748b559b1661a2b5327ca1b83e534
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176379"
---
# <a name="compiler-warning-level-1-c4117"></a>コンパイラの警告 (レベル 1) C4117

マクロ名 'name' は予約されています。"Command" は無視されます

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. 定義済みマクロを定義するか未定義にしようとしています。

1. プリプロセッサ演算子 **defined**を定義するか未定義にしようとしています。

次の例では C4117 が生成されます。

```cpp
// C4117.cpp
// compile with: /W1
#define __FILE__ test         // C4117. __FILE__ is a predefined macro
#define ValidMacroName test   // ok

int main() {
}
```
