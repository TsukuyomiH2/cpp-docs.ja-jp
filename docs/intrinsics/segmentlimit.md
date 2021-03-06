---
description: '詳細については、次を参照してください: __segmentlimit'
title: __segmentlimit
ms.date: 09/02/2019
f1_keywords:
- __segmentlimit
helpviewer_keywords:
- __segmentlimit intrinsic
- lsl instruction
ms.assetid: d0bc3630-90cb-4185-8667-686fd41e23d4
ms.openlocfilehash: 49f8688918e07e143615af7b184a784daa0eaaa1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307003"
---
# <a name="__segmentlimit"></a>__segmentlimit

**Microsoft 固有の仕様**

`lsl`(セグメントの読み込み制限) 命令を生成します。

## <a name="syntax"></a>構文

```C
unsigned long __segmentlimit(
   unsigned long a
);
```

### <a name="parameters"></a>パラメーター

*ある*\
からセグメントセレクターを指定する定数。

## <a name="return-value"></a>戻り値

セレクターが有効で現在のアクセス許可レベルで表示されている場合 *は、によって* 指定されたセグメントセレクターのセグメント制限。

## <a name="requirements"></a>要件

|Intrinsic|アーキテクチャ|
|---------------|------------------|
|`__segmentlimit`|x86、x64|

**ヘッダー ファイル** \<intrin.h>

## <a name="remarks"></a>解説

セグメントの上限を取得できない場合、この命令は失敗します。 エラーが発生すると、この命令は ZF フラグをクリアし、戻り値は未定義になります。

このルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```cpp
#include <stdio.h>

#ifdef _M_IX86
typedef unsigned int READETYPE;
#else
typedef unsigned __int64 READETYPE;
#endif

#define EFLAGS_ZF      0x00000040
#define KGDT_R3_DATA    0x0020
#define RPL_MASK        0x3

extern "C"
{
unsigned long __segmentlimit (unsigned long);
READETYPE __readeflags();
}

#pragma intrinsic(__readeflags)
#pragma intrinsic(__segmentlimit)

int main(void)
{
   const unsigned long initsl = 0xbaadbabe;
   READETYPE eflags = 0;
   unsigned long sl = initsl;

   printf("Before: segment limit =0x%x eflags =0x%x\n", sl, eflags);
   sl = __segmentlimit(KGDT_R3_DATA + RPL_MASK);

   eflags = __readeflags();

   printf("After: segment limit =0x%x eflags =0x%x eflags.zf = %s\n", sl, eflags, (eflags & EFLAGS_ZF) ? "set" : "clear");

   // If ZF is set, the call to lsl succeeded; if ZF is clear, the call failed.
   printf("%s\n", eflags & EFLAGS_ZF ? "Success!": "Fail!");

   // You can verify the value of sl to make sure that the instruction wrote to it
   printf("sl was %s\n", (sl == initsl) ? "unchanged" : "changed");

   return 0;
}
```

```Output
Before: segment limit =0xbaadbabe eflags =0x0
After: segment limit =0xffffffff eflags =0x256 eflags.zf = set
Success!
sl was changed
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
