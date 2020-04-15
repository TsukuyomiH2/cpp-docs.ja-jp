---
title: moneypunct クラス
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct
- xlocmon/std::moneypunct::char_type
- xlocmon/std::moneypunct::string_type
- xlocmon/std::moneypunct::curr_symbol
- xlocmon/std::moneypunct::decimal_point
- xlocmon/std::moneypunct::do_curr_symbol
- xlocmon/std::moneypunct::do_decimal_point
- xlocmon/std::moneypunct::do_frac_digits
- xlocmon/std::moneypunct::do_grouping
- xlocmon/std::moneypunct::do_neg_format
- xlocmon/std::moneypunct::do_negative_sign
- xlocmon/std::moneypunct::do_pos_format
- xlocmon/std::moneypunct::do_positive_sign
- xlocmon/std::moneypunct::do_thousands_sep
- xlocmon/std::moneypunct::frac_digits
- xlocmon/std::moneypunct::grouping
- xlocmon/std::moneypunct::neg_format
- xlocmon/std::moneypunct::negative_sign
- xlocmon/std::moneypunct::pos_format
- xlocmon/std::moneypunct::positive_sign
- xlocmon/std::moneypunct::thousands_sep
helpviewer_keywords:
- std::moneypunct [C++]
- std::moneypunct [C++], char_type
- std::moneypunct [C++], string_type
- std::moneypunct [C++], curr_symbol
- std::moneypunct [C++], decimal_point
- std::moneypunct [C++], do_curr_symbol
- std::moneypunct [C++], do_decimal_point
- std::moneypunct [C++], do_frac_digits
- std::moneypunct [C++], do_grouping
- std::moneypunct [C++], do_neg_format
- std::moneypunct [C++], do_negative_sign
- std::moneypunct [C++], do_pos_format
- std::moneypunct [C++], do_positive_sign
- std::moneypunct [C++], do_thousands_sep
- std::moneypunct [C++], frac_digits
- std::moneypunct [C++], grouping
- std::moneypunct [C++], neg_format
- std::moneypunct [C++], negative_sign
- std::moneypunct [C++], pos_format
- std::moneypunct [C++], positive_sign
- std::moneypunct [C++], thousands_sep
ms.assetid: cf2650da-3e6f-491c-95d5-23e57f582ee6
ms.openlocfilehash: 3a277b2f97fd53c52b705051c30eb18faf6364d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366248"
---
# <a name="moneypunct-class"></a>moneypunct クラス

クラス テンプレートは、通貨入力フィールドまたは通貨出力フィールドを表すために使用される*CharType*型のシーケンスを記述するロケール ファセットとして機能するオブジェクトを表します。 テンプレート パラメータ*Intl*が*true*の場合は、国際規則が守られます。

## <a name="syntax"></a>構文

```cpp
template <class CharType, bool Intl>
class moneypunct;
```

### <a name="parameters"></a>パラメーター

*Chartype*\
文字をエンコードするためにプログラム内で使用される型。

*国際 空港*\
国際的な規則を確認するかどうかを指定するフラグ。

## <a name="remarks"></a>解説

すべてのロケールのファセットと同様、静的オブジェクト ID に最初に格納されている値は 0 です。 格納されている値に初めてアクセスしようとすると、**id** に一意の正の値が格納されます。

const 静的オブジェクト intl は、テンプレート パラメーター *Intl* の値を格納します。

### <a name="constructors"></a>コンストラクター

|Constructor|説明|
|-|-|
|[moneypunct](#moneypunct)|`moneypunct` 型のオブジェクトのコンストラクター。|

### <a name="typedefs"></a>Typedefs

|種類の名前。|説明|
|-|-|
|[char_type](#char_type)|ロケールによって使用される文字を表すために使用される型。|
|[string_type](#string_type)|`CharType` 型の文字を格納する文字列を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[curr_symbol](#curr_symbol)|通貨記号として使用する要素のロケール固有のシーケンスを返します。|
|[decimal_point](#decimal_point)|小数点記号として使用する要素のロケール固有のシーケンスを返します。|
|[do_curr_symbol](#do_curr_symbol)|通貨記号として使用する要素のロケール固有のシーケンスを返すプロテクト仮想メンバー関数。|
|[do_decimal_point](#do_decimal_point)|小数点記号として使用する要素のロケール固有のシーケンスを返すために呼び出されるプロテクト仮想メンバー関数。|
|[do_frac_digits](#do_frac_digits)|このプロテクト仮想メンバー関数は、小数点の右側に表示する桁数のロケール固有の数を返します。|
|[do_grouping](#do_grouping)|このプロテクト仮想メンバー関数は、小数点の左側の数字をグループ化する方法を決定するロケール固有の規則を返します。|
|[do_neg_format](#do_neg_format)|負の値の出力を書式設定するためのロケール固有の規則を返すために呼び出されるプロテクト仮想メンバー関数。|
|[do_negative_sign](#do_negative_sign)|負の記号として使用する要素のロケール固有のシーケンスを返すために呼び出されるプロテクト仮想メンバー関数。|
|[do_pos_format](#do_pos_format)|正の値の出力を書式設定するためのロケール固有の規則を返すために呼び出されるプロテクト仮想メンバー関数。|
|[do_positive_sign](#do_positive_sign)|正の記号として使用する要素のロケール固有のシーケンスを返すために呼び出されるプロテクト仮想メンバー関数。|
|[do_thousands_sep](#do_thousands_sep)|桁区切り記号として使用する要素のロケール固有のシーケンスを返すために呼び出されるプロテクト仮想メンバー関数。|
|[frac_digits](#frac_digits)|小数点の右側に表示する桁数のロケール固有の数を返します。|
|[グループ](#grouping)|小数点の左側の数字をグループ化する方法を決定するロケール固有の規則を返します。|
|[neg_format](#neg_format)|負の値の出力を書式設定するためのロケール固有の規則を返します。|
|[negative_sign](#negative_sign)|負の記号として使用する要素のロケール固有のシーケンスを返します。|
|[pos_format](#pos_format)|正の値の出力を書式設定するためのロケール固有の規則を返します。|
|[positive_sign](#positive_sign)|正の記号として使用する要素のロケール固有のシーケンスを返します。|
|[thousands_sep](#thousands_sep)|桁区切り記号として使用する要素のロケール固有のシーケンスを返します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="moneypunctchar_type"></a><a name="char_type"></a>マネープンク::char_type

ロケールによって使用される文字を表すために使用される型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>解説

この型は、テンプレート パラメーター **CharType** のシノニムです。

## <a name="moneypunctcurr_symbol"></a><a name="curr_symbol"></a>マネープンク::curr_symbol

通貨記号として使用する要素のロケール固有のシーケンスを返します。

```cpp
string_type curr_symbol() const;
```

### <a name="return-value"></a>戻り値

通貨記号を含む文字列。

### <a name="remarks"></a>解説

このメンバー関数は、[do_curr_symbol](#do_curr_symbol) を返します。

### <a name="example"></a>例

```cpp
// moneypunct_curr_symbol.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct < char, true > &mpunct = use_facet < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international currency symbol "<<  mpunct.curr_symbol( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic currency symbol "<<  mpunct2.curr_symbol( ) << endl;
};
```

## <a name="moneypunctdecimal_point"></a><a name="decimal_point"></a>マネープンクト::dエシマル_ポイント

小数点記号として使用する要素のロケール固有のシーケンスを返します。

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>戻り値

小数点記号として使用する要素のロケール固有のシーケンス。

### <a name="remarks"></a>解説

このメンバー関数は、[do_decimal_point](#do_decimal_point) を返します。

### <a name="example"></a>例

```cpp
// moneypunct_decimal_pt.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc("german_germany");

   const moneypunct < char, true > &mpunct = use_facet
      < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international decimal point "
        << mpunct.decimal_point( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet
      < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic decimal point "
        << mpunct2.decimal_point( ) << endl;
}
```

```Output
German_Germany.1252 international decimal point ,
German_Germany.1252 domestic decimal point ,
```

## <a name="moneypunctdo_curr_symbol"></a><a name="do_curr_symbol"></a>マネープンク::do_curr_シンボル

通貨記号として使用する要素のロケール固有のシーケンスを返すプロテクト仮想メンバー関数。

```cpp
virtual string_type do_curr_symbol() const;
```

### <a name="return-value"></a>戻り値

小数点記号として使用する要素のロケール固有のシーケンス。

### <a name="example"></a>例

[curr_symbol](#curr_symbol) の例 (仮想メンバー関数が `curr_symbol` で呼び出される) を参照してください。

## <a name="moneypunctdo_decimal_point"></a><a name="do_decimal_point"></a>マネープンク::do_小数点

小数点記号として使用する要素のロケール固有のシーケンスを返すプロテクト仮想メンバー関数。

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>戻り値

小数点記号として使用する要素のロケール固有のシーケンス。

### <a name="example"></a>例

[decimal_point](#decimal_point) の例 (仮想メンバー関数が `decimal_point` で呼び出される) を参照してください。

## <a name="moneypunctdo_frac_digits"></a><a name="do_frac_digits"></a>マネープンク::do_frac_digits

小数点の右側に表示する桁数のロケール固有の数を返すプロテクト仮想メンバー関数。

```cpp
virtual int do_frac_digits() const;
```

### <a name="return-value"></a>戻り値

小数点の右側に表示する桁数のロケール固有の数。

### <a name="example"></a>例

[frac_digits](#frac_digits) の例 (仮想メンバー関数が `frac_digits` で呼び出される) を参照してください。

## <a name="moneypunctdo_grouping"></a><a name="do_grouping"></a>マネープンク::do_グループ化

小数点の左側の数字をグループ化する方法を決定するロケール固有の規則を返すプロテクト仮想メンバー関数。

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>戻り値

小数点の左側の数字をグループ化する方法を決定するロケール固有の規則。

### <a name="example"></a>例

仮想メンバー関数が[grouping](#grouping)によって`grouping`呼び出される grouping の例を参照してください。

## <a name="moneypunctdo_neg_format"></a><a name="do_neg_format"></a>マネープンク::do_neg_format

負の値の出力を書式設定するためのロケール固有の規則を返すために呼び出されるプロテクト仮想メンバー関数。

```cpp
virtual pattern do_neg_format() const;
```

### <a name="return-value"></a>戻り値

このプロテクト仮想メンバー関数は、負の値の通貨出力フィールドを生成する方法を決定する、ロケール固有の規則を返します。 の 4 つの要素`pattern::field`のそれぞれは、値を持つことができます。

- `none`0 個以上のスペースを一致させるか、何も生成しない場合。

- `sign`をクリックして、正または負の符号を一致または生成します。

- `space`0 個以上のスペースを一致させるか、スペースを生成します。

- `symbol`をクリックして通貨記号を照合または生成します。

- `value`を使用して、通貨値を照合または生成します。

通貨出力フィールドのコンポーネントが生成され、通貨入力フィールドのコンポーネントが、 でこれらの要素が出現する順序で`pattern::field`照合されます。 値`sign`、 `symbol`、、、`value`および 、`none`いずれか`space`一方が 1 回だけ出現する必要があります。 値`none`を最初に指定することはできません。 値 space を最初または最後に出現させることは**できません**。 true`Intl`の場合、順序は`symbol`、 `sign` `none`、、`value`その後、 になります。

`moneypunct` のテンプレート バージョン \< **CharType**, **Intl**> は、`{`**money_base::symbol**、**money_base::sign**、**money_base::value**、**money_base::none**`}` を返します。

### <a name="example"></a>例

[neg_format](#neg_format) の例 (仮想メンバー関数が `neg_format` で呼び出される) を参照してください。

## <a name="moneypunctdo_negative_sign"></a><a name="do_negative_sign"></a>マネープンク::do_負の符号

負の記号として使用する要素のロケール固有のシーケンスを返すために呼び出されるプロテクト仮想メンバー関数。

```cpp
virtual string_type do_negative_sign() const;
```

### <a name="return-value"></a>戻り値

負の記号として使用する要素のロケール固有のシーケンス。

### <a name="example"></a>例

[negative_sign](#negative_sign) の例 (仮想メンバー関数が `negative_sign` で呼び出される) を参照してください。

## <a name="moneypunctdo_pos_format"></a><a name="do_pos_format"></a>マネープンク::do_pos_フォーマット

正の値の出力を書式設定するためのロケール固有の規則を返すために呼び出されるプロテクト仮想メンバー関数。

```cpp
virtual pattern do_pos_format() const;
```

### <a name="return-value"></a>戻り値

このプロテクト仮想メンバー関数は、正の値の通貨出力フィールドを生成する方法を決定する、ロケール固有の規則を返します。 (また、通貨入力フィールドのコンポーネントを照合する方法も決定します)。エンコードは[、do_neg_format](#do_neg_format)の場合と同じです。

moneypunct のテンプレート バージョン \< **CharType**, **Inputlterator**> は、`{`**money_base::symbol**, **money_base::sign**, **money_base::value**, **money_base::none**`}` を返します。

### <a name="example"></a>例

[pos_format](#pos_format) の例 (仮想メンバー関数が `pos_format` で呼び出される) を参照してください。

## <a name="moneypunctdo_positive_sign"></a><a name="do_positive_sign"></a>マネープンク::do_positive_sign

正の記号として使用する要素のロケール固有のシーケンスを返すプロテクト仮想メンバー関数。

```cpp
virtual string_type do_positive_sign() const;
```

### <a name="return-value"></a>戻り値

正の記号として使用する要素のロケール固有のシーケンス。

### <a name="example"></a>例

[positive_sign](#positive_sign) の例 (仮想メンバー関数が `positive_sign` で呼び出される) を参照してください。

## <a name="moneypunctdo_thousands_sep"></a><a name="do_thousands_sep"></a>マネープンク::do_千_9月

小数点の左側の桁区切り記号として使用するロケール固有の要素を返すプロテクト仮想メンバー関数。

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>戻り値

小数点の左側の桁区切り記号として使用するロケール固有の要素。

### <a name="example"></a>例

[thousands_sep](#thousands_sep) の例 (仮想メンバー関数が `thousands_sep` で呼び出される) を参照してください。

## <a name="moneypunctfrac_digits"></a><a name="frac_digits"></a>マネープンク::frac_digits

小数点の右側に表示する桁数のロケール固有の数を返します。

```cpp
int frac_digits() const;
```

### <a name="return-value"></a>戻り値

小数点の右側に表示する桁数のロケール固有の数。

### <a name="remarks"></a>解説

このメンバー関数は、[do_frac_digits](#do_frac_digits) を返します。

### <a name="example"></a>例

```cpp
// moneypunct_frac_digits.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >(loc);
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >(loc);
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="moneypunctgrouping"></a><a name="grouping"></a>マネープンクスト::グループ化

小数点の左側の数字をグループ化する方法を決定するロケール固有の規則を返します。

```cpp
string grouping() const;
```

### <a name="return-value"></a>戻り値

小数点の左側の数字をグループ化する方法を決定するロケール固有の規則。

### <a name="remarks"></a>解説

このメンバー関数は、[do_grouping](#do_grouping) を返します。

### <a name="example"></a>例

```cpp
// moneypunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >( loc );
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >( loc );
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="moneypunctmoneypunct"></a><a name="moneypunct"></a>マネープンク::マネープンク

`moneypunct` 型のオブジェクトのコンストラクター。

```cpp
explicit moneypunct(size_t _Refs = 0);
```

### <a name="parameters"></a>パラメーター

*_Refs*\
オブジェクトのメモリ管理の種類を指定するために使用する整数値。

### <a name="remarks"></a>解説

*_Refs*パラメータとその有意性の値は次のとおりです。

- 0: オブジェクトの有効期間はそれが含まれるロケールによって管理されます。

- 1: オブジェクトの有効期間を手動で管理する必要があります。

- \>1: これらの値は定義されていません。

デストラクターが保護されているため、利用できる直接的な例はありません。

コンストラクターは、[locale::facet](../standard-library/locale-class.md#facet_class)(_ *Refs*) を使用して、その基本オブジェクトを初期化します。

## <a name="moneypunctneg_format"></a><a name="neg_format"></a>マネープンク::neg_format

負の値の出力を書式設定するためのロケール固有の規則を返します。

```cpp
pattern neg_format() const;
```

### <a name="return-value"></a>戻り値

負の値の出力を書式設定するためのロケール固有の規則。

### <a name="remarks"></a>解説

このメンバー関数は、[do_neg_format](#do_neg_format) を返します。

### <a name="example"></a>例

```cpp
// moneypunct_neg_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( ) {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international negative number format: "
        << mpunct.neg_format( ).field[0]
        << mpunct.neg_format( ).field[1]
        << mpunct.neg_format( ).field[2]
        << mpunct.neg_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative number format: "
        << mpunct2.neg_format( ).field[0]
        << mpunct2.neg_format( ).field[1]
        << mpunct2.neg_format( ).field[2]
        << mpunct2.neg_format( ).field[3] << endl;
}
```

## <a name="moneypunctnegative_sign"></a><a name="negative_sign"></a>マネープンク::negative_sign

負の記号として使用する要素のロケール固有のシーケンスを返します。

```cpp
string_type negative_sign() const;
```

### <a name="return-value"></a>戻り値

負の記号として使用する要素のロケール固有のシーケンスを返します。

### <a name="remarks"></a>解説

このメンバー関数は、[do_negative_sign](#do_negative_sign) を返します。

### <a name="example"></a>例

```cpp
// moneypunct_neg_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international negative sign: "
        << mpunct.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative sign: "
        << mpunct2.negative_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international negative sign: "
        << mpunct3.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic negative sign: "
        << mpunct4.negative_sign( ) << endl;
};
```

```Output
German_Germany.1252 international negative sign: -
German_Germany.1252 domestic negative sign: -
French_France.1252 international negative sign: -
French_France.1252 domestic negative sign: -
```

## <a name="moneypunctpos_format"></a><a name="pos_format"></a>マネープンク::pos_フォーマット

正の値の出力を書式設定するためのロケール固有の規則を返します。

```cpp
pattern pos_format() const;
```

### <a name="return-value"></a>戻り値

正の値の出力を書式設定するためのロケール固有の規則。

### <a name="remarks"></a>解説

このメンバー関数は、[do_pos_format](#do_pos_format) を返します。

### <a name="example"></a>例

```cpp
// moneypunct_pos_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main() {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international positive number format: "
        << mpunct.pos_format( ).field[0]
        << mpunct.pos_format( ).field[1]
        << mpunct.pos_format( ).field[2]
        << mpunct.pos_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive number format: "
        << mpunct2.pos_format( ).field[0]
        << mpunct2.pos_format( ).field[1]
        << mpunct2.pos_format( ).field[2]
        << mpunct2.pos_format( ).field[3] << endl;
}
```

## <a name="moneypunctpositive_sign"></a><a name="positive_sign"></a>マネープンク::pオシティブ_サイン

正の記号として使用する要素のロケール固有のシーケンスを返します。

```cpp
string_type positive_sign() const;
```

### <a name="return-value"></a>戻り値

正の記号として使用する要素のロケール固有のシーケンス。

### <a name="remarks"></a>解説

このメンバー関数は、[do_positive_sign](#do_positive_sign) を返します。

### <a name="example"></a>例

```cpp
// moneypunct_pos_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international positive sign:"
        << mpunct.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive sign:"
        << mpunct2.positive_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international positive sign:"
        << mpunct3.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic positive sign:"
        << mpunct4.positive_sign( ) << endl;
};
```

```Output
German_Germany.1252 international positive sign:
German_Germany.1252 domestic positive sign:
French_France.1252 international positive sign:
French_France.1252 domestic positive sign:
```

## <a name="moneypunctstring_type"></a><a name="string_type"></a>マネープンク::string_type

**CharType** 型の文字を格納する文字列を表す型。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>解説

この型は、句読点シーケンスのコピーを格納できるオブジェクトを持つクラス テンプレート[basic_string](../standard-library/basic-string-class.md)の特殊化を表します。

## <a name="moneypunctthousands_sep"></a><a name="thousands_sep"></a>マネープンク::thousands_sep

桁区切り記号として使用する要素のロケール固有のシーケンスを返します。

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>戻り値

桁区切り記号として使用する要素のロケール固有のシーケンス。

### <a name="remarks"></a>解説

このメンバー関数は、[do_thousands_sep](#do_thousands_sep) を返します。

### <a name="example"></a>例

```cpp
// moneypunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international thousands separator: "
        << mpunct.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic thousands separator: "
        << mpunct2.thousands_sep( ) << endl << endl;

   locale loc2( "english_canada" );

   const moneypunct <char, true> &mpunct3 =
       use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international thousands separator: "
        << mpunct3.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic thousands separator: "
        << mpunct4.thousands_sep( ) << endl;
}
```

```Output
German_Germany.1252 international thousands separator: .
German_Germany.1252 domestic thousands separator: .

English_Canada.1252 international thousands separator: ,
English_Canada.1252 domestic thousands separator: ,
```

## <a name="see-also"></a>関連項目

[\<ロケール>](../standard-library/locale.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
