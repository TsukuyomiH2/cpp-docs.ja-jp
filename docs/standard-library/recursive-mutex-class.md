---
title: recursive_mutex クラス
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: 9ab7a96a7c07582450ab41b140dcc5494a63661f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320205"
---
# <a name="recursive_mutex-class"></a>recursive_mutex クラス

*ミューテックス型*を表します。 [mutex](../standard-library/mutex-class-stl.md) とは異なり、既にロックされているオブジェクトのロック メソッドを呼び出す動作は詳細に定義されています。

## <a name="syntax"></a>構文

```cpp
class recursive_mutex;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|`recursive_mutex` オブジェクトを構築します。|
|[~recursive_mutex デストラクター](#dtorrecursive_mutex_destructor)|`recursive_mutex` オブジェクトによって使用されるすべてのリソースを解放します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[ロック](#lock)|呼び出しスレッドがミューテックスの所有権を取得するまでそのスレッドをブロックします。|
|[try_lock](#try_lock)|ブロックせずにミューテックスの所有権を取得しようとします。|
|[ロック 解除](#unlock)|ミューテックスの所有権を解放します。|

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

## <a name="recursive_mutex"></a><a name="recursive_mutex"></a>recursive_mutex

ロックされていない `recursive_mutex` オブジェクトを構築します。

```cpp
recursive_mutex();
```

## <a name="recursive_mutex"></a><a name="dtorrecursive_mutex_destructor"></a>  ~recursive_mutex

オブジェクトによって使用されるすべてのリソースを解放します。

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>解説

デストラクターの実行時にオブジェクトがロックされる場合の動作は未定義です。

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

ブロックせずに `mutex` の所有権を取得しようとします。

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>戻り値

**true**メソッドが の所有権を正常に取得した場合`mutex`、または呼び出し元の`mutex**; otherwise, **false`スレッドが 既にを所有している場合は true です。

### <a name="remarks"></a>解説

呼び出し元のスレッド`mutex`が 既に を所有している場合、関数はすぐに**true**を返し、前のロックは有効なままです。

## <a name="unlock"></a><a name="unlock"></a>ロック 解除

ミューテックスの所有権を解放します。

```cpp
void unlock();
```

### <a name="remarks"></a>解説

このメソッドが `mutex` の所有権を開放するのは、[lock](#lock) および [try_lock](#try_lock) が `recursive_mutex` オブジェクト上で正常に呼び出されたのと同じ回数だけ呼び出された後のみです。

呼び出しスレッドが `mutex` を所有していない場合の動作は未定義です。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<ミューテックス>](../standard-library/mutex.md)
