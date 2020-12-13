---
description: 詳細については、「コンパイラエラー C2238」を参照してください。
title: コンパイラ エラー C2238
ms.date: 11/04/2016
f1_keywords:
- C2238
helpviewer_keywords:
- C2238
ms.assetid: 3d53060c-d6b7-4603-b9cf-d7c65eb64cd2
ms.openlocfilehash: 90c5eb840c300aa18b06f49a7e160c6cb7bd8e9e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338744"
---
# <a name="compiler-error-c2238"></a>コンパイラ エラー C2238

'token' の前に無効なトークンがあります。

正しくないトークンが見つかりました。

次の例では C2238 が生成されます。

```cpp
// C2238.cpp
// compile with: /c
class v {
virtual: int vvv;   // C2238
};
```
