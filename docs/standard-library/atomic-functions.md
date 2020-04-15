---
title: '&lt;atomic&gt; 関数'
ms.date: 07/11/2018
f1_keywords:
- atomic/std::atomic_compare_exchange_strong
- atomic/std::atomic_compare_exchange_strong_explicit
- atomic/std::atomic_compare_exchange_weak
- atomic/std::atomic_compare_exchange_weak_explicit
- atomic/std::atomic_exchange
- atomic/std::atomic_exchange_explicit
- atomic/std::atomic_fetch_add
- atomic/std::atomic_fetch_add_explicit
- atomic/std::atomic_fetch_and
- atomic/std::atomic_fetch_and_explicit
- atomic/std::atomic_fetch_or
- atomic/std::atomic_fetch_or_explicit
- atomic/std::atomic_fetch_sub
- atomic/std::atomic_fetch_sub_explicit
- atomic/std::atomic_fetch_xor
- atomic/std::atomic_fetch_xor_explicit
- atomic/std::atomic_flag_clear
- atomic/std::atomic_flag_clear_explicit
- atomic/std::atomic_flag_test_and_set
- atomic/std::atomic_flag_test_and_set_explicit
- atomic/std::atomic_init
- atomic/std::atomic_is_lock_free
- atomic/std::atomic_load
- atomic/std::atomic_load_explicit
- atomic/std::atomic_signal_fence
- atomic/std::atomic_store
- atomic/std::atomic_store_explicit
- atomic/std::atomic_thread_fence
- atomic/std::kill_dependency
ms.assetid: 5c53b4f8-6ff5-47d7-beb2-2d6ee3c6ea89
helpviewer_keywords:
- std::atomic_compare_exchange_strong [C++]
- std::atomic_compare_exchange_strong_explicit [C++]
- std::atomic_compare_exchange_weak [C++]
- std::atomic_compare_exchange_weak_explicit [C++]
- std::atomic_exchange [C++]
- std::atomic_exchange_explicit [C++]
- std::atomic_fetch_add [C++]
- std::atomic_fetch_add_explicit [C++]
- std::atomic_fetch_and [C++]
- std::atomic_fetch_and_explicit [C++]
- std::atomic_fetch_or [C++]
- std::atomic_fetch_or_explicit [C++]
- std::atomic_fetch_sub [C++]
- std::atomic_fetch_sub_explicit [C++]
- std::atomic_fetch_xor [C++]
- std::atomic_fetch_xor_explicit [C++]
- std::atomic_flag_clear [C++]
- std::atomic_flag_clear_explicit [C++]
- std::atomic_flag_test_and_set [C++]
- std::atomic_flag_test_and_set_explicit [C++]
- std::atomic_init [C++]
- std::atomic_is_lock_free [C++]
- std::atomic_load [C++]
- std::atomic_load_explicit [C++]
- std::atomic_signal_fence [C++]
- std::atomic_store [C++]
- std::atomic_store_explicit [C++]
- std::atomic_thread_fence [C++]
- std::kill_dependency [C++]
ms.openlocfilehash: b6d03da446e4a3bae02f662e5b106bd5de534d0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376900"
---
# <a name="ltatomicgt-functions"></a>&lt;atomic&gt; 関数

||||
|-|-|-|
|[atomic_compare_exchange_strong](#atomic_compare_exchange_strong)|[atomic_compare_exchange_strong_explicit](#atomic_compare_exchange_strong_explicit)|[atomic_compare_exchange_weak](#atomic_compare_exchange_weak)|
|[atomic_compare_exchange_weak_explicit](#atomic_compare_exchange_weak_explicit)|[atomic_exchange](#atomic_exchange)|[atomic_exchange_explicit](#atomic_exchange_explicit)|
|[atomic_fetch_add](#atomic_fetch_add)|[atomic_fetch_add_explicit](#atomic_fetch_add_explicit)|[atomic_fetch_and](#atomic_fetch_and)|
|[atomic_fetch_and_explicit](#atomic_fetch_and_explicit)|[atomic_fetch_or](#atomic_fetch_or)|[atomic_fetch_or_explicit](#atomic_fetch_or_explicit)|
|[atomic_fetch_sub](#atomic_fetch_sub)|[atomic_fetch_sub_explicit](#atomic_fetch_sub_explicit)|[atomic_fetch_xor](#atomic_fetch_xor)|
|[atomic_fetch_xor_explicit](#atomic_fetch_xor_explicit)|[atomic_flag_clear](#atomic_flag_clear)|[atomic_flag_clear_explicit](#atomic_flag_clear_explicit)|
|[atomic_flag_test_and_set](#atomic_flag_test_and_set)|[atomic_flag_test_and_set_explicit](#atomic_flag_test_and_set_explicit)|[atomic_init](#atomic_init)|
|[atomic_is_lock_free](#atomic_is_lock_free)|[atomic_load](#atomic_load)|[atomic_load_explicit](#atomic_load_explicit)|
|[atomic_signal_fence](#atomic_signal_fence)|[atomic_store](#atomic_store)|[atomic_store_explicit](#atomic_store_explicit)|
|[atomic_thread_fence](#atomic_thread_fence)|[kill_dependency](#kill_dependency)|

## <a name="atomic_compare_exchange_strong"></a><a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

アトミックの比較および交換の操作を実行します。

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
type`Ty`の値を格納する*アトミック*オブジェクトへのポインター。

*Exp*\
`Ty` 型の値へのポインター。

*値*\
`Ty` 型の値。

### <a name="return-value"></a>戻り値

値が等しい場合は**true、** それ以外の場合は**false。**

### <a name="remarks"></a>解説

このメソッドは暗黙の `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引数でアトミックを比較し、交換の操作を実行します。 詳細については、「[atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)」を参照してください。

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

*アトミック比較および交換操作を*実行します。

```cpp
template <class T>
inline bool atomic_compare_exchange_strong_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `Ty` オブジェクトへのポインター。

*Exp*\
`Ty` 型の値へのポインター。

*値*\
`Ty` 型の値。

*注文1*\
最初の [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引数。

*注文2*\
2 番目の `memory_order` 引数。 *Order2*の値は`memory_order_release`、`memory_order_acq_rel`または 、 という値を*指定*できません。

### <a name="return-value"></a>戻り値

値が等しい場合は**true、** それ以外の場合は**false。**

### <a name="remarks"></a>解説

*アトミック比較および交換操作*は *、Atom*が指すオブジェクトに格納されている値を *、Exp*が指す値と比較します。値が等しい場合 *、atom*が指しているオブジェクトに格納されている値は、操作を`read-modify-write`使用して*Order1*で指定されたメモリ順序制約を適用することによって Value に*Order1*置き換えられます。 値が等しくない場合、この操作は *、Exp*が指す値を*Atom*が指すオブジェクトに格納されている値に置き換え *、Order2*で指定されたメモリ順序制約を適用します。

## <a name="atomic_compare_exchange_weak"></a><a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

*弱いアトミックの比較および交換*の操作を実行します。

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `Ty` オブジェクトへのポインター。

*Exp*\
`Ty` 型の値へのポインター。

*値*\
`Ty` 型の値。

### <a name="return-value"></a>戻り値

値が等しい場合は**true、** それ以外の場合は**false。**

### <a name="remarks"></a>解説

このメソッドは、暗黙の `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引数を持つ*弱いアトミックの比較および交換の操作*を実行します。 詳細については、「[atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)」を参照してください。

## <a name="atomic_compare_exchange_weak_explicit"></a><a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

*弱いアトミックの比較および交換*の操作を実行します。

```cpp
template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `Ty` オブジェクトへのポインター。

*Exp*\
`Ty` 型の値へのポインター。

*値*\
`Ty` 型の値。

*注文1*\
最初の [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引数。

*注文2*\
2 番目の `memory_order` 引数。 *Order2*の値は、 `memory_order_release` `memory_order_acq_rel`または 、*または 、Order1*の値より強くすることはできません。

### <a name="return-value"></a>戻り値

値が等しい場合は**true、** それ以外の場合は**false。**

### <a name="remarks"></a>解説

*アトミック比較と交換操作*の強いフレーバーと弱いフレーバーの両方が、予期される値と現在の値が等しくない場合に新しい値を格納しないことを保証します。 強いフレーバーは、期待値と現在値が等しい場合に、新しい値を格納することを保証します。 弱いフレーバーは、現在の値と期待値が等しい場合でも **、false**を返し、新しい値を格納しないことがあります。 つまり、関数は**false**を返しますが、後で期待値を調べると、その値が変更されなかったことが明らかになるため、等しいと比較する必要があります。

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a>atomic_exchange

*値*を使用して *、Atom*の格納された値を置き換えます。

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `Ty` オブジェクトへのポインター。

*値*\
`Ty` 型の値。

### <a name="return-value"></a>戻り値

交換前の*Atom*の格納値。

### <a name="remarks"></a>解説

この`atomic_exchange`関数は、 `read-modify-write` *atom*に格納されている値と*Value*を交換する操作`memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)を実行します。

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

*Atom*の格納された値を*Value*に置き換えます。

```cpp
template <class Ty>
inline Ty atomic_exchange_explicit(
    volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_exchange_explicit(
    atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `Ty` オブジェクトへのポインター。

*値*\
`Ty` 型の値。

*順序*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>戻り値

交換前の*Atom*の格納値。

### <a name="remarks"></a>解説

この`atomic_exchange_explicit`関数`read-modify-write`は *、Order*で指定されたメモリ制約内で *、Atom* with *Value*に格納されている値を交換する操作を実行します。

## <a name="atomic_fetch_add"></a><a name="atomic_fetch_add"></a>atomic_fetch_add

`atomic` オブジェクトに格納されている既存の値に値を加算します。

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型のポインターが格納された `T` オブジェクトへのポインター。

*値*\
`ptrdiff_t` 型の値。

### <a name="return-value"></a>戻り値

操作の直前にアトミック オブジェクトによって格納されたポインター。

### <a name="remarks"></a>解説

この`atomic_fetch_add`関数は`memory_order_seq_cst`[、memory_order](../standard-library/atomic-enums.md#memory_order_enum)制約を`read-modify-write`使用して *、Atom*の格納された値に*Value*をアトミックに加算する演算を実行します。

アトミック型が`atomic_address`の場合 *、Value*は型`ptrdiff_t`を持ち、ストアド`char *`ポインターは .

この操作は、整数型に対してもオーバーロードします。

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a><a name="atomic_fetch_add_explicit"></a>atomic_fetch_add_explicit

`atomic` オブジェクトに格納されている既存の値に値を加算します。

```cpp
template <class T>
T* atomic_fetch_add_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_add_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型のポインターが格納された `T` オブジェクトへのポインター。

*値*\
`ptrdiff_t` 型の値。

### <a name="return-value"></a>戻り値

操作の直前にアトミック オブジェクトによって格納されたポインター。

### <a name="remarks"></a>解説

この`atomic_fetch_add_explicit`関数は、`read-modify-write`で`Order`指定された[memory_order](../standard-library/atomic-enums.md#memory_order_enum)制約の中で *、Atom*の格納された値に*値*をアトミックに追加する演算を実行します。

アトミック型が `atomic_address` の場合、`Value` に `ptrdiff_t` 型があり、操作は `char *` として格納されているポインターを処理します。

この操作は、整数型に対してもオーバーロードします。

```cpp
integral atomic_fetch_add_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_add_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_and"></a><a name="atomic_fetch_and"></a>atomic_fetch_and

値と `and` オブジェクトに格納されている既存の値にビットごとの `atomic` を実行します。

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `T` オブジェクトへのポインター。

*値*\
`T` 型の値。

### <a name="return-value"></a>戻り値

操作の直前にアトミック オブジェクトによって格納された値。

### <a name="remarks"></a>解説

この`atomic_fetch_and`関数は`read-modify-write`[、memory_order](../standard-library/atomic-enums.md#memory_order_enum)制約を使用して *、Atom*の格納された値`and`を *、値*のビット単位と *、Atom*に格納されている現在`memory_order_seq_cst`の値に置き換える操作を実行します。

## <a name="atomic_fetch_and_explicit"></a><a name="atomic_fetch_and_explicit"></a>atomic_fetch_and_explicit

値と `and` オブジェクトに格納されている既存の値のビットごとの `atomic` を実行します。

```cpp
template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `T` オブジェクトへのポインター。

*値*\
`T` 型の値。

*順序*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>戻り値

操作の直前にアトミック オブジェクトによって格納された値。

### <a name="remarks"></a>解説

この`atomic_fetch_and_explicit``read-modify-write`関数は *、Order*で指定されたメモリ制約内で *、Atom* `and`の格納された値を *、値*のビット単位と*Atom*に格納されている現在の値に置き換える操作を実行します。

## <a name="atomic_fetch_or"></a><a name="atomic_fetch_or"></a>atomic_fetch_or

値と `or` オブジェクトに格納されている既存の値にビットごとの `atomic` を実行します。

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `T` オブジェクトへのポインター。

*値*\
`T` 型の値。

### <a name="return-value"></a>戻り値

操作の直前にアトミック オブジェクトによって格納された値。

### <a name="remarks"></a>解説

この`atomic_fetch_or`関数は`read-modify-write`、Memory_order を使用して *、Atom*の格納された値`or`を *、値*のビット単位と *、Atom*に格納されている現在`memory_order_seq_cst`の値に置き換える[操作を実行](../standard-library/atomic-enums.md#memory_order_enum)します。

## <a name="atomic_fetch_or_explicit"></a><a name="atomic_fetch_or_explicit"></a>atomic_fetch_or_explicit

値と `or` オブジェクトに格納されている既存の値にビットごとの `atomic` を実行します。

```cpp
template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `T` オブジェクトへのポインター。

*値*\
`T` 型の値。

*順序*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>戻り値

操作の直前にアトミック オブジェクトによって格納された値。

### <a name="remarks"></a>解説

この`atomic_fetch_or_explicit``read-modify-write`関数は *、Order*で指定された[memory_order](../standard-library/atomic-enums.md#memory_order_enum)制約の中で *、Atom*の格納された値を`or`*、値*のビット単位と *、Atom*に格納されている現在の値に置き換える操作を実行します。

## <a name="atomic_fetch_sub"></a><a name="atomic_fetch_sub"></a>atomic_fetch_sub

`atomic` オブジェクトに格納されている既存の値から値を減算します。

```cpp
template <class T>
T* atomic_fetch_sub(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;

template <class T>
T* atomic_fetch_sub(
    atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型のポインターが格納された `T` オブジェクトへのポインター。

*値*\
`ptrdiff_t` 型の値。

### <a name="return-value"></a>戻り値

操作の直前にアトミック オブジェクトによって格納されたポインター。

### <a name="remarks"></a>解説

この`atomic_fetch_sub`関数は`read-modify-write`[、memory_order](../standard-library/atomic-enums.md#memory_order_enum)制約を使用して *、Atom*に格納されている値から*値*を`memory_order_seq_cst`アトミックに減算する演算を実行します。

アトミック型が`atomic_address`の場合 *、Value*は型`ptrdiff_t`を持ち、ストアド`char *`ポインターは .

この操作は、整数型に対してもオーバーロードします。

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a><a name="atomic_fetch_sub_explicit"></a>atomic_fetch_sub_explicit

`atomic` オブジェクトに格納されている既存の値から値を減算します。

```cpp
template <class T>
T* atomic_fetch_sub_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_sub_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value, memory_order Order) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型のポインターが格納された `T` オブジェクトへのポインター。

*値*\
`ptrdiff_t` 型の値。

### <a name="return-value"></a>戻り値

操作の直前にアトミック オブジェクトによって格納されたポインター。

### <a name="remarks"></a>解説

この`atomic_fetch_sub_explicit`関数は、`read-modify-write`で`Order`指定された[memory_order](../standard-library/atomic-enums.md#memory_order_enum)制約内の*Atom*に格納されている値から*値*をアトミックに減算する演算を実行します。

アトミック型が`atomic_address`の場合 *、Value*は型`ptrdiff_t`を持ち、ストアド`char *`ポインターは .

この操作は、整数型に対してもオーバーロードします。

```cpp
integral atomic_fetch_sub_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_sub_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_xor"></a><a name="atomic_fetch_xor"></a>atomic_fetch_xor

値と `exclusive or` オブジェクトに格納されている既存の値にビットごとの `atomic` を実行します。

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `T` オブジェクトへのポインター。

*値*\
`T` 型の値。

### <a name="return-value"></a>戻り値

操作の直前にアトミック オブジェクトによって格納された値。

### <a name="remarks"></a>解説

この`atomic_fetch_xor`関数は`read-modify-write`、Memory_order を使用して *、Atom*の格納された値`exclusive or`を *、値*のビット単位と *、Atom*に格納されている現在`memory_order_seq_cst`の値に置き換える[操作を実行](../standard-library/atomic-enums.md#memory_order_enum)します。

## <a name="atomic_fetch_xor_explicit"></a><a name="atomic_fetch_xor_explicit"></a>atomic_fetch_xor_explicit

値と `exclusive or` オブジェクトに格納されている既存の値にビットごとの `atomic` を実行します。

```cpp
template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `T` オブジェクトへのポインター。

*値*\
`T` 型の値。

*順序*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>戻り値

操作の直前にアトミック オブジェクトによって格納された値。

### <a name="remarks"></a>解説

この`atomic_fetch_xor_explicit``read-modify-write`関数は *、Order*で指定された[memory_order](../standard-library/atomic-enums.md#memory_order_enum)制約内で *、Atom* `exclusive or`の格納された値を *、値*のビット単位と *、Atom*に格納されている現在の値に置き換える操作を実行します。

## <a name="atomic_flag_clear"></a><a name="atomic_flag_clear"></a>atomic_flag_clear

[atomic_flag](../standard-library/atomic-flag-structure.md)オブジェクトの**bool**フラグを**false**に設定`memory_order_seq_cst`[します](../standard-library/atomic-enums.md#memory_order_enum)( memory_order 内)。

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>パラメーター

*フラグ*\
`atomic_flag` オブジェクトへのポインター。

## <a name="atomic_flag_clear_explicit"></a><a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit

指定した[memory_order](../standard-library/atomic-enums.md#memory_order_enum)制約内で[、atomic_flag](../standard-library/atomic-flag-structure.md)オブジェクトの**bool**フラグを**false**に設定します。

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>パラメーター

*フラグ*\
`atomic_flag` オブジェクトへのポインター。

*順序*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="atomic_flag_test_and_set"></a><a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set

atomic_flag[オブジェクトの](../standard-library/atomic-flag-structure.md) **bool**フラグを**true**に設定します( `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)の制約内で)。

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>パラメーター

*フラグ*\
`atomic_flag` オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

*フラグ*の初期値。

## <a name="atomic_flag_test_and_set_explicit"></a><a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit

指定した[memory_order](../standard-library/atomic-enums.md#memory_order_enum)制約内の[atomic_flag](../standard-library/atomic-flag-structure.md)オブジェクトの**bool**フラグを**true**に設定します。

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>パラメーター

*フラグ*\
`atomic_flag` オブジェクトへのポインター。

*順序*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>戻り値

*フラグ*の初期値。

## <a name="atomic_init"></a><a name="atomic_init"></a>atomic_init

`atomic` オブジェクトに格納されている値を設定します。

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `Ty` オブジェクトへのポインター。

*値*\
`Ty` 型の値。

### <a name="remarks"></a>解説

`atomic_init` はアトミック操作ではありません。 これはスレッド セーフではありません。

## <a name="atomic_is_lock_free"></a><a name="atomic_is_lock_free"></a>atomic_is_lock_free

`atomic` オブジェクトに対するアトミック操作が*ロック制御不要*であるかどうかを指定します。

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `T` オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

*Atom*のアトミック操作がロックフリーである場合は**true。** それ以外の場合**は false。**

### <a name="remarks"></a>解説

その型に対してロックを使用するアトミック操作がない場合、atomic 型はロック制御不要になります。 この関数が true を返す場合、その型はシグナル ハンドラーで使用しても安全です。

## <a name="atomic_load"></a><a name="atomic_load"></a>atomic_load

`atomic` オブジェクトに格納されている値を取得します。

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `Ty` オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

*Atom*に格納されている取得された値。

### <a name="remarks"></a>解説

`atomic_load` は暗黙的に `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) を使用します。

## <a name="atomic_load_explicit"></a><a name="atomic_load_explicit"></a>atomic_load_explicit

指定された [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 内の `atomic` オブジェクトに格納されている値を取得します。

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `Ty` オブジェクトへのポインター。

*順序*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。 `memory_order_release` または `memory_order_acq_rel` を使用しないでください。

### <a name="return-value"></a>戻り値

*Atom*に格納されている取得された値。

## <a name="atomic_signal_fence"></a><a name="atomic_signal_fence"></a>atomic_signal_fence

同じスレッドで実行されるシグナル ハンドラーを持つ呼び出し元のスレッドで、他のフェンス間で (読み込み/ストア操作間の命令を実装するメモリの同期プリミティブである) *フェンス*として機能します。

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>パラメーター

*順序*\
フェンスの種類を決定するメモリ オーダリングの制約。

### <a name="remarks"></a>解説

*Order*引数はフェンスの種類を決定します。

|||
|-|-|
|`memory_order_relaxed`|フェンスは無効です。|
|`memory_order_consume`|フェンスは取得フェンスです。|
|`memory_order_acquire`|フェンスは取得フェンスです。|
|`memory_order_release`|フェンスは解放フェンスです。|
|`memory_order_acq_rel`|フェンスは取得フェンスと解放フェンスの両方です。|
|`memory_order_seq_cst`|フェンスは取得フェンスと解放フェンスの両方であり、順番に一貫性があります。|

## <a name="atomic_store"></a><a name="atomic_store"></a>atomic_store

アトミック オブジェクトに値をアトミックに格納します。

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`Ty` 型の値が格納されたアトミック オブジェクトへのポインター。

*値*\
`Ty` 型の値。

### <a name="remarks"></a>解説

`atomic_store`は、Memory_order[制約内](../standard-library/atomic-enums.md#memory_order_enum)の*Atom*が指すオブジェクトに`memory_order_seq_cst` *Value*を格納します。

## <a name="atomic_store_explicit"></a><a name="atomic_store_explicit"></a>atomic_store_explicit

アトミック オブジェクトに値をアトミックに格納します。

```cpp
template <class Ty>
inline Ty atomic_store_explicit(
    const volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_store_explicit(
    const atomic<Ty>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>パラメーター

*原子*\
`atomic` 型の値が格納された `Ty` オブジェクトへのポインター。

*値*\
`Ty` 型の値。

*順序*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。 `memory_order_consume`、`memory_order_acquire`、または `memory_order_acq_rel` を使用しないでください。

### <a name="remarks"></a>解説

`atomic_store`によって指定された内に*Atom*`memory_order`によってポイントされるオブジェクトに*値*を格納*します*。

## <a name="atomic_thread_fence"></a><a name="atomic_thread_fence"></a>atomic_thread_fence

関連付けられているアトミックな操作なしで、読み込み/ストア操作間の命令を実装するメモリの同期プリミティブである*フェンス*として機能します。

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>パラメーター

*順序*\
フェンスの種類を決定するメモリ オーダリングの制約。

### <a name="remarks"></a>解説

*Order*引数はフェンスの種類を決定します。

|||
|-|-|
|`memory_order_relaxed`|フェンスは無効です。|
|`memory_order_consume`|フェンスは取得フェンスです。|
|`memory_order_acquire`|フェンスは取得フェンスです。|
|`memory_order_release`|フェンスは解放フェンスです。|
|`memory_order_acq_rel`|フェンスは取得フェンスと解放フェンスの両方です。|
|`memory_order_seq_cst`|フェンスは取得フェンスと解放フェンスの両方であり、順番に一貫性があります。|

## <a name="kill_dependency"></a><a name="kill_dependency"></a>kill_dependency

依存関係を削除します。

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>パラメーター

*Arg*\
`Ty` 型の値。

### <a name="return-value"></a>戻り値

戻り値は*Arg*です。 *Arg*の評価は、関数呼び出しに依存しません。 可能な依存関係チェーンを分割することで、関数はより効率的なコードを生成することをコンパイラに許可できます。

## <a name="see-also"></a>関連項目

[\<原子>](../standard-library/atomic.md)
