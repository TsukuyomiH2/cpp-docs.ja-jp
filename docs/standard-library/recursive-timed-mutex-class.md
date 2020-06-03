---
title: recursive_timed_mutex クラス
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::lock
- mutex/std::recursive_timed_mutex::try_lock
- mutex/std::recursive_timed_mutex::try_lock_for
- mutex/std::recursive_timed_mutex::try_lock_until
- mutex/std::recursive_timed_mutex::unlock
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
helpviewer_keywords:
- std::recursive_timed_mutex [C++]
- std::recursive_timed_mutex [C++], recursive_timed_mutex
- std::recursive_timed_mutex [C++], lock
- std::recursive_timed_mutex [C++], try_lock
- std::recursive_timed_mutex [C++], try_lock_for
- std::recursive_timed_mutex [C++], try_lock_until
- std::recursive_timed_mutex [C++], unlock
ms.openlocfilehash: 93ce7b99728d1ce89c8124efd6c74aea7ff66d22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320146"
---
# <a name="recursive_timed_mutex-class"></a>recursive_timed_mutex クラス

*時間指定ミューテックス型*を表します。 この型のオブジェクトは、プログラム内での時間制限ブロックを使った相互排他を強制するのに使用されます。 [timed_mutex](../standard-library/timed-mutex-class.md) 型のオブジェクトとは異なり、`recursive_timed_mutex` オブジェクトにロック メソッドを呼び出すことによる影響は詳細に定義されています。

## <a name="syntax"></a>構文

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|ロックされていない `recursive_timed_mutex` オブジェクトを構築します。|
|[~recursive_timed_mutexデストラクタ](#dtorrecursive_timed_mutex_destructor)|`recursive_timed_mutex` オブジェクトによって使用されるすべてのリソースを解放します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[ロック](#lock)|呼び出しスレッドが `mutex` の所有権を取得するまでそのスレッドをブロックします。|
|[try_lock](#try_lock)|ブロックせずに `mutex` の所有権を取得しようとします。|
|[try_lock_for](#try_lock_for)|指定した時間のあいだ `mutex` の所有権の取得を試みます。|
|[try_lock_until](#try_lock_until)|指定した時刻まで `mutex` の所有権の取得を試みます。|
|[ロック 解除](#unlock)|`mutex` の所有権を解放します。|

## <a name="requirements"></a>必要条件

**ヘッダー:**\<ミューテックス>

**名前空間:** std

## <a name="lock"></a><a name="lock"></a>ロック

呼び出しスレッドが `mutex` の所有権を取得するまでそのスレッドをブロックします。

```cpp
void lock();
```

### <a name="remarks"></a>解説

呼び出しスレッドが既に `mutex` を所有している場合、メソッドが直ちに返され、以前のロックは有効のままになります。

## <a name="recursive_timed_mutex-constructor"></a><a name="recursive_timed_mutex"></a>recursive_timed_mutexコンストラクタ

ロックされていない `recursive_timed_mutex` オブジェクトを構築します。

```cpp
recursive_timed_mutex();
```

## <a name="recursive_timed_mutex-destructor"></a><a name="dtorrecursive_timed_mutex_destructor"></a>  ~recursive_timed_mutex デストラクター

`recursive_timed_mutex` オブジェクトによって使用されるすべてのリソースを解放します。

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>解説

デストラクターの実行時にオブジェクトがロックされる場合の動作は未定義です。

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

ブロックせずに `mutex` の所有権を取得しようとします。

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>戻り値

メソッドが の所有権を取得できた場合`mutex`、または呼び出し元のスレッド`mutex`が既に所有している場合は**true。** それ以外の場合**は false。**

### <a name="remarks"></a>解説

呼び出し元のスレッド`mutex`が 既に を所有している場合、関数はすぐに**true**を返し、前のロックは有効なままです。

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

ブロックせずに `mutex` の所有権を取得しようとします。

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>パラメーター

*Rel_time*\
メソッドが `mutex` の所有権の取得を試行する時間について、その最大値を指定する [chrono::duration](../standard-library/duration-class.md) オブジェクト。

### <a name="return-value"></a>戻り値

メソッドが の所有権を正常に取得した場合`mutex`、または呼び出し元の`mutex`スレッドが既に所有している場合は**true。** それ以外の場合**は false。**

### <a name="remarks"></a>解説

呼び出し元のスレッド`mutex`が 既に を所有している場合、メソッドはすぐに**true**を返し、前のロックは有効なままです。

## <a name="try_lock_until"></a><a name="try_lock_until"></a>try_lock_until

ブロックせずに `mutex` の所有権を取得しようとします。

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>パラメーター

*Abs_time*\
メソッドが `mutex` の所有権の取得を止めるしきい値を指定する時点。

### <a name="return-value"></a>戻り値

メソッドが の所有権を正常に取得した場合`mutex`、または呼び出し元の`mutex`スレッドが既に所有している場合は**true。** それ以外の場合**は false。**

### <a name="remarks"></a>解説

呼び出し元のスレッド`mutex`が 既に を所有している場合、メソッドはすぐに**true**を返し、前のロックは有効なままです。

## <a name="unlock"></a><a name="unlock"></a>ロック 解除

`mutex` の所有権を解放します。

```cpp
void unlock();
```

### <a name="remarks"></a>解説

このメソッドが `mutex` の所有権を開放するのは、[lock](#lock)、[try_lock](#try_lock)、[try_lock_for](#try_lock_for)、および [try_lock_until](#try_lock_until) が `recursive_timed_mutex` オブジェクト上で正常に呼び出されたのと同じ回数だけ呼び出された後のみです。

呼び出しスレッドが `mutex` を所有していない場合の動作は未定義です。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<ミューテックス>](../standard-library/mutex.md)
