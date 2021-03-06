---
description: '詳細については、次を参照してください: __int8、__int16、__int32、__int64'
title: __int8、__int16、__int32、__int64
ms.date: 10/09/2018
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
- __int8
- __int16
- __int32
- __int64
- _int8
- _int16
- _int32
- _int64
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
ms.openlocfilehash: 8dddb8dc63b8aa9898b78ee02ea2dc904b362442
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332511"
---
# <a name="__int8-__int16-__int32-__int64"></a>__int8、__int16、__int32、__int64

**Microsoft 固有の仕様**

Microsoft C/C++ の機能では、サイズ設定された整数型をサポートします。 型指定子を使用して、8ビット、16ビット、32ビット、または64ビットの整数変数を宣言でき **`__intN`** ます。ここで、* *_`N`_* _ は8、16、32、または64です。

次の例は、サイズ設定された整数のこれらの型のそれぞれに 1 つの変数を宣言しています。

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

型 _ * `__int8` * *、 **`__int16`** 、およびは、 **`__int32`** 同じサイズを持つ ANSI 型のシノニムであり、複数のプラットフォームで同じように動作する移植性のあるコードを記述する場合に便利です。 データ型は、型と同義であり、型と同義であり、型と同義です **`__int8`** **`char`** **`__int16`** **`short`** **`__int32`** **`int`** 。 型は、 **`__int64`** 型と同義です **`long long`** 。

以前のバージョンとの互換性のため、、、 **`_int8`** **`_int16`** **`_int32`** 、および **`_int64`** は **`__int8`** 、 **`__int16`** コンパイラオプションの [ **`__int32`** **`__int64`** [ `/Za` \( 言語拡張を無効にする](../build/reference/za-ze-disable-language-extensions.md)] が指定されていない限り、、、、およびのシノニムです。

## <a name="example"></a>例

次の例は、パラメーターがに昇格されることを示してい `__intN` **`int`** ます。

```cpp
// sized_int_types.cpp

#include <stdio.h>

void func(int i) {
    printf_s("%s\n", __FUNCTION__);
}

int main()
{
    __int8 i8 = 100;
    func(i8);   // no void func(__int8 i8) function
                // __int8 will be promoted to int
}
```

```Output
func
```

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)<br/>
[組み込み型](../cpp/fundamental-types-cpp.md)<br/>
[データ型の範囲](../cpp/data-type-ranges.md)<br/>
