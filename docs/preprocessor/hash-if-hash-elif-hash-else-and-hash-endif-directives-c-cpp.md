---
description: '詳細については、「#if、#elif、#else、および #endif ディレクティブ (C/c + +)」を参照してください。'
title: '#if、#elif、#else、および #endif ディレクティブ (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
helpviewer_keywords:
- '#elif directive'
- conditional compilation, directives
- endif directive (#endif)
- preprocessor, directives
- '#else directive'
- '#endif directive'
- if directive (#if)
- else directive (#else)
- '#if directive'
- elif directive (#elif)
- defined directive
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
ms.openlocfilehash: 511f79da4957f7a26c9af9dbcad46fc29e70d785
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300483"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if、#elif、#else、および #endif ディレクティブ (C/c + +)

**#If** ディレクティブは、 **#elif**、 **#else**、および **#endif** ディレクティブを使用して、ソースファイルの一部のコンパイルを制御します。 ( **#If** の後に) 記述する式が0以外の値を持つ場合、 **#if** ディレクティブの直後の行グループが翻訳単位に保持されます。

## <a name="grammar"></a>文法

*条件* : \
&nbsp;&nbsp;&nbsp;&nbsp;*if-parts elif-* part <sub>opt</sub> <sub></sub> *endif-line*

*if-part* : \
&nbsp;&nbsp;&nbsp;&nbsp;*行のテキスト*

*改行* : \
&nbsp;&nbsp;&nbsp;&nbsp;**#if** *定数式*\
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef** *識別子*\
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef** *識別子*

*elif-parts* : \
&nbsp;&nbsp;&nbsp;&nbsp;*elif 行のテキスト*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif-部分テキスト*

*elif 行* : \
&nbsp;&nbsp;&nbsp;&nbsp;**#elif**  *定数式*

*else-パート* : \
&nbsp;&nbsp;&nbsp;&nbsp;*他の行のテキスト*

*他の行* : \
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*endif-行* : \
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

## <a name="remarks"></a>解説

ソースファイル内の各 **#if** ディレクティブは、終了 **#endif** ディレクティブで一致する必要があります。 **#If** ディレクティブと **#endif** ディレクティブの間には、任意の数の **#elif** ディレクティブを含めることができますが、最大で1つの **#else** ディレクティブを使用できます。 **#Else** ディレクティブ (存在する場合) は、 **#endif** する前に最後のディレクティブである必要があります。

**#If**、 **#elif**、 **#else**、および **#endif** ディレクティブは、他の **#if** ディレクティブの *テキスト* 部分で入れ子にすることができます。 入れ子になった各 **#else**、 **#elif**、または **#endif** ディレクティブは、最も近い前の **#if** ディレクティブに属します。

**#If** や **#ifdef** など、すべての条件付きコンパイルディレクティブは、ファイルの終わりの前にある **#endif** ディレクティブの終わりと一致する必要があります。 それ以外の場合は、エラーメッセージが生成されます。 条件付きコンパイル ディレクティブがインクルード ファイルに含まれている場合も同じ条件を満たす必要があります。つまり、インクルード ファイルの終わりに対になる条件付きコンパイル ディレクティブが必要です。

マクロの置換は、 **#elif** コマンドの後の行の部分で行われるため、 *定数式* でマクロ呼び出しを使用できます。

プリプロセッサは、指定されたいずれかの *テキスト* を選択して、後続の処理を行います。 *テキスト* で指定されたブロックは、任意のテキストシーケンスにすることができます。 複数行にまたがる場合があります。 通常、 *text* はコンパイラまたはプリプロセッサに対して意味のあるプログラムテキストです。

プリプロセッサは、選択された *テキスト* を処理し、コンパイラに渡します。 *テキスト* にプリプロセッサディレクティブが含まれている場合、プリプロセッサはこれらのディレクティブを実行します。 プリプロセッサによって選択されたテキスト ブロックだけがコンパイルされます。

プリプロセッサは、true (0 以外) の定数式が見つかるまで、各 **#if** または **#elif** ディレクティブの後に続く定数式を評価することによって、1つの *テキスト* 項目を選択します。 このメソッド **#** は、関連付けられている **#elif**、 **#else**、または **#endif** まで、すべてのテキスト (で始まる他のプリプロセッサディレクティブを含む) を選択します。

すべての *定数式* が false の場合、または **#elif** ディレクティブがない場合、プリプロセッサは **#else** 句の後にテキストブロックを選択します。 **#Else** 句がなく、 **#if** ブロック内の *定数式* のすべてのインスタンスが false の場合、テキストブロックは選択されません。

*定数式* は、次の追加の制限付き整数定数式です。

- 式には整数型を指定する必要があり、整数定数、文字定数、および **定義され** た演算子のみを含めることができます。

- 式では、 **`sizeof`** または型キャスト演算子を使用できません。

- ターゲット環境は、整数のすべての範囲を表すことができない可能性があります。

- 変換は、型 **`int`** と同じ方法で型を表し **`long`** **`unsigned int`** **`unsigned long`** ます。

- トランスレーターは、ターゲット環境とは別のコード値のセットに文字定数を翻訳できます。 ターゲット環境のプロパティを確認するには、その環境用にビルドされたアプリを使用して、制限の値を確認し *ます。H* マクロ。

- 式は環境に対してクエリを実行することはできません。また、対象のコンピューターで実装の詳細から分離された状態を維持する必要があります。

## <a name="preprocessor-operators"></a>プリプロセッサ演算子

### <a name="defined"></a>定義済み

**定義されている** プリプロセッサ演算子は、次の構文に示すように、特殊な定数式で使用できます。

> **定義済み (** *識別子* **)**\
> **定義済み** *識別子*

*識別子* が現在定義されている場合、この定数式は true (0 以外) と見なされます。 それ以外の場合、条件は False (0) です。 空のテキストとして定義された識別子は、定義されていると見なされます。 **定義** された演算子は、 **#if** と **#elif** ディレクティブでは使用できますが、それ以外は使用できません。

次の例では、 **#if** ディレクティブと **#endif** ディレクティブは、次の3つの関数呼び出しのいずれかのコンパイルを制御します。

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

`credit` の関数呼び出しは、`CREDIT` 識別子が定義されている場合、コンパイルされます。 `DEBIT` 識別子が定義されている場合、`debit` の関数呼び出しがコンパイルされます。 どちらの識別子も定義されていない場合、`printerror` の呼び出しがコンパイルされます。 とはどちらも、 `CREDIT` `credit` c と C++ の異なる識別子であり、ケースは異なっています。

次の例の条件付きコンパイル ステートメントは、`DLEVEL` というシンボリック定数が定義済みとします。

```C
#if DLEVEL > 5
    #define SIGNAL  1
    #if STACKUSE == 1
        #define STACK   200
    #else
        #define STACK   100
    #endif
#else
    #define SIGNAL  0
    #if STACKUSE == 1
        #define STACK   100
    #else
        #define STACK   50
    #endif
#endif
#if DLEVEL == 0
    #define STACK 0
#elif DLEVEL == 1
    #define STACK 100
#elif DLEVEL > 5
    display( debugptr );
#else
    #define STACK 200
#endif
```

最初の **#if** ブロックには、入れ子になった **#if**、 **#else**、および **#endif** ディレクティブの2つのセットが表示されます。 最初のセットのディレクティブは、`DLEVEL > 5` が true の場合にのみ処理されます。 それ以外の場合は、 **#else** 後のステートメントが処理されます。

2番目の例の **#elif** ディレクティブと **#else** ディレクティブは、の値に基づいて4つの選択肢のいずれかを作成するために使用され `DLEVEL` ます。 `STACK` の定義により、定数 `DLEVEL` は 0、100、または 200 に設定されます。 `DLEVEL` が 5 より大きい場合、次のステートメントがコンパイルされます。

```C
#elif DLEVEL > 5
display(debugptr);
```

はコンパイルされ、定義されてい `STACK` ません。

条件付きコンパイルの一般的な用途は、同じヘッダー ファイルの多重インクルードを防ぐことです。 C++ では、多くの場合、クラスがヘッダーファイルで定義されているので、次のようなコンストラクトを使用して複数の定義を防ぐことができます。

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
    //...
};

#endif // !defined( EXAMPLE_H )
```

前のコードは、シンボリック定数 `EXAMPLE_H` が定義されているかどうかを確認します。 その場合、ファイルは既に含まれており、再処理は必要ありません。 定義されていない場合、EXAMPLE.H が処理されてから、`EXAMPLE_H` が処理済みとマークされます。

### <a name="__has_include"></a>__has_include

**Visual Studio 2017 バージョン15.3 以降**: ライブラリヘッダーを含めることができるかどうかを判断します。

```cpp
#ifdef __has_include
#  if __has_include(<filesystem>)
#    include <filesystem>
#    define have_filesystem 1
#  elif __has_include(<experimental/filesystem>)
#    include <experimental/filesystem>
#    define have_filesystem 1
#    define experimental_filesystem
#  else
#    define have_filesystem 0
#  endif
#endif
```

## <a name="see-also"></a>関連項目

[プリプロセッサ ディレクティブ](../preprocessor/preprocessor-directives.md)
