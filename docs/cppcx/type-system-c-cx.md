---
description: '詳細情報: 型システム (C++/CX)'
title: 型システム (C++/CX)
ms.date: 02/03/2017
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
ms.openlocfilehash: 43b1e9dd2df6e9e457525ebf337604f68f0c267f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288166"
---
# <a name="type-system-ccx"></a>型システム (C++/CX)

Windows ランタイムアーキテクチャを使用すると、C++/CX、Visual Basic、Visual C#、および JavaScript を使用して、Windows API に直接アクセスし、他の Windows ランタイムのアプリやコンポーネントと相互運用するアプリやコンポーネントを作成できます。 C++ で記述されたアプリユニバーサル Windows プラットフォーム、CPU で直接実行されるネイティブコードにコンパイルされます。 C# または Visual Basic で記述されたアプリは、Microsoft 中間言語 (MSIL) にコンパイルされ、共通言語ランタイム (CLR) で実行ユニバーサル Windows プラットフォームます。 JavaScript で記述されたユニバーサル Windows プラットフォームアプリは、実行時環境で実行されます。 Windows ランタイムオペレーティングシステムコンポーネント自体は、C++ で記述され、ネイティブコードとして実行されます。 これらのコンポーネントとユニバーサル Windows プラットフォームアプリはすべて、Windows ランタイムアプリケーションバイナリインターフェイス (ABI) を介して直接通信します。

最新の C++ 表現で Windows ランタイムのサポートを有効にするために、Microsoft は C++/CX を作成しました。 C++/CX には、組み込みの基本型と基本的な Windows ランタイム型の実装が用意されています。これにより、C++ アプリとコンポーネントは、他の言語で記述されたアプリと ABI を介して通信できます。 任意の Windows ランタイム型を使用することも、他のユニバーサル Windows プラットフォームアプリやコンポーネントが使用できるクラス、構造体、インターフェイス、およびその他のユーザー定義型を作成することもできます。 C++/CX で記述されたユニバーサル Windows プラットフォームアプリは、パブリックアクセシビリティがない限り、通常の C++ クラスおよび構造体を使用することもできます。

C++/CX 言語プロジェクションと内部動作の詳しい説明については、次のブログ記事を参照してください。

- [C++/CX パート 0/ \[ n \] : 概要](https://devblogs.microsoft.com/cppblog/ccx-part-0-of-n-an-introduction/)

- [C++/CX パート 1/ \[ n \] : 単純なクラス](https://devblogs.microsoft.com/cppblog/ccx-part-1-of-n-a-simple-class/)

- [C++/CX パート 2/ \[ n \] : 摩耗帽子](https://devblogs.microsoft.com/cppblog/ccx-part-2-of-n-types-that-wear-hats/)

- [C++/CX パート 3/ \[ n \] : 構築中](https://devblogs.microsoft.com/cppblog/ccx-part-3-of-n-under-construction/)

- [C++/CX パート 4 of \[ n \] : 静的メンバー関数](https://devblogs.microsoft.com/cppblog/ccx-part-4-of-n-static-member-functions/)

## <a name="windows-metadata-winmd-files"></a>Windows メタデータ (.winmd) ファイル

C++ で記述されたユニバーサル Windows プラットフォームアプリをコンパイルすると、コンパイラはネイティブコンピューターコードで実行可能ファイルを生成します。また、クラス、構造体、列挙体、インターフェイス、パラメーター化されたインターフェイス、デリゲートなど、パブリック Windows ランタイム型の説明を含む個別の Windows メタデータ (winmd) ファイルも生成します。 メタデータの形式は、.NET Framework アセンブリで使用される形式に似ています。  C++ コンポーネントでは、.winmd ファイルにはメタデータのみ含まれています。実行可能コードは、別個のファイルに存在します。 これは、Windows に含まれている Windows ランタイムコンポーネントの場合に当てはまります。 WinMD ファイルの名前はソース コードのルート名前空間のプレフィックスに一致またはそれ自体である必要があります。 (.NET Framework 言語の場合、.winmd ファイルには、.NET Framework アセンブリのようにコードとメタデータの両方が含まれます。)

.winmd ファイルのメタデータは、コードの公開されたサーフェイスを表します。 他のアプリがどの言語で記述されているかにかかわらず、公開されている型は他のユニバーサル Windows プラットフォームにも表示されます。 したがって、メタデータまたは公開されたコードには、Windows ランタイム型システムによって指定された型のみを含めることができます。 標準クラス、配列、テンプレートまたは STL コンテナーなど、C++ 固有の言語構造体は、メタデータで発行できません。理由は、JavaScript または C# クライアント アプリケーションが対処できないからです。

型またはメソッドがメタデータに表示されるかどうかは、適用されるアクセシビリティ修飾子によって異なります。 型を表示するには、型が名前空間で宣言され、パブリックとして宣言されている必要があります。 非パブリックの ref クラスは、コード内で内部ヘルパー型として許可されています。これは、メタデータでは表示されません。 パブリック ref クラスでも、すべてのメンバーが表示されるとは限りません。 次の表は、パブリック ref クラスでの C++ アクセス指定子と Windows ランタイムメタデータの可視性の関係を示しています。

| メタデータで公開 | メタデータで非公開 |
|--|--|
| public | private |
| protected | internal |
| public protected | private protected |

.winmd ファイルの内容を表示するために、 **オブジェクト ブラウザー** を使用できます。 Windows に含まれる Windows ランタイムコンポーネントは、Windows の winmd ファイルにあります。 既定の winmd ファイルには、C++/CX で使用される基本的な型が含まれています。また、platform.object には、Platform 名前空間からの追加の型が含まれています。 既定では、これら3つの winmd ファイルは、ユニバーサル Windows プラットフォームアプリのすべての C++ プロジェクトに含まれています。

> [!TIP]
> [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md) 型は、パブリックではないので、.winmd ファイルには表示されません。 これらは、 `Windows::Foundation::Collections`で定義されているインターフェイスのプライベート C++ 固有の実装です。 JavaScript または C# で記述された Windows ランタイムアプリは、 [Platform:: Collections:: Vector クラス](../cppcx/platform-collections-vector-class.md) がどのようなものであるかを認識しませんが、を使用することはでき `Windows::Foundation::Collections::IVector` ます。 `Platform::Collections` 型は、collection.h で定義されます。

## <a name="windows-runtime-type-system-in-ccx"></a>C++/CX の Windows ランタイム型システム

次のセクションでは、Windows ランタイム型システムの主な機能と、C++/CX でサポートされるしくみについて説明します。

### <a name="namespaces"></a>名前空間

すべての Windows ランタイム型は名前空間内で宣言する必要があります。Windows API 自体は、名前空間によって整理されています。 .winmd ファイルには、ルート名前空間と同じ名前が必要です。 たとえば、A.B.C.MyClass という名前のクラスは、A.winmd または A.B.winmd または A.B.C.winmd という名前のメタデータ ファイルで定義されている場合のみインスタンス化できます。 DLL の名前が .winmd ファイル名と一致する必要はありません。

Windows API 自体が、名前空間ごとに構成された、十分にファクタリングされたクラス ライブラリとして再開発されました。  すべての Windows ランタイムコンポーネントは、Windows. * 名前空間で宣言されています。

詳細については、「 [名前空間と型の可視性](../cppcx/namespaces-and-type-visibility-c-cx.md)」を参照してください。

### <a name="fundamental-types"></a>基本的な型

Windows ランタイムでは、UInt8、Int16、UInt16、Int32、UInt32、Int64、UInt64、Single、Double、Char16、Boolean、および String の基本型が定義されています。 C++/CX では、uint16、uint32、uint64、int16、int32、int64、float32、float64、および char16 として、既定の名前空間の基本的な数値型がサポートされています。 ブール値と文字列も、Platform 名前空間で定義されます。

C++/CX では、uint8 も定義 **`unsigned char`** されています。これは Windows ランタイムではサポートされておらず、パブリック api では使用できません。

基本型を null 許容にするには、 [Platform::IBox インターフェイス](../cppcx/platform-ibox-interface.md) にラップします。 詳細については、「 [値クラスと構造体](../cppcx/value-classes-and-structs-c-cx.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。

基本型の詳細については、「 [基本型](../cppcx/fundamental-types-c-cx.md)

### <a name="strings"></a>文字列

Windows ランタイム文字列は、16ビットの UNICODE 文字の変更できないシーケンスです。 Windows ランタイム文字列はとして投影され `Platform::String^` ます。 このクラスには、文字列の構築、操作、およびからの変換のためのメソッドが用意されて **`wchar_t`** います。

詳細については、「 [文字列](../cppcx/strings-c-cx.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。

### <a name="arrays"></a>配列

Windows ランタイムは、任意の型の1次元配列をサポートしています。 配列の配列はサポートされていません。  C++/CX では、Windows ランタイム配列は [Platform:: Array クラス](../cppcx/platform-array-class.md)として射影されます。

詳細については、「 [array と WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md) 」を参照してください。

### <a name="ref-classes-and-structs"></a>Ref クラスと構造体

Windows ランタイムクラスは、参照によってコピーされるため、C++/CX で ref クラスまたは ref 構造体として射影されます。 ref クラスと ref 構造体のメモリ管理は、参照カウントによって透過的に処理されます。 オブジェクトへの最後の参照がスコープ外に出ると、オブジェクトは破棄されます。 ref クラスまたは ref 構造体では、次のことができます。

- コンストラクター、メソッド、プロパティ、およびイベントをメンバーとして格納できます。 これらのメンバーには、パブリック、プライベート、プロテクト、または内部のアクセシビリティを指定できます。

- プライベートの入れ子になった構造体、列挙体、またはクラス定義を格納できます。

- 1 つの基底クラスから直接継承し、任意の数のインターフェイスを実装できます。 ref クラスは、いずれも [Platform::Object Class](../cppcx/platform-object-class.md) に暗黙的に変換可能で、 [Object::ToString](../cppcx/platform-object-class.md#tostring)などの仮想メソッドをオーバーライドできます。

パブリック コンストラクターを持つ ref クラスは、さらに派生されることを防ぐために、シール済みとして宣言する必要があります。

詳細については、「 [Ref クラスと構造体](../cppcx/ref-classes-and-structs-c-cx.md)」を参照してください。

### <a name="value-classes-and-structs"></a>値クラスと構造体

値クラスまたは値の構造体は、基本的なデータ構造体を表し、フィールドのみ格納できます。フィールドには、値クラス、値構造体、または `Platform::String^`型が含まれます。  値構造体と値クラスは、値によってコピーされます。

値構造体を null 許容にするには、IBox インターフェイスにラップします。

詳細については、「 [値クラスと構造体](../cppcx/value-classes-and-structs-c-cx.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。

### <a name="partial-classes"></a>部分クラス

部分クラスの機能を使用して、1 つのクラスを複数のファイルに対して定義できます。 この機能は主に、XAML エディターなどのコード生成ツールで、編集するファイルにアクセスせずに 1 つのファイルを変更するために使用されます。

詳細については、「 [部分クラス](../cppcx/partial-classes-c-cx.md)

### <a name="properties"></a>Properties

プロパティは、任意の Windows ランタイム型のパブリックデータメンバーであり、get/set メソッドのペアとして実装されます。 クライアント コードは、パブリック フィールドのようにプロパティにアクセスします。 カスタムの get または set コードを必要とするプロパティは、 *trivial プロパティ* と呼ばれ、明示的な get または set メソッドを使用せずに宣言できます。

詳細については、「 [プロパティ](../cppcx/properties-c-cx.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。

### <a name="windows-runtime-collections-in-ccx"></a>C++/CX の Windows ランタイムコレクション

Windows ランタイムは、各言語が独自の方法で実装するコレクション型の一連のインターフェイスを定義します。 C++/CX は、 [platform:: collections:: Vector クラス](../cppcx/platform-collections-vector-class.md)、 [Platform:: Collections:: Map クラス](../cppcx/platform-collections-map-class.md)、およびそれに対応する標準テンプレートライブラリ (STL) と互換性のあるその他の関連する具象コレクション型の実装を提供します。

詳細については、[コレクション](../cppcx/collections-c-cx.md) を参照してください。

### <a name="template-ref-classes"></a>テンプレート ref クラス

プライベート ref クラスおよび内部 ref クラスは、テンプレート化および特化できます。

詳細については、「 [テンプレート ref クラス](../cppcx/template-ref-classes-c-cx.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。

### <a name="interfaces"></a>インターフェイス

Windows ランタイムインターフェイスは、ref クラスまたは ref 構造体がインターフェイスから継承する場合に実装する必要があるパブリックプロパティ、メソッド、およびイベントのセットを定義します。

詳細については、「[インターフェイス](../cppcx/interfaces-c-cx.md)」を参照してください。

### <a name="enums"></a>列挙型

Windows ランタイムの列挙型クラスは、C++ のスコープ列挙型に似ています。 基になる型は int32 です。[Flags] 属性が適用された場合、基になる型は uint32 です。

詳細については、「 [列挙体](../cppcx/enums-c-cx.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。

### <a name="delegates"></a>代理人

Windows ランタイム内のデリゲートは、C++ の std:: function オブジェクトに似ています。 これは、互換性のあるシグニチャを持つクライアント提供関数を呼び出すために使用される、特殊な種類の ref クラスです。  デリゲートは、イベントの種類として Windows ランタイムで最もよく使用されます。

詳細については、「[デリゲート](../cppcx/delegates-c-cx.md)」を参照してください。

### <a name="exceptions"></a>例外

C++/CX では、カスタムの例外の種類、 [std::exception](../standard-library/exception-class.md) 型、および [Platform::Exception](../cppcx/platform-exception-class.md) 型をキャッチできます。

詳細については、「 [例外](../cppcx/exceptions-c-cx.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。

### <a name="events"></a>イベント

イベントは、型がデリゲート型の、ref クラスまたは ref 構造体のパブリック メンバーです。 イベントに対して可能なのは、所有するクラスによる呼び出し (つまり、発生) だけです。 ただし、クライアント コードが独自の関数を提供することはできます。それらの関数はイベント ハンドラーと呼ばれ、所有クラスでイベントが発生したときに呼び出されます。

詳細については、「[イベント](../cppcx/events-c-cx.md)」を参照してください。

### <a name="casting"></a>キャスト

C++/CX は、標準 C++ のキャスト演算子 [static_cast](../cpp/static-cast-operator.md)、 [dynamic_cast](../cpp/dynamic-cast-operator.md)、および [reinterpret_cast](../cpp/reinterpret-cast-operator.md)をサポートし、C++/CX に固有の **safe_cast** 演算子もサポートします。

詳細については、「 [キャスト](../cppcx/casting-c-cx.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。

### <a name="boxing"></a>ボックス化

ボックス化された変数は、参照セマンティクスが必要な場合に参照型にラップされる値の型です。

詳細については、「 [ボックス化](../cppcx/boxing-c-cx.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。

### <a name="attributes"></a>属性

属性は、任意の Windows ランタイム型または型のメンバーに適用でき、実行時に検査できるメタデータ値です。 Windows ランタイムは、名前空間の一連の共通属性を定義し `Windows::Foundation::Metadata` ます。 パブリックインターフェイスのユーザー定義属性は、このリリースの Windows ランタイムではサポートされていません。

## <a name="api-deprecation"></a>API の非推奨

Windows ランタイムシステム型で使用されているのと同じ属性を使用して、パブリック Api を非推奨としてマークする方法について説明します。

詳細については、「 [非推奨 types and members](../cppcx/deprecating-types-and-members-c-cx.md)」を参照してください。

## <a name="see-also"></a>関連項目

[C++/CX 言語リファレンス](../cppcx/visual-c-language-reference-c-cx.md)
