---
title: CRT でのグローバル状態
description: Microsoft Universal C ランタイムで共有グローバル状態を処理する方法について説明します。
ms.topic: conceptual
ms.date: 10/02/2020
helpviewer_keywords:
- CRT global state
ms.openlocfilehash: 6c8b97e2bd6fa71891aedacb1fbfec2bbe382d84
ms.sourcegitcommit: faedcc3be78b29c78e5d51e3c7c7c2f448c745bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91717516"
---
# <a name="global-state-in-the-crt"></a>CRT でのグローバル状態

ユニバーサル C ランタイム (UCRT) の一部の関数は、グローバル状態を使用します。 たとえば、は `setlocale()` プログラム全体のロケールを設定します。これは、桁区切り記号、テキストコードページなどに影響します。

UCRT のグローバル状態は、アプリケーションと OS 間で共有されません。 たとえば、アプリケーションがを呼び出す場合、 `setlocale()` C ランタイムを使用する OS コンポーネントのロケールや、その逆の方法には影響しません。

## <a name="os-specific-versions-of-crt-functions"></a>CRT 関数の OS 固有バージョン

UCRT では、グローバル状態と対話する関数に "ツイン" 関数があります。この関数の先頭にはが付き `_o_` ます。 次に例を示します。

- `setlocale()` アプリ固有のグローバルな状態に影響します。
- `_o_setlocale()` アプリではなく、すべての OS コンポーネントによって共有されるグローバル状態に影響を及ぼします。

これらの "ツイン" 関数の唯一の違いは、グローバル CRT 状態の読み取り/書き込みを行うときに OS 固有のバージョン (つまり、で始まるバージョン) では、 `_o_` アプリのグローバル状態のコピーではなく、グローバル状態の os コピーを使用することです。

これらの関数の OS 固有のバージョンは、に `ucrt.osmode.lib` あります。 たとえば、の OS 固有バージョンは次のようになります。 `setlocale()``_o_setlocale()`

コンポーネントの CRT 状態をアプリの CRT 状態から分離するには、次の2つの方法があります。

- コンパイラオプション `/MT` (release) または (デバッグ) を使用して、コンポーネントを静的にリンク `/MTd` します。 詳細については、「 [/md、/mt、/ld](../build/reference/md-mt-ld-use-run-time-library.md)」を参照してください。 静的リンクを使用すると、バイナリサイズを大幅に増やすことができます。
- Windows 10 バージョン2004以降では、CRT に動的にリンクしますが、OS モードのエクスポート ( _o_で始まる関数) を呼び出します。 OS モードのエクスポートを呼び出すには、を前と同じように静的にリンクしますが、リンカーオプション `/NODEFAULTLIB:libucrt.lib` (release) または (debug) を使用して静的 UCRT を無視し `/NODEFAULTLIB:libucrtd.lib` ます。 とを `ucrt.osmode.lib` リンカー入力に追加します。 詳細については、「 [/NODEFAULTLIB (ライブラリを無視する)](../build/reference/nodefaultlib-ignore-libraries.md) 」を参照してください。

> [!Note]
> ソースコードでは、では `setlocale()` なく、を記述し `_o_setlocale()` ます。 に対してリンクすると `ucrt.osmode.lib` 、リンカーは自動的に OS 固有の関数のバージョンに置き換えます。 つまり、は `setlocale()` に置き換えられ `_o_setlocale()` ます。

に対するリンク `ucrt.osmode.lib` は、アプリモードでのみ使用できる UCRT 呼び出しを無効にします。 これらを呼び出そうとすると、リンクエラーが発生します。

## <a name="global-state-affected-by-appos-separation"></a>アプリと OS の分離の影響を受けるグローバルな状態

アプリと OS の状態の分離によって影響を受けるグローバルな状態には、次のものが含まれます。

- [ロケールデータ](locale.md)
- [シグナルによっ](reference/signal.md)て設定されるシグナルハンドラー
- [終了](reference/set-terminate-crt.md)によって設定される終了ルーチン
- [errno と _doserrno](errno-doserrno-sys-errlist-and-sys-nerr.md)
- [Rand](reference/rand.md)および[srand](reference/srand.md)で使用されるランダムな数値生成状態
- ユーザーが解放する必要のないバッファーを返す関数:   [strtok、wcstok、_mbstok](reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) [Tmpnam、_wtmpnam](reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [asctime、_wasctime](reference/asctime-wasctime.md) [gmtime、_gmtime32、_gmtime64](reference/gmtime-gmtime32-gmtime64.md) [_fcvt](reference/fcvt.md) [_ecvt](reference/ecvt.md) [strerror、_strerror、_wcserror、__wcserror](reference/strerror-strerror-wcserror-wcserror.md)
- _Putch によって使用されるバッファー、 [_putwch](reference/putch-putwch.md)
- [_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)
- [_set_new_handler](reference/set-new-handler.md) と [_set_new_mode](reference/set-new-mode.md)
- [fmode](text-and-binary-mode-file-i-o.md)
- [タイムゾーン情報](time-management.md)

## <a name="see-also"></a>参照

[C ランタイムライブラリリファレンス](c-run-time-library-reference.md)
