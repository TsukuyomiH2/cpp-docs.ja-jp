---
title: 複数のターゲット
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
ms.openlocfilehash: 43e5216d5e11e89aff9b6f0c69ff4e76a8cc9da8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826341"
---
# <a name="multiple-targets"></a>複数のターゲット

(Nmake の) は、個別の記述ブロックでそれぞれ指定した場合と、単一の依存関係の複数のターゲットを評価します。

例えばこの。。。

```Output
bounce.exe leap.exe : jump.obj
   echo Building...
```

.. 評価結果。

```Output
bounce.exe : jump.obj
   echo Building...
leap.exe : jump.obj
   echo Building...
```

## <a name="see-also"></a>関連項目

[ターゲット](targets.md)