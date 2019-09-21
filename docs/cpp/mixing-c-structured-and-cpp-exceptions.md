﻿---
title: C (構造化) と C++ 例外の混合
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: 94d6dc249cb130aaf09d3202b9e8f437d00a9597
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345952"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>C (構造化) と C++ 例外の混合

移植可能なコードを記述する場合は、構造化例外 (SEH) を C++ プログラムで処理の使用はお勧めしません。 ただしを使用してコンパイルすることがありますも[/EHa](../build/reference/eh-exception-handling-model.md)構造化例外と C++ のソース コードを混在させるし、両方の種類の例外を処理するためのいくつかの機能を必要しします。 構造化例外ハンドラーにオブジェクトまたは型指定された例外の概念があるないために、C++ コードによってスローされた例外を処理できません。 ただし、C++**catch**ハンドラーは、構造化例外を処理できます。 C++例外処理構文 (**try**、**throw**、**catch**) が、C コンパイラは構造化例外処理の構文で受け入れられない ( **__try**、 **__except**、 **__finally**) でサポートされて、C++コンパイラ。

参照してください[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)として構造化例外を処理する方法についてC++例外。

構造化が混在する場合と C++ 例外、これらの潜在的な問題に注意してください。

- C++ の例外と構造化例外を、同じ関数内で混在させることはできません。

- 終了ハンドラー ( **__finally**ブロック)、例外がスローされた後のアンワインド中にも、常に実行します。

- C++ 例外処理をキャッチできるし、保持で、アンワインド セマンティクスでコンパイルされたすべてのモジュール、 [/EH](../build/reference/eh-exception-handling-model.md)コンパイラ オプション、アンワインド セマンティクスを有効にします。

- デストラクター関数がすべてのオブジェクトに対して呼び出されない状況もあります。 たとえば場合は、初期化されていない関数ポインターを通じて呼び出す関数を作成しようとしています。 構造化例外が発生し、その関数が呼び出しの前に構築されたオブジェクトをパラメーターとして受け取り、それらのオブジェクトのデストラクターは呼び出されません中にスタックのアンワインドを実行します。

## <a name="next-steps"></a>次の手順

- [C++ プログラムでの setjmp または longjmp の使用](../cpp/using-setjmp-longjmp.md)

  使用方法の詳細を参照してください`setjmp`と`longjmp`C++ プログラムでします。

- [C++ での構造化例外の処理](../cpp/exception-handling-differences.md)

  C++ を使用して、例外処理構造化する方法の例を参照してください。

## <a name="see-also"></a>関連項目

[C++ 例外処理](../cpp/cpp-exception-handling.md)
