---
title: _popen、_wpopen
ms.date: 11/04/2016
apiname:
- _popen
- _wpopen
apilocation:
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
ms.openlocfilehash: 03eb36573abe8e26c47e6dd38c009e5819e60f8f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499596"
---
# <a name="_popen-_wpopen"></a>_popen、_wpopen

パイプを作成し、コマンドを実行します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
FILE *_popen(
    const char *command,
    const char *mode
);
FILE *_wpopen(
    const wchar_t *command,
    const wchar_t *mode
);
```

### <a name="parameters"></a>パラメーター

*command*<br/>
実行するコマンド。

*モード*<br/>
返されるストリームのモード。

## <a name="return-value"></a>戻り値

作成されたパイプの一方の端に関連付けられているストリームを返します。 パイプのもう一方の端は、開始されたコマンドの標準入力または標準出力に関連付けられます。 エラー発生時には、関数は **NULL** を返します。 *コマンド*または*モード*が null ポインターの場合や、*モード*が有効なモードでない場合など、エラーが無効なパラメーターである場合、 **errno**は**EINVAL**に設定されます。 有効なモードについては、「解説」を参照してください。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**_Popen**関数は、パイプを作成し、指定した文字列*コマンド*を使用して、コマンドプロセッサの生成されたコピーを非同期に実行します。 *mode* 文字列では、次のように、要求するアクセスの種類を指定します。

|アクセス モード|説明|
|-|-|
|**"r"**|呼び出しプロセスは、返されたストリームを使用して、開始されたコマンドの標準出力を読み取ることができます。|
|**"w"**|呼び出しプロセスは、返されたストリームを使用して、開始されたコマンドの標準入力に書き込むことができます。|
|**"b"**|バイナリ モードで開きます。|
|**"t"**|テキスト モードで開きます。|

> [!NOTE]
> Windows プログラムで使用した場合、 **_popen**関数は無効なファイルポインターを返し、プログラムは無期限に応答を停止します。 **_popen**は、コンソールアプリケーションで正常に動作します。 入力と出力をリダイレクトする Windows アプリケーションを作成するには、「Windows SDK にリダイレクトされた[入力と出力を持つ子プロセスの作成](/windows/win32/ProcThread/creating-a-child-process-with-redirected-input-and-output)」を参照してください。

**_wpopen**は、 **_popen**のワイド文字バージョンです。 **_wpopen**への*パス*引数は、ワイド文字列です。 それ以外では、 **_wpopen**と **_popen**は同じように動作します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_popen.c
/* This program uses _popen and _pclose to receive a
* stream of text from a system process.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{

   char   psBuffer[128];
   FILE   *pPipe;

        /* Run DIR so that it writes its output to a pipe. Open this
         * pipe with read text attribute so that we can read it
         * like a text file.
         */

   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )
      exit( 1 );

   /* Read pipe until end of file, or an error occurs. */

   while(fgets(psBuffer, 128, pPipe))
   {
      printf(psBuffer);
   }

   /* Close pipe and print return value of pPipe. */
   if (feof( pPipe))
   {
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );
   }
   else
   {
     printf( "Error: Failed to read the pipe to the end.\n");
   }
}
```

### <a name="sample-output"></a>出力例

この出力は、現在のディレクトリに .c ファイル名拡張子を持つファイルが 1 個だけあると仮定しています。

```Output
Volume in drive C is CDRIVE
Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pclose](pclose.md)<br/>
[_pipe](pipe.md)<br/>
