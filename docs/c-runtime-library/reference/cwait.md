---
title: _cwait
ms.date: 4/2/2020
api_name:
- _cwait
- _o__cwait
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
- api-ms-win-crt-process-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: d54f62c8ce391b2c8ead92a0a73ac48e6f2b3cb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348152"
---
# <a name="_cwait"></a>_cwait

ほかのプロセスが終了するまで待機します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
intptr_t _cwait(
   int *termstat,
   intptr_t procHandle,
   int action
);
```

### <a name="parameters"></a>パラメーター

*用語スタット*<br/>
指定されたプロセスの結果コードが格納されるバッファーへのポインター、 または**NULL。**

*ハンドルを処理する*<br/>
待機するプロセス (つまり **、_cwait**が戻る前に終了する必要があるプロセス) へのハンドル。

*action*<br/>
NULL: Windows オペレーティング システム アプリケーションによって無視されます。他のアプリケーションの場合: *procHandle*で実行するアクション コード 。

## <a name="return-value"></a>戻り値

指定されたプロセスが正常に完了すると、指定されたプロセスのハンドルを返し、指定されたプロセスによって返される結果コードに*termstat*を設定します。 それ以外の場合は-1 を返し **、errno**を次のように設定します。

|[値]|説明|
|-----------|-----------------|
|**ECHILD**|指定されたプロセスが存在しないか、*プロセスハンドル*が無効であるか、または[呼](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess)び出しが[WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)失敗しました。|
|**Einval**|*アクション*が無効です。|

これらのリターン コードとその他のリターン コードの詳細については、「[errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>解説

**_cwait**関数は *、procHandle*によって提供される指定されたプロセスのプロセス ID の終了を待機します。 **_cwait**に渡される*procHandle*の値は、指定されたプロセスを作成した[_spawn](../../c-runtime-library/spawn-wspawn-functions.md)関数の呼び出しによって返される値である必要があります。 **_cwait**が呼び出される前にプロセス ID が終了すると **、_cwait**はすぐに戻ります。 **_cwait**は、有効なハンドル (*procHandle*) が存在する他の既知のプロセスを待機するために、任意のプロセスで使用できます。

*termstat*は、指定されたプロセスの戻りコードが格納されるバッファーを指します。 *用語スタット*の値は、指定されたプロセスが Windows [ExitProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) API を呼び出すことによって正常に終了したかどうかを示します。 **ExitProcess**は、指定されたプロセスが**exit**または **_exit**を呼び出した**場合、内部**で呼び出**されます。** *用語スタット*を通じて渡される値の詳細については、[を](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess)参照してください。 **_cwait**が *、termstat*に**NULL**値を使用して呼び出された場合、指定されたプロセスの戻りコードは保管されません。

これらの環境では親子関係が実装されていないため *、Windows*オペレーティング システムではアクション パラメーターは無視されます。

*procHandle*が -1 または -2 (現在のプロセスまたはスレッドへのハンドル) でない限り、ハンドルは閉じられます。 したがって、この状況では、返されたハンドルは使用しないでください。

既定では、この関数のグローバル状態はアプリケーションにスコープされます。 これを変更するには[、CRT のグローバル状態を](../global-state.md)参照してください。

## <a name="requirements"></a>必要条件

|ルーチン|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="example"></a>例

```C
// crt_cwait.c
// compile with: /c
// This program launches several processes and waits
// for a specified process to finish.

#define _CRT_RAND_S

#include <windows.h>
#include <process.h>
#include <stdlib.h>
#include <stdio.h>
#include <time.h>

// Macro to get a random integer within a specified range
#define getrandom( min, max ) (( (rand_s (&number), number) % (int)((( max ) + 1 ) - ( min ))) + ( min ))

struct PROCESS
{
   int     nPid;
   char    name[40];
} process[4] = { { 0, "Ann" }, { 0, "Beth" }, { 0, "Carl" }, { 0, "Dave" } };

int main( int argc, char *argv[] )
{
   int termstat, c;
   unsigned int number;

   srand( (unsigned)time( NULL ) );    // Seed randomizer

   // If no arguments, this is the calling process
   if ( argc == 1 )
   {
      // Spawn processes in numeric order
      for ( c = 0; c < 4; c++ ) {
         _flushall();
         process[c].nPid = _spawnl( _P_NOWAIT, argv[0], argv[0],
                                    process[c].name, NULL );
      }

      // Wait for randomly specified process, and respond when done
      c = getrandom( 0, 3 );
      printf( "Come here, %s.\n", process[c].name );
      _cwait( &termstat, process[c].nPid, _WAIT_CHILD );
      printf( "Thank you, %s.\n", process[c].name );

   }
   // If there are arguments, this must be a spawned process
   else
   {
      // Delay for a period that's determined by process number
      Sleep( (argv[1][0] - 'A' + 1) * 1000L );
      printf( "Hi, Dad. It's %s.\n", argv[1] );
   }
}
```

```Output
Hi, Dad. It's Ann.
Come here, Ann.
Thank you, Ann.
Hi, Dad. It's Beth.
Hi, Dad. It's Carl.
Hi, Dad. It's Dave.
```

## <a name="see-also"></a>関連項目

[プロセスと環境の制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn 系関数と _wspawn 系関数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
