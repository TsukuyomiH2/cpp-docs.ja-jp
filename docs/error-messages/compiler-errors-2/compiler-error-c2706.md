---
title: コンパイラ エラー C2706
ms.date: 11/04/2016
f1_keywords:
- C2706
helpviewer_keywords:
- C2706
ms.assetid: e18da924-c42d-4b09-8e29-f4e0382d7dc6
ms.openlocfilehash: 9767d36d44b99423d600d299d0803901d3dbfec5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161109"
---
# <a name="compiler-error-c2706"></a>コンパイラ エラー C2706

\__try に一致しておらず、__except が正しくありません(\__try ブロックに '}' があることを確認してください)。

`__try`ブロックの右中かっこ (}) が見つかりませんでした。

次の例では、C2706 エラーが生成されます。

```
// C2706.cpp
int main() {
   __try {
      void f();
   // C2706  } missing here
   __except(GetExceptionCode() == 0x0) {
   }
}
```
