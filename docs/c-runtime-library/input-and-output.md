---
description: '詳細情報: 入力と出力'
title: 入力と出力
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- input routines
- I/O [CRT]
- I/O routines
- I/O [CRT], routines
- output routines
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
ms.openlocfilehash: 0edd66765f1633dc0adf12b311faf81d3a030512
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334281"
---
# <a name="input-and-output"></a>入力と出力

I/O 関数はファイルやデバイスとの間でデータの読み書きを行います。 ファイル I/O 操作は、テキスト モードまたはバイナリ モードで行われます。 Microsoft ランタイム ライブラリには、次の 3 つの種類の I/O 関数があります。

- [ストリーム入出力](../c-runtime-library/stream-i-o.md)関数は、データを個々の文字のストリームとして処理します。

- [下位入出力](../c-runtime-library/low-level-i-o.md)関数は、ストリーム入出力の操作より下位の操作に対してオペレーティング システムを直接呼び出します。

- [コンソール入出力とポート入出力](../c-runtime-library/console-and-port-i-o.md)関数は、コンソール () または入出力ポートに対して読み書きを直接実行します。

   > [!NOTE]
   > ストリーム関数はバッファーされ、下位入出力関数はバッファーされないため、これら 2 つの種類の関数には一般的に互換性がありません。 特定のファイルを処理するとき、ストリーム関数または下位入出力関数のいずれかを排他的に使用してください。

## <a name="see-also"></a>関連項目

[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
