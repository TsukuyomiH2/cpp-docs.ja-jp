---
title: Unicode と MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], Unicode
- MFC [C++], character sets
- character sets [C++], multibyte
- run-time libraries [C++], language portability
- character sets [C++], Unicode
- Unicode [C++], MFC and C run-time functions
- multibyte characters [C++]
- runtime [C++], language portability
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
ms.openlocfilehash: 063c8b39ee0d29403b382b57a236f2a3e8759e3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375752"
---
# <a name="unicode-and-mbcs"></a>Unicode と MBCS

MFC (Microsoft Foundation Class) ライブラリ、Visual C++ の C ランタイム ライブラリ、および Visual C++ 開発環境では、国際対応のプログラミングを支援できます。 次のようなサポート方法があります。

- Windows でのユニコード標準のサポート。 Unicode は現在の標準です。できる限りこれを使用することをお勧めします。

   Unicode は 16 ビットの文字セットで、すべての言語に対する十分な表現能力を持っています。 すべての ASCII 文字は、拡張文字として Unicode の中に含まれます。

- すべてのプラットフォームにおけるマルチバイト文字セット (MBCS: Multibyte Character Set) の形式のサポート。マルチバイト文字セットは、2 バイト文字セット (DBCS: Double Byte Character Set) とも呼ばれています。

   DBCS 文字は、1 バイトまたは 2 バイトで構成されます。 特定の範囲のバイトは、先頭バイトとして予約されています。 先頭バイトとは、先頭バイト自体とその後ろに続く後続バイトが 1 組の 2 バイト幅文字を構成することを明示するバイトのことです。 プログラマは、どのバイトが先行バイトになるかを把握しておく必要があります。 特殊なマルチバイト文字セットでは、先行バイトが後続バイトと同じ範囲の値を持っている場合があります。 先頭バイトと後続バイトの範囲が重複する場合は、コンテキストを確認し、指定したバイトが先頭バイトと後続バイトのどちらであるかを判断する必要があります。

- 国際市場向けに作成されたアプリケーションの MBCS プログラミングを簡略化するツールをサポート。

   MBCS をサポートしている Windows オペレーティング システム上で Visual C++ 開発システムを実行すると、システム内の統合ソース コード エディター、デバッガー、コマンド ライン ツールなどを含むすべてが MBCS をサポートします。 詳細については、「 [Visual C++ での MBCS サポート](../text/mbcs-support-in-visual-cpp.md)」を参照してください。

> [!NOTE]
> このドキュメントでは、MBCS は、Unicode でサポートされていないすべてのマルチバイト文字を指します。 Visual C++ では、MBCS は常に DBCS を意味します。 2 バイトを超える文字セットはサポートされていません。

定義上、ASCII 文字セットは、すべてのマルチバイト文字セットのサブセットと考えることができます。 多くのマルチバイト文字セットでは、0x00 から 0x7F の範囲内の各文字が、ASCII 文字セットで同じ値を持つ文字と一致します。 たとえば、ASCII 文字列でも MBCS 文字列でも、1 バイトの NULL 文字 (\0) の値は 0x00 で、終端の null 文字を意味します。

## <a name="see-also"></a>関連項目

[テキストと文字列](../text/text-and-strings-in-visual-cpp.md)<br/>
[国際化実現](../text/international-enabling.md)
