---
description: 詳細については、「装飾名」を参照してください。
title: 装飾名
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: 65135b4f5b85cfae7a25513763b998d304e79a0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201717"
---
# <a name="decorated-names"></a>装飾名

C および C++ プログラム内の関数、データ、オブジェクトは、内部ではそれぞれの装飾名で表されます。 *装飾名* は、オブジェクト、データ、または関数定義のコンパイル時にコンパイラによって作成されるエンコードされた文字列です。 これにより、呼び出し規約、型、関数のパラメーター、およびその他の情報が、名前と共に記録されます。 この名前の装飾は、 *名前の変形* とも呼ばれ、リンカーが実行可能ファイルをリンクするときに、正しい関数とオブジェクトを検索するのに役立ちます。

修飾された名前付け規則は、Visual Studio のさまざまなバージョンで変更されており、ターゲットアーキテクチャによって異なる場合もあります。 Visual Studio を使用して作成されたソースファイルと正しくリンクするには、C および C++ の Dll とライブラリを、同じコンパイラツールセット、フラグ、およびターゲットアーキテクチャを使用してコンパイルする必要があります。

> [!NOTE]
> Visual studio 2015 でビルドされたライブラリは、Visual Studio 2017 または Visual Studio 2019 でビルドされたアプリケーションで使用できます。

## <a name="using-decorated-names"></a><a name="Using"></a> 装飾名の使用

正常にコンパイルされ、リンクされるコードを記述するために、通常は装飾名を把握している必要はありません。 装飾名は、コンパイラおよびリンカー内部の実装の詳細です。 通常、ツールは非装飾形式の名前を処理できます。 ただし、リンカーやその他のツールに関数名を指定するときは、装飾名が必要な場合もあります。 たとえば、オーバーロードされた C++ 関数、名前空間のメンバー、クラス コンストラクター、デストラクターと、特殊メンバー関数を一致させるには、装飾名を指定する必要があります。 オプション フラグや、装飾名を必要とするその他の状況の詳細については、使用しているツールおよびオプションに関するドキュメントを参照してください。

関数名、クラス、呼び出し規約、戻り値の型、またはいずれかのパラメーターを変更する場合、装飾名も同様に変更されます。 この場合、新しい装飾名を取得し、それを装飾名が指定されているすべての場所で使用する必要があります。

名前の装飾は、他のプログラミング言語で記述されたコードにリンクする場合や、他のコンパイラを使用する場合にも重要です。 コンパイラによって、使用する名前装飾規約は異なります。 実行可能ファイルを別の言語で記述されたコードにリンクする場合、エクスポートおよびインポートされた名前と呼び出し規約を一致させるには、特別な配慮が必要です。 アセンブリ言語コードでは、MSVC を使用して記述されたソースコードにリンクするために、MSVC の装飾名と呼び出し規約を使用する必要があります。

## <a name="format-of-a-c-decorated-name"></a><a name="Format"></a> C++ の装飾名の形式

C++ の関数の装飾名には、次の情報が含まれます。

- 関数名。

- 関数をメンバーに持つクラス (その関数がメンバー関数の場合)。 これには、関数を含むクラスの外側のクラスなども含まれます。

- 関数が属している名前空間 (その関数が名前空間の一部である場合)。

- 関数のパラメーターの型。

- 呼び出し規則

- 関数の戻り値の型。

装飾名では、関数とクラスの名前はエンコードされます。 装飾名の残りの部分は、コンパイラとリンカーに対してのみ内部的な意味を持つコードです。 C++ の非装飾名および装飾名の例を次に示します。

|非装飾名|装飾名|
|----------------------|--------------------|
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|

## <a name="format-of-a-c-decorated-name"></a><a name="FormatC"></a> C の装飾名の形式

C の関数の装飾形式は、次の表に示すように、その宣言で使用される呼び出し規則によって決まります。 これは、C++ のコードが `extern "C"` リンケージを持つように宣言されている場合に使用される装飾形式でも同様です。 既定の呼び出し規約は **`__cdecl`** です。 64 ビット環境では、関数は装飾されません。

|呼び出し規約|[装飾]|
|------------------------|----------------|
|**`__cdecl`**|先頭のアンダースコア ( **`_`** )|
|**`__stdcall`**|先頭のアンダースコア ( **`_`** ) と末尾のアットマーク () と、 **`@`** その後に続くパラメーターリスト内のバイト数 (10 進数)|
|**`__fastcall`**|先頭と末尾の記号 ( **`@`** ) の後に、パラメーターリスト内のバイト数を表す10進数。|
|**`__vectorcall`**|2つの末尾のアット記号 () の後に、 **`@@`** パラメーターリスト内の10進数のバイト数。|

## <a name="viewing-decorated-names"></a><a name="Viewing"></a> 装飾名の表示

データ、オブジェクト、関数定義、または関数プロトタイプを含むソース ファイルをコンパイルした後に、装飾形式のシンボル名を取得できます。 プログラム内の修飾名を確認するために、次のいずれかのメソッドを使用できます。

#### <a name="to-use-a-listing-to-view-decorated-names"></a>リスティング ファイルを使用して装飾名を確認するには

1. データ、オブジェクト、または関数の定義またはプロトタイプを含むソースファイルを、 [リスティングファイルの種類](fa-fa-listing-file.md) のコンパイラオプションがソースコード (**/Dns**) でアセンブリに設定された状態でコンパイルして、一覧を生成します。

   たとえば、開発者コマンドプロンプトで「」と入力して、 `cl /c /FAs example.cpp` リスティングファイルを生成します。たとえば、「.asm」と入力します。

2. 結果として得られるリスティング ファイルから、先頭が PUBLIC で、末尾にはセミコロンと非装飾のデータまたは関数名が続く行を見つけます。 PUBLIC とセミコロンの間にあるシンボルが、装飾名です。

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>DUMPBIN を使用して装飾名を確認するには

1. エクスポートされたシンボルを .obj ファイルまたは .lib ファイルで表示するには、 `dumpbin /symbols` `objfile` 開発者コマンドプロンプトで「」と入力します。

2. 装飾形式のシンボルを見つけるには、かっこに囲まれた非装飾名を探します。 装飾名は、パイプ (&#124;) 文字の後、非装飾名の前にある同じ行にあります。

## <a name="viewing-undecorated-names"></a><a name="Undecorated"></a> 非装飾名の表示

undname.exe を使用すると、装飾名を非装飾形式に変換できます。 変換の動作を次の例に示します。

```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation. All rights reserved.

Undecoration of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## <a name="see-also"></a>関連項目

[その他の MSVC ビルドツール](c-cpp-build-tools.md)<br/>
[extern を使用したリンケージの指定](../../cpp/extern-cpp.md)
