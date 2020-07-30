---
title: '移植のガイド: Spy++'
ms.date: 10/23/2019
ms.assetid: e558f759-3017-48a7-95a9-b5b779d5e51d
ms.openlocfilehash: 6f63f082d96f33246592b0e7f39b6788417f8a32
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217858"
---
# <a name="porting-guide-spy"></a>移植のガイド: Spy++

この移植のケース スタディは、一般的な移植プロジェクトのアイデア、発生する可能性がある問題の種類、および移植の問題に対応するための一般的なヒントとコツを理解できるように設計されています。 プロジェクトの移植に関するエクスペリエンスは、コードの仕様により大きく依存するため、移植をわかりやすく案内するためのものではありません。

## <a name="spy"></a>Spy++

Spy++ は Windows デスクトップで広く使用される GUI 診断ツールであり、Windows デスクトップのユーザー インターフェイス要素に関するあらゆる種類の情報を提供します。 ウィンドウの完全な階層を表示し、各ウィンドウとコントロールについてのメタデータへのアクセスを提供します。 この便利なアプリケーションは、多年にわたって、Visual Studio に付属しています。 最後にコンパイルされたのが Visual C++ 6.0 で、Visual Studio 2015 に移植された古いバージョンも見つかっています。 Visual Studio 2017 または Visual Studio 2019 のエクスペリエンスはほぼ同じである必要があります。

私たちは、MFC と Win32 API を使用する Windows デスクトップ アプリケーションの移植で、特に Visual C++ 6.0 以降の Visual C++ のリリースごとに更新されていない古いプロジェクトでは、このようなケースが標準的であると考えました。

## <a name="step-1-converting-the-project-file"></a><a name="convert_project_file"></a> 手順 1. プロジェクト ファイルを変換する

Visual C++ 6.0 からの 2 つの古い .dsw ファイルのプロジェクト ファイルは、とくに注意が必要な問題はなく、簡単に変換されました。 1 つのプロジェクトは、spy++ アプリケーションです。 もう 1 つは SpyHk で、C で作成され、DLL をサポートします。 より複雑なプロジェクトは、[ここ](../porting/visual-cpp-porting-and-upgrading-guide.md)で説明するように、簡単にアップグレードできないことがあります。

2 つのプロジェクトをアップグレードした後、ソリューションは次のようになります。

![Spy&#43;&#43; ソリューション](../porting/media/spyxxsolution.PNG "Spy&#43;&#43; ソリューション")

1 つは多数の C++ ファイルを持ち、もう 1 つは C で作成された DLL ファイルを持つ 2 つのプロジェクトがあります。

## <a name="step-2-header-file-problems"></a><a name="header_file_problems"></a>ステップ 2.  ヘッダー ファイルの問題

新しく変換されたプロジェクトのビルド時に、プロジェクトで使用するヘッダー ファイルが見つからないことがよくあります。

Spy++ で見つからないファイルの 1 つが verstamp.h でした。 インターネットの検索から、これは DAO SDK という古いデータ テクノロジからのものであることがわかりました。 このヘッダー ファイルから使用されているシンボルを探し、ファイルが本当に必要なのか、それともこれらのシンボルが別の場所で定義されているのか確認しようと思い、ヘッダー ファイルの宣言をコメント化して、再コンパイルしました。 その結果、必要なシンボルは VER_FILEFLAGSMASK の 1 つだけだということがわかりました。

```Output
1>C:\Program Files (x86)\Windows Kits\8.1\Include\shared\common.ver(212): error RC2104: undefined keyword or key name: VER_FILEFLAGSMASK
```

使用可能なインクルードファイルでシンボルを検索する最も簡単な方法は、 **[フォルダー**を指定して検索] (**Ctrl** + **Shift** + **F**) を使用して**Visual C++ インクルードディレクトリ**を指定することです。 ntverp.h でこれを検出しました。 verstamp.h のインクルードを ntverp.h に置き換えることで、このエラーが表示されなくなりました。

## <a name="step-3-linker-outputfile-setting"></a><a name="linker_output_settings"></a>手順 3. リンカー出力ファイルの設定

古いプロジェクトでは、ファイルが通常とは異なる場所に配置されていることがあり、これによりアップグレード後に問題が発生することがあります。 この場合、`$(SolutionDir)` をプロジェクトのプロパティの**インクルード** パスに追加して、そこに配置されたいくつかのヘッダー ファイルが、そこから Visual Studio により確実に検出されるようにします (いずれか 1 つのプロジェクト フォルダーで検出されるのではなく)。

MSBuild は、 **OutputFile**プロパティが**TargetPath**および**TargetName**値と一致せず、MSB8012 を発行していることを苦情としています。

```Output
warning MSB8012: TargetPath(...\spyxx\spyxxhk\.\..\Debug\SpyxxHk.dll) does not match the Linker's OutputFile property value (...\spyxx\Debug\SpyHk55.dll). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).warning MSB8012: TargetName(SpyxxHk) does not match the Linker's OutputFile property value (SpyHk55). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).
```

**Link.OutputFile** はビルド出力であり (EXE、DLL など)、通常はパス、ファイル名、および拡張機能を示す `$(TargetDir)$(TargetName)$(TargetExt)` から構成されます。 これは、古い Visual C++ ビルド ツール (vcbuild.exe) から新しいビルド ツール (MSBuild.exe) にプロジェクトを移行する場合の一般的なエラーです。 Visual Studio 2010 でビルド ツールの変更が発生したため、2010 より前のプロジェクトを 2010 以降のバージョンに移行するたびに、この問題が発生する可能性があります。 基本的な問題は、プロジェクトの移行ウィザードで**OutputFile**値が更新されないことです。これは、他のプロジェクト設定に基づいて値を決定することが常に可能であるとは限りません。 そのため、通常は手動で設定する必要があります。 詳細については、Visual C++ ブログのこの[投稿](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/)を参照してください。

このケースでは、変換されたプロジェクトの **Link.OutputFile** プロパティが Spy++ プロジェクト用の .\Debug\Spyxx.exe と .\Release\Spyxx.exe に設定されました (構成に応じて異なります)。 確実な方法は、これらのハードコードされた値を**すべての構成**で `$(TargetDir)$(TargetName)$(TargetExt)` に置き換えることです。 それでもうまくいかない場合は、そこからカスタマイズしたり、これらの値が設定されている **[全般**] セクションのプロパティを変更したりできます (プロパティは [**出力ディレクトリ**]、[**ターゲット名**]、および [**ターゲットの拡張子**] です)。 なお、表示しているプロパティがマクロを使用している場合は、ドロップダウン リストで **[編集]** を選択して、マクロの置き換えが行われた最終的な文字列を示すダイアログ ボックスを表示することができます。 **[マクロ]** ボタンを選択することで、利用可能なすべてのマクロと現在の値を表示することができます。

## <a name="step-4-updating-the-target-windows-version"></a><a name="updating_winver"></a>手順 4. ターゲットの Windows バージョンを更新する

次のエラーは、WINVER バージョンが MFC ではサポートされないことを示します。 WINVER for Windows XP は 0x0501 です。

```Output
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxv_w32.h(40): fatal error C1189: #error:  MFC does not support WINVER less than 0x0501.  Please change the definition of WINVER in your project properties or precompiled header.
```

Windows XP は Microsoft によってサポートされなくなったので、Visual Studio で対象にすることが許可されていても、アプリケーションでのサポートを段階的に停止し、新しいバージョンの Windows を採用するようユーザーに推奨してください。

エラーを解消するには、**[プロジェクトのプロパティ]** の設定を、現在対象にしている Windows の最小バージョンに更新します。 さまざまな Windows リリースの値を示した表については、[ここ](/windows/win32/WinProg/using-the-windows-headers)を参照してください。

*stdafx.h* ファイルには、これらのマクロ定義のいくつかが含まれていました。

```cpp
#define WINVER       0x0500  // these defines are set so that we get the
#define _WIN32_WINNT 0x0500  // maximum set of message/flag definitions,
#define _WIN32_IE    0x0400  // from both winuser.h and commctrl.h.
```

WINVER については、Windows 7 に設定します。 値自体 (0x0601) ではなく、Windows 7 のマクロ (_WIN32_WINNT_WIN7) を使用すると、後でコードを読みやすくなります。

```cpp
#define WINVER _WINNT_WIN32_WIN7 // Minimum targeted Windows version is Windows 7
```

## <a name="step-5-linker-errors"></a><a name="linker_errors"></a>手順 5. リンカー エラー

これらの変更によって、SpyHk (DLL) プロジェクトがビルドされますが、リンカー エラーが生成されます。

```Output
LINK : warning LNK4216: Exported entry point _DLLEntryPoint@12
```

DLL のエントリ ポイントをエクスポートしないでください。 エントリ ポイントは、DLL が最初にメモリに読み込まれたときにローダーによって読み込まれることのみが想定されているので、エクスポート テーブル (これは他の呼び出し元のためのもの) に含めないでください。 ここでは、ディレクティブがアタッチされていないことを確認する必要があり **`__declspec(dllexport)`** ます。 spyxxhk.c では、`DLLEntryPoint` の宣言と定義の 2 か所からそれを削除する必要があります。 このディレクティブを使用することは意味がありませんが、前のバージョンのリンカーとコンパイラは、問題のフラグを立てませんでした。 リンカーの新しいバージョンでは、警告を出します。

```cpp
// deleted __declspec(dllexport)
BOOL WINAPI DLLEntryPoint(HINSTANCE hinstDLL,DWORD fdwReason, LPVOID lpvReserved);
```

これで、C DLL プロジェクトの SpyHK.dll が、エラーなしでビルドしてリンクされるようになりました。

## <a name="step-6-more-outdated-header-files"></a><a name="outdated_header_files"></a>手順 6. その他の期限切れのヘッダー ファイル

この時点で、メインの実行可能プロジェクト Spyxx の作業を開始します。

他の 2 つのインクルード ファイル (ctl3d.h と penwin.h) が見つかりませんでした。 ヘッダーが含まれているものを識別するためにインターネットを検索すると便利な場合もありますが、情報がそれほど役に立たないことがあります。 ctl3d.h が Exchange Development Kit の一部であることがわかり、Windows 95 の特定のコントロールのスタイルをサポートしていたことがわかり、また、penwin.h が廃止された API の Window Pen Computing に関連していることがわかりました。 このケースでは、`#include` 行をコメント化し、未定義のシンボルを verstamp.h の場合と同じように処理します。 3D コントロールまたは Pen Computing に関連するものは、すべてプロジェクトから削除されました。

多数のコンパイル エラーがあるプロジェクトで、エラーを徐々に解決している場合に、`#include` ディレクティブを削除するときに古くなった API の使用箇所をすべて即座に見つけることは現実的ではありません。 私たちはすぐにはそれを検出しませんでした。後ほど、WM_DLGBORDER が未定義であるというエラーが発生しました。 実際には、それは ctl3d.h からの未定義の多数のシンボルの 1つです。 私たちは古くなった API に関連すると判断したので、コードでそれへの参照をすべて削除しました。

## <a name="step-7-updating-old-iostreams-code"></a><a name="updating_iostreams_code"></a>手順 7. 古い iostreams コードを更新する

次のエラーは、iostreams を使用する古い C++ コードで一般的なエラーです。

```Output
mstream.h(40): fatal error C1083: Cannot open include file: 'iostream.h': No such file or directory
```

問題は、古い iostreams ライブラリが削除され、置き換えられたことです。 古い iostreams を新しい標準で置き換える必要があります。

```cpp
#include <iostream.h>
#include <strstrea.h>
#include <iomanip.h>
```

これらは、更新されたインクルードです:

```cpp
#include <iostream>
#include <sstream>
#include <iomanip>
```

この変更により、もう使用されなくなった `ostrstream` に関する問題が発生します。 適切な置換は ostringstream です。 **`typedef`** `ostrstream` 少なくとも最初のコードがあまり変更されないように、のを追加しようとしています。

```cpp
typedef std::basic_ostringstream<TCHAR> ostrstream;
```

現在、プロジェクトは MBCS (マルチバイト文字セット) を使用してビルドされます。したがって、 **`char`** は適切な文字データ型です。 ただし、コードを UTF-16 Unicode に簡単に更新できるようにするために、これをに更新し `TCHAR` ます。これは、 **`char`** **`wchar_t`** プロジェクト設定の**文字セット**プロパティが MBCS または Unicode に設定されているかどうかによって、またはに解決されます。

コードの他の部分を、いくつか更新する必要があります。  基本クラスをに置き換えまし `ios` た `ios_base` 。 ostream は basic_ostream に置き換えられました \<T> 。 2 つの typedef を追加し、このセクションをコンパイルします。

```cpp
typedef std::basic_ostream<TCHAR> ostream;
typedef ios_base ios;
```

これらの typedef を使用することは、一時的な解決策にすぎません。 より永続的なソリューションのためには、名前が変更された、または古い API への各参照を更新することができます。

次のエラーがあります。

```Output
error C2039: 'freeze': is not a member of 'std::basic_stringbuf<char,std::char_traits<char>,std::allocator<char>>'
```

次の問題は、にメソッドがないことです `basic_stringbuf` `freeze` 。 `freeze` メソッドは、古い `ostream` でメモリ リークを防ぐために使用されます。 新しいを使用しているので、これは必要ありません `ostringstream` 。 `freeze` への呼び出しを削除できます。

```cpp
//rdbuf()->freeze(0);
```

次の 2 つのエラーは、隣接する行で発生しました。 の使用に関する最初の苦情は `ends` 、 `iostream` null 終端文字を文字列に追加する古いライブラリの IO マニピュレーターです。 これらのエラーの2つ目は、メソッドの出力を `str` 非定数ポインターに割り当てることができないことを示しています。

```cpp
// Null terminate the string in the buffer and
// get a pointer to it.
//
*this << ends;
LPSTR psz = str();
```

```Output
2>mstream.cpp(167): error C2065: 'ends': undeclared identifier2>mstream.cpp(168): error C2440: 'initializing': cannot convert from 'std::basic_string<char,std::char_traits<char>,std::allocator<char>>' to 'LPSTR'
```

新しいストリーム ライブラリを使用すると、文字列が常に null で終わり、行を削除できるため、`ends` は必要ありません。 2番目の問題では、は、 `str()` 文字列の文字配列へのポインターが返されないという問題です。これにより、型が返され `std::string` ます。 2 つ目の問題の解決策は、型を `LPCSTR` に変更し、`c_str()` メソッドを使用してポインターを要求することです。

```cpp
//*this << ends;
LPCTSTR psz = str().c_str();
```

このコードで、しばらく私たちを悩ませたエラーが発生しました。

```cpp
MOUT << _T(" chUser:'") << chUser
<< _T("' (") << (INT)(UCHAR)chUser << _T(')');
```

マクロ MOUT が、型 `mstream` のオブジェクトである `*g_pmout` に解決されます。 `mstream` クラスは標準出力文字列クラス `std::basic_ostream<TCHAR>` から派生します。 ただし、文字列リテラルの周囲に \_T があり、私たちはこれを Unicode への変換の準備で挿入しましたが、**演算子 <<** のオーバーロードの解決法が、次のエラー メッセージを表示して失敗します。

```Output
1>winmsgs.cpp(4612): error C2666: 'mstream::operator <<': 2 overloads have similar conversions
1>  c:\source\spyxx\spyxx\mstream.h(120): note: could be 'mstream &mstream::operator <<(ios &(__cdecl *)(ios &))'
1>  c:\source\spyxx\spyxx\mstream.h(118): note: or       'mstream &mstream::operator <<(ostream &(__cdecl *)(ostream &))'
1>  c:\source\spyxx\spyxx\mstream.h(116): note: or       'mstream &mstream::operator <<(ostrstream &(__cdecl *)(ostrstream &))'
1>  c:\source\spyxx\spyxx\mstream.h(114): note: or       'mstream &mstream::operator <<(mstream &(__cdecl *)(mstream &))'
1>  c:\source\spyxx\spyxx\mstream.h(109): note: or       'mstream &mstream::operator <<(LPTSTR)'
1>  c:\source\spyxx\spyxx\mstream.h(104): note: or       'mstream &mstream::operator <<(TCHAR)'
1>  c:\source\spyxx\spyxx\mstream.h(102): note: or       'mstream &mstream::operator <<(DWORD)'
1>  c:\source\spyxx\spyxx\mstream.h(101): note: or       'mstream &mstream::operator <<(WORD)'
1>  c:\source\spyxx\spyxx\mstream.h(100): note: or       'mstream &mstream::operator <<(BYTE)'
1>  c:\source\spyxx\spyxx\mstream.h(95): note: or       'mstream &mstream::operator <<(long)'
1>  c:\source\spyxx\spyxx\mstream.h(90): note: or       'mstream &mstream::operator <<(unsigned int)'
1>  c:\source\spyxx\spyxx\mstream.h(85): note: or       'mstream &mstream::operator <<(int)'
1>  c:\source\spyxx\spyxx\mstream.h(83): note: or       'mstream &mstream::operator <<(HWND)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1132): note: or       'CDumpContext &operator <<(CDumpContext &,COleSafeArray &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1044): note: or       'CArchive &operator <<(CArchive &,ATL::COleDateTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1042): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::COleDateTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1037): note: or       'CArchive &operator <<(CArchive &,ATL::COleDateTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1035): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::COleDateTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1030): note: or       'CArchive &operator <<(CArchive &,COleCurrency)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1028): note: or       'CDumpContext &operator <<(CDumpContext &,COleCurrency)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(955): note: or       'CArchive &operator <<(CArchive &,ATL::CComBSTR)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(951): note: or       'CArchive &operator <<(CArchive &,COleVariant)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(949): note: or       'CDumpContext &operator <<(CDumpContext &,COleVariant)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(248): note: or       'CArchive &operator <<(CArchive &,const RECT &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(247): note: or       'CArchive &operator <<(CArchive &,POINT)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(246): note: or       'CArchive &operator <<(CArchive &,SIZE)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(242): note: or       'CDumpContext &operator <<(CDumpContext &,const RECT &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(241): note: or       'CDumpContext &operator <<(CDumpContext &,POINT)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(240): note: or       'CDumpContext &operator <<(CDumpContext &,SIZE)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1639): note: or       'CArchive &operator <<(CArchive &,const CObject *)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1425): note: or       'CArchive &operator <<(CArchive &,ATL::CTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1423): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::CTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1418): note: or       'CArchive &operator <<(CArchive &,ATL::CTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1416): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::CTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(694): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const char *)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(741): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(866): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const _Elem *)'
1>          with
1>          [
1>              _Elem=wchar_t
1>          ]
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(983): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>,wchar_t[10]>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &&,const _Ty (&))'
1>          with
1>          [
1>              _Ty=wchar_t [10]
1>          ]
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(1021): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const std::error_code &)'
1>  winmsgs.cpp(4612): note: while trying to match the argument list '(CMsgStream, const wchar_t [10])'
```

**演算子 <<** の定義が多すぎて、この種類のエラーに圧倒されることがあります。 使用可能なオーバーロードをもう少し詳しく見てみると、それらのほとんどが無関係であることがわかり、`mstream` クラス定義をさらに詳しく確認すると、このケースでは次の関数と思われるものが呼び出されるべきであることを特定しました。

```cpp
mstream& operator<<(LPTSTR psz)
{
  return (mstream&)ostrstream::operator<<(psz);
}
```

これが呼び出されていないのは、この長いエラー メッセージの最後の行からわかるように、文字列リテラルが型 `const wchar_t[10]` を持つので、非 const ポインターへの変換が自動的でないことが原因です。 ただし、その演算子は入力パラメーターを変更すべきではないため、より適切なパラメーター型は、`LPTSTR` (MBCS としてコンパイルしたときは `char*`、Unicode のときは `wchar_t*`) ではなく `LPCTSTR` (MBCS としてコンパイルしたときは `const char*`、Unicode のときは `const wchar_t*`) です。 このように変更すると、このエラーが解決されます。

この種類の変換は、古く、厳密でないコンパイラでは許容されていましたが、より最近の準拠性の変更により、より正確なコードが求められています。

## <a name="step-8-the-compilers-more-strict-conversions"></a><a name="stricter_conversions"></a>手順 8. コンパイラのより厳密な変換

次のようなエラーも多数表示されます。

```Output
error C2440: 'static_cast': cannot convert from 'UINT (__thiscall CHotLinkCtrl::* )(CPoint)' to 'LRESULT (__thiscall CWnd::* )(CPoint)'
```

単にマクロであるメッセージ マップで、エラーが発生しています。

```cpp
BEGIN_MESSAGE_MAP(CFindToolIcon, CWnd)
// other messages omitted...
ON_WM_NCHITTEST() // Error occurs on this line.
END_MESSAGE_MAP()
```

このマクロの定義に移動すると、関数 `OnNcHitTest` を参照していることがわかります。

```cpp
#define ON_WM_NCHITTEST() \
{ WM_NCHITTEST, 0, 0, 0, AfxSig_l_p, \
(AFX_PMSG)(AFX_PMSGW) \
(static_cast< LRESULT (AFX_MSG_CALL CWnd::*)(CPoint) > (&ThisClass :: OnNcHitTest)) },
```

問題は、メンバー関数の型へのポインターの不一致に関係しています。 この問題は、クラス型からへの変換が、 `CHotLinkCtrl` 有効な派生から基本への変換であるため、クラス型としてからに変換されることではありません `CWnd` 。 この問題は、戻り値の型である UINT と LRESULT です。 LRESULT は、対象となるバイナリ型に応じて、64 ビットのポインターまたは 32 ビットのポインターである LONG_PTR UINT に解決されるため、UINT はこの型に変換されません。 これは、2005 年以前に作成されたコードをアップグレードするときには一般的ではありません。なぜなら、多くのメッセージの戻り値の型が、64 ビットの互換性の変更の一部として、Visual Studio 2005 で UINT から LRESULT に変更されているためです。 次のコードの戻り値の型を UINT から LRESULT に変更します。

```cpp
afx_msg UINT OnNcHitTest(CPoint point);
```

変更後のコードは次のようになります。

```cpp
afx_msg LRESULT OnNcHitTest(CPoint point);
```

この関数は、CWnd から派生したさまざまなクラスに約10回出現するため、カーソルがエディターの関数上にあるときは、[**定義へ移動**] (キーボード: **f12**) と [**宣言へ移動**] (キーボード: **Ctrl**F12) を使用すると便利です。これを + **F12**見つけるには、[**シンボルの検索**] ツールウィンドウから移動します。 **[定義へ移動]** は通常、この 2 つの中ではより便利です。 **[宣言へ移動]** は、フレンド クラスの宣言や前方参照など、定義しているクラス宣言以外の宣言を検索します。

## <a name="step-9-mfc-changes"></a><a name="mfc_changes"></a>手順 9. MFC の変更

次のエラーも変更された宣言型に関連し、マクロでも発生します。

```Output
error C2440: 'static_cast': cannot convert from 'void (__thiscall CFindWindowDlg::* )(BOOL,HTASK)' to 'void (__thiscall CWnd::* )(BOOL,DWORD)'
```

問題なのは、`CWnd::OnActivateApp` の 2 番目のパラメーターを HTASK から DWORD に変更することです。 Visual Studio の 2002 年のリリースである、Visual Studio .NET でこの変更が発生しました。

```cpp
afx_msg void OnActivateApp(BOOL bActive, HTASK hTask);
```

それに応じて、派生クラスの OnActivateApp の宣言を、次のように更新する必要があります。

```cpp
afx_msg void OnActivateApp(BOOL bActive, DWORD dwThreadId);
```

この時点で、プロジェクトをコンパイルできます。 ただし、全体で使用するといくつかの警告が表示され、MBCS から Unicode への変換や、安全な CRT 関数を使用したセキュリティの向上など、アップグレードのオプションの部分があります。

## <a name="step-10-addressing-compiler-warnings"></a><a name="compiler_warnings"></a>手順 10. コンパイラの警告に対応する

警告の完全な一覧を取得するには、通常のビルドではなく、ソリューションで **[すべてリビルド]** を実行して、以前コンパイルしたものが、すべて再コンパイルされることを確認する必要があります。これは、現在のコンパイルからの警告レポートのみを取得するためです。 もう 1 つ、現在の警告レベルを受け入れるか、より高い警告レベルを使用するかとい問いがあります。  大量のコード、特に古いコードを移植するときは、より高い警告レベルを使用することが適切である可能性があります。  既定の警告レベルで開始し、すべての警告を取得するために、警告レベルを上げることもできます。 `/Wall` を使用する場合は、システムのヘッダー ファイルでいくつかの警告を取得するため、多数のユーザーが、`/W4` を使用して、システムのヘッダーの警告は取得せずに、コードの大多数の警告を取得しています。 警告をエラーとして表示する場合は、`/WX` オプションを追加します。 これらの設定は、[**プロジェクトのプロパティ**] ダイアログボックスの [ **C/c + +** ] セクションにあります。

`CSpyApp` クラスのメソッドのいずれかが、サポートされなくなった関数に関する警告を生成します。

```cpp
void SetDialogBkColor() {CWinApp::SetDialogBkColor(::GetSysColor(COLOR_BTNFACE));}
```

警告は次のとおりです。

```Output
warning C4996: 'CWinApp::SetDialogBkColor': CWinApp::SetDialogBkColor is no longer supported. Instead, handle WM_CTLCOLORDLG in your dialog
```

メッセージ WM_CTLCOLORDLG は既に Spy++ コードで処理されているので、必要な唯一の変更は、必要なくなった `SetDialogBkColor` への参照を削除することです。

次の警告は、変数名をコメント化することで、すぐに解決できます。 次のような警告を受け取りました。

```Output
warning C4456: declaration of 'lpszBuffer' hides previous local declaration
```

これを生成するコードには、マクロが含まれています。

```cpp
DECODEPARM(CB_GETLBTEXT)
{
  P2WPOUT();

  P2LPOUTPTRSTR;
  P2IFDATA()
  {
    PARM(lpszBuffer, PPACK_STRINGORD, ED2);

    INDENT();

    P2IFISORD(lpszBuffer)
    {
      P2OUTORD(lpszBuffer);
    }
    else
    {
      PARM(lpszBuffer, LPTSTR, ED2);
      P2OUTS(lpszBuffer);
    }
  }
}
```

このコードでは、マクロを多用しているため、保守が難しくなっています。 このケースでは、マクロには変数の宣言が含まれています。 マクロ PARM は次のように定義されています。

```cpp
#define PARM(var, type, src)type var = (type)src
```

このため、`lpszBuffer` 変数が同じ関数内で 2 回宣言されています。 この問題を修正するのは、(2 番目の型宣言を削除するだけの) マクロを使用していないコードと比較すると、簡単ではありません。 このように、マクロのコードを通常のコードとして書き直すか (大変でエラーが発生しやすい作業です) 、警告を無効にするという選択肢しか、残念ながらありません。

このケースでは、警告を無効にすることを選択します。 次のように、プラグマを追加することで実行できます。

```cpp
#pragma warning(disable : 4456)
```

警告を無効化する際に、警告を生成するコードのみに無効化の影響を制限して、有益な情報を表示している可能性がある警告を無効にしないようにすることができます。 警告を復元するコードを、生成する行の直後に追加するか、もっとよい方法として、この警告はマクロで発生しているので、マクロで機能する **__pragma** キーワードを使用します (`#pragma` はマクロでは機能しません)。

```cpp
#define PARM(var, type, src)__pragma(warning(disable : 4456))  \
type var = (type)src \
__pragma(warning(default : 4456))
```

次の警告には、いくらかのコードの変更が必要です。 Win32 API `GetVersion` (および `GetVersionEx`) は非推奨です。

```Output
warning C4996: 'GetVersion': was declared deprecated
```

バージョンを取得する方法を次のコードに示します。

```cpp
// check Windows version and set m_bIsWindows9x/m_bIsWindows4x/m_bIsWindows5x flags accordingly.
DWORD dwWindowsVersion = GetVersion();
```

この後に、dwWindowsVersion の値を検証して、Windows 95 で動作するかどうか、どのバージョンの Windows NT なのかを判断する大量のコードが続きます。 これはすべて古いものであるため、コードを削除してそれらの変数への参照を処理します。

記事「[Windows 8.1 と Windows Server 2012 R2 のオペレーティング システムのバージョンの変更](/windows/win32/w8cookbook/operating-system-version-changes-in-windows-8-1)」で、この状況について説明しています。

`CSpyApp` クラスには、オペレーティング システムのバージョンのクエリを実行する `IsWindows9x`、`IsWindows4x`、および `IsWindows5x` のメソッドがあります。 適切な開始点は、この古いアプリケーションで使用されるテクノロジを考慮すると、サポートしようとする Windows のバージョン (Windows 7 以降) は、すべて Windows NT 5 に近いと想定することです。 これらのメソッドは、古いオペレーティング システムの制限に対処する場合に使用します。 このため、これらのメソッドを、`IsWindows5x` では TRUE を返し、他は FALSE を返すよう変更しました。

```cpp
BOOL IsWindows9x() {/*return(m_bIsWindows9x);*/ return FALSE;  }
BOOL IsWindows4x() {/*return(m_bIsWindows4x);*/ return FALSE;  }
BOOL IsWindows5x() {/*return(m_bIsWindows5x);*/ return TRUE;  }
```

これにより、内部変数が直接使用される部分は数か所だけになりました。 これらの変数を削除したので、明示的に対処する必要があるエラーが数個になります。

```Output
error C2065: 'm_bIsWindows9x': undeclared identifier
```

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(m_bIsWindows9x || hToolhelp32 != NULL);
}
```

これをメソッド呼び出しで置き換えることも、単純に TRUE を渡し、Windows 9x の古い特別なケースを削除することもできます。

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(TRUE /*!m_bIsWindows9x || hToolhelp32 != NULL*/);
}
```

既定のレベル (3) の最後の警告は、ビットフィールドに関係しています。

```Output
treectl.cpp(1656): warning C4463: overflow; assigning 1 to bit-field that can only hold values from -1 to 0
```

これをトリガーするコードは、次のとおりです。

```cpp
m_bStdMouse = TRUE;
```

`m_bStdMouse` の宣言は、ビットフィールドであることを示します。

```cpp
class CTreeListBox : public CListBox
{
  DECLARE_DYNCREATE(CTreeListBox)

  CTreeListBox();

  private:
  int ItemFromPoint(const CPoint& point);

  class CTreeCtl* m_pTree;
  BOOL m_bGotMouseDown : 1;
  BOOL m_bDeferedDeselection : 1;
  BOOL m_bStdMouse : 1;
```

このコードは、組み込みの bool 型が Visual C++ でサポートされる前に作成されました。 このようなコードでは、BOOL は **`typedef`** for **`int`** です。 型は型であり、 **`int`** **`signed`** のビット表現 **`signed int`** は、最初のビットを符号ビットとして使用するため、int 型のビットフィールドは、0または-1 を表すものとして解釈される可能性があります。これは意図したものではない可能性があります。

これらがなぜビットフィールドなのかは、コードを見てもわかりません。 オブジェクトのサイズを小さくすることを目的としているのでしょうか。または、オブジェクトのバイナリ形式が使用されている場所があるのでしょうか。 ビットフィールドを使用する理由が見当たらないため、これらを BOOL の通常のメンバーに変更しました。 ビットフィールドを使用して、オブジェクトのサイズを小さく維持することは、動作が保証されていません。 これは、コンパイラが型をレイアウトする方法に依存しています。

標準的な型を使用することは、役に立つかもしれ **`bool`** ません。 BOOL 型などの古いコードパターンの多くは、後で標準 C++ で解決された問題を解決するために考案されています。したがって、BOOL から組み込み型への変更 **`bool`** は、新しいバージョンでコードを最初に実行した後に検討する変更の一例にすぎません。

既定のレベル (レベル 3) で表示されるすべての警告に対処したら、追加の警告をいくつかキャッチするように、レベル 4 に変更しました。 最初に表示されたのは、次のとおりです。

```Output
warning C4100: 'nTab': unreferenced formal parameter
```

この警告を生成するコードは、次のとおりです。

```cpp
virtual void OnSelectTab(int nTab) {};
```

これは害がないように思えますが、`/W4` および `/WX` を設定したクリーン コンパイルを必要としているため、変数名をコメント化して、読みやすさのためにそのまま残しました。

```cpp
virtual void OnSelectTab(int /*nTab*/) {};
```

他に受け取った警告は、一般的なコードのクリーンアップに便利です。 またはから WORD への暗黙的な **`int`** 変換 **`unsigned int`** (の typedef) がいくつかあり **`unsigned short`** ます。 これらには、データ損失の可能性があります。 これらのケースでは、キャストを WORD に追加しました。

このコードで受け取った別のレベル 4 の警告は、次のとおりです。

```Output
warning C4211: nonstandard extension used: redefined extern to static
```

この問題は、変数が最初に宣言されて **`extern`** から、後で宣言されたときに発生し **`static`** ます。 これら 2 つのストレージ クラス指定子の意味は相互に排他的ですが、これは、Microsoft 拡張機能として許容されます。 コードを他のコンパイラに移植可能にしたい場合、または `/Za` (ANSI 互換性) を指定してコンパイルしたい場合は、宣言が一致するストレージ クラス指定子を持つように変更します。

## <a name="step-11-porting-from-mbcs-to-unicode"></a><a name="porting_to_unicode"></a>手順 11. MBCS から Unicode に移植する

Windows では、Unicode という場合は、通常 UTF-16 を意味することに注意してください。 Linux などの他のオペレーティング システムは UTF-8 を使用しますが、Windows では通常は使用しません。 MFC の MBCS バージョンは、Visual Studio 2013 および 2015 では非推奨でしたが、Visual Studio 2017 においては非推奨ではなくなりました。 Visual Studio 2013 または 2015 を使っている場合、MBCS コードを UTF-16 Unicode に実際に移植する手順を実行する前に、他の作業を実行するためや、都合のよいときに移植を延期するために、MBCS が非推奨であることを示す警告を一時的に削除します。 現在のコードは MBCS を使用しており、続行するには、MFC の ANSI/MBCS バージョンをインストールする必要があります。 比較的大きい MFC ライブラリは Visual Studio の既定の **C++ によるデスクトップ開発**インストールの一部ではないので、インストーラーのオプション コンポーネントから選ぶ必要があります。 「[MFC MBCS DLL アドオン](../mfc/mfc-mbcs-dll-add-on.md)」を参照してください。 これをダウンロードして Visual Studio を再起動すると、MFC の MBCS バージョンとコンパイルしてリンクすることができますが、Visual Studio 2013 または NO_WARN_MBCS_MFC_DEPRECATION 2015 を使用している場合は、MBCS に関する警告を回避するために、プロジェクトプロパティの**プリプロセッサ**セクション、または*stdafx.h*ヘッダーファイルまたはその他の共通ヘッダーファイルの先頭に、定義済みマクロの一覧

ここで、いくつかのリンカー エラーが表示されます。

```Output
fatal error LNK1181: cannot open input file 'mfc42d.lib'
```

LNK1181 は、スタティック ライブラリの古いバージョンの mfc がリンカーの入力に含まれているために発生します。 MFC を動的にリンクできるため、これは必要ありません。そのため、プロジェクトのプロパティの [**リンカー** ] セクションの [**入力**] プロパティからすべての mfc スタティックライブラリを削除する必要があります。 このプロジェクトは、`/NODEFAULTLIB` オプションも使用していて、ライブラリのすべての依存関係を代わりに一覧表示します。

```
msvcrtd.lib;msvcirtd.lib;kernel32.lib;user32.lib;gdi32.lib;advapi32.lib;Debug\SpyHk55.lib;%(AdditionalDependencies)
```

これで、実際に古いマルチバイト文字セット (MBCS) のコードを Unicode に更新できます。 これは Windows デスクトップ プラットフォームに密接に関連付けられている Windows アプリケーションであるため、Windows で使用される UTF-16 Unicode に移植します。 クロスプラット フォームのコードを作成しているか、別のプラットフォームに Windows アプリケーションを移植している場合は、他のオペレーティング システムで広く使用されている UTF-8 への移植を検討することができます。

UTF-16 Unicode への移植では、引き続き MBCS にコンパイルするオプションも必要かどうかを決定しなければなりません。  MBCS をサポートするオプションを使用する場合は、TCHAR マクロを文字型として使用する必要があります。これは、 **`char`** **`wchar_t`** \_ \_ コンパイル時に mbcs または UNICODE が定義されているかどうかによって、またはのいずれかに解決されます。 とそれに関連付けられている Api ではなく、TCHAR および TCHAR バージョンに切り替えると、UNICODE では **`wchar_t`** なく mbcs マクロを定義するだけで、mbcs バージョンのコードに戻ることができ \_ \_ ます。 TCHAR に加えて、幅広く使用される typedef、マクロ、関数など、様々なバージョンの TCHAR が存在します。 たとえば、LPCSTR の代わりに LPCTSTR を使用するなどです。 [プロジェクトのプロパティ] ダイアログの **[構成プロパティ]** の **[全般]** セクションで、**[文字セット]** プロパティを **[MBCS 文字セットを使用する]** から **[Unicode 文字セットを使用する]** に変更します。 この設定は、コンパイル時にどのマクロが事前に定義されるかに影響します。 UNICODE マクロと \_UNICODE マクロの両方が存在します。 プロジェクト プロパティは一貫して両方に影響します。 MFC などの Visual C++ ヘッダーが \_UNICODE を使用する場所で Windows ヘッダーは UNICODE を使用しますが、一方が定義されると、他方も常に定義されます。

TCHAR を使用して MBCS から UTF-16 Unicode に移植するための適切なガイドについては、[こちら](/previous-versions/cc194801(v=msdn.10))をご利用ください。 私たちはこのルートを選択します。 最初に、**[文字セット]** プロパティを **[Unicode 文字セットを使用する]** に変更してプロジェクトをリビルドします。

コードの一部は既に TCHAR を使用していて、最終的に Unicode をサポートしようとしていたことが明らかです。 コードの一部はそうではありませんでした。 CHAR のインスタンスを検索しました。これはので、 **`typedef`** **`char`** ほとんどは TCHAR に置き換えられています。 また、`sizeof(CHAR)` も検索しました。 CHAR から TCHAR に変更するたびに、通常 `sizeof(TCHAR)` に変更しなければなりませんでした。というのも、これはよく文字列の文字数を判断するのに使用されていたからです。 ここで間違った型を使用しても、コンパイラ エラーが生成されないため、このケースでは少し慎重になります。

この種類のエラーは、Unicode への切り替え直後に非常に一般的に発生します。

```Output
error C2664: 'int wsprintfW(LPWSTR,LPCWSTR,...)': cannot convert argument 1 from 'CHAR [16]' to 'LPWSTR'
```

これを生成するコードの例を次に示します。

```cpp
wsprintf(szTmp, "%d.%2.2d.%4.4d", rmj, rmm, rup);
```

\_T を文字列リテラルの周囲に置き、エラーを取り除きます。

```cpp
wsprintf(szTmp, _T("%d.%2.2d.%4.4d"), rmj, rmm, rup);
```

\_T マクロは、 **`char`** **`wchar_t`** MBCS または UNICODE の設定に応じて、文字列リテラルのコンパイルを文字列または文字列として行う効果を持ちます。 Visual Studio ですべての文字列を \_T に置き換えるには、最初に **[クイック置換]** (キーボード: **Ctrl**+**F**) ボックスまたは **[フォルダーを指定して置換]** (キーボード: **Ctrl**+**Shift**+**H**) を開いてから、**[正規表現の使用]** チェック ボックスを選択します。 `((\".*?\")|('.+?'))` を検索文字列として入力し、`_T($1)` を置換テキストとして入力します。 \_T マクロが既に一部の文字列の周囲にある場合は、この手順でもう一度追加され、`#include` を使用しているときなど、\_T が必要ないケースもあるため、**[すべて置換]** ではなく、**[次を置換]** を使用してください。

この特定の関数 [wsprintf](/windows/win32/api/winuser/nf-winuser-wsprintfw) は、実際に Windows のヘッダーで定義されていて、これに関するドキュメントでは、バッファー オーバーランの可能性があるため、使用しないことが推奨されています。 `szTmp` バッファーに対してサイズが指定されていないため、書き込まれるすべてのデータをバッファーが保持できるか関数でチェックする方法はありません。 Secure CRT への移植については、次のセクションを参照してください。次のセクションでは他の同様の問題も修正します。 最後に [_stprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) に置換して終了します。

Unicode への変換でよく見られるもう1つの一般的なエラーは次のようになります。

```Output
error C2440: '=': cannot convert from 'char *' to 'TCHAR *'
```

これを生成するコードは、次のとおりです。

```cpp
pParentNode->m_szText = new char[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

文字列をコピーする TCHAR strcpy 関数である関数が使用されていた場合でも、 `_tcscpy` 割り当てられたバッファーはバッファーでした **`char`** 。 これを TCHAR に変更するのは簡単です。

```cpp
pParentNode->m_szText = new TCHAR[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

同様に、コンパイル エラーによって保証されたので、LPSTR (STRing への Long ポインター) と LPCSTR (定数 STRing への Long ポインター) を、それぞれ LPTSTR (TCHAR STRing への Long ポインター) と LPCTSTR (定数 TCHAR STRing への Long ポインター) に変更しました。 それぞれの状況を個別に調査する必要があるので、グローバル検索と置換を使用してこのような置換を行わないことを選択しました。 場合によっては、 **`char`** サフィックスを持つ windows 構造体を使用する特定の windows メッセージを処理するとき**A**などに、バージョンが必要になります。 Windows API では、サフィックス**A**は ASCII または ANSI (および MBCS にも適用されます) を意味し、サフィックス**W**はワイド文字または utf-16 Unicode を意味します。 この名前付けパターンは、Windows のヘッダーで使用されますが、MBCS バージョンだけで既に定義されている関数の Unicode バージョンを追加する必要があるときに、Spy++ コードでも従います。

場合によっては、適切に解決されるバージョンを使用するよう型を置換しなければならないことがあります (WNDCLASSA の代わりに WNDCLASS を使用する場合など)。

多くの場合に、(`GetClassNameA` の代わりに) `GetClassName` など、Win32 API のジェネリック バージョン (マクロ) を使用しなければなりません。 メッセージハンドラーの switch ステートメントでは、一部のメッセージは MBCS または Unicode に固有です。その**ような場合**は、一般的な名前付き関数をと**w**の特定の関数に置き換え、Unicode が定義されているかどうかに基づいて **、正しい A**または**w**の名前に解決される汎用名のマクロを追加しました。  コードの多くの部分で、UNICODE の定義に切り替えたときに、 \_ バージョンが必要な場合でも**A** 、W バージョンが選択されるようになりました。

特別な操作を実行する必要がある箇所がいくつかあります。 `WideCharToMultiByte` または `MultiByteToWideChar` の使用箇所は、すべて詳しく確認しなければならない可能性があります。 `WideCharToMultiByte` を使用した例を次に示します。

```cpp
BOOL C3dDialogTemplate::GetFont(CString& strFace, WORD& nFontSize)
{
  ASSERT(m_hTemplate != NULL);

  DLGTEMPLATE* pTemplate = (DLGTEMPLATE*)GlobalLock(m_hTemplate);
  if ((pTemplate->style & DS_SETFONT) == 0)
  {
    GlobalUnlock(m_hTemplate);
    return FALSE;
  }

  BYTE* pb = GetFontSizeField(pTemplate);
  nFontSize = *(WORD*)pb;
  pb += sizeof (WORD);
  WideCharToMultiByte(CP_ACP, 0, (LPCWSTR)pb, -1,
  strFace.GetBufferSetLength(LF_FACESIZE), LF_FACESIZE, NULL, NULL);
  strFace.ReleaseBuffer();
  GlobalUnlock(m_hTemplate);
  return TRUE;
}
```

これに対応するには、この処理が行われた理由が、フォントの名前を示すワイド文字列を `CString`、`strFace` の内部バッファーにコピーするためであることを理解する必要がありました。 マルチバイトの `CString` 文字列に対しては、ワイド文字の `CString` 文字列とは少し異なるコードが必要になるため、このケースでは `#ifdef` を追加しました。

```cpp
#ifdef _MBCS
WideCharToMultiByte(CP_ACP, 0, (LPCWSTR)pb, -1,
strFace.GetBufferSetLength(LF_FACESIZE), LF_FACESIZE, NULL, NULL);
strFace.ReleaseBuffer();
#else
wcscpy(strFace.GetBufferSetLength(LF_FACESIZE), (LPCWSTR)pb);
strFace.ReleaseBuffer();
#endif
```

もちろん実際には、`wcscpy` の代わりに、より安全なバージョンである `wcscpy_s` を使用する必要があります。 次のセクションでは、この問題に対処します。

作業を確認するために、**マルチバイト文字セットを使用**するように**文字セット**をリセットし、コードが引き続き MBCS と Unicode を使用してコンパイルされていることを確認する必要があります。 言うまでもなく、これらをすべて変更した後で、再コンパイルされたアプリケーションで、テストを実施して完全に成功する必要があります。

この spy++ ソリューションでの作業では、平均的な C++ 開発者がコードを Unicode に変換するのに作業日数がおよそ 2 日かかりました。 これには再テストの時間は含まれていません。

## <a name="step-12-porting-to-use-the-secure-crt"></a><a name="porting_to_secure_crt"></a>手順 12. Secure CRT を使用するよう移植する

次は CRT 関数のセキュリティで保護されたバージョン (**_s** サフィックス付きのバージョン) を使用したコードの移植です。 このケースでの一般的な戦略は、関数を **_s** バージョンに置き換えてから、通常は、必要な追加のバッファーのサイズ パラメーターを追加することです。 多くの場合、サイズがわかっているため、これは簡単です。 サイズがすぐに利用できない可能性がある場合は、CRT 関数を使用する関数にパラメーターを追加するか、またはターゲットバッファーの使用状況を調べて、適切なサイズ制限を確認する必要があります。

Visual C++ は、サイズ パラメーターを多数追加しなくても、テンプレートのオーバーロードを使用する、安全にコードを取得できるようにするトリックを提供しています。 これらのオーバーロードはテンプレートなので、C ではなく C++ としてコンパイルするときにのみ利用できます。Spyxxhk は C プロジェクトであり、このトリックは利用できません。  ただし、Spyxx は違うので、このトリックを利用できます。 このトリックでは、stdafx.h のように、プロジェクトのすべてのファイルでコンパイルされる場所に、次のような行を追加します。

```cpp
#define _CRT_SECURE_TEMPLATE_OVERLOADS 1
```

これを定義するとき、バッファーが生のポインターではなく配列である場合は、サイズが配列の型から推論されて、サイズのパラメーターとして使用され、ユーザーが指定する必要はありません。 これは、コードの書き直しの複雑さを削減するのに役立ちます。 関数名を **_s** のバージョンで置換する必要がありますが、多くの場合、これは検索と置換の操作によって実行できます。

いくつかの関数の戻り値が変更されています。 たとえば、`_itoa_s` (および `_itow_s` とマクロ `_itot_s`) は、文字列ではなくエラー コード (`errno_t`) を返します。 したがって、そのような場合は、`_itoa_s` への呼び出しを別の行に移動して、バッファーの識別子で置き換える必要があります。

いくつかの一般的なケース: `memcpy` では、多くの場合、`memcpy_s` に切り替えるときに、コピー先の構造のサイズを追加します。 同様に、ほとんどの文字列とバッファーでは、配列またはバッファーのサイズが、バッファーの宣言、またはバッファーが最初に割り当てられた場所を検索することで、簡単に判断できます。 状況によっては、実際に使用可能なバッファーの大きさを判断する必要があります。また、変更しようとしている関数のスコープでその情報が利用できない場合は、追加のパラメーターとして追加し、呼び出し元のコードを変更して情報を提供する必要があります。

これらのテクニックを使用して、Secure CRT 関数を使用するようコードを変換するのに、約半日かかりました。 テンプレートのオーバー ロードではなく、サイズのパラメーターを手動で追加するよう選択した場合は、おそらく時間が 2 ～ 3 倍多くかかります。

## <a name="step-13-zcforscope--is-deprecated"></a><a name="deprecated_forscope"></a>手順 13. /Zc:forScope- が非推奨とされます

Visual C++ 6.0 以降、コンパイラは現在の標準に準拠し、ループで宣言される変数のスコープがループのスコープに制限されています。 コンパイラ オプション [/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) (**プロジェクトのプロパティのループのスコープの強制準拠**) は、これがエラーとして報告されるかどうかを制御します。 準拠するようコードを更新して、ループのすぐ外側に宣言を追加する必要があります。 コードを変更しなくて済むように、C++ プロジェクトのプロパティの **[言語]** セクションで、設定を `No (/Zc:forScope-)` に変更できます。 ただし、`/Zc:forScope-` はこれ以降の Visual C++ のリリースで削除される可能性があるため、最終的には標準に準拠するようにコードを変更する必要があります。

これらの問題は、比較的簡単に解決できますが、コードによっては、大量のコードに影響する可能性があります。 一般的な問題を次に示します。

```cpp
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const
{
  for (int n = 0; mszStrings[0] != 0; n++)
  mszStrings = _tcschr(mszStrings, 0) + 1;
  return(n);
}
```

上記のコードは次のエラーを生成します。

```Output
'n': undeclared identifier
```

これは、コンパイラが、C++ 標準にもはや準拠しないコードを許可するコンパイラ オプションを非推奨にしたために発生します。 標準では、ループ内で変数を宣言すると、そのスコープがループのみに制限されるため、ループの外側でループ カウンターを使用する一般的な処理では、次の修正後の例のように、カウンターの宣言もループの外側に移動する必要があります。

```cpp
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const
{
  int n;
  for (n = 0; mszStrings[0] != 0; n++)
  mszStrings = _tcschr(mszStrings, 0) + 1;
  return(n);
}
```

## <a name="summary"></a>まとめ

元の Visual C++ 6.0 のコードから最新のコンパイラに Spy++ を移植するのに、コーディングが約 20 時間かかり、およそ 1 週間必要でした。 私たちは、Visual Studio 6.0 から Visual Studio 2015 まで、8 つの製品リリースを通じて直接アップグレードしました。 これは、現時点で、プロジェクトの大小にかかわらずすべてのアップグレードで推奨される方法です。

## <a name="see-also"></a>関連項目

[移植およびアップグレード: 例とケース スタディ](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[前のケース スタディ: COM Spy](../porting/porting-guide-com-spy.md)
