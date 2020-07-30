---
title: rts_alloc クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
ms.openlocfilehash: f422b171c14695a1207a30419a10d50cdfb5adf0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228129"
---
# <a name="rts_alloc-class"></a>rts_alloc クラス

Rts_alloc クラステンプレートは、キャッシュインスタンスの配列を保持し、コンパイル時ではなく実行時に割り当てと割り当て解除に使用するインスタンスを決定する[フィルター](../standard-library/allocators-header.md)を記述します。

## <a name="syntax"></a>構文

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*キャッシュ*|配列に含まれているキャッシュ インスタンスの型。 これは、[cache_chunklist クラス](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md)、[cache_suballoc](../standard-library/cache-suballoc-class.md) のいずれかです。|

## <a name="remarks"></a>解説

このクラステンプレートは、複数のブロックアロケーターインスタンスを保持し、コンパイル時ではなく、実行時に割り当てまたは割り当て解除に使用するインスタンスを決定します。 再バインドをコンパイルできないコンパイラと一緒に使用します。

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[allocate](#allocate)|メモリのブロックを割り当てます。|
|[配置](#deallocate)|指定した位置で始まるストレージから、指定された数のオブジェクトを解放します。|
|[equals](#equals)|2 つのキャッシュが等しいかどうかを比較します。|

## <a name="requirements"></a>必要条件

**ヘッダー:**\<allocators>

**名前空間:** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a>rts_alloc:: allocate

メモリのブロックを割り当てます。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*count*|割り当てられる配列内の要素の数。|

### <a name="return-value"></a>戻り値

割り当てられたオブジェクトへのポインター。

### <a name="remarks"></a>解説

このメンバー関数は `caches[_IDX].allocate(count)` 、 `_IDX` 要求されたブロックサイズの*カウント*によってインデックスが決定されるを返します。また、 *count*が大きすぎる場合は、を返し `operator new(count)` ます。 キャッシュ オブジェクトを表す `cache`。

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a>rts_alloc::d eallocate

指定した位置で始まるストレージから、指定された数のオブジェクトを解放します。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*ptr*|記憶域から割り当てを解除される最初のオブジェクトへのポインター。|
|*count*|記憶域から割り当てを解除されるオブジェクトの数。|

### <a name="remarks"></a>解説

このメンバー関数は `caches[_IDX].deallocate(ptr, count)` 、 `_IDX` 要求されたブロックサイズの*カウント*によってインデックスが決定されるを呼び出します。 *count*が大きすぎる場合は、を返し `operator delete(ptr)` ます。

## <a name="rts_allocequals"></a><a name="equals"></a>rts_alloc:: equals

2 つのキャッシュが等しいかどうかを比較します。

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*_Cache*|フィルターに関連付けられているキャッシュ オブジェクト。|
|*_Other*|等しいかどうかを比較するキャッシュ オブジェクト。|

### <a name="remarks"></a>解説

**`true`** の結果の場合は `caches[0].equals(other.caches[0])` 。それ以外の場合は **`false`** 。 `caches` はキャッシュ オブジェクトの配列を表します。

## <a name="see-also"></a>関連項目

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<allocators>](../standard-library/allocators-header.md)
