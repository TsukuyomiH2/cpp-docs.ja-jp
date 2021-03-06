---
description: '詳細については、次を参照してください: _ITERATOR_DEBUG_LEVEL'
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: 769b7f3a8eecd3c994ee82b67385f080f0945f33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306639"
---
# <a name="_iterator_debug_level"></a>_ITERATOR_DEBUG_LEVEL

_ITERATOR_DEBUG_LEVEL マクロは、チェックを行う [反復](../standard-library/checked-iterators.md) 子と [デバッグ反復子のサポート](../standard-library/debug-iterator-support.md) を有効にするかどうかを制御します。 このマクロは、以前の _SECURE_SCL と _HAS_ITERATOR_DEBUGGING マクロの機能を置き換え、その機能を組み合わせたものです。

## <a name="macro-values"></a>マクロの値

次の表は、_ITERATOR_DEBUG_LEVEL マクロで使用可能な値をまとめたものです。

|コンパイル モード|マクロの値|説明|
|----------------------|----------------|-----------------|
|**デバッグ**|||
||0|チェックを行う反復子を無効にし、反復子のデバッグを無効にします。|
||1|チェックを行う反復子を有効にし、反復子のデバッグを無効にします。|
||2 (既定値)|反復子のデバッグを有効にします。チェックを行う反復子は関連しません。|
|**リリース**|||
||0 (既定値)|チェックを行う反復子を無効にします。|
||1|チェックを行う反復子を有効にします。反復子のデバッグは関連しません。|

リリースモードでは、_ITERATOR_DEBUG_LEVEL を2に指定すると、コンパイラによってエラーが生成されます。

## <a name="remarks"></a>解説

_ITERATOR_DEBUG_LEVEL マクロは、チェックを行う [反復子](../standard-library/checked-iterators.md) を有効にするかどうかを制御します。デバッグモードでは、 [デバッグ反復子のサポート](../standard-library/debug-iterator-support.md) が有効かどうかを制御します。 _ITERATOR_DEBUG_LEVEL が1または2として定義されている場合、チェックを行う反復子は、コンテナーの境界が上書きされないようにします。 _ITERATOR_DEBUG_LEVEL が0の場合、反復子はチェックされません。 _ITERATOR_DEBUG_LEVEL が1と定義されている場合、安全ではない反復子を使用すると、ランタイムエラーが発生し、プログラムが終了します。 _ITERATOR_DEBUG_LEVEL が2と定義されている場合、アンセーフ反復子を使用すると、アサートと、デバッガーを中断するランタイムエラーダイアログが発生します。

_ITERATOR_DEBUG_LEVEL マクロは、_SECURE_SCL および _HAS_ITERATOR_DEBUGGING マクロと同様の機能をサポートしているため、特定の状況で使用するマクロとマクロの値がわからない場合があります。 混乱を防ぐために、_ITERATOR_DEBUG_LEVEL マクロのみを使用することをお勧めします。 次の表では、_SECURE_SCL のさまざまな値に使用する同等の _ITERATOR_DEBUG_LEVEL マクロ値と、既存のコード内の _HAS_ITERATOR_DEBUGGING について説明します。

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (リリースの既定値)|0 (無効)|0 (無効)|
|1|1 (有効)|0 (無効)|
|2 (デバッグの既定値)|(関連性なし)|1 (デバッグ モードで有効)|

チェックを行う反復子に関する警告を無効にする方法の詳細については、「[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)」を参照してください。

### <a name="example"></a>例

_ITERATOR_DEBUG_LEVEL マクロの値を指定するには、 [/d](../build/reference/d-preprocessor-definitions.md) コンパイラオプションを使用してコマンドラインで定義します。または、 `#define` C++ 標準ライブラリヘッダーがソースファイルに含まれる前にを使用します。 たとえば、コマンドラインで、デバッグモードで *サンプル .cpp* をコンパイルし、デバッグ反復子のサポートを使用するには、_ITERATOR_DEBUG_LEVEL マクロ定義を指定します。

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

ソース ファイルで、反復子を定義する標準ライブラリ ヘッダーの前にマクロを指定します。

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>関連項目

[チェックを行う反復子](../standard-library/checked-iterators.md)\
[反復子のデバッグのサポート](../standard-library/debug-iterator-support.md)\
[安全なライブラリ: C++ 標準ライブラリ](../standard-library/safe-libraries-cpp-standard-library.md)
