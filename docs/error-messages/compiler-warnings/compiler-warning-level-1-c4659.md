---
description: '詳細情報: コンパイラの警告 (レベル 1) C4659'
title: コンパイラの警告 (レベル 1) C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 05ec1e088e00b184ba083b6b197afc6041707449
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318815"
---
# <a name="compiler-warning-level-1-c4659"></a>コンパイラの警告 (レベル 1) C4659

\#プラグマ ' pragma ': 予約セグメント ' segment ' の使用には定義されていない動作があります。 #pragma コメントを使用してください (リンカー,...)

.Drectve オプションは、リンカーにオプションを渡すために使用されました。 代わりに、リンカーオプションを渡すためにプラグマ [コメント](../../preprocessor/comment-c-cpp.md) を使用してください。

```cpp
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```
