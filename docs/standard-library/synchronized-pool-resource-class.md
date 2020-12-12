---
description: '詳細情報: synchronized_pool_resource クラス'
title: synchonized_pool_resource クラス
ms.date: 11/04/2016
f1_keywords:
- memory_resource/std::synchronized_pool_resource
helpviewer_keywords:
- std::synchronized_pool_resource
ms.openlocfilehash: fa34765f75bb578fb49ffad27c3ade9306672ba9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183257"
---
# <a name="synchronized_pool_resource-class"></a>synchronized_pool_resource クラス

## <a name="syntax"></a>構文

```cpp
class synchronized_pool_resource : public memory_resource {
    synchronized_pool_resource(const pool_options& opts, memory_resource* upstream);
    synchronized_pool_resource()
        : synchronized_pool_resource(pool_options(), get_default_resource()) {}
    explicit synchronized_pool_resource(memory_resource* upstream)
        : synchronized_pool_resource(pool_options(), upstream) {}
    explicit synchronized_pool_resource(const pool_options& opts)
        : synchronized_pool_resource(opts, get_default_resource()) {}
    synchronized_pool_resource(const synchronized_pool_resource&) = delete;
    virtual ~synchronized_pool_resource();
    synchronized_pool_resource&
        operator=(const synchronized_pool_resource&) = delete;
    void release();
    memory_resource* upstream_resource() const;
    pool_options options() const;
};
```
