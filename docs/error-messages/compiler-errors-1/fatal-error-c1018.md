---
description: '詳細情報: 致命的なエラー C1018'
title: 致命的なエラー C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 68b81406916ef358a73112c9f6f8b2370c627e54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316415"
---
# <a name="fatal-error-c1018"></a>致命的なエラー C1018

予期しない #elif です。

`#elif` ディレクティブが、 `#if`、 `#ifdef`、または `#ifndef` コンストラクトの外側に置かれています。 `#elif` は、これらのコンストラクトのいずれかの内側だけで使用してください。

次の例では C1018 が生成されます。

```cpp
// C1018.cpp
#elif      // C1018
#endif

int main() {}
```

考えられる解決策:

```cpp
// C1018b.cpp
#if 1
#elif
#endif

int main() {}
```
