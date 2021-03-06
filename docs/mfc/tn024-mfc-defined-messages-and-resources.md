---
description: '詳細については、「テクニカルノート 24: MFC-Defined メッセージとリソース」を参照してください。'
title: 'テクニカル ノート 24: MFC で定義されているメッセージおよびリソース'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 7ead4d72588b9acae125cbe90be67d1e03230de8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215756"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>テクニカル ノート 24: MFC で定義されているメッセージおよびリソース

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

このメモでは、MFC で使用される内部の Windows メッセージとリソース形式について説明します。 この情報は、フレームワークの実装について説明し、アプリケーションのデバッグに役立ちます。 このような情報はすべて公式にサポートされていませんが、これらの情報の一部を高度な実装に使用することもできます。

このメモには、MFC のプライベート実装の詳細が含まれています。すべての内容は将来変更される可能性があります。 MFC のプライベート Windows メッセージは、1つのアプリケーションのスコープでのみ意味を持ちますが、将来はシステム全体のメッセージを格納するように変更されます。

MFC のプライベート Windows メッセージとリソースの種類の範囲は、Microsoft Windows によって確保されている予約済みの "システム" 範囲に含まれています。 現在、範囲内のすべての数値が使用されているわけではありません。将来、範囲内の新しい数値が使用される可能性があります。 現在使用されている数値は変更される可能性があります。

MFC のプライベート Windows メッセージは、>0x360 0x37F の範囲内にあります。

MFC プライベートリソースの種類は、0xF0 ~ >0xFF の範囲内です。

**MFC プライベート Windows メッセージ**

これらの Windows メッセージは、C++ 仮想関数の代わりに使用されます。この場合、ウィンドウオブジェクト間に比較的緩い結合が必要であり、C++ 仮想関数は適切ではありません。

これらのプライベート Windows メッセージと関連するパラメーター構造は、MFC プライベートヘッダー ' AFXPRIV.H で宣言されています。H '。 このヘッダーを含むコードは、ドキュメント化されていない動作に依存している可能性があり、MFC の将来のバージョンでは機能しない可能性があることに注意してください。

これらのメッセージのいずれかを処理する必要がある場合はまれに、ON_MESSAGE message map マクロを使用して、generic LRESULT/WPARAM/LPARAM 形式でメッセージを処理する必要があります。

**WM_QUERYAFXWNDPROC**

このメッセージは、作成中のウィンドウに送信されます。 これは、WndProc が AfxWndProc かどうかを判断する方法として、作成プロセスの早い段階で送信され **ます。AfxWndProc** は1を返します。

| パラメーターと戻り値 | 説明 |
|-|-|
|wParam|使用されていない|
|lParam|使用されていない|
|は、次の値は返します。|**AfxWndProc** によって処理された場合は1|

**WM_SIZEPARENT**

このメッセージは、サイズ変更 (を呼び出す呼び出し) 中に、フレームウィンドウによって直接の子に送信され、 `CFrameWnd::OnSize` `CFrameWnd::RecalcLayout` `CWnd::RepositionBars` フレームの周囲のコントロールバーの位置を変更します。 AFX_SIZEPARENTPARAMS 構造体には、親の現在使用可能なクライアントの四角形と、の再描画を最小化するために呼び出す HDWP (NULL の場合もあります) が含まれ `DeferWindowPos` ます。

| パラメーターと戻り値 | 説明 |
|-|-|
|wParam|使用されていない|
|lParam|AFX_SIZEPARENTPARAMS 構造体のアドレス|
|は、次の値は返します。|使用されていません (0)|

メッセージを無視すると、ウィンドウがレイアウトに含まれないことを示します。

**WM_SETMESSAGESTRING**

このメッセージはフレームウィンドウに送信され、ステータスバーのメッセージ行を更新するように要求されます。 文字列 ID または LPCSTR のいずれかを指定できます (両方を指定することはできません)。

| パラメーターと戻り値 | 説明 |
|-|-|
|wParam|文字列 ID (またはゼロ)|
|lParam|文字列の LPCSTR (または NULL)|
|は、次の値は返します。|使用されていません (0)|

**WM_IDLEUPDATECMDUI**

このメッセージは、アイドル時間に送信され、更新コマンドの UI ハンドラーのアイドルタイムの更新を実装します。 ウィンドウ (通常はコントロールバー) がメッセージを処理する場合は、 `CCmdUI` オブジェクト (または派生クラスのオブジェクト) を作成し、 `CCmdUI::DoUpdate` ウィンドウ内の各 "項目" に対してを呼び出します。 これにより、コマンドハンドラーチェーン内のオブジェクトの ON_UPDATE_COMMAND_UI ハンドラーが確認されます。

| パラメーターと戻り値 | 説明 |
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|使用されていません (0)|
|は、次の値は返します。|使用されていません (0)|

ON_UPDATE_COMMAND_UI も ON_COMMAND ハンドラーも存在しない場合、 *Bdisableifnohandler* は0以外の場合、UI オブジェクトを無効にします。

**WM_EXITHELPMODE**

このメッセージは、 `CFrameWnd` 状況依存のヘルプモードを終了するにポストされます。 このメッセージの受信は、によって開始されたモーダルループを終了し `CFrameWnd::OnContextHelp` ます。

| パラメーターと戻り値 | 説明 |
|-|-|
|wParam|使用されていません (0)|
|lParam|使用されていません (0)|
|は、次の値は返します。|使用されていない|

**WM_INITIALUPDATE**

このメッセージは、最初の更新を実行するのが安全な場合に、ドキュメントテンプレートによってフレームウィンドウのすべての子孫に送信されます。 はの呼び出しにマップさ `CView::OnInitialUpdate` れますが、他の1回の更新では他の派生クラスで使用でき `CWnd` ます。

| パラメーターと戻り値 | 説明 |
|-|-|
|wParam|使用されていません (0)|
|lParam|使用されていません (0)|
|は、次の値は返します。|使用されていません (0)|

**WM_RECALCPARENT**

このメッセージは、(を通じて取得された) 親ウィンドウにビューによって送信され、 `GetParent` レイアウトの再計算を強制的に実行します (通常は親がを呼び出し `RecalcLayout` ます)。 これは、ビューの合計サイズが大きくなるにつれてフレームのサイズを大きくする必要がある OLE サーバーアプリケーションで使用されます。

親ウィンドウがこのメッセージを処理する場合は、TRUE を返し、クライアント領域の新しいサイズを使用して、lParam で渡された四角形に入力する必要があります。 これは、 `CScrollView` サーバーオブジェクトが埋め込み先でアクティブになっているときに、スクロールバーを正しく処理するためにで使用されます (その後、追加時にウィンドウの外側に配置されます)。

| パラメーターと戻り値 | 説明 |
|-|-|
|wParam|使用されていません (0)|
|lParam|LPRECT rectClient、NULL にすることができます|
|は、次の値は返します。|新しいクライアントの四角形が返された場合は TRUE、それ以外の場合は FALSE。|

**WM_SIZECHILD**

このメッセージは、ユーザーがサイズ変更ハンドルを使用してサイズ変更バーのサイズを変更したときに、によって `COleResizeBar` (経由で) 所有者ウィンドウに送信され `GetOwner` ます。 `COleIPFrameWnd` ユーザーが要求したときにフレームウィンドウの位置を変更しようとすることによって、このメッセージに応答します。

新しい四角形が、サイズ変更バーを含むフレームウィンドウに対して相対的に指定されている場合は、lParam によって示されます。

| パラメーターと戻り値 | 説明 |
|-|-|
|wParam|使用されていません (0)|
|lParam|LPRECT rectNew|
|は、次の値は返します。|使用されていません (0)|

**WM_DISABLEMODAL**

このメッセージは、非アクティブ化されているフレームウィンドウによって所有されているすべてのポップアップウィンドウに送信されます。 フレームウィンドウでは、結果を使用して、ポップアップウィンドウを無効にするかどうかを判断します。

これを使用すると、フレームがモーダル状態になるとき、または特定のポップアップウィンドウが無効になるのを防ぐために、ポップアップウィンドウで特殊な処理を実行できます。 ツールヒントは、フレームウィンドウがモーダル状態になったときに、このメッセージを使用して自分自身を破棄します (たとえば、)。

| パラメーターと戻り値 | 説明 |
|-|-|
|wParam|使用されていません (0)|
|lParam|使用されていません (0)|
|は、次の値は返します。|0以外の場合、ウィンドウを無効にし **ない** でください。0は、ウィンドウが無効になることを示します。|

**WM_FLOATSTATUS**

このメッセージは、フレームがアクティブになっているか、別のトップレベルのフレームウィンドウによって非アクティブにされたときに、フレームウィンドウによって所有されているすべてのポップアップウィンドウに送信されます。 これは、の MFS_SYNCACTIVE の実装によって使用され `CMiniFrameWnd` ます。これらのポップアップウィンドウのアクティブ化を、最上位レベルのフレームウィンドウのアクティブ化と同期させます。

| パラメーター | 説明 |
|-|-|
|wParam|次のいずれかの値を指定します。<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|使用されていません (0)|

FS_SYNCACTIVE が設定されていて、ウィンドウが親フレームを使用してアクティブ化を syncronizes 場合、戻り値は0以外である必要があります。 `CMiniFrameWnd` スタイルが MFS_SYNCACTIVE に設定されている場合は、0以外の値を返します。

詳細については、「の実装」を参照してください `CMiniFrameWnd` 。

## <a name="wm_activatetoplevel"></a>WM_ACTIVATETOPLEVEL

このメッセージは、"最上位グループ" のウィンドウがアクティブ化または非アクティブ化されたときにトップレベルのウィンドウに送信されます。 最上位レベルのウィンドウ (親または所有者が存在しない) である場合、またはウィンドウがそのウィンドウによって所有されている場合、ウィンドウはトップレベルグループの一部です。 このメッセージは WM_ACTIVATEAPP に使用されるのと似ていますが、異なるプロセスに属するウィンドウが1つのウィンドウ階層 (OLE アプリケーションでは共通) に混在している場合にも機能します。

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP、WM_HELPHITTEST、WM_EXITHELPMODE

これらのメッセージは、状況依存のヘルプの実装で使用されます。 詳細については、 [テクニカルノート 28](../mfc/tn028-context-sensitive-help-support.md) を参照してください。

## <a name="mfc-private-resource-formats"></a>MFC プライベートリソース形式

現在、MFC では、RT_TOOLBAR と RT_DLGINIT の2つのプライベートリソース形式が定義されています。

## <a name="rt_toolbar-resource-format"></a>RT_TOOLBAR リソース形式

AppWizard によって提供される既定のツールバーは、MFC 4.0 で導入された RT_TOOLBAR カスタムリソースに基づいています。 このリソースは、ツールバーエディターを使用して編集できます。

## <a name="rt_dlginit-resource-format"></a>RT_DLGINIT リソース形式

追加のダイアログ初期化情報を格納するために、1つの MFC プライベートリソース形式が使用されます。 これには、コンボボックスに格納されている最初の文字列が含まれます。 このリソースの形式は、手動で編集するように設計されていませんが、Visual C++ によって処理されます。

Visual C++ とこの RT_DLGINIT リソースでは、リソース内の情報を使用する API の代替手段があるため、MFC の関連機能を使用する必要はありません。 Visual C++ を使用すると、長時間実行されるアプリケーションの記述、保守、および変換が非常に簡単になります。

RT_DLGINIT リソースの基本的な構造は次のとおりです。

```
+---------------+    \
| Control ID    |   UINT             |
+---------------+    |
| Message #     |   UINT             |
+---------------+    |
|length of data |   DWORD            |
+---------------+    |   Repeated
|   Data        |   Variable Length  |   for each control
|   ...         |   and Format       |   and message
+---------------+    /
|     0         |   BYTE
+---------------+
```

繰り返されるセクションには、メッセージの送信先となるコントロール ID、送信するメッセージ # (通常の Windows メッセージ)、および可変長のデータが含まれます。 Windows メッセージは次の形式で送信されます。

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

これは非常に一般的な形式であり、Windows メッセージとデータコンテンツを許可します。 Visual C++ リソースエディターと MFC でサポートされるのは、Windows メッセージの限られたサブセットのみ CB_ADDSTRING です。コンボボックス (データはテキスト文字列) の最初の一覧を選択します。

## <a name="see-also"></a>関連項目

[番号別テクニカルノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカルノート](../mfc/technical-notes-by-category.md)
