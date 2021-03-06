---
description: '詳細については、次を参照してください: _aligned_offset_recalloc'
title: _aligned_offset_recalloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_recalloc
- _o__aligned_offset_recalloc
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- aligned_offset_recalloc
- _aligned_offset_recalloc
helpviewer_keywords:
- aligned_offset_recalloc function
- _aligned_offset_recalloc function
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
ms.openlocfilehash: ce24dd0394d8bde67811bc0a175bbbfbb45dc67a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135760"
---
# <a name="_aligned_offset_recalloc"></a>_aligned_offset_recalloc

[_aligned_malloc](aligned-malloc.md) または [_aligned_offset_malloc](aligned-offset-malloc.md) で割り当てられたメモリ ブロックのサイズを変更し、メモリを 0 に初期化します。

## <a name="syntax"></a>構文

```C
void * _aligned_offset_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>パラメーター

*memblock*<br/>
現在のメモリ ブロック ポインター。

*number*<br/>
要素の数。

*size*<br/>
各要素の長さ (バイト単位)。

*配置*<br/>
アラインメント値。2 の整数乗である必要があります。

*offset*<br/>
アラインメントを強制するためのメモリ割り当てへのオフセット。

## <a name="return-value"></a>戻り値

**_aligned_offset_recalloc** は、再割り当てされた (移動された可能性がある) メモリブロックへの void ポインターを返します。 サイズが0でバッファー引数が **null** でない場合、またはブロックを指定されたサイズに拡張するのに十分なメモリがない場合、戻り値は **null** になります。 最初の場合には、元のブロックは解放されます。 2 番目の場合には、元のブロックは変更されません。 戻り値は、どの型のオブジェクトを格納する場合でも適切なアラインメントが保証されるストレージ領域を指します。 void 以外の型へのポインターを取得するには、戻り値の型キャストを使用します。

**_aligned_offset_recalloc** はとマークされ `__declspec(noalias)` `__declspec(restrict)` ます。つまり、関数は、グローバル変数を変更せず、返されるポインターがエイリアス化されていないことを保証します。 詳細については、「[noalias](../../cpp/noalias.md)」、および「[restrict](../../cpp/restrict.md)」を参照してください。

## <a name="remarks"></a>解説

[_Aligned_offset_malloc](aligned-offset-malloc.md)と同様に、 **_aligned_offset_recalloc** を使用すると、構造体内のオフセットに構造体を配置できます。

**_aligned_offset_recalloc** は **malloc** に基づいています。 **_Aligned_offset_malloc** の使用方法の詳細については、「 [malloc](malloc.md)」を参照してください。 *Memblock* が **NULL** の場合、関数は **_aligned_offset_malloc** を内部で呼び出します。

この関数は、メモリ割り当てが失敗した場合、または要求されたサイズ (*数値*   *  *サイズ*)**が _HEAP_MAXREQ** よりも大きい場合に、errno を ENOMEM に設定します。 **Errno** の詳細については、「 [errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。 また、 **_aligned_offset_recalloc** パラメーターを検証します。 *Alignment* が2の累乗でない場合、または *オフセット* が要求されたサイズ以上で0以外の場合、この関数は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は **NULL** を返し、 **errno** を **EINVAL** に設定します。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_aligned_offset_recalloc**|\<malloc.h>|

## <a name="see-also"></a>関連項目

[データの配置](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
