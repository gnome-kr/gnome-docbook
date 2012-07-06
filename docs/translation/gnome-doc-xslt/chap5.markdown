## 스타일시트 번역 ##
그놈 문서 스타일시트에서는 DocBook 문서의 표현물 출력의 지역화 지원을 제공합니다. 스타일시트의 지역화 가능한 문자열은 번역을 위해 확인되고 PO 파일과 `inittool` 로 가져옵니다. 그 다음에 이들이 번역되고 나서 `inittool`은 출력 내용을 지역화하는데 사용하는 스타일시트가 사용할 l10n.xml XML 파일로 합칩니다.

DocBook 스타일시트에 대한 완전한 국제화 지원 제공은 사소한 것이 아니며, 지역화를 제공하는 것은 문서의 형식이 어떻게 갖춰지는지 이해하는 번역자가 필요하며, 그 이외에도 DocBook이 어떻게 동작하는지도 알아야 합니다. DocBook은 고급 마크업 언어이며 문서를 수많은 구조화를 제공하는 프로그램의 처리를 필요로 합니다. DocBook 프로그램은 수많은 교차 참조 처리, 내용의 목차 생성, 머릿말 형식, 그리고 지역화가 필요한 다른 형식화 작업들을 수행합니다. 이 작업들을 지역화 하는 것은 단일 문장을 번역하는 것보다 더 많은 일들이 따라옵니다. 그래서 잘 갖춰진 자체 형식화 코드를 지역화 할 수 있습니다.


*우리를 돕는 것이 여러분을 돕는 길입니다*
`
문서를 형식화 하는 것은 전세계적으로 제각기 다릅니다. 각각의 로캘은 오랜 형식화 관습과 방법의 역사를 지니고 있습니다. 이 스타일시트의 관리자는 모든 로캘에서의 문서 형식화의 뉘앙스를 알지 못합니다. 여러분의 로캘에 대해 우리가 더 나은 결과를 줄 수 있는 유일한 방법은 얼마나 많은 문제가 있는지 여러분이 이야기를 해주었을 때 입니다.
`

모든 지역화가 PO 파일에서 문자열을 번역하는 것으로 끝나겠지만, 단순한 문장이나 어구가 아닌 번역 가능한 문장이 있는 여러가지 경우가 있습니다. 게다가 번역자들은 XML 단편화 요소를 사용하여 데이터를 제공해야 합니다. 이 구조화된 단편화 요소들은 문맥을 기반으로 대체 형식화를 제공하거나 형식 문자열을 제공하는  서수 양식을 작업할 때 사용합니다.

### 단순 문자열 ###
번역한 문자열은 _l10n.gettext_라는 템플릿에서 가져옵니다. 이 템플릿은 `inittool` 이 PO 파일로부터 만든 XML 파일에서 문자열을 가져옵니다. 예를 들어 _causion_요소의 머리부분으로 사용하는 *경고* 라는 문자열을 가정해봅니다. 스타일시트에서는 문서의 언어에 대한 문자열의 번역한 값을 가져오기 위해 _l10n.gettext_를 호출할 것입니다. l10n.xml 파일은 다음과 같은 목록을 가지게 됩니다.
`<msgset xmlns=""http://www.gnome.org/~shaunm/gnome-doc-utils/l10n">
  <msgid>Caution</msgid>
  <msg>Caution</msg>
  <msg xml:lang="ar">إنتباه</msg>
  <msg xml:lang="bg">Внимание</msg>
  <msg xml:lang="ca">Compte</msg>
  <msg xml:lang="cs">Upozornění</msg>
  <msg xml:lang="da">Forsigtig</msg>
  <msg xml:lang="de">Achtung</msg>
  <msg xml:lang="el">Προσοχή</msg>
  <msg xml:lang="en_CA">Caution</msg>
  <msg xml:lang="en_GB">Caution</msg>
  <msg xml:lang="es">Precaución</msg>
  <msg xml:lang="et">Ettevaatust</msg>
  <msg xml:lang="fi">Varoitus</msg>
  <msg xml:lang="fr">Attention</msg>
  <msg xml:lang="gu">સાવધાન</msg>
  <msg xml:lang="hi">चेतावनी</msg>
  <msg xml:lang="hu">Figyelem</msg>
  <msg xml:lang="id">Perhatian</msg>
  <msg xml:lang="it">Attenzione</msg>
  <msg xml:lang="ja">注意</msg>
  <msg xml:lang="ko">주의</msg>
  <msg xml:lang="lt">Įspėjimas</msg>
  <msg xml:lang="nb">Advarsel</msg>
  <msg xml:lang="ne">सावधानी</msg>
  <msg xml:lang="nl">Let op</msg>
  <msg xml:lang="no">Advarsel</msg>
  <msg xml:lang="pa">ਸਾਵਧਾਨ</msg>
  <msg xml:lang="pt"Cuidado</msg>>
  <msg xml:lang="pt_BR">Cuidado</msg>
  <msg xml:lang="ro">Atenţie</msg>
  <msg xml:lang="sk">Výstraha</msg>
  <msg xml:lang="sq">Kujdes</msg>
  <msg xml:lang="sr">Пажња</msg>
  <msg xml:lang="sr@Latn">Pažnja</msg>
  <msg xml:lang="sv">Varning</msg>
  <msg xml:lang="tr">Uyarı</msg>
  <msg xml:lang="uk">Застереження</msg>
  <msg xml:lang="vi">Cảnh báo</msg>
  <msg xml:lang="wa">Adviertance</msg>
  <msg xml:lang="zh_CN">小心</msg>
  <msg xml:lang="zh_TW">注意</msg>
</msgset>
`
그러나 번역자들은 단지 PO 파일로만 작업합니다. 이러한 문자열들을 위해 PO파일을 사용하는 것은 다른 단순한 문자열 번역과 다르지 않습니다. 위 문자열에 대한 _sr_로캘에 있는 PO 목록은 아래와 같은 모습을 지니게 될 것입니다.

`#: ../xslt/gettext/l10n.xml.in.h:1347
msgid "Caution"
msgstr "Пажња"
`
### 서수 표현 ###
대부분의 경우 정적 문자열은 내용을 알맞게 지역화 하기에는 부족합니다. 이런 경우에 스타일시트에서는 구조화된 XML 단편 요소에서 이들 문자열을 대체하는 방식으로 대체 문자열을 허용삽니다. 대체 문자열은 두가지 방법으로 사용하는데, 서수 양식의 제공은 언어의 서수 규칙을 따르며, 대체 양식의 제공은 지정한 역할을 기반으로 갑니다. 이 섹션에서는 서수 표현을 설명합니다.
