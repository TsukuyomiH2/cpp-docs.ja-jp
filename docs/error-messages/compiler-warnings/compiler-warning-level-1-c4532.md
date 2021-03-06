---
title: コンパイラの警告 (レベル 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: b8c7503c7d1c1b711006415a327c360731222042
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87196345"
---
# <a name="compiler-warning-level-1-c4532"></a>コンパイラの警告 (レベル 1) C4532

' continue ': __finally/finally ブロックからジャンプすると、終了処理中に未定義の動作が発生します

コンパイラは、次のいずれかのキーワードを検出しました。

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

異常終了時に[__finally](../../cpp/try-finally-statement.md)または[finally](../../dotnet/finally.md)ブロックからジャンプする。

例外が発生したとき、終了ハンドラー (または finally ブロック) の実行中にスタックがアンワインドされているときに、 **`__finally`** **`__finally`** ブロックが終了する前にコードがブロックから移動した場合 **`__finally`** 、動作は未定義になります。 コントロールはアンワインドコードに戻らない場合があるため、例外が適切に処理されない可能性があります。

ブロックから移動する必要がある場合は **`__finally`** 、最初に異常終了を確認してください。

次の例では、C4532 が生成されます。警告を解決するには、ジャンプステートメントをコメントアウトするだけです。

```cpp
// C4532.cpp
// compile with: /W1
// C4532 expected
int main() {
   int i;
   for (i = 0; i < 10; i++) {
      __try {
      } __finally {
         // Delete the following line to resolve.
         continue;
      }

      __try {
      } __finally {
         // Delete the following line to resolve.
         break;
      }
   }
}
```
