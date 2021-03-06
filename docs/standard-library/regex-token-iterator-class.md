---
title: regex_token_iterator クラス
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_token_iterator
- regex/std::regex_token_iterator::regex_type
- regex/std::regex_token_iterator::value_type
- regex/std::regex_token_iterator::iterator_category
- regex/std::regex_token_iterator::difference_type
- regex/std::regex_token_iterator::pointer
- regex/std::regex_token_iterator::reference
- regex/std::regex_token_iterator::operator==
- regex/std::regex_token_iterator::operator!=
- regex/std::regex_token_iterator::operator*
- regex/std::regex_token_iterator::operator->
- regex/std::regex_token_iterator::operator++
helpviewer_keywords:
- std::regex_token_iterator [C++]
- std::regex_token_iterator [C++], regex_type
- std::regex_token_iterator [C++], value_type
- std::regex_token_iterator [C++], iterator_category
- std::regex_token_iterator [C++], difference_type
- std::regex_token_iterator [C++], pointer
- std::regex_token_iterator [C++], reference
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
ms.openlocfilehash: 5ada2ad69cbcac15e09968045e54095dfb2623d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366397"
---
# <a name="regex_token_iterator-class"></a>regex_token_iterator クラス

サブマッチ用の反復子クラス。

## <a name="syntax"></a>構文

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator
```

## <a name="parameters"></a>パラメーター

*ビッドイット*\
サブマッチ用の反復子の型。

*Elem*\
一致させる要素の型。

*ラックストレイツ*\
要素の特徴 (traits) クラス。

## <a name="remarks"></a>解説

クラス テンプレートは、定数の前方反復オブジェクトを記述します。 概念的には、文字シーケンスで正規表現と一致するものを検索するために使用される `regex_iterator` オブジェクトを保持します。 また、正規表現の一致ごとに、格納されているベクター `sub_match<BidIt>` 内のインデックス値で識別されるサブマッチを表す `subs` 型のオブジェクトを抽出します。

-1 のインデックス値は、前回の正規表現の一致の直後から始まる文字シーケンスまたは前回の正規表現の一致が存在しなかった場合の文字シーケンスの先頭から始まって現在の正規表現の一致の最初の文字の直前まで続く、または、現在の一致が存在しない場合の文字シーケンスの最後まで続く文字シーケンスを指定します。 その他のインデックス値 `idx` は、 `it.match[idx]`に保持されているキャプチャ グループの内容を指定します。

### <a name="members"></a>メンバー

|メンバー|Default value|
|-|-|
|`private regex_iterator<BidIt, Elem, RXtraits> it`||
|`private vector<int> subs`||
|`private int pos`||

### <a name="constructors"></a>コンストラクター

|Constructor|説明|
|-|-|
|[regex_token_iterator](#regex_token_iterator)|反復子を構築します。|

### <a name="typedefs"></a>Typedefs

|種類の名前。|説明|
|-|-|
|[difference_type](#difference_type)|反復子の差の型です。|
|[iterator_category](#iterator_category)|反復子カテゴリの型。|
|[ポインター (pointer)](#pointer)|一致へのポインターの型です。|
|[参照](#reference)|サブマッチへの参照の型です。|
|[regex_type](#regex_type)|一致させる正規表現の型。|
|[Value_type](#value_type)|サブマッチの型。|

### <a name="operators"></a>オペレーター

|演算子|説明|
|-|-|
|[演算子!=](#op_neq)|反復子の非等値を比較します。|
|[演算子*](#op_star)|指定されたサブマッチにアクセスします。|
|[演算子++](#op_add_add)|反復子をインクリメントします。|
|[演算子==](#op_eq_eq)|反復子が等しいかどうかを比較します。|
|[オペレーター->](#op_arrow)|指定されたサブマッチにアクセスします。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<regex>

**名前空間:** std

## <a name="example"></a>例

```cpp
#include <regex>
#include <iostream>

typedef std::regex_token_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "aaxaayaaz";
    Myiter::regex_type rx("(a)a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

// show whole match
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefix before match
    next = Myiter(pat, pat + strlen(pat), rx, -1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show (a) submatch only
    next = Myiter(pat, pat + strlen(pat), rx, 1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and submatches
    std::vector<int> vec;
    vec.push_back(-1);
    vec.push_back(1);
    next = Myiter(pat, pat + strlen(pat), rx, vec);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and whole matches
    int arr[] = {-1, 0};
    next = Myiter(pat, pat + strlen(pat), rx, arr);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// other members
    Myiter it1(pat, pat + strlen(pat), rx);
    Myiter it2(it1);
    next = it1;

    Myiter::iterator_category cat = std::forward_iterator_tag();
    Myiter::difference_type dif = -3;
    Myiter::value_type mr = *it1;
    Myiter::reference ref = mr;
    Myiter::pointer ptr = &ref;

    dif = dif; // to quiet "unused" warnings
    ptr = ptr;

    return (0);
    }
```

```Output
match == aa
match == aa
match == aa

match ==
match == x
match == y
match == z

match == a
match == a
match == a

match ==
match == a
match == x
match == a
match == y
match == a
match == z

match ==
match == aa
match == x
match == aa
match == y
match == aa
match == z
```

## <a name="regex_token_iteratordifference_type"></a><a name="difference_type"></a>regex_token_iterator::difference_type

反復子の差の型です。

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>解説

この型は `std::ptrdiff_t` の同意語です。

## <a name="regex_token_iteratoriterator_category"></a><a name="iterator_category"></a>regex_token_iterator::iterator_category

反復子カテゴリの型。

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>解説

この型は `std::forward_iterator_tag` の同意語です。

## <a name="regex_token_iteratoroperator"></a><a name="op_neq"></a>regex_token_iterator::演算子!=

反復子の非等値を比較します。

```cpp
bool operator!=(const regex_token_iterator& right);
```

### <a name="parameters"></a>パラメーター

*そうです*\
比較する反復子。

### <a name="remarks"></a>解説

このメンバー関数は、`!(*this == right)` を返します。

## <a name="regex_token_iteratoroperator"></a><a name="op_star"></a>regex_token_iterator::演算子*

指定されたサブマッチにアクセスします。

```cpp
const sub_match<BidIt>& operator*();
```

### <a name="remarks"></a>解説

このメンバー関数は、インデックス値 `sub_match<BidIt>` で識別されるキャプチャ グループを表す `subs[pos]` オブジェクトを返します。

## <a name="regex_token_iteratoroperator"></a><a name="op_add_add"></a>regex_token_iterator::演算子++

反復子をインクリメントします。

```cpp
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```

### <a name="remarks"></a>解説

格納された反復子 `it` が、シーケンス末尾の反復子の場合、最初の演算子は、格納された値 `pos` を `subs.size()` の値に設定します (シーケンス末尾の反復子にするため)。 それ以外の場合、格納された値 `pos` をインクリメントします。結果が値 `subs.size()` に等しい場合は、格納された値 `pos` をゼロに設定し、格納された反復子 `it` をインクリメントします。 格納された反復子をインクリメントしてもシーケンス末尾の反復子と等しくならない場合、演算子はそれ以上何もしません。 それ以外の場合で、前の一致の末尾が文字シーケンスの末尾にある場合は、`pos` の格納された値を `subs.size()` に設定します。 それ以外の場合は、格納された値 `pos` を、`pos == subs.size()` または `subs[pos] == -1` になるまで繰り返しインクリメントします (インデックス値のいずれかが -1 の場合、反復子の次の逆参照で文字シーケンスの末尾が返されるようにします)。 すべての場合に、演算子はオブジェクトを返します。

2 つ目の演算子は、オブジェクトのコピーを作成して、オブジェクトをインクリメントしてから、そのコピーを返します。

## <a name="regex_token_iteratoroperator"></a><a name="op_eq_eq"></a>regex_token_iterator::演算子==

反復子が等しいかどうかを比較します。

```cpp
bool operator==(const regex_token_iterator& right);
```

### <a name="parameters"></a>パラメーター

*そうです*\
比較する反復子。

### <a name="remarks"></a>解説

このメンバー関数は、`it == right.it && subs == right.subs && pos == right.pos` を返します。

## <a name="regex_token_iteratoroperator-gt"></a><a name="op_arrow"></a>regex_token_iterator::演算子-&gt;

指定されたサブマッチにアクセスします。

```cpp
const sub_match<BidIt> * operator->();
```

### <a name="remarks"></a>解説

このメンバー関数は、インデックス値 `sub_match<BidIt>` で識別されるキャプチャ グループを表す `subs[pos]` オブジェクトのポインタを返します。

## <a name="regex_token_iteratorpointer"></a><a name="pointer"></a>regex_token_iterator::pオインター

一致へのポインターの型です。

```cpp
typedef sub_match<BidIt> *pointer;
```

### <a name="remarks"></a>解説

この型は `sub_match<BidIt>*`のシノニムです。ここで `BidIt` はテンプレート パラメーターです。

## <a name="regex_token_iteratorreference"></a><a name="reference"></a>regex_token_iterator::参照

サブマッチへの参照の型です。

```cpp
typedef sub_match<BidIt>& reference;
```

### <a name="remarks"></a>解説

この型は `sub_match<BidIt>&`のシノニムです。ここで `BidIt` はテンプレート パラメーターです。

## <a name="regex_token_iteratorregex_token_iterator"></a><a name="regex_token_iterator"></a>regex_token_iterator::regex_token_iterator

反復子を構築します。

```cpp
regex_token_iterator();

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, int submatch = 0,
    regex_constants::match_flag_type f = regex_constants::match_default);

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const vector<int> submatches,
    regex_constants::match_flag_type f = regex_constants::match_default);

template <std::size_t N>
regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const int (&submatches)[N],
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>パラメーター

*まずは*\
一致させるシーケンスの先頭。

*前の*\
一致させるシーケンスの末尾。

*再*\
照合する正規表現。

*F*\
一致のフラグ。

### <a name="remarks"></a>解説

1 つ目のコンストラクターは、シーケンス末尾の反復子を構築します。

2 つ目のコンストラクターは、格納されている反復子 `it` が `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`に初期化され、格納されているベクター `subs` が値 `submatch`を含む正確に 1 つの整数を保持し、格納されている値 `pos` が 0 のオブジェクトを構築します。 メモ: 生成されたオブジェクトは、正規表現が一致するたびに、インデックス値 `submatch` によって識別されるサブマッチを抽出します。

3 つ目のコンストラクターは、格納されている反復子 `it` が `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`に初期化され、格納されているベクター `subs` がコンストラクター引数 `submatches`のコピーを保持し、格納されている値 `pos` が 0 のオブジェクトを構築します。

4 つ目のコンストラクターは、格納されている反復子 `it` が `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`に初期化され、格納されているベクター `subs` がコンストラクター引数 `N` によって示される `submatches`の値を保持し、格納されている値 `pos` が 0 のオブジェクトを構築します。

## <a name="regex_token_iteratorregex_type"></a><a name="regex_type"></a>regex_token_iterator::regex_type

一致させる正規表現の型。

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>解説

typedef は、`basic_regex<Elem, RXtraits>` の同意語です。

## <a name="regex_token_iteratorvalue_type"></a><a name="value_type"></a>regex_token_iterator::value_type

サブマッチの型。

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>解説

この型は `sub_match<BidIt>`のシノニムです。ここで `BidIt` はテンプレート パラメーターです。

## <a name="see-also"></a>関連項目

[\<正規表現>](../standard-library/regex.md)\
[regex_constantsクラス](../standard-library/regex-constants-class.md)\
[regex_errorクラス](../standard-library/regex-error-class.md)\
[\<正規表現>関数](../standard-library/regex-functions.md)\
[regex_iteratorクラス](../standard-library/regex-iterator-class.md)\
[\<正規表現>演算子](../standard-library/regex-operators.md)\
[regex_traitsクラス](../standard-library/regex-traits-class.md)\
[\<正規表現>のタイプ定義](../standard-library/regex-typedefs.md)
