---
description: 詳細については、「リンカーツールの警告 LNK4037」を参照してください。
title: リンカー ツールの警告 LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 78fd5ed9f8e2f82221b64053607846f1b8abc00a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331956"
---
# <a name="linker-tools-warning-lnk4037"></a>リンカー ツールの警告 LNK4037

>'*symbol*' は存在しません。無効

装飾名 *シンボル* は、プログラムで見つからなかったため、 [/order](../../build/reference/order-put-functions-in-order.md) オプションを使用して並べ替えることができませんでした。 注文応答ファイルで *シンボル* の仕様を確認します。 詳細については、「 [/order 関数を順序どおりに配置](../../build/reference/order-put-functions-in-order.md) する」リンカーオプションを参照してください。

> [!NOTE]
> 静的関数名がパブリックシンボル名ではないため、リンクで静的関数を順序付けることはできません。 **/Order** が指定されている場合、このリンカー警告は、順序応答ファイル内の各シンボルに対して、静的な、または見つからないシンボルごとに生成されます。
