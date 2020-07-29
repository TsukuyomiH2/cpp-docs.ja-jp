---
title: Cアーカイブ例外クラス
ms.date: 11/04/2016
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
ms.openlocfilehash: 68f64cfd7dc96da04fcc0945a6b996eab4101487
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231885"
---
# <a name="carchiveexception-class"></a>Cアーカイブ例外クラス

シリアル化の例外条件を表します。

## <a name="syntax"></a>構文

```
class CArchiveException : public CException
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[Cアーカイブ例外:: Cアーカイブ例外](#carchiveexception)|`CArchiveException` オブジェクトを構築します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[Cアーカイブ例外:: m_cause](#m_cause)|例外の原因を示します。|
|[Cアーカイブ例外:: m_strFileName](#m_strfilename)|この例外条件のファイルの名前を指定します。|

## <a name="remarks"></a>解説

クラスには、 `CArchiveException` 例外の原因を示すパブリックデータメンバーが含まれています。

`CArchiveException`オブジェクトは、 [CArchive](../../mfc/reference/carchive-class.md)メンバー関数内で構築およびスローされます。 これらのオブジェクトには、 **CATCH**式のスコープ内でアクセスできます。 原因コードは、オペレーティングシステムに依存しません。 例外処理の詳細については、「[例外処理 (MFC)](../../mfc/exception-handling-in-mfc.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>必要条件

**ヘッダー:** afx

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>Cアーカイブ例外:: Cアーカイブ例外

オブジェクトの `CArchiveException` *原因*の値を格納して、オブジェクトを構築します。

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>パラメーター

*こと*<br/>
例外の理由を示す列挙型変数。 列挙子の一覧については、「 [m_cause](#m_cause)データメンバー」を参照してください。

*Lpszアーカイブ*<br/>
例外を発生させたオブジェクトの名前を含む文字列を指し `CArchive` ます。

### <a name="remarks"></a>解説

`CArchiveException`ヒープ上にオブジェクトを作成し、自分でスローするか、グローバル関数で[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)に処理させることができます。

このコンストラクターを直接使用しないでください。代わりに、グローバル関数を呼び出し `AfxThrowArchiveException` ます。

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a>Cアーカイブ例外:: m_cause

例外の原因を指定します。

```
int m_cause;
```

### <a name="remarks"></a>解説

このデータメンバーは、型のパブリック変数です **`int`** 。 この値は列挙型によって定義され `CArchiveException` ます。 列挙子とその意味は次のとおりです。

- `CArchiveException::none`エラーは発生しませんでした。

- `CArchiveException::genericException`指定されていないエラー。

- `CArchiveException::readOnly`読み込み用に開いているアーカイブに書き込もうとしました。

- `CArchiveException::endOfFile`オブジェクトの読み取り中にファイルの終わりに達しました。

- `CArchiveException::writeOnly`保存用に開いているアーカイブから読み取ろうとしました。

- `CArchiveException::badIndex`ファイル形式が無効です。

- `CArchiveException::badClass`オブジェクトを間違った型のオブジェクトに読み取ろうとしました。

- `CArchiveException::badSchema`異なるバージョンのクラスを使用してオブジェクトを読み取ろうとしました。

    > [!NOTE]
    >  これらの `CArchiveException` 原因列挙子は、`CFileException` 原因列挙子とは異なります。

    > [!NOTE]
    > `CArchiveException::generic` は非推奨とされます。 代わりに `genericException` を使用してください **ジェネリック**がアプリケーションで使用されていて、/clr でビルドされている場合、解読が容易ではない構文エラーが発生します。

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a>Cアーカイブ例外:: m_strFileName

この例外条件のファイルの名前を指定します。

```
CString m_strFileName;
```

## <a name="see-also"></a>関連項目

[CException クラス](../../mfc/reference/cexception-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CArchive クラス](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[例外処理](../../mfc/reference/exception-processing.md)
