---
title: Visual C++  移植とアップグレードのガイド
ms.date: 09/18/2018
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: landing-page
ms.openlocfilehash: eed1f3d6ba66aa77561d610530f820b09cf439df
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216376"
---
# <a name="visual-c-porting-and-upgrading-guide"></a>Visual C++  移植とアップグレードのガイド

このトピックは、Visual C++ コードをアップグレードするためのガイドを提供します。 これには、新しいリリースのツールでコードを適切にコンパイルして実行し、新しい言語と Visual Studio の機能を利用する方法も含まれます。 このトピックには、最新のプラットフォームへのレガシー アプリケーションの移行に関する情報も含まれています。

## <a name="reasons-to-upgrade-visual-c-code"></a>Visual C++ コードをアップグレードする理由

次の理由により、コードのアップグレードを検討してください。

- 強化されたコンパイラの最適化によるコードの高速化。

- コンパイラ自体のパフォーマンス向上によるビルドの高速化。

- 標準への準拠の強化。 Visual C++ が、最新の C++ 標準からの多くの機能を実装するようになりました。

- セキュリティの強化。 ガード チェックなどのセキュリティ機能。

### <a name="porting-your-code"></a>コードの移植

アップグレードするときには、まずアプリケーションのコードとプロジェクトを検討します。 アプリケーションは Visual Studio でビルドされましたか。 その場合は、関連するプロジェクトを特定します。  カスタム ビルド スクリプトはありますか。 Visual Studio のビルド システムを使用する代わりにカスタム ビルド スクリプトがある場合は、Visual Studio がプロジェクト ファイルとビルド設定を更新することで時間を節約することはできないため、アップグレードを行うのにより多くの作業が必要になります。

Visual Studio のビルド システムとプロジェクト ファイルの形式が、Visual Studio 2008 までの vcbuild から、2010 以降のサーバーの MSBuild に変更になりました。 2010 より前のバージョンからアップグレードし、高度にカスタマイズされたビルド システムがある場合は、アップグレードにさらに多くの作業が求められる可能性があります。 Visual Studio 2010 以降からアップグレードしている場合、プロジェクトは既に MSBuild を使用しているため、プロジェクトのアップグレードとアプリケーションのビルドはより簡単になります。

Visual Studio のビルド システムを使用していない場合は、MSBuild を使用するようにアップグレードを検討する必要があります。 MSBuild を使用するようにアップグレードする場合は、今後のアップグレードが簡単になり、Visual Studio Online などのサービスを使いやすくなります。 MSBuild は Visual Studio がサポートするすべてのターゲット プラットフォームをサポートします。

### <a name="porting-visual-studio-projects"></a>Visual Studio プロジェクトを移植する

プロジェクトまたはソリューションのアップグレードを開始するには、新しいバージョンの Visual Studio でソリューションを開き、アップグレードを開始する手順に従います。  プロジェクトをアップグレードするときは、UpgradeLog.htm としてプロジェクト フォルダーにも保存されているアップグレード レポートを受け取ります。 アップグレード レポートは、アップグレード プロセス中に発生した問題の概要と、加えられた変更に関する情報、または自動的に対応できなかった問題の概要を示します。

1. プロジェクト プロパティ

2. インクルード ファイル

3. コンパイラ準拠の強化または標準の変更により、正常にコンパイルされなくなったコード

4. Visual Studio または Windows の利用できなくなった機能に依存するコードや、Visual Studio の既定のインストールに含まれなくなった、または製品から削除されたヘッダー ファイルに依存するコード

5. API の名前変更、関数シグネチャの変更、非推奨の関数など、API の変更によってコンパイルされなくなったコード

6. 警告がエラーになるなど、診断の変更によってコンパイルされなくなったコード

7. 特に /NODEFAULTLIB が使用される場合の、変更されたライブラリによるリンカー エラー

8. 動作の変更による実行時エラーまたは予期しない結果

9. ツールで導入されたエラーによるエラー 問題が発生した場合には、通常のサポート チャネルを通じて、または [Visual Studio C++ 開発者コミュニティ](https://developercommunity.visualstudio.com/spaces/62/index.html) ページを使用して、Visual C++ チームに報告してください。

コンパイラのエラーにより回避することができない変更の他に、次のようないくつかの変更は、アップグレード プロセスで省略可能です。

1. 新しい警告は、コードをクリーンアップする方が良いことを示す場合があります。 特定の診断によっては、移植性、標準への準拠性、およびコードのセキュリティが向上する可能性があります。

2. 新しいコンパイラの機能を利用できます。たとえば、[/guard:cf (フロー制御ガードを有効にする)](../build/reference/guard-enable-control-flow-guard.md) コンパイラ オプションは、不正なコードの実行のチェックを追加します。

3. コードを簡略化し、プログラムのパフォーマンスを向上させる新しい言語機能を使用するよう一部のコードを更新したり、最新ライブラリを使用し、最新の標準とベスト プラクティスに準拠するようコードを更新することが可能です。

プロジェクトをアップグレードしてテストしたら、コードをさらに改善させることを検討し、コードの今後の方向性を計画したり、場合によってはプロジェクトのアーキテクチャについても再考します。 継続中の開発作業を受け取ることはありますか。 コードを他のプラットフォームで実行することは重要ですか。  その場合は、どのプラットフォームですか。  C++ は、移植性とクロス プラットフォーム開発を念頭に置いて設計された標準言語ですが、多くの Windows アプリケーションのコードは、Windows プラットフォームに強く結びついています。 Windows プラットフォームに一層結びついているこれらのパーツを分離するために、コードをリファクタリングしますか。

ユーザー インターフェイスはどうでしょうか。 MFC を使用している場合は、UI を更新することができます。 Feature Pack として 2008 年に導入された、新しい MFC 機能のいずれかを使用していますか。 アプリ全体を作成し直さずに、アプリに新しいルック アンド フィールを提供する場合は、MFC のリボン API を使用するか、MFC の新機能の一部を使用することを検討できます。

プログラムに XAML ユーザー インターフェイスを設定するが、UWP アプリは作成しない場合は、C# と WPF を使用して UI レイヤーを作成し、標準の C++ ロジックを DLL にリファクターすることができます。 C++/CLI に互換性レイヤーを作成して、ネイティブ コードで C# に接続します。 または、[C++/CX](../cppcx/visual-c-language-reference-c-cx.md) または [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/) を使用して UWP アプリを作成する方法もあります。 Windows 10 では、[Desktop App Converter](/windows/msix/desktop/desktop-to-uwp-run-desktop-app-converter) を使用すると、コードを変更せずに既存のデスクトップ アプリケーションを UWP アプリとしてパッケージ化できます。

また、新しい要件があったり、Windows Phone、Android デバイスなどの Windows デスクトップ以外のプラットフォームを対象とする必要が予測されるかもしれません。 クロスプラット フォームの UI ライブラリに、ユーザー インターフェイスのコードを移植することができます。 これらの UI フレームワークを使用して、複数のデバイスを対象にしながら、開発環境として Visual Studio や Visual Studio デバッガーを使用できます。

## <a name="related-topics"></a>関連トピック

|Title|説明|
|-----------|-----------------|
|[旧バージョンの Visual C++ からのプロジェクトのアップグレード](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|以前のバージョンの Visual Studio で作成されたプロジェクトを使用する方法について説明します。|
|[Visual Studio での C++ コンパイラの新機能](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)|現行版の Visual Studio に合わせた IDE とツールの変更|
|[Visual Studio の C++ 準拠の強化](../overview/cpp-conformance-improvements.md)|Visual Studio 2015 から Visual Studio における標準の準拠の強化|
|[2003 から 2015 の Visual C++ の履歴の変更](visual-cpp-change-history-2003-2015.md)|コードの変更が必要となる可能性のある、Visual Studio 2003 から 2015 における Visual C++ ライブラリおよびビルド ツールのすべての変更の一覧。|
|[2003 ～ 2015 年の Visual C++ の新機能](visual-cpp-what-s-new-2003-through-2015.md)|Visual Studio 2003 から Visual Studio 2015 の Visual C++ の "新機能" に関するすべての情報。|
|[サード パーティ ライブラリの移植](porting-third-party-libraries.md)|**vcpkg** コマンド ライン ツールを使用して、古いオープンソース ライブラリを新しい Visual C++ ツールセットでコンパイルされたバージョンに移植する方法。|
|[移植とアップグレード: 例とケース スタディ](porting-and-upgrading-examples-and-case-studies.md)|このセクションでは、いくつかのサンプルとアプリケーションを移植してアップグレードし、エクスペリエンスと結果について説明しました。 これらを読むと、移植およびプロセスのアップグレードに関係する含意がわかります。 プロセス全体を通して、アップグレードに関するヒントとテクニックについて説明し、特定のエラーを修正する方法を示します。|
|[ユニバーサル Windows プラットフォームへの移植](porting-to-the-universal-windows-platform-cpp.md)|コードを Windows 10 に移植する方法を説明します。|
|[Visual C++ の紹介 (UNIX ユーザー向け)](introduction-to-visual-cpp-for-unix-users.md)|Visual C++ を初めて使用し、生産性を向上したい UNIX ユーザー向けの情報を提供します。|
|[UNIX から Win32 への移植](porting-from-unix-to-win32.md)|UNIX アプリケーションを Windows に移行するためのオプションについて説明します。|

## <a name="see-also"></a>関連項目

[Visual Studio での C++](../overview/visual-cpp-in-visual-studio.md)
