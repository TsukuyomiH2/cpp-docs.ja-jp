---
description: 詳細情報:/allowbind (DLL バインドを禁止)
title: /ALLOWBIND (DLL をバインドしない)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
ms.openlocfilehash: 727f1cae7d1b0a94a8f7faba90ee6994df8657e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187235"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (DLL をバインドしない)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>解説

/ALLOWBIND:NO は DLL のヘッダーにビットを設定して、イメージをバインドできないことを Bind.exe に示します。 DLL がデジタル署名されている場合はバインドしないほうがよいでしょう (バインドによって署名が無効になる)。

/Allowbind 機能の既存の DLL を編集するには、EDITBIN ユーティリティの [/allowbind](allowbind.md) オプションを使用します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. [ **構成プロパティ**]、[ **リンカー**] の順に展開し、[ **コマンドライン**] を選択します。

1. `/ALLOWBIND:NO`追加の **オプション** を入力します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)<br/>
[BindImage 関数](/windows/win32/api/imagehlp/nf-imagehlp-bindimage)<br/>
[BindImageEx 関数](/windows/win32/api/imagehlp/nf-imagehlp-bindimageex)
