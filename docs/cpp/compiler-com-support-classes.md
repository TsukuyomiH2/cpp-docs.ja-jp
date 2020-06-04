---
title: コンパイラ COM サポート クラス
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: a8b0845fdfa96c1cb4b8b67e9d39169d9f4d3737
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189703"
---
# <a name="compiler-com-support-classes"></a>コンパイラ COM サポート クラス

**Microsoft 固有の仕様**

標準クラスは、COM 型の一部をサポートするために使用されます。 クラスは \<comdef .h > と、タイプライブラリから生成されたヘッダーファイルで定義されています。

|クラス|目的|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|便利な演算子とメソッドを提供するために、`BSTR` 型をラップします。|
|[_com_error](../cpp/com-error-class.md)|ほとんどのエラーで[_com_raise_error](../cpp/com-raise-error.md)によってスローされるエラーオブジェクトを定義します。|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|COM インターフェイスポインターをカプセル化し、`AddRef`、`Release`、および `QueryInterface`への必要な呼び出しを自動化します。|
|[_variant_t](../cpp/variant-t-class.md)|便利な演算子とメソッドを提供するために、`VARIANT` 型をラップします。|

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[コンパイラ COM サポート](../cpp/compiler-com-support.md)<br/>
[コンパイラ COM のグローバル関数](../cpp/compiler-com-global-functions.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)
