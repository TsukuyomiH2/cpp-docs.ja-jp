---
description: 詳細については、「リンカツール Error LNK1277」を参照してください。
title: リンカ ツール エラー LNK1277
ms.date: 11/04/2016
f1_keywords:
- LNK1277
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
ms.openlocfilehash: 82a71878d30088bd018c4e54216d53228efe949d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193735"
---
# <a name="linker-tools-error-lnk1277"></a>リンカ ツール エラー LNK1277

オブジェクトレコードが pgd (ファイル名) に見つかりません

[/Ltcg: PG最適化 ze](../../build/reference/ltcg-link-time-code-generation.md)を使用する場合、入力 .lib、def、または .obj ファイルの1つのパスが、/LTCG: pgインストルメント中に検出されたパスと異なっていました。 これは、/LTCG: PGINSTRUMENT 後の LIB 環境変数の変更によって説明されている場合があります。 入力ファイルへの完全パスは、.pgd ファイルに格納されます。

/LTCG: PGOPTIMIZE では、入力が/LTCG: PGOPTIMIZE フェーズと同じである必要があります。

この警告を解決するには、次のいずれかの操作を行います。

- /LTCG: PGINSTRUMENT を実行し、すべてのテストの実行をやり直し、/LTCG: PGINSTRUMENT を実行します。

- LIB 環境変数を、/LTCG: PGINSTRUMENT を実行したときのものに変更します。

/LTCG: PGUPDATE を使用して LNK1277 を回避することはお勧めしません。
