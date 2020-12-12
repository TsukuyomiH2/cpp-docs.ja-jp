---
description: '詳細情報: コンパイラの警告 (レベル 1) C4632'
title: コンパイラの警告 (レベル 1) C4632
ms.date: 11/04/2016
f1_keywords:
- C4632
helpviewer_keywords:
- C4632
ms.assetid: 9e35d205-cf21-4e34-8bd5-e1e7b0e2cdd3
ms.openlocfilehash: a055f49a1aa71c36679f7c6177f502141e52dcde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318872"
---
# <a name="compiler-warning-level-1-c4632"></a>コンパイラの警告 (レベル 1) C4632

XML ドキュメントコメント: ファイルアクセスが拒否されました: 理由

.Xdc ファイル () へのパス `file` が有効ではなく、.xdc ファイルも作成されていません。

次の例では、C4632 が生成されます。

```cpp
// C4632.cpp
// compile with: /clr /docv:\\falsedir /LD /W1
// C4632 expected

/// Text for class MyClass.
public ref class MyClass {};
```
