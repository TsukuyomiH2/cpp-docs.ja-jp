---
title: C プラグマ
ms.date: 07/26/2020
helpviewer_keywords:
- pragmas, C/C++
ms.assetid: 3d6d36b4-d565-4632-a4cd-e39aeaded5ad
ms.openlocfilehash: d6f41db60b4724214cb0bdf04f88c9ac87fe44a0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227960"
---
# <a name="c-pragmas"></a>C プラグマ

**Microsoft 固有の仕様**

"*プラグマ*" は、コンパイル時に特定のアクションを実行するようにコンパイラに指示します。 プラグマは、コンパイラごとに異なります。 たとえば、`optimize` プラグマを使用すると、プログラムで実行する最適化を設定できます。 Microsoft C のプラグマは、次のとおりです。

:::row:::
    :::column:::
        [`alloc_text`](../preprocessor/alloc-text.md)<br/>
        [`auto_inline`](../preprocessor/auto-inline.md)<br/>
        [`bss_seg`](../preprocessor/bss-seg.md)<br/>
        [`check_stack`](../preprocessor/check-stack.md)<br/>
        [`code_seg`](../preprocessor/code-seg.md)<br/>
        [`comment`](../preprocessor/comment-c-cpp.md)<br/>
        [`component`](../preprocessor/component.md)<br/>
        [`const_seg`](../preprocessor/const-seg.md)<br/>
        [`data_seg`](../preprocessor/data-seg.md)<br/>
    :::column-end:::
    :::column:::
        [`deprecated`](../preprocessor/deprecated-c-cpp.md)<br/>
        [`detect_mismatch`](../preprocessor/detect-mismatch.md)<br/>
        [`fenv_access`](../preprocessor/fenv-access.md)<br/>
        [`float_control`](../preprocessor/float-control.md)<br/>
        [`fp_contract`](../preprocessor/fp-contract.md)<br/>
        [`function`](../preprocessor/function-c-cpp.md)<br/>
        [`hdrstop`](../preprocessor/hdrstop.md)<br/>
        [`include_alias`](../preprocessor/include-alias.md)<br/>
        [`inline_depth`](../preprocessor/inline-depth.md)<br/>
    :::column-end:::
    :::column:::
        [`inline_recursion`](../preprocessor/inline-recursion.md)<br/>
        [`intrinsic`](../preprocessor/intrinsic.md)<br/>
        [`make_public`](../preprocessor/make-public.md)<br/>
        [`managed`](../preprocessor/managed-unmanaged.md)<br/>
        [`message`](../preprocessor/message.md)<br/>
        [`omp`](../preprocessor/omp.md)<br/>
        [`once`](../preprocessor/once.md)<br/>
        [`optimize`](../preprocessor/optimize.md)<br/>
        [`pack`](../preprocessor/pack.md)<br/>
    :::column-end:::
    :::column:::
        [`pop_macro`](../preprocessor/pop-macro.md)<br/>
        [`push_macro`](../preprocessor/push-macro.md)<br/>
        [`region`, `endregion`](../preprocessor/region-endregion.md)<br/>
        [`runtime_checks`](../preprocessor/runtime-checks.md)<br/>
        [`section`](../preprocessor/section.md)<br/>
        [`setlocale`](../preprocessor/setlocale.md)<br/>
        [`strict_gs_check`](../preprocessor/strict-gs-check.md)<br/>
        [`unmanaged`](../preprocessor/managed-unmanaged.md)<br/>
        [`warning`](../preprocessor/warning.md)<br/>
    :::column-end:::
:::row-end:::

Microsoft C コンパイラのプラグマについては、「[プラグマ ディレクティブと `__Pragma` キーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)」をご覧ください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[ソース ファイルとソース プログラム](../c-language/source-files-and-source-programs.md)
