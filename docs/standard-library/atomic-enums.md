---
description: 詳細については、「 &lt; atomic 列挙型」をご覧ください。 &gt;
title: '&lt;atomic&gt; 列挙型'
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: 5144b936cbea8e16b5bf344f6fb776eefa6b09ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149527"
---
# <a name="ltatomicgt-enums"></a>&lt;atomic&gt; 列挙型

## <a name="memory_order-enum"></a><a name="memory_order_enum"></a> memory_order 列挙型

メモリ位置に対する同期操作のシンボル名を提供します。 これらの操作は、1 つのスレッドの割り当てが別のスレッドにおいて表示される方法に影響します。

```cpp
typedef enum memory_order {
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst,
} memory_order;
```

### <a name="enumeration-members"></a>列挙メンバー

|名前|説明|
|-|-|
|`memory_order_relaxed`|順序付けは必要ありません。|
|`memory_order_consume`|読み込み操作は、メモリ位置に対する消費操作として機能します。|
|`memory_order_acquire`|読み込み操作は、メモリ位置に対する取得操作として機能します。|
|`memory_order_release`|格納操作は、メモリ位置に対する開放操作として機能します。|
|`memory_order_acq_rel`|`memory_order_acquire` と `memory_order_release` を組み合わせます。|
|`memory_order_seq_cst`|`memory_order_acquire` と `memory_order_release` を組み合わせます。 `memory_order_seq_cst` としてマークされたメモリ アクセスには、順番に一貫性がある必要があります。|

## <a name="see-also"></a>関連項目

[\<atomic>](../standard-library/atomic.md)
