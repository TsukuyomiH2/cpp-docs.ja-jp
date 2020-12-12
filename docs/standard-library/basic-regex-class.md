---
description: '詳細情報: basic_regex クラス'
title: basic_regex クラス
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 450f3945faeb088c975bb1657d69496bcf078ccd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325627"
---
# <a name="basic_regex-class"></a>basic_regex クラス

正規表現をラップします。

## <a name="syntax"></a>構文

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>パラメーター

*Elem*\
一致させる要素の型。

*RXtraits*\
要素の特徴 (traits) クラス。

## <a name="remarks"></a>解説

クラステンプレートは、正規表現を保持するオブジェクトを表します。 このクラステンプレートのオブジェクトは、正規表現に一致するテキストを検索するために、適切なテキスト文字列引数と共に、テンプレート関数 [regex_match](../standard-library/regex-functions.md#regex_match)、 [regex_search](../standard-library/regex-functions.md#regex_search)、および [regex_replace](../standard-library/regex-functions.md#regex_replace)に渡すことができます。 このクラステンプレートの特殊化は2つあり、型の要素の型定義 [regex](../standard-library/regex-typedefs.md#regex) **`char`** と型の要素の [wregex](../standard-library/regex-typedefs.md#wregex) を使用し **`wchar_t`** ます。

テンプレート引数 *RXtraits* は、クラステンプレートがサポートする正規表現の構文のさまざまな重要なプロパティについて説明します。 これらの正規表現の特徴を指定するクラスは、 [Regex_traits クラス](../standard-library/regex-traits-class.md)型のオブジェクトと同じ外部インターフェイスを持つ必要があります。

一部の関数は、正規表現を定義するオペランド シーケンスを受け取ります。 その場合、オペランド シーケンスは次のような方法で指定できます。

`ptr` : (null ポインターではない) から始まる、null で終わるシーケンス (型の *Elem* の場合は C 文字列など **`char`** )。 `ptr` 終端の要素は値であり、 `value_type()` オペランドシーケンスの一部ではありません

`ptr`、`count` : `count` (null ポインター以外) で始まる `ptr` 個の要素のシーケンスとして。

`str` : `basic_string` オブジェクト `str` によって指定されたシーケンスとして。

`first`、`last` : `first` と `last` の 2 つの反復子で区切られた範囲 `[first, last)` 内の要素のシーケンスとして。

`right` : `basic_regex` オブジェクト `right` として。

これらのメンバー関数は、 `flags` *RXtraits* 型で記述されているものに加えて、正規表現の解釈に関するさまざまなオプションを指定する引数も受け取ります。

### <a name="members"></a>メンバー

|メンバー|既定値|
|-|-|
|public static const flag_type icase|regex_constants:: icase|
|public static const flag_type nosubs|regex_constants:: nosubs|
|public static const flag_type optimize|regex_constants:: optimize|
|パブリック static const flag_type collate|regex_constants:: collate|
|ECMAScript の public static const flag_type|regex_constants:: ECMAScript|
|public static const flag_type basic|regex_constants:: basic|
|パブリック static const flag_type 拡張|regex_constants:: extended|
|public static const flag_type awk|regex_constants:: awk|
|public static const flag_type grep|regex_constants:: grep|
|public static const flag_type egrep|regex_constants:: egrep|
|プライベート RXtraits の特徴||

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[basic_regex](#basic_regex)|正規表現オブジェクトを構築します。|

### <a name="typedefs"></a>Typedefs

|型名|説明|
|-|-|
|[flag_type](#flag_type)|構文オプション フラグの型です。|
|[locale_type](#locale_type)|格納されているロケール オブジェクトの型。|
|[value_type](#value_type)|要素型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[assign](#assign)|値を正規表現オブジェクトに代入します。|
|[flags](#flags)|構文のオプション フラグを返します。|
|[getloc](#getloc)|格納されているロケール オブジェクトを返します。|
|[imbue](#imbue)|格納されているロケール オブジェクトを変更します。|
|[mark_count](#mark_count)|一致した部分式の数を返します。|
|[スワップ](#swap)|2 つの正規表現オブジェクトを交換します。|

### <a name="operators"></a>オペレーター

|演算子|説明|
|-|-|
|[operator =](#op_eq)|値を正規表現オブジェクトに代入します。|

## <a name="requirements"></a>要件

**ヘッダー:**\<regex>

**名前空間:** std

## <a name="example"></a>例

```cpp
// std__regex__basic_regex.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    regex::value_type elem = 'x';
    regex::flag_type flag = regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

    // constructors
    regex rx0;
    cout << "match(\"abc\", \"\") == " << boolalpha
        << regex_match("abc", rx0) << endl;

    regex rx1("abcd", regex::ECMAScript);
    cout << "match(\"abc\", \"abcd\") == " << boolalpha
        << regex_match("abc", rx1) << endl;

    regex rx2("abcd", 3);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx2) << endl;

    regex rx3(rx2);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx3) << endl;

    string str("abcd");
    regex rx4(str);
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx4) << endl;

    regex rx5(str.begin(), str.end() - 1);
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx5) << endl;
    cout << endl;

    // assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

    // mark_count
    cout << "\"abc\" mark_count == "
        << regex("abc").mark_count() << endl;
    cout << "\"(abc)\" mark_count == "
        << regex("(abc)").mark_count() << endl;

    // locales
    regex::locale_type loc = rx0.imbue(locale());
    cout << "getloc == imbued == " << boolalpha
        << (loc == rx0.getloc()) << endl;

    // initializer_list
    regex rx6({ 'a', 'b', 'c' }, regex::ECMAScript);
    cout << "match(\"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}
```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
match("abc") == true
```

## <a name="basic_regexassign"></a><a name="assign"></a> basic_regex:: assign

値を正規表現オブジェクトに代入します。

```cpp
basic_regex& assign(
    const basic_regex& right);

basic_regex& assign(
    const Elem* ptr,
    flag_type flags = ECMAScript);

basic_regex& assign(
    const Elem* ptr,
    size_type len,
    flag_type flags = ECMAScript);

basic_regex& assign(
    initializer_list<_Elem> IList,
    flag_type flags = regex_constants::ECMAScript);

template <class STtraits, class STalloc>
basic_regex& assign(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags = ECMAScript);

template <class InIt>
basic_regex& assign(
    InIt first, InIt last,
    flag_type flags = ECMAScript);
```

### <a name="parameters"></a>パラメーター

*STtraits*\
文字列ソースの特徴 (traits) クラス。

*STalloc*\
文字列ソースのアロケーター クラス。

*初期化*\
範囲ソースの入力反復子の型。

*そうです*\
コピーする Regex ソース。

*ポインター*\
コピーするシーケンスの先頭を指すポインター。

*示す*\
コピー中に追加する構文オプション フラグ。

*len/TD>*\
コピーするシーケンスの長さ。

*引数*\
コピーする文字列。

*まずは*\
コピーするシーケンスの最初。

*前の*\
コピーするシーケンスの最後。

*IList*\
コピーする initializer_list。

### <a name="remarks"></a>解説

各メンバー関数は、によって保持されている正規表現を、 **`*this`** オペランドシーケンスで記述された正規表現に置き換えてから、を返し **`*this`** ます。

## <a name="basic_regexbasic_regex"></a><a name="basic_regex"></a> basic_regex:: basic_regex

正規表現オブジェクトを構築します。

```cpp
basic_regex();

explicit basic_regex(
    const Elem* ptr,
    flag_type flags);

explicit basic_regex(
    const Elem* ptr,
    size_type len,
    flag_type flags);

basic_regex(
    const basic_regex& right);

basic_regex(
    initializer_list<Type> IList,
    flag_type flags);

template <class STtraits, class STalloc>
explicit basic_regex(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags);

template <class InIt>
explicit basic_regex(
    InIt first,
    InIt last,
    flag_type flags);
```

### <a name="parameters"></a>パラメーター

*STtraits*\
文字列ソースの特徴 (traits) クラス。

*STalloc*\
文字列ソースのアロケーター クラス。

*初期化*\
範囲ソースの入力反復子の型。

*そうです*\
コピーする Regex ソース。

*ポインター*\
コピーするシーケンスの先頭を指すポインター。

*示す*\
コピー中に追加する構文オプション フラグ。

*len/TD>*\
コピーするシーケンスの長さ。

*引数*\
コピーする文字列。

*まずは*\
コピーするシーケンスの最初。

*前の*\
コピーするシーケンスの最後。

*IList*\
コピーする initializer_list。

### <a name="remarks"></a>解説

すべてのコンストラクターは、既定で構築される、`RXtraits` 型のオブジェクトを格納します。

1 つ目のコンストラクターは、空の `basic_regex` オブジェクトを構築します。 それ以外のコンストラクターは、オペランド シーケンスで記述された正規表現を保持する `basic_regex` オブジェクトを構築します。

空 `basic_regex` のオブジェクトは、 [regex_match](../standard-library/regex-functions.md#regex_match)、 [regex_search](../standard-library/regex-functions.md#regex_search)、または [regex_replace](../standard-library/regex-functions.md#regex_replace)に渡されたときに、どの文字シーケンスとも一致しません。

## <a name="basic_regexflag_type"></a><a name="flag_type"></a> basic_regex:: flag_type

構文オプション フラグの型です。

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>解説

この型は [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type)のシノニムです。

## <a name="basic_regexflags"></a><a name="flags"></a> basic_regex:: flags

構文のオプション フラグを返します。

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>解説

このメンバー関数は、[basic_regex::assign](#assign) メンバー関数のうち直前に呼び出された関数に渡された `flag_type` 引数の値を返します。これに当たる呼び出しが行われていなかった場合は、コンストラクターに渡した値が返されます。

## <a name="basic_regexgetloc"></a><a name="getloc"></a> basic_regex:: getloc

格納されているロケール オブジェクトを返します。

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>解説

このメンバー関数は `traits.` [regex_traits:: getloc](../standard-library/regex-traits-class.md#getloc)を返し `()` ます。

## <a name="basic_regeximbue"></a><a name="imbue"></a> basic_regex:: imbue

格納されているロケール オブジェクトを変更します。

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>パラメーター

*loc*\
格納するロケール オブジェクト。

### <a name="remarks"></a>解説

このメンバー関数は、を空に **`*this`** して `traits.` [regex_traits:: imbue](../standard-library/regex-traits-class.md#imbue)を返し `(loc)` ます。

## <a name="basic_regexlocale_type"></a><a name="locale_type"></a> basic_regex:: locale_type

格納されているロケール オブジェクトの型。

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>解説

この型は [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type)のシノニムです。

## <a name="basic_regexmark_count"></a><a name="mark_count"></a> basic_regex:: mark_count

一致した部分式の数を返します。

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>解説

メンバー関数は、正規表現のキャプチャ グループの数を返します。

## <a name="basic_regexoperator"></a><a name="op_eq"></a> basic_regex:: operator =

値を正規表現オブジェクトに代入します。

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>パラメーター

*STtraits*\
文字列ソースの特徴 (traits) クラス。

*STalloc*\
文字列ソースのアロケーター クラス。

*そうです*\
コピーする Regex ソース。

*引数*\
コピーする文字列。

### <a name="remarks"></a>解説

それぞれの演算子は、によって保持されている正規表現を、 **`*this`** オペランドシーケンスで記述された正規表現に置き換えてから、を返し **`*this`** ます。

## <a name="basic_regexswap"></a><a name="swap"></a> basic_regex:: swap

2 つの正規表現オブジェクトを交換します。

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>パラメーター

*そうです*\
交換する正規表現オブジェクト。

### <a name="remarks"></a>解説

このメンバー関数は、との間で正規表現を交換し **`*this`** ます。  一定時間に実行し、例外をスローしません。

## <a name="basic_regexvalue_type"></a><a name="value_type"></a> basic_regex:: value_type

要素型。

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>解説

この型は、テンプレートパラメーター *Elem* のシノニムです。

## <a name="see-also"></a>関連項目

[\<regex>](../standard-library/regex.md)\
[regex_match](../standard-library/regex-functions.md#regex_match)\
[regex_search](../standard-library/regex-functions.md#regex_search)\
[regex_replace](../standard-library/regex-functions.md#regex_replace)\
[regex](../standard-library/regex-typedefs.md#regex)\
[wregex](../standard-library/regex-typedefs.md#wregex)\
[regex_traits クラス](../standard-library/regex-traits-class.md)
