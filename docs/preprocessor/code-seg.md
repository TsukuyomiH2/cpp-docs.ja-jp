---
description: '詳細については、次を参照してください: code_seg プラグマ'
title: code_seg プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: c303d7e86dc94be3c3d76368b92915cd06010567
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300841"
---
# <a name="code_seg-pragma"></a>code_seg プラグマ

関数がオブジェクト (.obj) ファイルに格納されるテキストセクション (セグメント) を指定します。

## <a name="syntax"></a>構文

> **#pragma code_seg (** ["*section-name*" [ **,** "*section-class*"]] **)**\
> **#pragma code_seg (** { **push**  |  **pop** } [ **,** *identifier* ] [ **,** "*section-name*" [ **,** "*section-class*"]] **)**

### <a name="parameters"></a>パラメーター

**押し付け**\
Optional内部コンパイラスタックにレコードを格納します。 **プッシュ** は *識別子* と *セクション名* を持つことができます。

**ショート**\
Optional内部コンパイラスタックの先頭からレコードを削除します。 **Pop** は *識別子* と *セクション名* を持つことができます。 *識別子* を使用して、 **pop** コマンドを1つだけ使用して複数のレコードをポップできます。 *セクション名* は、pop の後のアクティブなテキストセクション名になります。

*identifier*\
Optional **Push** と共に使用すると、内部コンパイラスタックのレコードに名前が割り当てられます。 **Pop** と共に使用する場合、ディレクティブは、*識別子* が削除されるまで、レコードを内部スタックからポップします。 *識別子* が内部スタックで見つからない場合は、何もポップされません。

"*section-name*" \
Optionalセクションの名前。 **Pop** と共に使用すると、スタックがポップされ、*セクション名* がアクティブなテキストセクション名になります。

"*セクションクラス*" \
Optionalは無視されますが、バージョン2.0 より前のバージョンの Microsoft C++ との互換性のために含まれています。

## <a name="remarks"></a>解説

オブジェクトファイルの *セクション* は、1つの単位としてメモリに読み込まれるデータの名前付きブロックです。 *テキストセクション* は、実行可能コードを含むセクションです。 この記事では、 *セグメント* と *セクション* は同じ意味を持ちます。

**Code_seg** pragma ディレクティブは、翻訳単位の後続のすべてのオブジェクトコードを、 *section-name* という名前のテキストセクションに配置するようコンパイラに指示します。 既定では、オブジェクトファイルの関数に使用される text セクションにはという名前が付けられ `.text` ます。 *セクション名* パラメーターを指定せずに **code_seg** プラグマディレクティブを実行すると、その後のオブジェクトコードのテキストセクション名がにリセットされ `.text` ます。

**Code_seg** プラグマディレクティブは、インスタンス化されたテンプレート用に生成されたオブジェクトコードの配置を制御しません。 また、特殊なメンバー関数など、コンパイラによって暗黙的に生成されるコードも制御しません。 このコードを制御するには、代わりに [__declspec (code_seg (...))](../cpp/code-seg-declspec.md) 属性を使用することをお勧めします。 コンパイラによって生成されるコードを含め、すべてのオブジェクトコードの配置を制御できます。

セクションの作成に使用しない名前の一覧については、「 [/SECTION](../build/reference/section-specify-section-attributes.md)」を参照してください。

初期化されたデータのセクション ([data_seg](../preprocessor/data-seg.md))、初期化されていないデータ ([bss_seg](../preprocessor/bss-seg.md))、および const 変数 ([const_seg](../preprocessor/const-seg.md)) を指定することもできます。

[DUMPBIN.EXE](../build/reference/dumpbin-command-line.md)アプリケーションを使用して、オブジェクトファイルを表示できます。 サポートされている各ターゲットアーキテクチャの DUMPBIN のバージョンは、Visual Studio に含まれています。

## <a name="example"></a>例

この例では、 **code_seg** pragma ディレクティブを使用して、オブジェクトコードの配置場所を制御する方法を示します。

```cpp
// pragma_directive_code_seg.cpp
void func1() {                  // stored in .text
}

#pragma code_seg(".my_data1")
void func2() {                  // stored in my_data1
}

#pragma code_seg(push, r1, ".my_data2")
void func3() {                  // stored in my_data2
}

#pragma code_seg(pop, r1)      // stored in my_data1
void func4() {
}

int main() {
}
```

## <a name="see-also"></a>関連項目

[code_seg (__declspec)](../cpp/code-seg-declspec.md)\
[プラグマ ディレクティブと __pragma キーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
