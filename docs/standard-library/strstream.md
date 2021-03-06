---
description: '詳細情報: &lt; strstream&gt;'
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: e99a07df2a63b991232440f8dad0eb299d0e00b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183556"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

オブジェクトの割り当てられた配列に格納されているシーケンスに対して iostreams 操作をサポートする複数のクラスを定義 **`char`** します。 このようなシーケンスは、C 文字列と簡単に相互変換できます。

## <a name="requirements"></a>要件

**ヘッダー:**\<strstream>

**名前空間:** std

## <a name="remarks"></a>解説

型のオブジェクト `strstream` **`char`** は、C 文字列である * を使用して処理されます。 [\<sstream>](../standard-library/sstream.md) [Basic_string](../standard-library/basic-string-class.md)型のオブジェクトを操作するために使用します。

> [!NOTE]
> \<strstream> のクラスの使用は非推奨とされます。 代わりに、\<sstream> のクラスの使用を検討してください。

## <a name="members"></a>メンバー

### <a name="classes"></a>クラス

|名前|説明|
|-|-|
|[strstreambuf クラス](../standard-library/strstreambuf-class.md)|クラスは、配列オブジェクトに格納されている要素のシーケンスとの間での要素の転送を制御するストリームバッファーを記述し **`char`** ます。|
|[istrstream クラス](../standard-library/istrstream-class.md)|このクラスは、クラス [strstreambuf](../standard-library/strstreambuf-class.md) のストリーム バッファーからの、要素とエンコードされたオブジェクトの抽出を制御するオブジェクトを表します。|
|[ostrstream クラス](../standard-library/ostrstream-class.md)|このクラスは、クラス [strstreambuf](../standard-library/strstreambuf-class.md) のストリーム バッファーへの、要素とエンコードされたオブジェクトの挿入を制御するオブジェクトを表します。|
|[strstream クラス](../standard-library/strstream-class.md)|このクラスは、クラス [strstreambuf](../standard-library/strstreambuf-class.md) のストリーム バッファーを使用して要素とエンコードされたオブジェクトの挿入と抽出を制御するオブジェクトを表します。|

### <a name="functions"></a>関数

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>関連項目

[\<strstream>](../standard-library/strstream.md)\
[ヘッダーファイルのリファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリのスレッドセーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
