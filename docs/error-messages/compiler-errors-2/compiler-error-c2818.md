---
title: コンパイラ エラー C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 786a38aca2c3b9674969018d9e5766eed29c358c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212671"
---
# <a name="compiler-error-c2818"></a>コンパイラ エラー C2818

オーバーロードされた ' operator-> ' のアプリケーションは型 ' type ' で再帰的です

クラスメンバーアクセス演算子の再定義には、再帰ステートメントが含まれてい **`return`** ます。 再帰を使用して演算子を再定義するには、 `->` 再帰ルーチンを、operator override 関数から呼び出された別の関数に移動する必要があります。
