---
title: 致命的なエラー C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: 9ea97bef16bebb8fc0e765ed708e54baee9a64de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220341"
---
# <a name="fatal-error-c1026"></a>致命的なエラー C1026

プログラムの解析でコンパイラ内でスタック オーバーフローが発生しました。プログラムが複雑すぎます。

プログラムを解析するために必要な領域が、コンパイラスタックオーバーフローを発生させました。

次のようにして、式の複雑さを軽減します。

- ステートメントとステートメントの入れ子を減らす **`for`** **`switch`** 。 より深い入れ子になったステートメントを個別の関数に配置します。

- コンマ演算子や関数呼び出しを含む長い式を分割します。
