---
description: '詳細情報: コンパイラの警告 (レベル 1) C4047'
title: コンパイラの警告 (レベル 1) C4047
ms.date: 11/04/2016
f1_keywords:
- C4047
helpviewer_keywords:
- C4047
ms.assetid: b75ad6fb-5c93-4434-a85f-c4083051a5de
ms.openlocfilehash: 45a628f0ef84d634ee301d5980394a1cec503aeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160624"
---
# <a name="compiler-warning-level-1-c4047"></a>コンパイラの警告 (レベル 1) C4047

'operator' : 間接参照のレベルが 'identifier1' と 'identifier2' で異なっています。

ポインターは、変数 (1 レベルの間接参照)、変数 (2 つのレベルの間接参照) を指す別のポインターを指すことができます。

## <a name="examples"></a>例

次の例では、C4047 が生成されます。

```c
// C4047.c
// compile with: /W1

int main() {
   char **p = 0;   // two levels of indirection
   char *q = 0;   // one level of indirection

   char *p2 = 0;   // one level of indirection
   char *q2 = 0;   // one level of indirection

   p = q;   // C4047
   p2 = q2;
}
```

次の例では、C4047 が生成されます。

```c
// C4047b.c
// compile with: /W1
#include <stdio.h>

int main() {
   int i;
   FILE *myFile = NULL;
   errno_t  err = 0;
   char file_name[256];
   char *cs = 0;

   err = fopen_s(&myFile, "C4047.txt", "r");
   if ((err != 0) || (myFile)) {
      printf_s("fopen_s failed!\n");
      exit(-1);
    }
   i = fgets(file_name, 256, myFile);   // C4047
   cs = fgets(file_name, 256, myFile);   // OK
}
```
