---
title: 属性 (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: b9e645de021e8618d1dc15a7d58dbbe5998e6fbc
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032383"
---
# <a name="attributes-ccx"></a>属性 (C++/CX)

属性は、メタデータの作成で特定の動作を指定するために、Windows ランタイムの型とメソッドに角かっこで付加できる特殊な種類の ref クラスです。 いくつかの定義済み属性 (例: [Windows:ファンデーション:メタデータ::WebHostHidden)](/uwp/api/windows.foundation.metadata.webhosthiddenattribute)は、C++/CX コードで一般的に使用されています。 この例では、属性がクラスに適用される方法を示します。

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>カスタム属性

カスタム属性も定義できます。 カスタム属性は、次の Windows ランタイム ルールに準拠する必要があります。

- カスタム属性は、パブリック フィールドだけを格納できます。

- カスタム属性フィールドは、属性がクラスに適用されるときに初期化できます。

- フィールドは、次に示すいずれかの型になることができます。

  - int32 (int)

  - uint32 (unsigned int)

  - [bool]

  - Platform::String^

  - Windows::Foundation::HResult

  - Platform::Type^

  - パブリック列挙型クラス (ユーザー定義列挙型を含む)

次の例では、カスタム属性を定義し、使用時に初期化する方法を示します。

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>関連項目

[タイプ システム (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[C++/CX 言語リファレンス](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[名前空間参照](../cppcx/namespaces-reference-c-cx.md)
