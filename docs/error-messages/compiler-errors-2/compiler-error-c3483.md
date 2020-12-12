---
description: 詳細については、「コンパイラエラー C3483」を参照してください。
title: コンパイラ エラー C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: 7c67e1e4d44c64fbcc023ee410dff2ecdd92c361
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113389"
---
# <a name="compiler-error-c3483"></a>コンパイラ エラー C3483

'var' は既にラムダ キャプチャ リストに含まれています

ラムダ式のキャプチャ リストに同じ変数を複数回渡しました。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- キャプチャ リストから変数のすべての追加インスタンスを削除します。

## <a name="example"></a>例

次の例では、変数 `n` がラムダ式のキャプチャ リストに複数回出現するため、C3483 が生成されます。

```cpp
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>関連項目

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)
