---
title: コンパイラ エラー C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: 97f3290ef8bcb6a91442effdbf84261c03545ce2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87209527"
---
# <a name="compiler-error-c2218"></a>コンパイラ エラー C2218

> '__vectorcall' と '/arch:IA32' は同時に使用できません

**`__vectorcall`** 呼び出し規則は、ストリーミング SIMD 拡張命令 2 (SSE2) 以上を含む x86 および x64 プロセッサのネイティブコードでのみサポートされています。 詳細については、「[`__vectorcall`](../../cpp/vectorcall.md)」を参照してください。

このエラーを修正するには、SSE2、AVX、または AVX2 をターゲットにするようにコンパイラ オプションを変更します。 詳細については、「 [ `/arch` (x86)](../../build/reference/arch-x86.md)」を参照してください。
