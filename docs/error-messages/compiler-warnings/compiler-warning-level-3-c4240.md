---
title: コンパイラの警告 (レベル 3) C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: 9e4d33bd0151e4355903c7d10b667ced405a2471
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161569"
---
# <a name="compiler-warning-level-3-c4240"></a>コンパイラの警告 (レベル 3) C4240

非標準の拡張機能が使用されています: ' classname ' へのアクセスは ' アクセス指定子 ' として定義されましたが、以前は ' access 指定子 ' として定義されました

ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) では、入れ子になったクラスへのアクセスを変更することはできません。 既定の Microsoft 拡張機能 (/Ze) では、この警告が表示されます。

## <a name="example"></a>例

```cpp
// C4240.cpp
// compile with: /W3
class X
{
private:
   class N;
public:
   class N
   {   // C4240
   };
};

int main()
{
}
```
