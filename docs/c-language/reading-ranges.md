---
title: 範囲の読み取り
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: 86bb24647084d8bdc452960bab631587c2413276
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343149"
---
# <a name="reading-ranges"></a>範囲の読み取り

**ANSI 4.9.6.2**`fscanf` 関数の % [ 変換でのスキャン リストの最初または最後の文字ではないダッシュ (-) 文字の解釈

次の行

```
fscanf( fileptr, "%[A-Z]", strptr);
```

`strptr` が指す文字列に A から Z の範囲の任意の文字数を読み取ります。

## <a name="see-also"></a>関連項目

[ライブラリ関数](../c-language/library-functions.md)
