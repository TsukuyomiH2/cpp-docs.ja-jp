---
title: C++ 識別子
ms.date: 05/07/2019
helpviewer_keywords:
- decorated names
- decorated names, about decorated names
- identifiers, C++
- white space, in C++ identifiers
- identifiers [C++]
ms.assetid: 03a0dfb1-4530-4cdf-8295-5ea4dca4c1b8
ms.openlocfilehash: 2d16dd318cd42b6294ef60edf44a16ccaf47b99b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187674"
---
# <a name="identifiers-c"></a>C++ 識別子

識別子は、次のいずれかを示すために使用される文字のシーケンスです。

- オブジェクトまたは変数名

- クラス、構造体、または共用体の名前

- 列挙型の名前

- クラス、構造体、共用体、または列挙体のメンバー

- 関数またはクラス メンバー関数

- typedef 名

- ラベル名

- マクロ名

- マクロ パラメーター

次の文字は、識別子内の文字として使用できます。

```
_ a b c d e f g h i j k l m
n o p q r s t u v w x y z
A B C D E F G H I J K L M
N O P Q R S T U V W X Y Z
```

特定の範囲のユニバーサル文字名も識別子に使用できます。  識別子内に、制御文字または基本ソース文字セット内の文字を指すユニバーサル文字名を使用することはできません。 詳細については、「 [Character Sets](../cpp/character-sets.md)」を参照してください。 次の範囲の Unicode コード ポイント番号が、識別子内の文字として使用できるユニバーサル文字名です。

- 00A8、00AA、00AD、00AF、00B2 ～ 00B5、00B7 ～ 00BA、00BC ～ 00BE、00C0 ～ 00D6、00D8 ～ 00F6、00F8 ～ 00FF、0100 ～ 02FF、0370 ～ 167F、1681 ～ 180D、180F ～ 1DBF、1E00 ～ 1FFF、200B ～ 200D、202A ～ 202E、203F ～ 2040、2054、2060 ～ 206F、2070 ～ 20CF、2100 ～ 218F、2460 ～ 24FF、2776 ～ 2793、2C00 ～ 2DFF、2E80 ～ 2FFF、3004 ～ 3007、3021 ～ 302F、3031 ～ 303F、3040 ～ D7FF、F900 ～ FD3D、FD40 ～ FDCF、FDF0 ～ FE1F、FE30 ～ FE44、FE47 ～ FFFD、10000 ～ 1FFFD、20000 ～ 2FFFD、30000 ～ 3FFFD、40000 ～ 4FFFD、50000 ～ 5FFFD、60000 ～ 6FFFD、70000 ～ 7FFFD、80000 ～ 8FFFD、90000 ～ 9FFFD、A0000 ～ AFFFD、B0000 ～ BFFFD、C0000 ～ CFFFD、D0000 ～ DFFFD、E0000 ～ EFFFD

次の文字は、識別子内の文字 (最初の文字以外) として使用できます。

```
0 1 2 3 4 5 6 7 8 9
```

次の範囲の Unicode コード ポイント番号も、識別子内の文字 (最初の文字以外) として使用できるユニバーサル文字名です。

- 0300 ～ 036F、1DC0 ～ 1DFF、20D0 ～ 20FF、FE20 ～ FE2F

**Microsoft 固有の仕様**

Microsoft C++ 識別子の最初の 2048 文字だけが意味を持ちます。 ユーザー定義型の名前はコンパイラによって型情報を保持するように修飾されます。 結果の名前は、型情報を含め、2048 文字を超えることはできません (詳細については、「[装飾名](../build/reference/decorated-names.md)」を参照してください)。修飾された識別子の長さに影響する要因は次のとおりです。

- 識別子が、ユーザー定義型のオブジェクト、またはユーザー定義型から派生した型を表すかどうか。

- 識別子が、関数または関数から派生した型を表すかどうか。

- 関数の引数の数。

ドル記号 `$` は、Microsoft C++ コンパイラ (MSVC) の有効な識別子文字です。 また、MSVC では、許可されているユニバーサル文字名の範囲で表される実際の文字を識別子で使用することもできます。 これらの文字を使用するには、それらを含むファイル エンコーディング コードページを使用してファイルを保存する必要があります。  この例は、拡張文字とユニバーサル文字名の両方をコード内で区別せずに使用する方法を示しています。

```cpp
// extended_identifier.cpp
// In Visual Studio, use File, Advanced Save Options to set
// the file encoding to Unicode codepage 1200
struct テスト         // Japanese 'test'
{
    void トスト() {}  // Japanese 'toast'
};

int main() {
    テスト \u30D1\u30F3;  // Japanese パン 'bread' in UCN form
    パン.トスト();        // compiler recognizes UCN or literal form
}
```

識別子で許可される文字の範囲は、C++/CLI コードをコンパイルする場合よりも制限されません。 /clr を使用してコンパイルするコード内の識別子は、  [標準 ECMA 335: 共通言語基盤 (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm)に従う必要があります。

**Microsoft 固有の仕様はここまで**

識別子の先頭文字は、英字 (大文字でも小文字でもかまいません) またはアンダースコア ( **_** ) 文字にする必要があります。 C++ の識別子は大文字と小文字が区別されるため、 `fileName` は `FileName`とは異なります。

識別子をキーワードとまったく同じスペルおよび大文字小文字にすることはできません。 キーワードを含む識別子は有効です。 たとえば、は、キーワードであるが含まれている場合で `Pint` も、有効な識別子です **`int`** 。

識別子に2つの連続するアンダースコア文字 ( **__** ) を使用した場合、または1つの先頭にアンダースコアを付けた後に大文字が続く場合は、すべてのスコープで C++ の実装のために予約されています。 現在または将来の予約済み識別子と競合する可能性があるため、ファイルのスコープを含む名前には、先頭の 1 つのアンダースコアとそれに続く子文字を使用しないようにする必要があります。

## <a name="see-also"></a>関連項目

[字句表記規則](../cpp/lexical-conventions.md)
