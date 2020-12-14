---
description: '詳細情報: CEdit クラス'
title: CEdit Class
ms.date: 09/12/2018
f1_keywords:
- CEdit
- AFXWIN/CEdit
- AFXWIN/CEdit::CEdit
- AFXWIN/CEdit::CanUndo
- AFXWIN/CEdit::CharFromPos
- AFXWIN/CEdit::Clear
- AFXWIN/CEdit::Copy
- AFXWIN/CEdit::Create
- AFXWIN/CEdit::Cut
- AFXWIN/CEdit::EmptyUndoBuffer
- AFXWIN/CEdit::FmtLines
- AFXWIN/CEdit::GetCueBanner
- AFXWIN/CEdit::GetFirstVisibleLine
- AFXWIN/CEdit::GetHandle
- AFXWIN/CEdit::GetHighlight
- AFXWIN/CEdit::GetLimitText
- AFXWIN/CEdit::GetLine
- AFXWIN/CEdit::GetLineCount
- AFXWIN/CEdit::GetMargins
- AFXWIN/CEdit::GetModify
- AFXWIN/CEdit::GetPasswordChar
- AFXWIN/CEdit::GetRect
- AFXWIN/CEdit::GetSel
- AFXWIN/CEdit::HideBalloonTip
- AFXWIN/CEdit::LimitText
- AFXWIN/CEdit::LineFromChar
- AFXWIN/CEdit::LineIndex
- AFXWIN/CEdit::LineLength
- AFXWIN/CEdit::LineScroll
- AFXWIN/CEdit::Paste
- AFXWIN/CEdit::PosFromChar
- AFXWIN/CEdit::ReplaceSel
- AFXWIN/CEdit::SetCueBanner
- AFXWIN/CEdit::SetHandle
- AFXWIN/CEdit::SetHighlight
- AFXWIN/CEdit::SetLimitText
- AFXWIN/CEdit::SetMargins
- AFXWIN/CEdit::SetModify
- AFXWIN/CEdit::SetPasswordChar
- AFXWIN/CEdit::SetReadOnly
- AFXWIN/CEdit::SetRect
- AFXWIN/CEdit::SetRectNP
- AFXWIN/CEdit::SetSel
- AFXWIN/CEdit::SetTabStops
- AFXWIN/CEdit::ShowBalloonTip
- AFXWIN/CEdit::Undo
helpviewer_keywords:
- CEdit [MFC], CEdit
- CEdit [MFC], CanUndo
- CEdit [MFC], CharFromPos
- CEdit [MFC], Clear
- CEdit [MFC], Copy
- CEdit [MFC], Create
- CEdit [MFC], Cut
- CEdit [MFC], EmptyUndoBuffer
- CEdit [MFC], FmtLines
- CEdit [MFC], GetCueBanner
- CEdit [MFC], GetFirstVisibleLine
- CEdit [MFC], GetHandle
- CEdit [MFC], GetHighlight
- CEdit [MFC], GetLimitText
- CEdit [MFC], GetLine
- CEdit [MFC], GetLineCount
- CEdit [MFC], GetMargins
- CEdit [MFC], GetModify
- CEdit [MFC], GetPasswordChar
- CEdit [MFC], GetRect
- CEdit [MFC], GetSel
- CEdit [MFC], HideBalloonTip
- CEdit [MFC], LimitText
- CEdit [MFC], LineFromChar
- CEdit [MFC], LineIndex
- CEdit [MFC], LineLength
- CEdit [MFC], LineScroll
- CEdit [MFC], Paste
- CEdit [MFC], PosFromChar
- CEdit [MFC], ReplaceSel
- CEdit [MFC], SetCueBanner
- CEdit [MFC], SetHandle
- CEdit [MFC], SetHighlight
- CEdit [MFC], SetLimitText
- CEdit [MFC], SetMargins
- CEdit [MFC], SetModify
- CEdit [MFC], SetPasswordChar
- CEdit [MFC], SetReadOnly
- CEdit [MFC], SetRect
- CEdit [MFC], SetRectNP
- CEdit [MFC], SetSel
- CEdit [MFC], SetTabStops
- CEdit [MFC], ShowBalloonTip
- CEdit [MFC], Undo
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
ms.openlocfilehash: 8dbf5ffd05473720682703a9f309f8483591f143
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184687"
---
# <a name="cedit-class"></a>CEdit Class

Windows のエディット コントロールの機能が用意されています。

## <a name="syntax"></a>構文

```
class CEdit : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CEdit:: CEdit](#cedit)|`CEdit`コントロールオブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CEdit:: CanUndo](#canundo)|エディットコントロール操作を元に戻すことができるかどうかを判断します。|
|[CEdit:: CharFromPos](#charfrompos)|指定した位置に最も近い文字の行と文字のインデックスを取得します。|
|[CEdit:: Clear](#clear)|エディットコントロール内の現在の選択項目 (存在する場合) を削除 (クリア) します。|
|[CEdit:: コピー](#copy)|エディットコントロール内の現在の選択項目 (存在する場合) を CF_TEXT 形式でクリップボードにコピーします。|
|[CEdit:: Create](#create)|Windows のエディットコントロールを作成し、オブジェクトにアタッチし `CEdit` ます。|
|[CEdit:: Cut](#cut)|エディットコントロール内の現在の選択項目 (存在する場合) を削除 (切り取り) し、削除されたテキストを CF_TEXT 形式でクリップボードにコピーします。|
|[CEdit:: EmptyUndoBuffer](#emptyundobuffer)|エディットコントロールの元に戻すフラグをリセット (クリア) します。|
|[CEdit:: FmtLines](#fmtlines)|複数行のエディットコントロール内でソフト改行文字を含めるか無効にするかを設定します。|
|[CEdit:: GetCueBanner](#getcuebanner)|コントロールが空でフォーカスがない場合に、エディットコントロールにテキストキュー (ヒント) として表示されるテキストを取得します。|
|[CEdit:: GetFirstVisibleLine](#getfirstvisibleline)|エディットコントロールで最上位に表示される行を決定します。|
|[CEdit:: GetHandle](#gethandle)|複数行のエディットコントロールに現在割り当てられているメモリのハンドルを取得します。|
|[CEdit:: GetHighlight](#gethighlight)|現在の編集コントロールで強調表示されているテキスト範囲内の開始文字と終了文字のインデックスを取得します。|
|[CEdit:: GetLimitText](#getlimittext)|このに格納できるテキストの最大量を取得し `CEdit` ます。|
|[CEdit:: GetLine](#getline)|エディットコントロールからテキスト行を取得します。|
|[CEdit:: GetLineCount](#getlinecount)|複数行のエディットコントロールの行数を取得します。|
|[CEdit:: GetMargins](#getmargins)|このの左右の余白を取得し `CEdit` ます。|
|[CEdit:: GetModify](#getmodify)|エディットコントロールの内容が変更されているかどうかを判断します。|
|[CEdit:: GetPasswordChar](#getpasswordchar)|ユーザーがテキストを入力したときに編集コントロールに表示されるパスワード文字を取得します。|
|[CEdit:: GetRect](#getrect)|エディットコントロールの書式指定用の四角形を取得します。|
|[CEdit:: GetSel](#getsel)|エディットコントロール内の現在の選択範囲の最初と最後の文字位置を取得します。|
|[CEdit:: HideBalloonTip](#hideballoontip)|現在の編集コントロールに関連付けられているバルーンヒントを非表示にします。|
|[CEdit:: LimitText](#limittext)|ユーザーが編集コントロールに入力できるテキストの長さを制限します。|
|[CEdit:: LineFromChar](#linefromchar)|指定した文字インデックスを含む行の行番号を取得します。|
|[CEdit:: LineIndex](#lineindex)|複数行のエディットコントロール内の行の文字インデックスを取得します。|
|[CEdit:: LineLength](#linelength)|エディットコントロールの行の長さを取得します。|
|[CEdit:: LineScroll](#linescroll)|複数行のエディットコントロールのテキストをスクロールします。|
|[CEdit::P aste](#paste)|クリップボードのデータを現在のカーソル位置にあるエディットコントロールに挿入します。 クリップボードに CF_TEXT 形式のデータが含まれている場合にのみ、データが挿入されます。|
|[CEdit::P osFromChar](#posfromchar)|指定した文字インデックスの左上隅の座標を取得します。|
|[CEdit:: ReplaceSel](#replacesel)|エディットコントロール内の現在の選択項目を指定したテキストに置き換えます。|
|[CEdit:: SetCueBanner](#setcuebanner)|コントロールが空でフォーカスがない場合に、エディットコントロールにテキストキュー (ヒント) として表示されるテキストを設定します。|
|[CEdit:: SetHandle](#sethandle)|複数行のエディットコントロールで使用されるローカルメモリのハンドルを設定します。|
|[CEdit:: SetHighlight](#sethighlight)|現在の編集コントロールに表示されるテキストの範囲を強調表示します。|
|[CEdit:: SetLimitText](#setlimittext)|このに含めることができるテキストの最大量を設定 `CEdit` します。|
|[CEdit:: SetMargins](#setmargins)|このの左右の余白を設定 `CEdit` します。|
|[CEdit:: SetModify](#setmodify)|エディットコントロールの変更フラグを設定または解除します。|
|[CEdit:: SetPasswordChar](#setpasswordchar)|ユーザーがテキストを入力したときに編集コントロールに表示されるパスワード文字を設定または削除します。|
|[CEdit:: SetReadOnly](#setreadonly)|エディットコントロールの読み取り専用の状態を設定します。|
|[CEdit:: SetRect](#setrect)|複数行のエディットコントロールの書式指定用の四角形を設定し、コントロールを更新します。|
|[CEdit:: SetRectNP](#setrectnp)|コントロールウィンドウを再描画せずに、複数行のエディットコントロールの書式指定用の四角形を設定します。|
|[CEdit:: SetSel](#setsel)|エディットコントロール内の文字の範囲を選択します。|
|[CEdit:: SetTabStops](#settabstops)|複数行のエディットコントロールでタブストップを設定します。|
|[CEdit:: ShowBalloonTip](#showballoontip)|現在の編集コントロールに関連付けられているバルーンヒントを表示します。|
|[CEdit:: 元に戻す](#undo)|最後の編集コントロール操作を元に戻します。|

## <a name="remarks"></a>解説

エディットコントロールは、ユーザーがテキストを入力できる四角形の子ウィンドウです。

エディットコントロールは、ダイアログテンプレートから作成することも、コード内で直接作成することもできます。 どちらの場合も、最初にコンストラクターを呼び出してオブジェクトを構築し、 `CEdit` `CEdit` 次に [create](#create) member 関数を呼び出して Windows のエディットコントロールを作成し、それをオブジェクトにアタッチし `CEdit` ます。

構築は、から派生したクラスの1ステップのプロセスにすることができ `CEdit` ます。 派生クラスのコンストラクターを記述し、 `Create` コンストラクター内からを呼び出します。

`CEdit` は、の重要な機能を継承 `CWnd` します。 オブジェクトのテキストを設定および取得するには、 `CEdit` `CWnd` メンバー関数 [SetWindowText](cwnd-class.md#setwindowtext) と [getwindowtext](cwnd-class.md#getwindowtext)を使用します。これにより、複数行のコントロールであっても、エディットコントロールの内容全体が設定または取得されます。 複数行コントロールのテキスト行は、"\r\n" 文字シーケンスで区切られます。 また、編集コントロールが複数行の場合は、 `CEdit` [getline](#getline)、 [SetSel](#setsel)、 [getline](#getsel)、および [replacesel](#replacesel)メンバー関数を呼び出すことによって、コントロールのテキストの一部を取得して設定します。

編集コントロールから親 (通常はから派生したクラス) に送信される Windows 通知メッセージを処理する場合は `CDialog` 、各メッセージの親クラスにメッセージマップエントリとメッセージハンドラーメンバー関数を追加します。

各メッセージマップエントリには、次の形式があります。

  **ON_**_通知_**(** _id_**,** _memberFxn_ **)**

`id`は、通知を送信する編集コントロールの子ウィンドウ ID を指定し `memberFxn` ます。は、通知を処理するために記述した親メンバー関数の名前です。

親の関数プロトタイプは次のとおりです。

**afx_msg** void memberFxn **();**

次に示すのは、潜在的なメッセージマップエントリの一覧と、親に送信される可能性のあるケースの説明です。

- ユーザーが編集コントロールのテキストを変更した可能性のあるアクションを実行した ON_EN_CHANGE。 EN_UPDATE 通知メッセージとは異なり、この通知メッセージは Windows がディスプレイを更新した後に送信されます。

- ON_EN_ERRSPACE の編集コントロールは、特定の要求を満たすのに十分なメモリを割り当てることができません。

- ユーザーが編集コントロールの水平スクロールバーをクリック ON_EN_HSCROLL ます。 親ウィンドウには、画面が更新される前に通知されます。

- エディットコントロール ON_EN_KILLFOCUS 入力フォーカスを失います。

- 現在の挿入がエディットコントロールの指定された文字数を超えたため、切り捨てられた ON_EN_MAXTEXT。 また、エディットコントロールに ES_AUTOHSCROLL スタイルが設定されておらず、挿入される文字数がエディットコントロールの幅を超える場合にも送信されます。 また、エディットコントロールに ES_AUTOVSCROLL スタイルが設定されておらず、テキストの挿入によって生成される行の合計数がエディットコントロールの高さを超える場合にも送信されます。

- ON_EN_SETFOCUS、エディットコントロールが入力フォーカスを受け取ったときに送信されます。

- エディットコントロールが変更されたテキストを表示しようとしている ON_EN_UPDATE。 コントロールがテキストを書式設定した後、必要に応じてウィンドウサイズを変更できるように、テキストを表示する前に送信されます。

- ユーザーが編集コントロールの垂直スクロールバーをクリック ON_EN_VSCROLL ます。 親ウィンドウには、画面が更新される前に通知されます。

ダイアログボックス内にオブジェクトを作成すると、 `CEdit` `CEdit` ユーザーがダイアログボックスを閉じたときにオブジェクトが自動的に破棄されます。

ダイアログ `CEdit` エディターを使用してダイアログリソースからオブジェクトを作成すると、 `CEdit` ユーザーがダイアログボックスを閉じたときにオブジェクトが自動的に破棄されます。

ウィンドウ内にオブジェクトを作成する場合は `CEdit` 、そのオブジェクトを破棄することも必要になることがあります。 スタックにオブジェクトを作成すると `CEdit` 、そのオブジェクトは自動的に破棄されます。 関数を使用してヒープにオブジェクトを作成する場合は、 `CEdit` **`new`** **`delete`** ユーザーが Windows のエディットコントロールを終了したときにオブジェクトを破棄するために、を呼び出す必要があります。 オブジェクトにメモリを割り当てる場合は、デストラクターをオーバーライドして `CEdit` `CEdit` 割り当てを破棄します。

ES_READONLY などの編集コントロールで特定のスタイルを変更するには、 [Modifystyle](cwnd-class.md#modifystyle)を使用する代わりに、特定のメッセージをコントロールに送信する必要があります。 「Windows SDK での [コントロールスタイルの編集](/windows/win32/Controls/edit-control-styles) 」を参照してください。

の詳細につい `CEdit` ては、「 [コントロール](../../mfc/controls-mfc.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>要件

**ヘッダー:** afxwin.h

## <a name="ceditcanundo"></a><a name="canundo"></a> CEdit:: CanUndo

最後の編集操作を元に戻すことができるかどうかを判断するには、この関数を呼び出します。

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>戻り値

メンバー関数の呼び出しによって最後の編集操作を元に戻すことができる場合は0以外の場合は。 `Undo` 元に戻すことができない場合は0。

### <a name="remarks"></a>解説

詳細については、Windows SDK の「 [EM_CANUNDO](/windows/win32/Controls/em-canundo) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: Undo](#undo)」の例を参照してください。

## <a name="ceditcedit"></a><a name="cedit"></a> CEdit:: CEdit

`CEdit` オブジェクトを構築します。

```
CEdit();
```

### <a name="remarks"></a>解説

[Create](#create)を使用して、Windows のエディットコントロールを構築します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a> CEdit:: CharFromPos

このコントロール内の指定された位置に最も近い文字の0から始まる行と文字のインデックスを取得するには、この関数を呼び出します。 `CEdit`

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>パラメーター

*pt*<br/>
このオブジェクトのクライアント領域内の点の座標 `CEdit` 。

### <a name="return-value"></a>戻り値

下位ワードの文字インデックス、および上位ワード内の行のインデックスです。

### <a name="remarks"></a>解説

> [!NOTE]
> このメンバー関数は、Windows 95 および Windows NT 4.0 から使用できます。

詳細については、Windows SDK の「 [EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a> CEdit:: Clear

エディットコントロール内の現在の選択項目 (存在する場合) を削除する場合は、この関数を呼び出します。

```cpp
void Clear();
```

### <a name="remarks"></a>解説

によって実行される削除は、 `Clear` [Undo](#undo) メンバー関数を呼び出すことによって元に戻すことができます。

現在の選択範囲を削除し、削除された内容をクリップボードに配置するには、 [Cut](#cut) メンバー関数を呼び出します。

詳細については、Windows SDK の「 [WM_CLEAR](/windows/win32/dataxchg/wm-clear) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a> CEdit:: コピー

エディットコントロール内の現在の選択項目を CF_TEXT 形式でクリップボードにコピーするには、この関数を呼び出します。

```cpp
void Copy();
```

### <a name="remarks"></a>解説

詳細については、Windows SDK の「 [WM_COPY](/windows/win32/dataxchg/wm-copy) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a> CEdit:: Create

Windows のエディットコントロールを作成し、オブジェクトにアタッチし `CEdit` ます。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
エディットコントロールのスタイルを指定します。 [編集スタイル](styles-used-by-mfc.md#edit-styles)の任意の組み合わせをコントロールに適用します。

*rect*<br/>
エディットコントロールのサイズと位置を指定します。 は、 `CRect` オブジェクトまたは構造体にすることができ `RECT` ます。

*pParentWnd*<br/>
エディットコントロールの親ウィンドウ (通常は) を指定し `CDialog` ます。 NULL にすることはできません。

*nID*<br/>
エディットコントロールの ID を指定します。

### <a name="return-value"></a>戻り値

初期化が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

オブジェクトを構築するには、 `CEdit` 2 つの手順を実行します。 まず、コンストラクターを呼び出し、 `CEdit` 次に `Create` を呼び出します。これにより、Windows のエディットコントロールが作成され、オブジェクトにアタッチさ `CEdit` れます。

を実行すると、 `Create` Windows は [WM_NCCREATE](/windows/win32/winmsg/wm-nccreate)、 [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize)、 [WM_CREATE](/windows/win32/winmsg/wm-create)、および [WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo) のメッセージを編集コントロールに送信します。

これらのメッセージは、既定では、基本クラスの [OnNcCreate](cwnd-class.md#onnccreate)、 [OnNcCalcSize](cwnd-class.md#onnccalcsize)、 [OnCreate](cwnd-class.md#oncreate)、および [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) の各メンバー関数によって処理され `CWnd` ます。 既定のメッセージ処理を拡張するには、からクラスを派生させ、 `CEdit` 新しいクラスにメッセージマップを追加して、上記のメッセージハンドラーメンバー関数をオーバーライドします。 `OnCreate`たとえば、新しいクラスに必要な初期化を実行する場合は、をオーバーライドします。

次の [ウィンドウスタイル](styles-used-by-mfc.md#window-styles) を編集コントロールに適用します。

- 常に WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED はまれ

- グループコントロールに WS_GROUP

- タブオーダーにエディットコントロールを含める WS_TABSTOP

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a> CEdit:: Cut

エディットコントロール内の現在の選択範囲を削除 (切り取り) し、削除されたテキストを CF_TEXT 形式でクリップボードにコピーするには、この関数を呼び出します。

```cpp
void Cut();
```

### <a name="remarks"></a>解説

によって実行される削除は、 `Cut` [Undo](#undo) メンバー関数を呼び出すことによって元に戻すことができます。

削除されたテキストをクリップボードに配置せずに現在の選択項目を削除するには、 [Clear](#clear) メンバー関数を呼び出します。

詳細については、Windows SDK の「 [WM_CUT](/windows/win32/dataxchg/wm-cut) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a> CEdit:: EmptyUndoBuffer

この関数を呼び出して、エディットコントロールの元に戻すフラグをリセット (クリア) します。

```cpp
void EmptyUndoBuffer();
```

### <a name="remarks"></a>解説

エディットコントロールは、最後の操作を元に戻すことができなくなります。 元に戻すフラグは、エディットコントロール内の操作を元に戻すことができる場合に設定されます。

Undo フラグは、 [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)または[SetHandle](#sethandle) `CWnd` メンバー関数が呼び出されるたびに自動的にクリアされます。

詳細については、Windows SDK の「 [EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a> CEdit:: FmtLines

この関数を呼び出して、複数行のエディットコントロール内でソフト改行文字を含めるか無効にするかを設定します。

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>パラメーター

*bAddEOL*<br/>
ソフト改行文字を挿入するかどうかを指定します。 値が TRUE の場合は、文字が挿入されます。値が FALSE の場合は、削除されます。

### <a name="return-value"></a>戻り値

書式設定が行われる場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

ソフトライン改行は、2つのキャリッジリターンと、単語の折り返しによって改行される行の末尾に挿入される改行で構成されます。 ハード改行は、1つのキャリッジリターンとラインフィードで構成されます。 ハード改行で終わる行は、による影響を受けません `FmtLines` 。

ウィンドウは、 `CEdit` オブジェクトが複数行のエディットコントロールである場合にのみ応答します。

`FmtLines` は、 [GetHandle](#gethandle) によって返されるバッファーと [WM_GETTEXT](/windows/win32/winmsg/wm-gettext)によって返されるテキストにのみ影響します。 エディットコントロール内のテキストの表示には影響しません。

詳細については、Windows SDK の「 [EM_FMTLINES](/windows/win32/Controls/em-fmtlines) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a> CEdit:: GetCueBanner

コントロールが空の場合に、エディットコントロールにテキストキュー (ヒント) として表示されるテキストを取得します。

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
入出力キューテキストを含む文字列へのポインター。

*cchText*<br/>
から受信できる文字数。 この数値には、終端の NULL 文字が含まれます。

### <a name="return-value"></a>戻り値

最初のオーバーロードの場合は、メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

2番目のオーバーロードでは、メソッドが成功した場合は、キューのテキストを含む [CString](../../atl-mfc-shared/using-cstring.md) です。それ以外の場合は、空の文字列 ("") です。

### <a name="remarks"></a>解説

このメソッドは、Windows SDK で説明されている [EM_GETCUEBANNER](/windows/win32/Controls/em-getcuebanner) メッセージを送信します。 詳細については、 [Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext) マクロを参照してください。

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a> CEdit:: GetFirstVisibleLine

この関数を呼び出して、エディットコントロールで最上位に表示される行を決定します。

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>戻り値

最上位の行の0から始まるインデックス。 単一行エディットコントロールの場合、戻り値は0です。

### <a name="remarks"></a>解説

詳細については、Windows SDK の「 [EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a> CEdit:: GetHandle

この関数を呼び出して、複数行のエディットコントロールに現在割り当てられているメモリのハンドルを取得します。

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>戻り値

エディットコントロールの内容を保持しているバッファーを識別するローカルメモリハンドル。 単一行のエディットコントロールにメッセージを送信するなどのエラーが発生した場合、戻り値は0です。

### <a name="remarks"></a>解説

ハンドルはローカルメモリハンドルであり、ローカルメモリハンドルをパラメーターとして受け取る **ローカル** の Windows メモリ関数のいずれかによって使用される場合があります。

`GetHandle` は、複数行のエディットコントロールによってのみ処理されます。

ダイアログボックスが `GetHandle` DS_LOCALEDIT スタイルフラグが設定された状態で作成された場合にのみ、ダイアログボックスで複数行のエディットコントロールを呼び出します。 DS_LOCALEDIT スタイルが設定されていない場合でも、0以外の戻り値は取得されますが、戻り値を使用することはできません。

> [!NOTE]
> `GetHandle` Windows 95/98 では機能しません。 Windows 95/98 でを呼び出すと `GetHandle` 、NULL が返されます。 `GetHandle` は、「Windows NT バージョン3.51 以降」に記載されているとおりに動作します。

詳細については、Windows SDK の「 [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a> CEdit:: GetHighlight

現在の編集コントロールで強調表示されているテキスト範囲内の最初と最後の文字のインデックスを取得します。

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>パラメーター

*ピクチャの開始*\
入出力強調表示されているテキスト範囲内の最初の文字の0から始まるインデックス番号。

*ピクチャの終了*\
入出力強調表示されているテキスト範囲内の最後の文字の0から始まるインデックス番号。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

このメソッドは、Windows SDK で説明されている [EM_GETHILITE](/windows/win32/Controls/em-gethilite) メッセージを送信します。 `SetHighlight`とはどちらも、 `GetHighlight` 現在 UNICODE ビルドでのみ有効です。

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a> CEdit:: GetLimitText

このメンバー関数を呼び出して、このオブジェクトのテキスト制限を取得し `CEdit` ます。

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>戻り値

このオブジェクトの現在のテキストの制限 (TCHARs) `CEdit` 。

### <a name="remarks"></a>解説

テキストの上限は、エディットコントロールが受け入れることができるテキストの最大サイズ (TCHARs 単位) です。

> [!NOTE]
> このメンバー関数は、Windows 95 および Windows NT 4.0 から使用できます。

詳細については、Windows SDK の「 [EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a> CEdit:: GetLine

この関数を呼び出して、エディットコントロールからテキスト行を取得し、 *Lpszbuffer* に配置します。

```
int GetLine(
    int nIndex,
    LPTSTR lpszBuffer) const;

int GetLine(
    int nIndex,
    LPTSTR lpszBuffer,
    int nMaxLength) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
複数行のエディットコントロールから取得する行番号を指定します。 行番号は0から始まります。値0は最初の行を指定します。 このパラメーターは、単一行のエディットコントロールでは無視されます。

*lpszBuffer*<br/>
行のコピーを受け取るバッファーを指します。 バッファーの最初の単語では、バッファーにコピーできる TCHARs の最大数を指定する必要があります。

*nMaxLength*<br/>
バッファーにコピーできる TCHAR 文字の最大数を指定します。 `GetLine` Windows の呼び出しを行う前に、 *Lpszbuffer* の最初の単語にこの値を配置します。

### <a name="return-value"></a>戻り値

実際にコピーされた文字数。 *NIndex* によって指定された行番号がエディットコントロールの行数よりも大きい場合、戻り値は0です。

### <a name="remarks"></a>解説

コピーされた行に null 終端文字が含まれていません。

詳細については、Windows SDK の「 [EM_GETLINE](/windows/win32/Controls/em-getline) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: GetLineCount](#getlinecount)」の例を参照してください。

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a> CEdit:: GetLineCount

この関数を呼び出して、複数行のエディットコントロールの行数を取得します。

```
int GetLineCount() const;
```

### <a name="return-value"></a>戻り値

複数行のエディットコントロールの行数を格納している整数。 エディットコントロールにテキストが入力されていない場合、戻り値は1です。

### <a name="remarks"></a>解説

`GetLineCount` は、複数行のエディットコントロールによってのみ処理されます。

詳細については、Windows SDK の「 [EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a> CEdit:: GetMargins

このメンバー関数を呼び出して、この編集コントロールの左右の余白を取得します。

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>戻り値

下位ワードの左余白の幅、および上位の単語の右余白の幅です ()。

### <a name="remarks"></a>解説

余白はピクセル単位で計測されます。

> [!NOTE]
> このメンバー関数は、Windows 95 および Windows NT 4.0 から使用できます。

詳細については、Windows SDK の「 [EM_GETMARGINS](/windows/win32/Controls/em-getmargins) 」を参照してください。

### <a name="example"></a>例

  [CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl)の例を参照してください。

## <a name="ceditgetmodify"></a><a name="getmodify"></a> CEdit:: GetModify

この関数を呼び出して、エディットコントロールの内容が変更されているかどうかを確認します。

```
BOOL GetModify() const;
```

### <a name="return-value"></a>戻り値

編集コントロールの内容が変更されている場合は0以外の。変更されていない場合は0。

### <a name="remarks"></a>解説

Windows は、エディットコントロールの内容が変更されているかどうかを示す内部フラグを保持します。 このフラグは、エディットコントロールが最初に作成されたときにクリアされ、 [Setmodify](#setmodify) メンバー関数を呼び出すことによってクリアすることもできます。

詳細については、Windows SDK の「 [EM_GETMODIFY](/windows/win32/Controls/em-getmodify) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a> CEdit:: GetPasswordChar

ユーザーがテキストを入力したときに編集コントロールに表示されるパスワード文字を取得するには、この関数を呼び出します。

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>戻り値

ユーザーが入力した文字の代わりに表示される文字を指定します。 パスワード文字が存在しない場合、戻り値は NULL になります。

### <a name="remarks"></a>解説

ES_PASSWORD スタイルでエディットコントロールを作成すると、コントロールをサポートする DLL によって既定のパスワード文字が決定されます。 マニフェストまたは [Initcommoncontrolsex](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) メソッドは、どの DLL がエディットコントロールをサポートしているかを判断します。 user32.dll がエディットコントロールをサポートしている場合、既定のパスワード文字はアスタリスク (' * ', U + 002A) です。 バージョン 6 comctl32.dll がエディットコントロールをサポートしている場合、既定の文字は黒の円 (' ● ', U + 25CF) です。 共通コントロールをサポートしている DLL とバージョンの詳細については、「 [Shell および Common Controls Versions](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\))」を参照してください。

このメソッドは、Windows SDK で説明されている [EM_GETPASSWORDCHAR](/windows/win32/Controls/em-getpasswordchar) メッセージを送信します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a> CEdit:: GetRect

エディットコントロールの書式指定用の四角形を取得します。

```cpp
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
`RECT`書式指定四角形を受け取る構造体を指します。

### <a name="remarks"></a>解説

書式設定用の四角形は、エディットコントロールウィンドウのサイズに依存しない、テキストの限定された四角形です。

複数行のエディットコントロールの書式設定用の四角形は、 [SetRect](#setrect) および [SetRectNP](#setrectnp) メンバー関数によって変更できます。

詳細については、Windows SDK の「 [EM_GETRECT](/windows/win32/Controls/em-getrect) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: LimitText](#limittext)」の例を参照してください。

## <a name="ceditgetsel"></a><a name="getsel"></a> CEdit:: GetSel

戻り値またはパラメーターを使用して、エディットコントロール内の現在の選択範囲の開始文字位置と終了文字位置を取得します。

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>パラメーター

*nStartChar*<br/>
現在の選択範囲の最初の文字の位置を受け取る整数への参照。

*nEndChar*<br/>
現在の選択範囲の末尾を越えて最初に選択解除された文字の位置を受け取る整数への参照。

### <a name="return-value"></a>戻り値

DWORD を返すバージョンでは、下位ワードの開始位置を含む値、および上位ワードの選択範囲の終了後の最初の項目の位置を返します。

### <a name="remarks"></a>解説

詳細については、Windows SDK の「 [EM_GETSEL](/windows/win32/Controls/em-getsel) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a> CEdit:: HideBalloonTip

現在の編集コントロールに関連付けられているバルーンヒントを非表示にします。

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

この関数は、Windows SDK で説明されている [EM_HIDEBALLOONTIP](/windows/win32/Controls/em-hideballoontip) メッセージを送信します。

## <a name="ceditlimittext"></a><a name="limittext"></a> CEdit:: LimitText

ユーザーがエディットコントロールに入力できるテキストの長さを制限するには、この関数を呼び出します。

```cpp
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>パラメーター

*nChars*<br/>
ユーザーが入力できるテキストの長さ (TCHARs 単位) を指定します。 このパラメーターが0の場合、テキストの長さは UINT_MAX バイトに設定されます。 これが既定の動作です。

### <a name="remarks"></a>解説

テキストの制限を変更すると、ユーザーが入力できるテキストのみが制限されます。 エディットコントロールに既に存在するテキストには影響しません。また、の [SetWindowText](cwnd-class.md#setwindowtext) メンバー関数によってエディットコントロールにコピーされるテキストの長さにも影響しません `CWnd` 。 アプリケーションで関数を使用して、の `SetWindowText` 呼び出しで指定されたよりも多くのテキストを編集コントロールに配置する場合 `LimitText` 、ユーザーは編集コントロール内の任意のテキストを削除できます。 ただし、テキストの制限により、現在の選択範囲を削除してもテキストがテキストの上限を超えない限り、ユーザーは既存のテキストを新しいテキストに置き換えることができなくなります。

> [!NOTE]
> Win32 (Windows NT および Windows 95/98) では、 [Setlimittext](#setlimittext) はこの関数を置き換えます。

詳細については、Windows SDK の「 [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a> CEdit:: LineFromChar

この関数を呼び出して、指定した文字インデックスを含む行の行番号を取得します。

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
エディットコントロールのテキストに、目的の文字の0から始まるインデックス値を格納します。または、-1 を格納します。 *NIndex* が-1 の場合は、現在の行、つまり、カレットを含む行を指定します。

### <a name="return-value"></a>戻り値

*NIndex* によって指定された文字インデックスを含む行の0から始まる行番号。 *NIndex* が-1 の場合は、選択範囲の最初の文字を含む行の番号が返されます。 選択されていない場合は、現在の行番号が返されます。

### <a name="remarks"></a>解説

文字インデックスは、エディットコントロールの先頭からの文字数です。

このメンバー関数は、複数行のエディットコントロールによってのみ使用されます。

詳細については、Windows SDK の「 [EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a> CEdit:: LineIndex

この関数を呼び出して、複数行のエディットコントロール内の行の文字インデックスを取得します。

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>パラメーター

*N 行*<br/>
エディットコントロールのテキスト内の目的の行のインデックス値を格納します。または、-1 を格納します。 *N 行* が-1 の場合は、現在の行、つまり、カレットを含む行を指定します。

### <a name="return-value"></a>戻り値

*N 行* で指定された行の文字インデックス。または、指定した行番号が編集コントロールの行数よりも大きい場合は-1。

### <a name="remarks"></a>解説

文字インデックスは、エディットコントロールの先頭から指定した行までの文字数です。

このメンバー関数は、複数行のエディットコントロールによってのみ処理されます。

詳細については、Windows SDK の「 [EM_LINEINDEX](/windows/win32/controls/em-lineindex) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a> CEdit:: LineLength

エディットコントロールの行の長さを取得します。

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>パラメーター

*N 行*<br/>
長さを取得する行内の文字の0から始まるインデックス。 既定値は -1 です。

### <a name="return-value"></a>戻り値

単一行エディットコントロールの場合、戻り値は、エディットコントロール内のテキストの長さ (TCHARs 単位) です。

複数行のエディットコントロールの場合、戻り値は *n 行* パラメーターで指定された行の tchars の長さです。 ANSI テキストの場合、長さは行のバイト数です。Unicode テキストの場合、長さは行の文字数です。 長さには、行末の復帰文字は含まれません。

*N 行* パラメーターがコントロール内の文字数よりも大きい場合、戻り値は0になります。

*N 行* パラメーターが-1 の場合、戻り値は、選択された文字を含む行で選択されていない文字の数になります。 たとえば、1つの行の4番目の文字から、次の行の末尾の8番目の文字までを選択した場合、戻り値は10になります。 つまり、1行目に3文字、次に7つの文字があります。

TCHAR 型の詳細については、「 [Windows データ型](/windows/win32/WinProg/windows-data-types)」の表にある tchar 行を参照してください。

### <a name="remarks"></a>解説

このメソッドは、Windows SDK で説明されている [EM_LINELENGTH](/windows/win32/Controls/em-linelength) メッセージでサポートされています。

### <a name="example"></a>例

  「 [CEdit:: LineIndex](#lineindex)」の例を参照してください。

## <a name="ceditlinescroll"></a><a name="linescroll"></a> CEdit:: LineScroll

この関数を呼び出して、複数行のエディットコントロールのテキストをスクロールします。

```cpp
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>パラメーター

*nLines*<br/>
垂直方向にスクロールする行数を指定します。

*nChars*<br/>
水平方向にスクロールする文字位置の数を指定します。 エディットコントロールに ES_RIGHT スタイルまたは ES_CENTER スタイルが指定されている場合、この値は無視されます。

### <a name="remarks"></a>解説

このメンバー関数は、複数行のエディットコントロールによってのみ処理されます。

エディットコントロール内のテキストの最後の行を垂直方向にスクロールすることはできません。 現在の行と *nLines* で指定された行数が、エディットコントロールの行の合計数を超えた場合、エディットコントロールの最後の行が編集コントロールウィンドウの一番上にスクロールされるように値が調整されます。

`LineScroll` を使用すると、行の最後の文字を越えて水平方向にスクロールできます。

詳細については、Windows SDK の「 [EM_LINESCROLL](/windows/win32/Controls/em-linescroll) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: GetFirstVisibleLine](#getfirstvisibleline)」の例を参照してください。

## <a name="ceditpaste"></a><a name="paste"></a> CEdit::P aste

クリップボードから挿入ポイントのにデータを挿入するには、この関数を呼び出し `CEdit` ます。

```cpp
void Paste();
```

### <a name="remarks"></a>解説

クリップボードに CF_TEXT 形式のデータが含まれている場合にのみ、データが挿入されます。

詳細については、Windows SDK の「 [WM_PASTE](/windows/win32/dataxchg/wm-paste) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a> CEdit::P osFromChar

このオブジェクト内の特定の文字の位置 (左上隅) を取得するには、この関数を呼び出し `CEdit` ます。

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>パラメーター

*nChar*<br/>
指定した文字の0から始まるインデックス。

### <a name="return-value"></a>戻り値

*NChar* によって指定された文字の左上隅の座標。

### <a name="remarks"></a>解説

文字は、0から始まるインデックス値を指定することによって指定されます。 *NChar* がこのオブジェクトの最後の文字のインデックスよりも大きい場合 `CEdit` 、戻り値は、このオブジェクトの最後の文字の直後にある文字位置の座標を指定し `CEdit` ます。

> [!NOTE]
> このメンバー関数は、Windows 95 および Windows NT 4.0 から使用できます。

詳細については、Windows SDK の「 [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: LineFromChar](#linefromchar)」の例を参照してください。

## <a name="ceditreplacesel"></a><a name="replacesel"></a> CEdit:: ReplaceSel

エディットコントロールの現在の選択項目を、 *lpszNewText* で指定したテキストに置き換えるには、この関数を呼び出します。

```cpp
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>パラメーター

*lpszNewText*<br/>
置換テキストを含む null で終わる文字列を指します。

*bCanUndo*<br/>
この関数を元に戻すことができるように指定するには、このパラメーターの値を TRUE に設定します。 既定値は FALSE です。

### <a name="remarks"></a>解説

エディットコントロール内のテキストの一部だけを置換します。 すべてのテキストを置換する場合は、 [CWnd:: SetWindowText](cwnd-class.md#setwindowtext) メンバー関数を使用します。

現在選択されていない場合は、現在のカーソル位置に置換テキストが挿入されます。

詳細については、Windows SDK の「 [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: LineIndex](#lineindex)」の例を参照してください。

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a> CEdit:: SetCueBanner

コントロールが空の場合に、エディットコントロールにテキストキュー (ヒント) として表示されるテキストを設定します。

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
からエディットコントロールに表示するキューを含む文字列へのポインター。

*fDrawWhenFocused*<br/>
からFALSE の場合、ユーザーが編集コントロールをクリックしたときにキューバナーが描画されず、コントロールにフォーカスが移動します。

TRUE の場合、コントロールにフォーカスがあるときでも、キューバナーが描画されます。 ユーザーがコントロールの入力を開始すると、キューのバナーが表示されなくなります。

既定値は FALSE です。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

このメソッドは、Windows SDK で説明されている [EM_SETCUEBANNER](/windows/win32/Controls/em-setcuebanner) メッセージを送信します。 詳細については、 [Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused) マクロを参照してください。

### <a name="example"></a>例

次の例は、 [CEdit:: SetCueBanner](#setcuebanner) メソッドを示しています。

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a> CEdit:: SetHandle

この関数を呼び出して、複数行のエディットコントロールによって使用されるローカルメモリのハンドルを設定します。

```cpp
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>パラメーター

*hBuffer*<br/>
ローカルメモリへのハンドルを格納します。 このハンドルは、LMEM_MOVEABLE フラグを使用して、 [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) Windows 関数の前回の呼び出しによって作成されている必要があります。 メモリには、null で終わる文字列が含まれていると見なされます。 そうでない場合は、割り当てられたメモリの最初のバイトを0に設定する必要があります。

### <a name="remarks"></a>解説

エディットコントロールは、独自のバッファーを割り当てる代わりに、現在表示されているテキストを格納するために、このバッファーを使用します。

このメンバー関数は、複数行のエディットコントロールによってのみ処理されます。

アプリケーションで新しいメモリハンドルを設定する前に、 [GetHandle](#gethandle) メンバー関数を使用して、現在のメモリバッファーへのハンドルを取得し、Windows の関数を使用してそのメモリを解放する必要があり `LocalFree` ます。

`SetHandle` 元に戻すバッファー ( [Canundo](#canundo) メンバー関数は0を返します) をクリアし、内部変更フラグ ( [getmodify](#getmodify) メンバー関数は0を返します) をクリアします。 編集コントロールウィンドウが再描画されます。

このメンバー関数は、ダイアログボックスの複数行のエディットコントロールで、DS_LOCALEDIT スタイルフラグが設定されたダイアログボックスを作成した場合にのみ使用できます。

> [!NOTE]
> `GetHandle` Windows 95/98 では機能しません。 Windows 95/98 でを呼び出すと `GetHandle` 、NULL が返されます。 `GetHandle` は、「Windows NT バージョン3.51 以降」に記載されているとおりに動作します。

詳細については、Windows SDK の「 [EM_SETHANDLE](/windows/win32/Controls/em-sethandle)」、「 [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)」、および「 [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a> CEdit:: SetHighlight

現在の編集コントロールに表示されるテキストの範囲を強調表示します。

```cpp
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>パラメーター

*ichStart*\
から強調表示するテキスト範囲内の最初の文字の0から始まるインデックス番号。

*ichEnd*\
から強調表示するテキスト範囲内の最後の文字の0から始まるインデックス番号。

### <a name="remarks"></a>解説

このメソッドは、Windows SDK で説明されている [EM_SETHILITE](/windows/win32/Controls/em-sethilite) メッセージを送信します。  このメソッドは、Windows SDK で説明されている [EM_SETHILITE](/windows/win32/Controls/em-sethilite) メッセージを送信します。 `SetHighlight`とはどちらも、 `GetHighlight` UNICODE ビルドに対してのみ有効です。

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a> CEdit:: SetLimitText

このオブジェクトのテキスト制限を設定するには、このメンバー関数を呼び出し `CEdit` ます。

```cpp
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>パラメーター

*N1 日*<br/>
新しいテキストの制限値 (文字数)。

### <a name="remarks"></a>解説

Text 制限は、エディットコントロールが受け入れることができるテキストの最大量 (文字数) です。

テキストの制限を変更すると、ユーザーが入力できるテキストのみが制限されます。 エディットコントロールに既に存在するテキストには影響しません。また、の [SetWindowText](cwnd-class.md#setwindowtext) メンバー関数によってエディットコントロールにコピーされるテキストの長さにも影響しません `CWnd` 。 アプリケーションで関数を使用して、の `SetWindowText` 呼び出しで指定されたよりも多くのテキストを編集コントロールに配置する場合 `LimitText` 、ユーザーは編集コントロール内の任意のテキストを削除できます。 ただし、テキストの制限により、現在の選択範囲を削除してもテキストがテキストの上限を超えない限り、ユーザーは既存のテキストを新しいテキストに置き換えることができなくなります。

この関数は、Win32 の [Limittext](#limittext) を置き換えます。

詳細については、Windows SDK の「 [EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) 」を参照してください。

### <a name="example"></a>例

  [CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl)の例を参照してください。

## <a name="ceditsetmargins"></a><a name="setmargins"></a> CEdit:: SetMargins

このエディットコントロールの左右の余白を設定するには、このメソッドを呼び出します。

```cpp
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>パラメーター

*n 左*<br/>
新しい左余白の幅 (ピクセル単位)。

*nRight*<br/>
新しい右余白の幅 (ピクセル単位)。

### <a name="remarks"></a>解説

> [!NOTE]
> このメンバー関数は、Windows 95 および Windows NT 4.0 から使用できます。

詳細については、Windows SDK の「 [EM_SETMARGINS](/windows/win32/Controls/em-setmargins) 」を参照してください。

### <a name="example"></a>例

  [CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl)の例を参照してください。

## <a name="ceditsetmodify"></a><a name="setmodify"></a> CEdit:: SetModify

編集コントロールの変更されたフラグを設定またはクリアするには、この関数を呼び出します。

```cpp
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>パラメーター

*bModified*<br/>
値が TRUE の場合は、テキストが変更されたことを示します。値が FALSE の場合は、変更されていないことを示します。 既定では、modified フラグが設定されています。

### <a name="remarks"></a>解説

Modified フラグは、エディットコントロール内のテキストが変更されたかどうかを示します。 ユーザーがテキストを変更するたびに自動的に設定されます。 値を取得するには、 [Getmodify](#getmodify) メンバー関数を使用します。

詳細については、Windows SDK の「 [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: GetModify](#getmodify)」の例を参照してください。

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a> CEdit:: SetPasswordChar

ユーザーがテキストを入力したときに編集コントロールに表示されるパスワード文字を設定または削除するには、この関数を呼び出します。

```cpp
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>パラメーター

*ハーフ*<br/>
ユーザーが入力した文字の代わりに表示される文字を指定します。 *Ch* が0の場合は、ユーザーが入力した実際の文字が表示されます。

### <a name="remarks"></a>解説

パスワード文字を設定すると、ユーザーが入力した文字ごとにその文字が表示されます。

このメンバー関数は、複数行のエディットコントロールには影響しません。

`SetPasswordChar`メンバー関数が呼び出されると、 `CEdit` は、 *ch* によって指定された文字を使用して、表示されるすべての文字を再描画します。

エディットコントロールが [ES_PASSWORD](styles-used-by-mfc.md#edit-styles) スタイルで作成されている場合、既定のパスワード文字はアスタリスク () に設定され <strong>\*</strong> ます。 `SetPasswordChar` *Ch* を0に設定してを呼び出すと、このスタイルは削除されます。

詳細については、Windows SDK の「 [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a> CEdit:: SetReadOnly

エディットコントロールの読み取り専用の状態を設定するために、この関数を呼び出します。

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>パラメーター

*bReadOnly*<br/>
エディットコントロールの読み取り専用の状態を設定または削除するかどうかを指定します。 値が TRUE の場合は、状態が読み取り専用に設定されます。値が FALSE の場合、状態は読み取り/書き込みに設定されます。

### <a name="return-value"></a>戻り値

操作が成功した場合は0以外の場合は。エラーが発生した場合は0。

### <a name="remarks"></a>解説

現在の設定を検索するには、 [CWnd:: GetStyle](cwnd-class.md#getstyle)の戻り値の[ES_READONLY](styles-used-by-mfc.md#edit-styles)フラグをテストします。

詳細については、Windows SDK の「 [EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a> CEdit:: SetRect

この関数を呼び出して、指定した座標を使用して四角形の寸法を設定します。

```cpp
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
`RECT` `CRect` 書式指定用の四角形の新しい次元を指定する構造体またはオブジェクトを指します。

### <a name="remarks"></a>解説

このメンバーは、複数行のエディットコントロールによってのみ処理されます。

`SetRect`複数行のエディットコントロールの書式指定用の四角形を設定するには、を使用します。 書式設定用の四角形は、エディットコントロールウィンドウのサイズに依存しない、テキストの限定された四角形です。 エディットコントロールが最初に作成されたとき、書式設定の四角形は編集コントロールウィンドウのクライアント領域と同じになります。 メンバー関数を使用すると、 `SetRect` アプリケーションは、書式設定の四角形を編集コントロールウィンドウよりも大きくしたり小さくしたりすることができます。

エディットコントロールにスクロールバーがない場合、書式設定の四角形がウィンドウより大きい場合、テキストは切り取られずに切り取られます。 エディットコントロールに境界線が含まれている場合は、罫線のサイズによって書式設定の四角形が縮小されます。 メンバー関数によって返される四角形を調整する場合は、 `GetRect` 四角形をに渡す前に、境界線のサイズを削除する必要があり `SetRect` ます。

`SetRect`が呼び出されると、エディットコントロールのテキストも再フォーマットされ、再表示されます。

詳細については、Windows SDK の「 [EM_SETRECT](/windows/win32/Controls/em-setrect) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a> CEdit:: SetRectNP

複数行の編集コントロールの書式指定用の四角形を設定するには、この関数を呼び出します。

```cpp
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
`RECT` `CRect` 四角形の新しい寸法を指定する構造体またはオブジェクトを指します。

### <a name="remarks"></a>解説

書式設定用の四角形は、エディットコントロールウィンドウのサイズに依存しない、テキストの限定された四角形です。

`SetRectNP` は `SetRect` 、編集コントロールウィンドウが再描画されない点を除いて、メンバー関数と同じです。

エディットコントロールが最初に作成されたとき、書式設定の四角形は編集コントロールウィンドウのクライアント領域と同じになります。 アプリケーションでは、メンバー関数を呼び出すことにより、 `SetRectNP` 書式設定の四角形を編集コントロールウィンドウよりも大きくしたり小さくしたりすることができます。

エディットコントロールにスクロールバーがない場合、書式設定の四角形がウィンドウより大きい場合、テキストは切り取られずに切り取られます。

このメンバーは、複数行のエディットコントロールによってのみ処理されます。

詳細については、Windows SDK の「 [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: SetRect](#setrect)」の例を参照してください。

## <a name="ceditsetsel"></a><a name="setsel"></a> CEdit:: SetSel

エディットコントロール内の文字の範囲を選択するには、この関数を呼び出します。

```cpp
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>パラメーター

*dwSelection*<br/>
下位ワードの開始位置と上位ワードの終了位置を指定します。 下位ワードが0で、上位ワードが-1 の場合、エディットコントロール内のすべてのテキストが選択されます。 下位ワードが-1 の場合、現在の選択項目はすべて削除されます。

*bNoScroll*<br/>
キャレットをスクロールして表示するかどうかを示します。 FALSE の場合、キャレットはスクロールして表示されます。 TRUE の場合、キャレットはスクロールされずに表示されます。

*nStartChar*<br/>
開始位置を指定します。 *Nstartchar* が0で *nEndChar* が-1 の場合、エディットコントロール内のすべてのテキストが選択されます。 *Nstartchar* が-1 の場合、現在の選択はすべて削除されます。

*nEndChar*<br/>
終了位置を指定します。

### <a name="remarks"></a>解説

詳細については、Windows SDK の「 [EM_SETSEL](/windows/win32/Controls/em-setsel) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: GetSel](#getsel)」の例を参照してください。

## <a name="ceditsettabstops"></a><a name="settabstops"></a> CEdit:: SetTabStops

この関数を呼び出して、複数行のエディットコントロールでタブストップを設定します。

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>パラメーター

*cxEachStop*<br/>
すべての *cxEachStop* ダイアログ単位でタブストップを設定することを指定します。

*nTabStops*<br/>
*RgTabStops* に含まれるタブストップの数を指定します。 この数値は1より大きい値である必要があります。

*rgTabStops*<br/>
ダイアログ単位のタブストップを指定する符号なし整数の配列を指します。 ダイアログ単位は、水平方向または垂直方向の距離です。 水平ダイアログ単位は、現在のダイアログベースの幅の単位の1番目と同じです。また、1つの垂直ダイアログ単位は、現在のダイアログベースの高さ単位の8分の1と等しくなります。 ダイアログの基本単位は、現在のシステムフォントの高さと幅に基づいて計算されます。 `GetDialogBaseUnits`Windows 関数は、現在のダイアログベース単位をピクセル単位で返します。

### <a name="return-value"></a>戻り値

タブが設定されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

テキストが複数行の編集コントロールにコピーされると、テキスト内のタブ文字によって、次のタブストップまでの領域が生成されます。

タブストップを既定のサイズの32ダイアログ単位に設定するには、このメンバー関数のパラメーターなしのバージョンを呼び出します。 タブストップを32以外のサイズに設定するには、 *cxEachStop* パラメーターを使用してバージョンを呼び出します。 タブストップをサイズの配列に設定するには、2つのパラメーターを持つバージョンを使用します。

このメンバー関数は、複数行のエディットコントロールによってのみ処理されます。

`SetTabStops` 編集ウィンドウは自動的に再描画されません。 エディットコントロールに既に存在するテキストのタブストップを変更する場合は、 [CWnd:: InvalidateRect](cwnd-class.md#invalidaterect) を呼び出して編集ウィンドウを再描画します。

詳細については、Windows SDK の「 [EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops) 」と「 [Getのベースユニット](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) 」を参照してください。

### <a name="example"></a>例

  [CEditView:: SetTabStops](ceditview-class.md#settabstops)の例を参照してください。

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a> CEdit:: ShowBalloonTip

現在の編集コントロールに関連付けられているバルーンヒントを表示します。

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>パラメーター

*pEditBalloonTip*\
からバルーンヒントを記述する [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) 構造体へのポインター。

*lpszTitle*\
からバルーンヒントのタイトルを含む Unicode 文字列へのポインター。

*lpszText*\
からバルーンヒントテキストを含む Unicode 文字列へのポインター。

*ttiIcon*\
からバルーンヒントに関連付けるアイコンの種類を指定する **INT** 。 既定値は TTI_NONE です。 詳細については、 `ttiIcon` [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) 構造体のメンバーを参照してください。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

この関数は、Windows SDK で説明されている [EM_SHOWBALLOONTIP](/windows/win32/Controls/em-showballoontip) メッセージを送信します。 詳細については、 [Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip) マクロを参照してください。

### <a name="example"></a>例

`m_cedit`現在の編集コントロールにアクセスするために使用される変数を定義するコード例を次に示します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>例

次のコード例では、エディットコントロールのバルーンヒントを表示します。 [CEdit:: ShowBalloonTip](#showballoontip)メソッドは、タイトルとバルーンヒントテキストを指定します。

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a> CEdit:: 元に戻す

最後の編集コントロール操作を元に戻すには、この関数を呼び出します。

```
BOOL Undo();
```

### <a name="return-value"></a>戻り値

単一行のエディットコントロールの場合、戻り値は常に0以外になります。 複数行のエディットコントロールでは、元に戻す操作が成功した場合、戻り値は0以外の値になります。また、元に戻す操作が失敗した場合は0になります。

### <a name="remarks"></a>解説

元に戻す操作は元に戻すこともできます。 たとえば、の最初の呼び出しで、削除されたテキストを復元でき `Undo` ます。 編集操作が介在しない限り、の2回目の呼び出しでテキストを削除でき `Undo` ます。

詳細については、Windows SDK の「 [EM_UNDO](/windows/win32/Controls/em-undo) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプル CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC のサンプル CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CWnd クラス](cwnd-class.md)<br/>
[CButton クラス](cbutton-class.md)<br/>
[CComboBox クラス](ccombobox-class.md)<br/>
[CListBox クラス](clistbox-class.md)<br/>
[CScrollBar クラス](cscrollbar-class.md)<br/>
[CStatic クラス](cstatic-class.md)<br/>
[CDialog クラス](cdialog-class.md)
