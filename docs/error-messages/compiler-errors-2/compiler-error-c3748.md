---
description: 詳細については、「コンパイラエラー C3748」を参照してください。
title: コンパイラ エラー C3748
ms.date: 11/04/2016
f1_keywords:
- C3748
helpviewer_keywords:
- C3748
ms.assetid: 6fe71a0a-dd93-4ce6-9729-b9616360cf34
ms.openlocfilehash: f4cb51cfbb331867c18c0f892bd9527309fb4d63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340191"
---
# <a name="compiler-error-c3748"></a>コンパイラ エラー C3748

' interface ': マネージドインターフェイスはイベントを発生させることはできません

[__Event](../../cpp/event.md)キーワードは、インターフェイス内には記述できません。

次の例では、C3748 が生成されます。

```cpp
// C3748.cpp
__interface I {
// try the following line instead
// struct I {
   __event void f();   // C3748
};

int main() {
}
```
