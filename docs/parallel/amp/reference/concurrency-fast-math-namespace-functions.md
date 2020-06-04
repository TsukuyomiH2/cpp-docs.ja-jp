---
title: Concurrency::fast_math 名前空間関数
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math::acos
- amp_math/Concurrency::fast_math::asin
- amp_math/Concurrency::fast_math::asinf
- amp_math/Concurrency::fast_math::atan2
- amp_math/Concurrency::fast_math::atan2f
- amp_math/Concurrency::fast_math::ceil
- amp_math/Concurrency::fast_math::ceilf
- amp_math/Concurrency::fast_math::cosf
- amp_math/Concurrency::fast_math::cosh
- amp_math/Concurrency::fast_math::exp
- amp_math/Concurrency::fast_math::exp2
- amp_math/Concurrency::fast_math::expf
- amp_math/Concurrency::fast_math::fabs
- amp_math/Concurrency::fast_math::floor
- amp_math/Concurrency::fast_math::floorf
- amp_math/Concurrency::fast_math::fmaxf
- amp_math/Concurrency::fast_math::fmin
- amp_math/Concurrency::fast_math::fmod
- amp_math/Concurrency::fast_math::fmodf
- amp_math/Concurrency::fast_math::frexpf
- amp_math/Concurrency::fast_math::isfinite
- amp_math/Concurrency::fast_math::isnan
- amp_math/Concurrency::fast_math::ldexp
- amp_math/Concurrency::fast_math::log
- amp_math/Concurrency::fast_math::log10
- amp_math/Concurrency::fast_math::log2
- amp_math/Concurrency::fast_math::log2f
- amp_math/Concurrency::fast_math::modf
- amp_math/Concurrency::fast_math::modff
- amp_math/Concurrency::fast_math::powf
- amp_math/Concurrency::fast_math::round
- amp_math/Concurrency::fast_math::rsqrt
- amp_math/Concurrency::fast_math::rsqrtf
- amp_math/Concurrency::fast_math::signbitf
- amp_math/Concurrency::fast_math::sin
- amp_math/Concurrency::fast_math::sincosf
- amp_math/Concurrency::fast_math::sinf
- amp_math/Concurrency::fast_math::sinhf
- amp_math/Concurrency::fast_math::sqrt
- amp_math/Concurrency::fast_math::tan
- amp_math/Concurrency::fast_math::tanf
- amp_math/Concurrency::fast_math::tanhf
- amp_math/Concurrency::fast_math::trunc
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
ms.openlocfilehash: cd0882b072cfe26cd83e63024ae6837dc962ebf9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376395"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Concurrency::fast_math 名前空間関数

||||
|-|-|-|
|[Acos](#acos)|[acosf](#acosf)|[Asin](#asin)|
|[asinf](#asinf)|[Atan](#atan)|[atan2](#atan2)|
|[atan2f](#atan2f)|[atanf](#atanf)|[セイル](#ceil)|
|[ceilf](#ceilf)|[Cos](#cos)|[cosf](#cosf)|
|[Cosh](#cosh)|[coshf](#coshf)|[Exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|
|[fabs](#fabs)|[fabsf](#fabsf)|[床](#floor)|
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[frexp](#frexp)|[フインシュフ](#frexpf)|
|[イスフィント](#isfinite)|[イシンフ](#isinf)|[Isnan](#isnan)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[ログ](#log)|
|[ログ10](#log10)|[log10f](#log10f)|[ログ2](#log2)|
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[えい](#pow)|[powf](#powf)|
|[ラウンド](#round)|[roundf](#roundf)|[rsqrt](#rsqrt)|
|[を使用します。](#rsqrtf)|[signbit](#signbit)|[サインビットフ](#signbitf)|
|[罪](#sin)|[シンコス](#sincos)|[シンコスフ](#sincosf)|
|[sinf](#sinf)|[sinh](#sinh)|[sinhf](#sinhf)|
|[Sqrt](#sqrt)|[sqrtf](#sqrtf)|[日焼け](#tan)|
|[tanf](#tanf)|[Tanh](#tanh)|[tanhf](#tanhf)|
|[トランク](#trunc)|[truncf](#truncf)|

## <a name="acos"></a><a name="acos"></a>Acos

引数の逆余弦を計算します。

```cpp
inline float acos(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のアークコサイン値を返します。

## <a name="acosf"></a><a name="acosf"></a>アコスフ

引数の逆余弦を計算します。

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のアークコサイン値を返します。

## <a name="asin"></a><a name="asin"></a>Asin

引数の逆正弦を計算します。

```cpp
inline float asin(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のアークセイン値を返します。

## <a name="asinf"></a><a name="asinf"></a>アシンフ

引数の逆正弦を計算します。

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のアークセイン値を返します。

## <a name="atan"></a><a name="atan"></a>Atan

引数の逆正接を計算します。

```cpp
inline float atan(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のアークタンジェント値を返します。

## <a name="atan2"></a><a name="atan2"></a>atan2

_Y/_X の逆正接を計算します。

```cpp
inline float atan2(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_y*<br/>
浮動小数点値

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_Y/_Xのアークタンジェント値を返します。

## <a name="atan2f"></a><a name="atan2f"></a>atan2f

_Y/_X の逆正接を計算します。

```cpp
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_y*<br/>
浮動小数点値

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_Y/_Xのアークタンジェント値を返します。

## <a name="atanf"></a><a name="atanf"></a>アタンフ

引数の逆正接を計算します。

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のアークタンジェント値を返します。

## <a name="ceil"></a><a name="ceil"></a>セイル

引数の切り上げを計算します。

```cpp
inline float ceil(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の上限を返します。

## <a name="ceilf"></a><a name="ceilf"></a>セイルフ

引数の切り上げを計算します。

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の上限を返します。

## <a name="cosf"></a><a name="cosf"></a>コスフ

引数の余弦を計算します。

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の余弦値を返します。

## <a name="coshf"></a><a name="coshf"></a>コスフ

引数の双曲線余弦の値を計算します。

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の双曲線余弦値を返します。

## <a name="cos"></a><a name="cos"></a>Cos

引数の余弦を計算します。

```cpp
inline float cos(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の余弦値を返します。

## <a name="cosh"></a><a name="cosh"></a>Cosh

引数の双曲線余弦の値を計算します。

```cpp
inline float cosh(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の双曲線余弦値を返します。

## <a name="exp"></a><a name="exp"></a>Exp

e を底とする引数のべき乗を計算します。

```cpp
inline float exp(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の底から e の指数を返します。

## <a name="exp2"></a><a name="exp2"></a>exp2

2 を底とする引数のべき乗を計算します。

```cpp
inline float exp2(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

底 2 を引数で累乗した値を返します。

## <a name="exp2f"></a><a name="exp2f"></a>exp2f

2 を底とする引数のべき乗を計算します。

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

底 2 を引数で累乗した値を返します。

## <a name="expf"></a><a name="expf"></a>expf

e を底とする引数のべき乗を計算します。

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の底から e の指数を返します。

## <a name="fabs"></a><a name="fabs"></a>工場

引数の絶対値を返します。

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
整数値

### <a name="return-value"></a>戻り値

引数の絶対値を返します。

## <a name="fabsf"></a><a name="fabsf"></a>ファブスフ

引数の絶対値を返します。

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の絶対値を返します。

## <a name="floor"></a><a name="floor"></a>床

引数の切り捨てを計算します。

```cpp
inline float floor(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の階を返します。

## <a name="floorf"></a><a name="floorf"></a>フロアフ

引数の切り捨てを計算します。

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の階を返します。

## <a name="fmax"></a><a name="fmax"></a>fmax

引数の最大数値を判断します。

```cpp
inline float max(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
整数値

*_y*<br/>
整数値

### <a name="return-value"></a>戻り値

引数の最大数値を返します。

## <a name="fmaxf"></a><a name="fmaxf"></a>fマックスフ

引数の最大数値を判断します。

```cpp
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

*_y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の最大数値を返します。

## <a name="fmin"></a><a name="fmin"></a>fmin

引数の最小数値を判断します。

```cpp
inline float min(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
整数値

*_y*<br/>
整数値

### <a name="return-value"></a>戻り値

引数の最小数値を返します。

## <a name="fminf"></a><a name="fminf"></a>fminf

引数の最小数値を判断します。

```cpp
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

*_y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の最小数値を返します。

## <a name="fmod"></a><a name="fmod"></a>Fmod

_X/_Y の浮動小数点の剰余を計算します。

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

*_y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X/_Yの浮動小数点の剰余を返します。

## <a name="fmodf"></a><a name="fmodf"></a>フモドフ

_X/_Yの浮動小数点の剰余を計算します。

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

*_y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X/_Yの浮動小数点の剰余を返します。

## <a name="frexp"></a><a name="frexp"></a>フレエクス

_X の仮数と指数を取得します。

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

*_Exp*<br/>
浮動小数点値の_Xの整数指数を返します。

### <a name="return-value"></a>戻り値

カマシサ_Xを返します。

## <a name="frexpf"></a><a name="frexpf"></a>フインシュフ

_X の仮数と指数を取得します。

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

*_Exp*<br/>
浮動小数点値の_Xの整数指数を返します。

### <a name="return-value"></a>戻り値

カマシサ_Xを返します。

## <a name="isfinite"></a><a name="isfinite"></a>イスフィント

引数に有限値が存在するかどうかを判断します。

```cpp
inline int isfinite(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数に有限値がある場合にのみ、0 以外の値を返します。

## <a name="isinf"></a><a name="isinf"></a>イシンフ

引数が無限値であるかどうかを判断します。

```cpp
inline int isinf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数に無限の値がある場合に限り、0 以外の値を返します。

## <a name="isnan"></a><a name="isnan"></a>Isnan

引数が NaN であるかどうかを判断します。

```cpp
inline int isnan(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数に NaN 値がある場合にのみ、0 以外の値を返します。

## <a name="ldexp"></a><a name="ldexp"></a>ldexp

仮数と指数から実数を計算します。

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値、メンタ

*_Exp*<br/>
整数指数

### <a name="return-value"></a>戻り値

2^_Exp_X\*返します

## <a name="ldexpf"></a><a name="ldexpf"></a>ldexpf

仮数と指数から実数を計算します。

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値、メンタ

*_Exp*<br/>
整数指数

### <a name="return-value"></a>戻り値

2^_Exp_X\*返します

## <a name="log"></a><a name="log"></a>ログ

e を底とする引数の対数を計算します。

```cpp
inline float log(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の底を表す対数を返します。

## <a name="log10"></a><a name="log10"></a>ログ10

10 を底とする引数の対数を計算します。

```cpp
inline float log10(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の 10 を底数の対数で返します。

## <a name="log10f"></a><a name="log10f"></a>ログ10f

10 を底とする引数の対数を計算します。

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の 10 を底数の対数で返します。

## <a name="log2"></a><a name="log2"></a>ログ2

2 を底とする引数の対数を計算します。

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の底 2 の対数を返します。

## <a name="log2f"></a><a name="log2f"></a>ログ2f

2 を底とする引数の対数を計算します。

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の 10 を底数の対数で返します。

## <a name="logf"></a><a name="logf"></a>ログフ

e を底とする引数の対数を計算します。

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の底を表す対数を返します。

## <a name="modf"></a><a name="modf"></a>モドフ

_X を小数部と整数部に分割します。

```cpp
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

*_Ip*<br/>
値の整数部分を受け取ります

### <a name="return-value"></a>戻り値

_Xの符号付き小数部分を返します。

## <a name="modff"></a><a name="modff"></a>モッズフ

_X を小数部と整数部に分割します。

```cpp
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

*_Ip*<br/>
値の整数部分を受け取ります

### <a name="return-value"></a>戻り値

_Xの符号付き小数部分を返します。

## <a name="pow"></a><a name="pow"></a>えい

_X の _Y 乗を計算します。

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値、基数

*_y*<br/>
浮動小数点値,指数

### <a name="return-value"></a>戻り値

_Yの累乗に_Xの値を返します。

## <a name="powf"></a><a name="powf"></a>ポウフ

_X の _Y 乗を計算します。

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値、基数

*_y*<br/>
浮動小数点値,指数

### <a name="return-value"></a>戻り値

## <a name="round"></a><a name="round"></a>ラウンド

_X を最も近い整数値に丸めます。

```cpp
inline float round(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_Xの最も近い整数を返します。

## <a name="roundf"></a><a name="roundf"></a>ラウンドフ

_X を最も近い整数値に丸めます。

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_Xの最も近い整数を返します。

## <a name="rsqrt"></a><a name="rsqrt"></a>rsqrt

引数の平方根の逆数を返します。

```cpp
inline float rsqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の平方根の逆数を返します。

## <a name="rsqrtf"></a><a name="rsqrtf"></a>を使用します。

引数の平方根の逆数を返します。

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の平方根の逆数を返します。

## <a name="signbit"></a><a name="signbit"></a>サインビット

_Xの符号が負であるかどうかを判断します。

```cpp
inline int signbit(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_Xの符号が負の場合にのみ、0 以外の値を返します。

## <a name="signbitf"></a><a name="signbitf"></a>サインビットフ

_Xの符号が負であるかどうかを判断します。

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_Xの符号が負の場合にのみ、0 以外の値を返します。

## <a name="sin"></a><a name="sin"></a>罪

引数の正弦値を計算します。

```cpp
inline float sin(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の正常な値を返します。

## <a name="sinf"></a><a name="sinf"></a>シンフ

引数の正弦値を計算します。

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の正常な値を返します。

## <a name="sincos"></a><a name="sincos"></a>シンコス

_X の正弦と余弦の値を計算します

```cpp
inline void sincos(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

*_S*<br/>
_Xの右の値を返します。

*_C*<br/>
_Xの余弦値を返します。

## <a name="sincosf"></a><a name="sincosf"></a>シンコスフ

_X の正弦と余弦の値を計算します

```cpp
inline void sincosf(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

*_S*<br/>
_Xの右の値を返します。

*_C*<br/>
_Xの余弦値を返します。

## <a name="sinh"></a><a name="sinh"></a>Sinh

引数の双曲線正弦の値を計算します。

```cpp
inline float sinh(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の双曲線正弦の値を返します。

## <a name="sinhf"></a><a name="sinhf"></a>シンフ

引数の双曲線正弦の値を計算します。

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の双曲線正弦の値を返します。

## <a name="sqrt"></a><a name="sqrt"></a>Sqrt

引数のスコール ルートを計算します。

```cpp
inline float sqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のスコール ルートを返します。

## <a name="sqrtf"></a><a name="sqrtf"></a>sqrtf

引数のスコール ルートを計算します。

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のスコール ルートを返します。

## <a name="tan"></a><a name="tan"></a>日焼け

引数の正接値を計算します。

```cpp
inline float tan(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の正接値を返します。

## <a name="tanf"></a><a name="tanf"></a>タンフ

引数の正接値を計算します。

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の正接値を返します。

## <a name="tanh"></a><a name="tanh"></a>Tanh

引数の双曲線正接の値を計算します。

```cpp
inline float tanh(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の双曲線正接値を返します。

## <a name="tanhf"></a><a name="tanhf"></a>タンフ

引数の双曲線正接の値を計算します。

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の双曲線正接値を返します。

## <a name="trunc"></a><a name="trunc"></a>トランク

引数を整数コンポーネントに切り捨てます。

```cpp
inline float trunc(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の整数要素を返します。

## <a name="truncf"></a><a name="truncf"></a>を切り取る

引数を整数コンポーネントに切り捨てます。

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_x*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の整数要素を返します。

## <a name="requirements"></a>必要条件

**ヘッダー:** amp_math.h**名前空間:** 同時実行:fast_math

## <a name="see-also"></a>関連項目

[Concurrency::fast_math 名前空間](concurrency-fast-math-namespace.md)
