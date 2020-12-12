---
description: '詳細情報: XML ドキュメントジェネレーターツールのプロパティページ'
title: '[XML ドキュメント ジェネレーター] プロパティ ページ'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
ms.openlocfilehash: e344d8ef796a5c3455c88851a1fc410801b991bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260970"
---
# <a name="xml-document-generator-tool-property-pages"></a>[XML ドキュメント ジェネレーター] プロパティ ページ

[XML ドキュメント ジェネレーター] プロパティ ページでは、xdcmake.exe の機能が公開されます。 xdcmake.exe は、ソース コードにドキュメントのコメントが含まれていて、[/doc (ドキュメント コメントの処理) (C/C++)](doc-process-documentation-comments-c-cpp.md) が指定されている場合に、.xdc ファイルを .xml ファイルにマージします。 ドキュメントのコメントをソース コードに追加する詳細については、「[ドキュメント コメントとして推奨されるタグ](recommended-tags-for-documentation-comments-visual-cpp.md)」を参照してください。

> [!NOTE]
> 開発環境 (プロパティ ページ) の xdcmake.exe オプションは、コマンド ラインで xdcmake.exe を使用する場合のオプションとは異なります。 コマンド ラインで xdcmake.exe を使用する詳細については、「[XDCMake リファレンス](xdcmake-reference.md)」を参照してください。

## <a name="uielement-list"></a>UIElement の一覧

- **著作権情報の非表示**

   著作権メッセージを表示しません。

- **追加ドキュメント ファイル**

   プロジェクト システムが .xdc ファイルを検索する追加のディレクトリ。 xdcmake は、常に、プロジェクトによって生成される .xdc ファイルを探します。 複数のディレクトリを指定することができます。

- **出力ドキュメント ファイル**

   .xml 出力ファイルの名前とディレクトリの場所。 マクロを使用してディレクトリの場所を指定する方法については [、「ビルドコマンドとプロパティの一般的なマクロ](common-macros-for-build-commands-and-properties.md) 」を参照してください。

- **ドキュメント ライブラリの依存関係**

   プロジェクトにソリューション内の .lib プロジェクトへの依存関係がある場合は、.lib プロジェクトから現在のプロジェクトの .xml ファイルに .xdc ファイルを処理できます。

## <a name="see-also"></a>関連項目

[C++ プロジェクトのプロパティ ページのリファレンス](property-pages-visual-cpp.md)
