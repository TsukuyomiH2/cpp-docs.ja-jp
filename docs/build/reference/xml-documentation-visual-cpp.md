---
description: '詳細情報: XML ドキュメント (Visual C++)'
title: XML に関するドキュメント (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
ms.openlocfilehash: 762380d08483292866cb96b34be4d85f7a2f510a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260944"
---
# <a name="xml-documentation-visual-c"></a>XML に関するドキュメント (Visual C++)

Visual C++ では、.xml ファイルに出力されるソース コードにコメントを追加することができます。 このファイルは、コード内のクラスに関するドキュメントを作成するプロセスに入力することができます。

Visual C++ コード ファイル内では、メソッドまたは型の定義の直前に XML ドキュメント コメントを配置する必要があります。 次のシナリオでは、コメントを使用して IntelliSense QuickInfo データ ヒントを設定することができます。

1. 付属の .winmd ファイルを使用してコードを Windows ランタイム コンポーネントとしてコンパイルする場合

1. 現在のプロジェクトにソース コードを取り込む場合

1. 型の宣言と実装が同じヘッダー ファイルに置かれているライブラリの場合

> [!NOTE]
> 現在のリリースでは、テンプレートに対しても、テンプレートの種類を含む要素 (たとえば、テンプレートとしてパラメーターを取る関数) に対してもコード コメントは処理されません。 このようなコメントを追加すると、未定義の動作が発生します。

ドキュメント コメントを含む .xml ファイルの作成の詳細については、次のトピックを参照してください。

|対象|解決方法については、|
|---------------------------|---------|
|使用するコンパイラ オプション|[/doc](doc-process-documentation-comments-c-cpp.md)|
|ドキュメントで一般的に使用される機能を提供するために使用できるタグ|[ドキュメント コメントとして推奨されるタグ](recommended-tags-for-documentation-comments-visual-cpp.md)|
|コード内のコンストラクトを識別するために、コンパイラによって生成される ID 文字列|[.Xml ファイルの処理](dot-xml-file-processing.md)|
|ドキュメント タグを区切る方法|[Visual C++ ドキュメント タグの区切り記号](delimiters-for-visual-cpp-documentation-tags.md)|
|1 つまたは複数の .xdc ファイルからの .xml ファイルの生成。|[XDCMake リファレンス](xdcmake-reference.md)|
|Visual Studio の機能領域に関連している XML に関する情報へのリンク|[Visual Studio での XML](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

ドキュメント コメントのテキストに XML 特殊文字を配置する必要がある場合は、XML エンティティまたは CDATA セクションを使用する必要があります。

## <a name="see-also"></a>関連項目

[ランタイム プラットフォームのコンポーネントの拡張機能](../../extensions/component-extensions-for-runtime-platforms.md)
