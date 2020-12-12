---
description: '詳細情報: コンパイラの警告 (レベル 4) C4214'
title: コンパイラの警告 (レベル 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: afc3f425f0d37b3fb3063d18cb514336271a30ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297305"
---
# <a name="compiler-warning-level-4-c4214"></a>コンパイラの警告 (レベル 4) C4214

非標準の拡張機能が使用されています: int 以外のビットフィールド型

既定の Microsoft 拡張機能 (/Ze) では、ビットフィールド構造体のメンバーは任意の整数型にすることができます。

## <a name="example"></a>例

```c
// C4214.c
// compile with: /W4
struct bitfields
{
   unsigned short j:4;  // C4214
};

int main()
{
}
```

ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) では、このようなビットフィールドは無効です。
