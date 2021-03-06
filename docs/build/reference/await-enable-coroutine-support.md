---
description: 詳細については、次を参照してください:/await (コルーチンのサポートを有効にする)
title: /await (コルーチン サポートを有効にする)
ms.date: 08/15/2017
f1_keywords:
- /await
- -await
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
ms.openlocfilehash: a36c2233085a1c38ed61aed7d6ea757762179cc4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182763"
---
# <a name="await-enable-coroutine-support"></a>/await (コルーチン サポートを有効にする)

コルーチンのコンパイラサポートを有効にするには、 **/await** コンパイラオプションを使用します。

## <a name="syntax"></a>構文

> /await

## <a name="remarks"></a>解説

**/Await** コンパイラオプションを使用すると、C++ コルーチン、キーワード、、およびのコンパイラサポートが有効になり **`co_await`** **`co_yield`** **`co_return`** ます。 このオプションの既定値はオフです。 Visual Studio でのコルーチンのサポートについては、 [Visual Studio チームのブログ](https://devblogs.microsoft.com/cppblog/category/coroutine/)を参照してください。 コルーチン standard 提案の詳細については、「 [N4628 Working Draft」、「コルーチン用の C++ 拡張機能の技術仕様](https://wg21.link/n4628)」を参照してください。

**/Await** オプションは、Visual Studio 2015 以降で使用できます。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの [ **プロパティページ** ] ダイアログボックスを開きます。

1. [ **構成プロパティ**] で、[ **C/c + +** ] フォルダーを展開し、[ **コマンドライン** ] プロパティページをクリックします。

1. [**追加のオプション**] ボックスに、" **/await** " コンパイラオプションを入力します。 **[OK]** または [**適用**] を選択して、変更を保存します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC Compiler Command-Line 構文](compiler-command-line-syntax.md)
