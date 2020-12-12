---
description: '詳細情報: サンプラークラス'
title: sampler クラス
ms.date: 06/28/2018
f1_keywords:
- sampler
- AMP_GRAPHICS/sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::get_address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::get_border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::get_filter_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::filter_mode
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
ms.openlocfilehash: 61292cccb9e28ca76dc4ecaa1aaca849d9219ffc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327617"
---
# <a name="sampler-class"></a>sampler クラス

サンプラーのクラスは、テクスチャ サンプリングに使用するサンプリング構成情報を集計します。

## <a name="syntax"></a>構文

```cpp
class sampler;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[サンプラーコンストラクター](#ctor)|オーバーロードされます。 サンプラーのインスタンスを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|サンプラー オブジェクトに関連付けられている `address_mode` を返します。|
|[get_border_color](#get_border_color)|サンプラー オブジェクトに関連付けられている境界線の色を返します。|
|[get_filter_mode](#get_filter_mode)|サンプラー オブジェクトに関連付けられている `filter_mode` を返します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[operator =](#operator_eq)|オーバーロードされます。 代入演算子。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[address_mode](#address_mode)|`sampler` オブジェクトのアドレス モードを取得します。|
|[border_color](#border_color)|`sampler` オブジェクトの境界線の色を取得します。|
|[filter_mode](#filter_mode)|`sampler` オブジェクトのフィルター モードを取得します。|

## <a name="inheritance-hierarchy"></a>継承階層

`sampler`

## <a name="requirements"></a>要件

**ヘッダー:** amp_graphics

**名前空間:** concurrency:: graphics

## <a name="sampler"></a><a name="ctor"></a> カラーサンプラー

[サンプラークラス](sampler-class.md)のインスタンスを構築します。

```cpp
sampler() restrict(cpu);    // [1] default constructor

sampler(                    // [2] constructor
    filter_mode _Filter_mode) restrict(cpu);

sampler(                    // [3] constructor
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [4] constructor
    filter_mode _Filter_mode,
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [5] copy constructor
    const sampler& _Other) restrict(amp,
    cpu);

sampler(                    // [6] move constructor
    sampler&& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>パラメーター

*_Filter_mode*<br/>
サンプリングで使用するフィルター モード。

*_Address_mode*<br/>
すべての次元のサンプリングで使用されるアドレッシング モード。

*_Border_color*<br/>
アドレス モードが address_border である場合に使用される境界線の色。 既定値は `float_4(0.0f, 0.0f, 0.0f, 0.0f)` です。

*_Other*<br/>
[5] コピーコンストラクター `sampler` 新しいインスタンスにコピーするオブジェクト `sampler` 。

[6] `sampler` 新しいインスタンスに移動するオブジェクトをコンストラクターに移動し `sampler` ます。

## <a name="address_mode"></a><a name="address_mode"></a> address_mode

`sampler` オブジェクトのアドレス モードを取得します。

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

## <a name="border_color"></a><a name="border_color"></a> border_color

`sampler` オブジェクトの境界線の色を取得します。

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

## <a name="filter_mode"></a><a name="filter_mode"></a> filter_mode

`sampler` オブジェクトのフィルター モードを取得します。

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

## <a name="get_address_mode"></a><a name="get_address_mode"></a> get_address_mode

この `sampler` のために構成されたフィルター モードを返します。

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>戻り値

サンプラーのために構成されたアドレス モード。

## <a name="get_border_color"></a><a name="get_border_color"></a> get_border_color

この `sampler` に構成された境界線の色を返します。

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>戻り値

境界線の色が含まれる float_4。

## <a name="get_filter_mode"></a><a name="get_filter_mode"></a> get_filter_mode

この `sampler` のために構成されたフィルター モードを返します。

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>戻り値

サンプラーのために構成されたフィルター モード。

## <a name="operator"></a><a name="operator_eq"></a> operator =

別のサンプラー オブジェクトの値を既存のサンプラーに割り当てます。

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>パラメーター

*_Other*<br/>
[1] 代入演算子をコピー `sampler` するオブジェクトをこのにコピーし `sampler` ます。

[2] 代入演算子を `sampler` このに移動するオブジェクトに移動し `sampler` ます。

### <a name="return-value"></a>戻り値

このサンプラーのインスタンスへの参照。

## <a name="see-also"></a>関連項目

[Concurrency::graphics 名前空間](concurrency-graphics-namespace.md)
