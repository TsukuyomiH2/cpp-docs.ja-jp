---
title: コンパイラの警告 (レベル 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: e694f96d7f6271686d1b2a19e5a12e5e08e1cfbe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219951"
---
# <a name="compiler-warning-level-4-c4207"></a>コンパイラの警告 (レベル 4) C4207

非標準の拡張機能が使用されています: 拡張初期化子フォーム

Microsoft 拡張機能 (/Ze) では、 **`char`** 中かっこ内の文字列を使用しての可変長配列を初期化できます。

## <a name="example"></a>例

```c
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

このような初期化は、ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) では無効です。
