---
title: 国/地域別文字列
ms.date: 11/04/2016
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: 8556e005618a1b69c47498a07e218284dcb1164f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443440"
---
# <a name="countryregion-strings"></a>Country/Region Strings

国/地域識別文字列を言語識別文字列と組み合わせて、 `setlocale`、 `_wsetlocale`、 `_create_locale`、および `_wcreate_locale` の関数のロケール指定を作成できます。 Windows オペレーティング システムのさまざまなバージョンでサポートされている国と地域名の一覧については、[MS-LCID]: Windows Language Code Identifier (LCID) Reference ([MS-LCID]: Windows 言語コード識別子 (LCID) リファレンス) の「**Appendix A: Product Behavior**」(付録 A: 製品の動作) に記載されている表の、 **[Language]** 、 **[Location]** 、[[Language tag]](https://msdn.microsoft.com/library/cc233982.aspx) 列をご覧ください。 利用できるロケール名と関連する値を列挙するコードの例については、「[NLS: Name-based APIs Sample](/windows/win32/intl/nls--name-based-apis-sample)」(NSL: 名前ベースの API のサンプル) をご覧ください。

## <a name="additional-supported-country-and-region-strings"></a>サポートされるその他の国/地域識別文字列

Microsoft の C ランタイム ライブラリの実装では、次の追加の国/地域識別文字列および省略形もサポートされています。

|国/地域識別文字列|省略形|同等のロケール名|
|----------------------------|------------------|----------------------------|
|america|米国|ja-JP|
|britain|GBR|en-GB|
|china|CHN|zh-CN|
|czech|CZE|cs-CZ|
|england|GBR|en-GB|
|great britain|GBR|en-GB|
|holland|NLD|nl-NL|
|hong-kong|HKG|zh-HK|
|new-zealand|NZL|en-NZ|
|nz|NZL|en-NZ|
|pr china|CHN|zh-CN|
|pr-china|CHN|zh-CN|
|puerto-rico|PRI|es-PR|
|slovak|SVK|sk-SK|
|south africa|ZAF|af-ZA|
|south korea|KOR|ko-KR|
|south-africa|ZAF|af-ZA|
|south-korea|KOR|ko-KR|
|trinidad & tobago|TTO|en-TT|
|uk|GBR|en-GB|
|united-kingdom|GBR|en-GB|
|united-states|米国|ja-JP|
|us|米国|ja-JP|

## <a name="see-also"></a>参照

[ロケール名、言語、および国/地域識別文字列](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[言語識別文字列](../c-runtime-library/language-strings.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
