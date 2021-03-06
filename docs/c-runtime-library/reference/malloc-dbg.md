---
description: '詳細については、次を参照してください: _malloc_dbg'
title: _malloc_dbg
ms.date: 11/04/2016
api_name:
- _malloc_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- malloc_dbg
- _malloc_dbg
helpviewer_keywords:
- malloc_dbg function
- memory allocation
- _malloc_dbg function
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
ms.openlocfilehash: 56b39ecbbe5f90d9eee378d4ce42016e5960ff63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299814"
---
# <a name="_malloc_dbg"></a>_malloc_dbg

デバッグ ヘッダーと上書きバッファー用の追加の領域を持つメモリ ブロックをヒープに割り当てます (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
void *_malloc_dbg(
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*size*<br/>
要求するメモリ ブロックのサイズ (バイト単位)。

*blockType*<br/>
要求されたメモリブロックの種類: **_CLIENT_BLOCK** または **_NORMAL_BLOCK**。

*filename*<br/>
割り当て操作を要求したソースファイルの名前へのポインターまたは **NULL**。

*linenumber*<br/>
割り当て操作が要求されたソースファイル内の行番号または **NULL**。

*Filename* パラメーターと *linenumber* パラメーターは、 **_malloc_dbg** が明示的に呼び出された場合、または [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)プリプロセッサ定数が定義されている場合にのみ使用できます。

## <a name="return-value"></a>戻り値

正常に完了した場合、この関数は、割り当てられたメモリブロックのユーザー部分へのポインターを返すか、新しいハンドラー関数を呼び出すか、 **NULL** を返します。 戻る動作の詳細については、後の「解説」のセクションを参照してください。 新しいハンドラー関数がどのように使用されるかの詳細については、[malloc](malloc.md) 関数を参照してください。

## <a name="remarks"></a>解説

**_malloc_dbg** は、 [malloc](malloc.md) 関数のデバッグバージョンです。 [_DEBUG](../../c-runtime-library/debug.md)が定義されていない場合、 **_malloc_dbg** の各呼び出しは **malloc** への呼び出しに限定されます。 **Malloc** と **_malloc_dbg** は、ベースヒープ内にメモリブロックを割り当てますが、 **_malloc_dbg** はいくつかのデバッグ機能を提供します。リークをテストするためのブロックのユーザー部分の両側のバッファー、特定の割り当ての種類を追跡するためのブロック型パラメーター、割り当て要求の起点を特定するための *ファイル名* / *linenumber* 情報です。

**_malloc_dbg** は、要求された *サイズ* よりも若干多くの領域を使用してメモリブロックを割り当てます。 追加の領域は、デバッグ メモリ ブロックをリンクし、アプリケーションにデバッグ ヘッダー情報と上書きバッファーを提供するために、デバッグ ヒープ マネージャーによって使用されます。 ブロックが割り当てられると、ブロックのユーザー部分には値 0xCD が設定され、各上書きバッファーには 0xFD が設定されます。

**_malloc_dbg** は、メモリの割り当てが失敗した場合、または必要なメモリの量 (前に説明したオーバーヘッドを含む) が **_HEAP_MAXREQ** を超えた場合に、 **errno** を **ENOMEM** に設定します。 このエラー コードと他のエラーコードの詳細については、「[errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 割り当てブロックの型とその使用方法については、「 [デバッグヒープ上のブロックの型](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。 標準で呼び出すヒープ関数と、アプリケーションのデバッグ ビルドで呼び出すデバッグ バージョンのヒープ関数との違いの詳細については、「[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_malloc_dbg**|\<crtdbg.h>|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="example"></a>例

**_Malloc_dbg** の使用方法の例については、「 [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)」を参照してください。

## <a name="see-also"></a>関連項目

[デバッグルーチン](../../c-runtime-library/debug-routines.md)<br/>
[malloc](malloc.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
