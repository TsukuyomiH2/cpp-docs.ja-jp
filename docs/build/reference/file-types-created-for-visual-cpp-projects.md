---
description: '詳細情報: Visual Studio C++ プロジェクト用に作成されたファイルの種類'
title: Visual Studio の C++ プロジェクトに対して作成されるファイルの種類
ms.date: 04/08/2019
helpviewer_keywords:
- header files [C++], Visual Studio projects
- ActiveX controls [C++], Help files
- def files
- project items [C++], files
- Visual Studio C++ projects, files and directories
- resource files, created by wizard
- files [C++], extensions
- Help files, for ActiveX controls
- Web projects [C++], adding items
- .def files
- licensing ActiveX controls
ms.assetid: 2b0ee2e0-ae81-4185-9bb9-11da3c99a283
ms.openlocfilehash: bd1dad365ea2635549322c886f00f4e08ff47942
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200586"
---
# <a name="file-types-created-for-visual-studio-c-projects"></a>Visual Studio C++ プロジェクト用に作成されたファイルの種類

従来のデスクトップアプリケーションでは、多くの種類のファイルが Visual Studio プロジェクトに関連付けられています。 実際にプロジェクトにインクルードされるファイルは、プロジェクトの種類、およびウィザードで選択したオプションによって異なります。

- [プロジェクトファイルとソリューションファイル](project-and-solution-files.md)

- [CLR プロジェクト](files-created-for-clr-projects.md)

- [ATL プログラムまたはコントロールのソースファイルとヘッダーファイル](atl-program-or-control-source-and-header-files.md)

- [MFC プログラムまたはコントロールのソースファイルとヘッダーファイル](mfc-program-or-control-source-and-header-files.md)

- [プリコンパイル済みヘッダーファイル](../creating-precompiled-header-files.md)

- [リソースファイル](resource-files-cpp.md)

- [ヘルプ ファイル (WinHelp)](help-files-winhelp.md)

- [ヒント ファイル](hint-files.md)

Visual Studio プロジェクトを作成する場合は、新しいソリューションに作成するか、既存のソリューションにプロジェクトを追加することができます。 通常、複雑なアプリケーションの開発では、1 つのソリューションに複数のプロジェクトを作成します。

プロジェクトでは、通常、EXE ファイルまたは DLL ファイルが生成されます。 プロジェクトは相互に依存することができます。ビルド処理中、Visual Studio 環境はプロジェクト内とプロジェクト間の両方の依存関係をチェックします。 通常、各プロジェクトにはコアソースコードがあります。 プロジェクトの種類によっては、プロジェクトのさまざまな側面を含む他の多くのファイルが存在する場合があります。 これらのファイルの内容はファイル拡張子によって示されます。 Visual Studio 開発環境では、ファイル拡張子を使用して、ビルド時のファイル内容の処理方法を判断します。

次の表は、Visual Studio プロジェクトの共通ファイルを示しています。ファイル拡張子で識別されます。

|[ファイル拡張子]|Type|内容|
|--------------------|----------|--------------|
|.asmx|source|配置ファイル。|
|.asp|source|ASP (Active Server Page) ファイル。|
|.atp|Project|アプリケーション テンプレート プロジェクト ファイル。|
|.bmp、.dib、.gif、.jpg、.jpe、.png|リソース|一般的なイメージ ファイル。|
|.bsc|コンパイル|ブラウザー コード ファイル。|
|.cpp、.c|source|アプリケーションの主要なソース コード ファイル。|
|.cur|リソース|カーソルのビットマップ グラフィック ファイル。|
|.dbp|Project|データベース プロジェクト ファイル。|
|.disco|source|動的探索ドキュメント ファイル。 XML Web サービス探索を処理します。|
|.exe、.dll|Project|実行可能ファイルまたはダイナミック リンク ライブラリ ファイル。|
|.h|source|ヘッダー ファイルまたはインクルード ファイル。|
|.htm、.html、.xsp、.asp、.htc、.hta、.xml|リソース|共通 Web ファイル。|
|.HxC|Project|ヘルプ プロジェクト ファイル。|
|.ico|リソース|アイコンのビットマップ グラフィック ファイル。|
|.idb|コンパイル|ソースファイルとクラス定義の間の依存関係情報を格納している状態ファイル。 これは、インクリメンタルコンパイル中にコンパイラによって使用されます。 .idb ファイルの名前は [/Fd](fd-program-database-file-name.md) コンパイラ オプションで指定します。|
|.idl|コンパイル|インターフェイス定義言語ファイル。 詳細については、Windows SDK の「[Interface Definition (IDL) File](/windows/win32/Rpc/the-interface-definition-language-idl-file)」(インターフェイス定義 (IDL) ファイル) を参照してください。|
|.ilk|リンク|インクリメンタル リンク ファイル。 詳細については、「 [/INCREMENTAL](incremental-link-incrementally.md)」を参照してください。|
|.map|リンク|リンカー情報を含むテキスト ファイル。 マップ ファイルの名前は、 [/Fm](fm-name-mapfile.md) コンパイラ オプションで指定します。 詳細については、「 [/map](map-generate-mapfile.md)」を参照してください。|
|.mfcribbon-ms|リソース|リボンの MFC ボタン、コントロール、および属性を定義する XML コードを含むリソースファイル。 詳細については、「 [Ribbon Designer](../../mfc/ribbon-designer-mfc.md)」を参照してください。|
|.obj、.o||オブジェクト ファイル。コンパイルはされますが、リンクはされません。|
|.pch|デバッグ|プリコンパイル済みヘッダー ファイル。|
|.rc、.rc2|リソース|リソースを生成するための[リソース スクリプト ファイル](../../windows/working-with-resource-files.md) 。|
|.sbr|コンパイル|ソース ブラウザー中間ファイル。 [BSCMAKE](bscmake-options.md)の入力ファイルです。|
|.sln|解答|[ソリューション](/visualstudio/ide/solutions-and-projects-in-visual-studio) ファイル。|
|.suo|解答|ソリューション オプション ファイル。|
|.txt|リソース|テキスト ファイル。通常は README ファイルです。|
|.vap|Project|Visual Studio Analyzer プロジェクト ファイル。|
|.vbg|解答|互換性のあるプロジェクト グループ ファイル。|
|.vbp、.vip、.vbproj|Project|Visual Basic プロジェクト ファイル。|
|.vcxitems|Project|複数の C++ プロジェクト間でコード ファイルを共有するための共有アイテム プロジェクト。 詳細については、「 [プロジェクトファイルとソリューションファイル](project-and-solution-files.md)」を参照してください。|
|.vcxproj|Project|Visual Studio プロジェクトファイル。 詳細については、「 [プロジェクトファイルとソリューションファイル](project-and-solution-files.md)」を参照してください。|
|.vcxproj.filters|Project|ソリューションエクスプローラーを使用してプロジェクトにファイルを追加するときに使用します。 フィルターファイルは、ファイル名拡張子に基づいて、ソリューションエクスプローラーツリービューでファイルを追加する場所を定義します。|
|.vdproj|Project|Visual Studio 配置プロジェクト ファイル。|
|.vmx|Project|マクロ プロジェクト ファイル。|
|.vup|Project|ユーティリティ プロジェクト ファイル。|

Visual Studio に関連するその他のファイルの詳細については、「 [Visual Studio .NET のファイルの種類と拡張子](/visualstudio/ide/reference/project-and-solution-file-types)」を参照してください。

プロジェクト ファイルは、ソリューション エクスプローラーで複数のフォルダーに分けて編成されています。 Visual Studio では、ソースファイル、ヘッダーファイル、およびリソースファイル用のフォルダーが作成されますが、これらのフォルダーを再編成したり、新しいフォルダーを作成したりすることができます。 フォルダーを使用すると、プロジェクト階層内で論理ファイル クラスターを明示的に編成できます。 たとえば、すべてのユーザーインターフェイスのソースファイルを格納するフォルダーを作成できます。 または、仕様、ドキュメント、またはテストスイートのフォルダー。 すべてのファイル フォルダーに一意の名前を指定する必要があります。

プロジェクトに項目を追加すると、そのプロジェクトのすべての構成に項目が追加されます。 ビルド可能かどうかにかかわらず、項目が追加されます。 たとえば、MyProject というプロジェクトに項目を追加すると、プロジェクトのデバッグ構成とリリース構成の両方にその項目が追加されます。

## <a name="see-also"></a>関連項目

[Visual Studio C++ プロジェクトの作成と管理](../creating-and-managing-visual-cpp-projects.md)<br>
[Visual Studio C++ プロジェクトの種類](visual-cpp-project-types.md)<br>
