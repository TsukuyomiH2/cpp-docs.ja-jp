---
description: 詳細については、「呼び出し規約」を参照してください。
title: 呼び出し規則
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: bb5dab14e9d046b6ccee75a4fb37bd7b105902dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308654"
---
# <a name="calling-conventions"></a>呼び出し規則

Visual C/C++ コンパイラには、内部関数と外部関数の呼び出し規約がいくつか用意されています。 これらの異なる方法を理解することは、プログラムをデバッグし、コードをアセンブリ言語ルーチンとリンクするときに役立ちます。

この話題に関するトピックでは、呼び出し規則の違い、引数の渡し方、関数による値の返し方について説明します。 naked 関数の呼び出し (独自のプロローグおよびエピローグ コードを記述できる高度な機能) についても説明します。

X64 プロセッサの呼び出し規約の詳細については、「 [呼び出し規約](../build/x64-calling-convention.md)」を参照してください。

## <a name="topics-in-this-section"></a>このセクションのトピック

- [引数の引き渡し規則と名前付け規則](../cpp/argument-passing-and-naming-conventions.md) ( **`__cdecl`** 、、 **`__stdcall`** **`__fastcall`** 、その他)

- [呼び出しの例: 関数プロトタイプと呼び出し](../cpp/calling-example-function-prototype-and-call.md)

- [naked 関数の呼び出しを使用したカスタム プロローグ/エピローグ コードの作成](../cpp/naked-function-calls.md)

- [浮動小数点コプロセッサと呼び出し規約](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [古い呼び出し規則](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>関連項目

[Microsoft 固有の修飾子](../cpp/microsoft-specific-modifiers.md)
