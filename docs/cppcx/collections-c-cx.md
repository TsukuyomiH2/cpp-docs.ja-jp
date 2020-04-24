---
title: コレクション (C++/CX)
ms.date: 11/19/2018
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: 59e73b803a0878e88361c7fe75cff556b8eeedcd
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032318"
---
# <a name="collections-ccx"></a>コレクション (C++/CX)

C++/CX プログラムでは、標準テンプレート ライブラリ (STL) コンテナー、またはその他のユーザー定義コレクション型を自由に使用できます。 ただし、コレクションを Windows ランタイム アプリケーション バイナリ インターフェイス (ABI) を渡す場合 (XAML コントロールや JavaScript クライアントなど) には、Windows ランタイム コレクション型を使用する必要があります。

Windows ランタイムはコレクションと関連する型のインターフェイスを定義し、C++/CX は、コレクション.h ヘッダー ファイルに具体的な C++ の実装を提供します。 この図は、コレクション型間のリレーションシップを示しています。

![コレクションタイプのCX継承ツリーを&#43;&#43;&#47;C](../cppcx/media/cppcxcollectionsinheritancetree.png "コレクションタイプのCX継承ツリーを&#43;&#43;&#47;C")

- [Platform::Collections::Vector クラス](../cppcx/platform-collections-vector-class.md) は [std::vector クラス](../standard-library/vector-class.md)と似ています。

- [Platform::Collections::Map クラス](../cppcx/platform-collections-map-class.md) は [std::map class クラス](../standard-library/map-class.md)と似ています。

- [Platform::Collections::VectorView クラス](../cppcx/platform-collections-vectorview-class.md) と[Platform::Collections::MapView クラス](../cppcx/platform-collections-mapview-class.md) は `Vector` と `Map`の読み取り専用のバージョンです。

- 反復子は [Platform::Collections 名前空間](../cppcx/platform-collections-namespace.md)で定義されます。 これらの反復子は、STL 反復子の要件を満たし、任意の [Windows::Foundation::Collections](../standard-library/algorithm-functions.md#find)インターフェイス型や  [Platform::Collections](../standard-library/algorithm-functions.md#count_if)具象型で [std::find](/uwp/api/windows.foundation.collections) 、 [std::count_if](../cppcx/platform-collections-namespace.md) などの STL アルゴリズムを使えるようにします。 たとえば、C# で作成された Windows ランタイム コンポーネントのコレクションを反復処理して、STL アルゴリズムを適用できます。

   > [!IMPORTANT]
   > プロキシ反復子 `VectorIterator` と `VectorViewIterator` は、プロキシ オブジェクト `VectoryProxy<T>` と `ArrowProxy<T>` を利用して、STL コンテナーでの使用を有効にします。 詳細については、この記事で後述する「VectorProxy 要素」を参照してください。

- C++/CX コレクション型は、STL コンテナーがサポートするのと同じスレッド セーフ保証をサポートします。

- [Windows::Foundation::Collections::IObservableVector](/uwp/api/windows.foundation.collections.iobservablevector-1) と [Windows::Foundation::Collections::IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) は、コレクションがさまざまな方法で変更されるときに発生するイベントを定義します。 これらのインターフェイスを実装すると、  [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) と [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) は、XAML コレクションとのデータ バインドをサポートします。 たとえば、 `Vector` にデータ バインドされている `Grid`がある場合、コレクションに項目を追加すると、変更がグリッド UI に反映されます。

## <a name="vector-usage"></a>ベクターの使用

クラスがシーケンス コンテナーを別の Windows ランタイム コンポーネントに渡す必要がある場合は、パラメーターまたは戻り値の型として[IVector\<T>、](/uwp/api/windows.foundation.collections.ivector-1)具象実装として[プラットフォーム::コレクション\<::ベクター T>](../cppcx/platform-collections-vector-class.md)を使用します。 パブリックの戻り値またはパラメーターで `Vector` 型を使用しようとすると、コンパイラ エラー C3986 が発生します。 このエラーは、 `Vector` を `IVector`に変更することで解決できます。

> [!IMPORTANT]
> 独自のプログラム内のシーケンスを渡している場合は、 `Vector` か `std::vector` のどちらかを使用します。それらの方が `IVector`より効率的であるためです。 ABI を介してコンテナーを渡す場合にのみ、 `IVector` を使用します。
>
> Windows ランタイム型システムは、ジャグ配列の概念をサポートしていないため、IVector<プラットフォーム::配列\<T>> を戻り値またはメソッド パラメーターとして渡すことはできません。 ABI を通じてジャグ配列またはシーケンスのシーケンスを渡すには、 `IVector<IVector<T>^>`を使用します。

`Vector<T>` は、コレクションでの項目の追加、削除、およびアクセスに必要なメソッドを提供します。暗黙的に `IVector<T>`に変換可能です。 `Vector<T>`のインスタンスで STL アルゴリズム使用することもできます。 次の例は、基本的な使用法をいくつか示しています。 [begin 関数](../cppcx/begin-function.md) と [end 関数](../cppcx/end-function.md) は `Platform::Collections` 名前空間のもので、 `std` 名前空間のものではありません。

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

既存の`std::vector`コードを使用して Windows ランタイム コンポーネントで再利用する場合は、`Vector``std::vector`または反復子のペアを使用するコンストラクターのいずれかを使用して、コレクションを ABI に渡す`Vector`ポイントにを構築します。 次の例は、 `Vector` からの効率的な初期化のために `std::vector`移動コンストラクターを使用する方法を示しています。 移動操作の後、元の `vec` 変数は有効でなくなります。

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

今後のいつか、ABI を介して渡す必要がある文字列ベクターがある場合、その文字列を最初に `std::wstring` 型として作成するのかそれとも `Platform::String^` 型として作成するのかを決定する必要があります。 その文字列に対して多くの処理を実行する必要がある場合、 `wstring`を使用します。 それ以外の場合は、文字列を `Platform::String^` 型として作成して、後で変換するコストを回避してください。 また、これらの文字列を `std:vector` と `Platform::Collections::Vector` のどちらに内部的に埋め込むのかも決定する必要があります。 一般に、 `std::vector` を使用し、ABI を介してコンテナーを渡す場合にのみ、そこから `Platform::Vector` を作成します。

## <a name="value-types-in-vector"></a>ベクターにおける値の型

[Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) に格納される要素は、暗黙的にまたは指定したカスタム [std::equal_to](../standard-library/equal-to-struct.md) 比較子を使用するかして、等値比較をサポートする必要があります。 すべての参照型とすべてのスカラー型は、暗黙的に等値比較をサポートしています。 [Windows::Foundation::DateTime](/uwp/api/windows.foundation.datetime)などの非スカラー値型の場合や、カスタム比較 ( `objA->UniqueID == objB->UniqueID`など) の場合、カスタム関数オブジェクトを提供する必要があります。

## <a name="vectorproxy-elements"></a>VectorProxy 要素

[プラットフォーム::コレクション::ベクターイテレータ](../cppcx/platform-collections-vectoriterator-class.md)と[プラットフォーム::コレクション:VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md)は`range for`[、ivector\<T>](/uwp/api/windows.foundation.collections.ivector-1)コンテナでのループとアルゴリズム[std::sort](../standard-library/algorithm-functions.md#sort)の使用を可能にします。 ただし、C++ ポインターの逆参照を使って `IVector` 要素にアクセスすることはできません。これらの要素には、 [GetAt](/uwp/api/windows.foundation.collections.ivector-1.getat) メソッドと [SetAt](/uwp/api/windows.foundation.collections.ivector-1.setat) メソッドを使ってアクセスすることしかできません。 したがって`Platform::Details::VectorProxy<T>`、これらの反復子はプロキシ クラスを使用し`Platform::Details::ArrowProxy<T>`、標準ライブラリの要求に応じて__\*__、 __->__、__\[__ および ) 演算子を通じて個々の要素にアクセスします。 厳密には、 `IVector<Person^> vec`が指定されている場合、 `*begin(vec)` の型は `VectorProxy<Person^>`になります。 ただし、プロキシ オブジェクトは、ほとんどの場合、コードに対して透過的です。 これらのプロキシ オブジェクトは反復子によって内部でのみ使用されるため文書化されませんが、その機構の動作がわかっていると便利です。

`range for` コンテナーに対して `IVector` ループを使用する場合は、 `auto&&` を使用して反復子変数が `VectorProxy` 要素に正しくバインドされるようにします。 `auto` または `auto&`を使用すると、コンパイラ警告 C4239 が発生し、警告テキストに `VectoryProxy` が示されます。

`range for` に対する `IVector<Person^>`ループ処理の例を次に示します。 実行が 64 行のブレークポイントで停止していることに注意してください。 **[クイック ウォッチ]** ウィンドウには、反復子変数 `p` が実際には `VectorProxy<Person^>` メンバー変数と `m_v` メンバー変数を持つ `m_i` であることが示されています。 ただし、この変数で `GetType` を呼び出すと、 `Person` インスタンス `p2`と同一の型が返されます。 `VectorProxy` と `ArrowProxy` が **[クイック ウォッチ]**、デバッガーの一部のコンパイラ エラー、またはその他の場所に表示される場合でも、通常はそれらについて明示的にコーディングする必要はありません。

![ループに基づく範囲&#45;内のベクトル プロキシ](../cppcx/media/vectorproxy-1.png "ループに基づく範囲&#45;内のベクトル プロキシ")

プロキシ オブジェクトに関してコーディングする必要があるのは、 `dynamic_cast` 要素コレクションで特定の型の XAML オブジェクトを探している場合など、要素で `UIElement` を実行する必要がある場合です。 この場合は、最初に [Platform::Object](../cppcx/platform-object-class.md)^ に要素をキャストし、その後に動的キャストを実行する必要があります。

```cpp
void FindButton(UIElementCollection^ col)
{
    // Use auto&& to avoid warning C4239
    for (auto&& elem : col)
    {
        Button^ temp = dynamic_cast<Button^>(static_cast<Object^>(elem));
        if (nullptr != temp)
        {
            // Use temp...
        }
    }
}
```

## <a name="map-usage"></a>マップの使用

この例では、 [Platform::Collections::Map](../cppcx/platform-collections-map-class.md)で項目の挿入と検索を行う方法と、 `Map` を読み取り専用の [Windows::Foundation::Collections::IMapView](/uwp/api/windows.foundation.collections.imapview-2) 型として返す方法を示しています。

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

一般に、内部マップ機能については、パフォーマンス上の理由で `std::map` 型を優先します。 ABI を介してコンテナーを渡す必要がある場合は、 [std::map](../cppcx/platform-collections-map-class.md) から [Platform::Collections::Map](../standard-library/map-class.md) を構築し、 `Map` を [Windows::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2)として返します。 パブリックの戻り値またはパラメーターで `Map` 型を使用しようとすると、コンパイラ エラー C3986 が発生します。 このエラーは、 `Map` を `IMap`に変更することで解決できます。 たとえば、実行するルックアップや挿入の数が多くなく、ABI を介して頻繁にコレクションを渡すなどの場合、最初から `Platform::Collections::Map` を使用し `std::map`を変換するコストを回避した方がコストを抑えられることがあります。 どちらの場合も、 `IMap` のルックアップ操作と挿入操作は、3 つの種類で最もパフォーマンスが低いので避けます。 ABI を介してコンテナーを渡すポイントでのみ、 `IMap` に変換します。

## <a name="value-types-in-map"></a>マップにおける値の型

[Platform::Collections::Map](../cppcx/platform-collections-map-class.md) 内の要素は、順序付きです。 `Map` に格納しようとする要素は、厳密な弱い順序付けに基づき、"より小さい" 比較をサポートする必要があります。このために、暗黙的な比較、または開発者が指定したカスタム比較子 [stl::less](../standard-library/less-struct.md) が使用されます。 スカラー型では、この比較を暗黙的にサポートしています。 `Windows::Foundation::DateTime`などの非スカラー値型、またはカスタム比較 ( `objA->UniqueID < objB->UniqueID`など) の場合、カスタム比較子を提供する必要があります。

## <a name="collection-types"></a>コレクション型

コレクションは、シーケンス コレクションと関連コレクションそれぞれの変更可能バージョンと読み取り専用バージョンという 4 つのカテゴリに分類されます。 さらに、C++/CX は、コレクションへのアクセスを簡素化する 3 つの反復子クラスを提供することで、コレクションを拡張します。

変更可能なコレクションの要素は変更できますが、 *ビュー*と呼ばれる読み取り専用コレクションの要素は読み取りしか実行できません。 プラットフォームの要素[::コレクション::ベクトル](../cppcx/platform-collections-vector-class.md)または[プラットフォーム:コレクション::VectorView](../cppcx/platform-collections-vectorview-class.md)コレクションは、反復子またはコレクションの[Vector::GetAt](../cppcx/platform-collections-vector-class.md#getat)とインデックスを使用してアクセスできます。 連想コレクションの要素には、コレクションの[Map::Lookup](../cppcx/platform-collections-map-class.md#lookup)とキーを使用してアクセスできます。

[Platform::Collections::Map クラス](../cppcx/platform-collections-map-class.md)<br/>
変更可能な関連コレクション。 マップ要素は、キーと値のペアです。 キーを検索してその関連付けられた値を取得することと、キーと値のペアをすべて繰り返すことの両方がサポートされています。

`Map` と `MapView` は、 `<K, V, C = std::less<K>>`で template 宣言されるので、比較子をカスタマイズできます。  さらに、 `Vector` と `VectorView` は `<T, E = std::equal_to<T>>` で template 宣言されるので、 `IndexOf()`の動作をカスタマイズできます。 これは、値の構造体の `Vector` と `VectorView` について特に重要です。 たとえば、ベクター\<Windows::Foundation::DateTime>を作成するには、DateTime が == 演算子をオーバーロードしないため、カスタムコンパレータを用意する必要があります。

[Platform::Collections::MapView クラス](../cppcx/platform-collections-mapview-class.md)<br/>
`Map`の読み取り専用バージョン。

[Platform::Collections::Vector クラス](../cppcx/platform-collections-vector-class.md)<br/>
変更可能なシーケンス コレクション。 `Vector<T>` は、定数時間ランダム アクセス操作と償却定数時間の [追加](../cppcx/platform-collections-vector-class.md#append) 操作をサポートしています。

[Platform::Collections::VectorView クラス](../cppcx/platform-collections-vectorview-class.md)<br/>
`Vector`の読み取り専用バージョン。

[Platform::Collections::InputIterator クラス](../cppcx/platform-collections-inputiterator-class.md)<br/>
STL 入力反復子の要件を満たす STL の反復子。

[Platform::Collections::VectorIterator クラス](../cppcx/platform-collections-vectoriterator-class.md)<br/>
変更可能な STL ランダム アクセス反復子の要件を満たす STL 反復子。

[プラットフォーム:コレクション::ベクタービュー反復器クラス](../cppcx/platform-collections-vectorviewiterator-class.md)<br/>
STL の  `const` ランダム アクセス反復子の要件を満たす STL 反復子。

### <a name="begin-and-end-functions"></a>begin() および end() 関数

`Vector`STL を処理するを簡略化するために、 `VectorView`、 `Map` `MapView`、、および`Windows::Foundation::Collections`任意のオブジェクト、 C++/CX 関数の[開始関数](../cppcx/begin-function.md)と[終了関数](../cppcx/end-function.md)の非メンバー関数のオーバーロードをサポートします。

次の表は、使用できる反復子と関数の一覧を示しています。

|Iterators|関数|
|---------------|---------------|
|[プラットフォーム:コレクション::ベクター反復T>\<](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (内部的には[Windowsを保存します::財団:コレクション::\<IVector T>](/uwp/api/windows.foundation.collections.ivector-1)とint。|[終了](../cppcx/begin-function.md)/ [(](../cppcx/end-function.md)[ウィンドウズ:ファウンデーション:コレクション::\<IVector T>](/uwp/api/windows.foundation.collections.ivector-1))|
|[プラットフォーム:コレクション::ベクタービューイットエレータ\<T>](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (内部的には[IVectorView\<T>](/uwp/api/windows.foundation.collections.ivectorview-1)^ と int を格納します。|[開始](../cppcx/begin-function.md)/ [終了](../cppcx/end-function.md)([\<IVectorView T>](/uwp/api/windows.foundation.collections.ivectorview-1)^)|
|[プラットフォーム::コレクション::入力反復T>\<](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (内部的に[IIterator\<T>](/uwp/api/windows.foundation.collections.iiterator-1)^ と T を格納します。|[begin](../cppcx/begin-function.md)/ [開始終了](../cppcx/end-function.md)([IIterable\<T>](/uwp/api/windows.foundation.collections.iiterable-1))|
|[プラットフォーム::コレクション::入力イテレータ<IKeyValuePair\<K、V>^>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (内部的に[IIterator\<T>](/uwp/api/windows.foundation.collections.iiterator-1)^ と T を格納します。|[begin](../cppcx/begin-function.md)/ [開始終了](../cppcx/end-function.md)([IMap\<K,V>](/uwp/api/windows.foundation.collections.imap-2).|
|[プラットフォーム::コレクション::入力イテレータ<IKeyValuePair\<K、V>^>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (内部的に[IIterator\<T>](/uwp/api/windows.foundation.collections.iiterator-1)^ と T を格納します。|[終了](../cppcx/begin-function.md)/ [(](../cppcx/end-function.md) [ウィンドウズ:ファウンデーション:コレクション::IMapView](/uwp/api/windows.foundation.collections.imapview-2))|

### <a name="collection-change-events"></a>コレクション変更イベント

`Vector` と `Map` は、XAML コレクションでのデータ バインドをサポートしていますが、これは、コレクション オブジェクトが変更またはリセットされたとき、またはコレクションのいずれかの要素が挿入、削除、または変更されたときに発生するイベントを実装することで実現されています。 データ バインドをサポートする独自の型を作成できます。ただし、 `Map` と `Vector` から継承することはできません。これらの型はシールされているためです。

[Windows::Foundation::Collections::VectorChangedEventHandler](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1) デリゲートと [Windows::Foundation::Collections::MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) デリゲートは、コレクション変更イベントのイベント ハンドラーのシグネチャを指定します。 [Windows::Foundation::Collections::CollectionChange](/uwp/api/windows.foundation.collections.collectionchange) パブリック列挙型クラス、 `Platform::Collection::Details::MapChangedEventArgs` 、 `Platform::Collections::Details::VectorChangedEventArgs` ref クラスは、イベントの原因を特定するためにイベント引数を格納します。 型`*EventArgs`は、 または`Details``Map``Vector`を使用するときに明示的に作成または使用する必要がないため、名前空間で定義されます。

## <a name="see-also"></a>関連項目

[型システム](../cppcx/type-system-c-cx.md)<br/>
[C++/CX 言語リファレンス](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[名前空間参照](../cppcx/namespaces-reference-c-cx.md)
