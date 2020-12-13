---
description: '詳細情報: unsynchronized_pool_resource クラス'
title: unsynchonized_pool_resource クラス
ms.date: 11/04/2016
f1_keywords:
- memory_resource/std::unsynchronized_pool_resource
helpviewer_keywords:
- std::unsynchronized_pool_resource
ms.openlocfilehash: fe26a71b39d485fcead966e63ee52b9b6f0d6f86
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153643"
---
# <a name="unsynchronized_pool_resource-class"></a>unsynchronized_pool_resource クラス

## <a name="syntax"></a>構文

```cpp
class unsynchronized_pool_resource : public memory_resource {
    unsynchronized_pool_resource(const pool_options& opts, memory_resource* upstream);
    unsynchronized_pool_resource()
        : unsynchronized_pool_resource(pool_options(), get_default_resource()) {}
    explicit unsynchronized_pool_resource(memory_resource* upstream)
        : unsynchronized_pool_resource(pool_options(), upstream) {}
    explicit unsynchronized_pool_resource(const pool_options& opts)
        : unsynchronized_pool_resource(opts, get_default_resource()) {}
    unsynchronized_pool_resource(const unsynchronized_pool_resource&) = delete;
    virtual ~unsynchronized_pool_resource();
    unsynchronized_pool_resource&
        operator=(const unsynchronized_pool_resource&) = delete;
    void release();
    memory_resource *upstream_resource() const;
    pool_options options() const;
};
```
