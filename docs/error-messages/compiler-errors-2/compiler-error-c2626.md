---
description: 詳細については、「コンパイラエラー C2626」を参照してください。
title: コンパイラエラー C2626
ms.date: 11/04/2016
f1_keywords:
- C2626
helpviewer_keywords:
- C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
ms.openlocfilehash: 1a89d63d18fd029daa98ce1d248da24296ee2d4f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123547"
---
# <a name="compiler-error-c2626"></a>コンパイラエラー C2626

'identifier': プライベートまたはプロテクト データ メンバーは、匿名構造体または共用体では許可されていません

匿名構造体または共用体のメンバーは、パブリック アクセスを持つ必要があります。

次の例では C2626 が生成されます。

```cpp
// C2626.cpp
int main() {
   union {
   protected:
      int j;     // C2626, j is protected
   private:
      int k;     // C2626, k is private
   };
}
```

この問題を解決するには、プライベートまたはプロテクト タグを削除します。

```cpp
// C2626b.cpp
int main() {
   union {
   public:
      int i;   // OK, i is public
   };
}
```
