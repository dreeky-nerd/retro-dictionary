# 일본어·영어 사전 데이터와 신조어 출처 조사

- 조사일: 2026-09-30
- 전제: 앱에 **실제 조회 가능한 사전**이 필요하다. 기본은 사용자의 언어에 맞는 사전 풀이를 보여주고, 요청하면 한국어·영어 풀이도 추가로 보여준다. 번역기가 아니라 사전이므로 각 뜻·품사·용례의 원문 언어와 출처를 유지한다. 아래는 일본어·영어 쪽 원천 자료 조사다. 한국어 풀이가 없는 자료를 일한·영한 사전으로 간주하지 않는다.
- 범위: 데이터 후보와 재사용 조건. API나 SDK 구현 방법은 다루지 않는다.

## 바로 검토할 후보

| 후보 | 맡을 수 있는 역할 | 확인된 허가·운영 조건 | 한계 |
| --- | --- | --- | --- |
| **EDRDG JMdict** | 일본어 표제어·읽기·영어 풀이의 기본 데이터. 전체 XML 파일을 내려받아 내부 검색용으로 가공할 수 있다. | [공식 프로젝트](https://www.edrdg.org/wiki/Main_Page.html)는 매일 생성되는 `JMdict.gz`, 영문 풀이만 든 `JMdict_e.gz` 등의 파일을 제공한다. [공식 라이선스](https://www.edrdg.org/edrdg/licence.html)는 일본어·영어 성분을 CC BY-SA 4.0으로 제공하며 상업 사용을 허용한다. 앱의 출처/라이선스 화면과 정기 갱신 절차가 필요하다. | 공식 전체판에 열거된 풀이 언어는 영어·독일어·프랑스어·러시아어·스페인어·헝가리어·슬로베니아어·네덜란드어다. **한국어 풀이가 없다.** 신조어 수록 속도나 사용자 목표 단어의 포함률은 검증 전이다. |
| **EDRDG JMnedict / KANJIDIC2** | 일본 인명·지명 등 고유명사, 한자 읽기·획수·부수의 보조 자료. | [EDRDG](https://www.edrdg.org/wiki/Main_Page.html)는 JMnedict를 별도 XML 파일로, [KANJIDIC2](https://www.edrdg.org/wiki/KANJIDIC_Project.html)를 UTF-8 XML 파일로 배포한다. [라이선스](https://www.edrdg.org/edrdg/licence.html)는 이 파일에도 적용되며 KANJIDIC 계열은 공헌자에 관한 별도 조건을 적고 있다. | 일반 단어 뜻풀이의 대체재가 아니다. KANJIDIC2의 `korean_h`는 **한자의 한글 음**이지 일본어 단어의 한국어 번역이 아니다. |
| **Wiktionary 원문 / Kaikki 추출본** | 영어·일본어 표제어와 최신 어휘의 폭을 넓히는 보조 데이터. Wiktionary는 원문, Kaikki는 그 원문을 가공한 JSONL 다운로드다. | [Wiktionary 저작권 안내](https://en.wiktionary.org/wiki/Wiktionary:Copyrights)는 사전 항목 원문을 CC BY-SA 4.0/GFDL 이중 라이선스로 제공한다. CC BY-SA 4.0은 상업적 재사용을 허용하되 출처 표시·변경 고지·동일조건을 요구한다. [Wikimedia 덤프](https://dumps.wikimedia.org/enwiktionary/)는 원문 대량 다운로드, [Kaikki 원시 다운로드](https://kaikki.org/dictionary/rawdata.html)는 Wiktextract가 뽑은 JSONL을 제공한다. [Kaikki 운영자의 설명](https://github.com/tatuylonen/wiktextract#pre-extracted-data)에 단어별·언어별 다운로드가 명시돼 있다. | Kaikki **도구의 MIT 라이선스는 추출된 Wiktionary 사전 내용의 라이선스가 아니다.** 항목별 외부 이미지·음성·인용 예문은 별도 권리 표시가 있을 수 있다. 영어판 Wiktionary의 일본어 항목에는 대체로 영어 뜻풀이가 담겨 있어, 이것만으로 일한 사전은 완성되지 않는다. |
| **Oxford Languages 계약형 사전 데이터** | 편집된 한국어 단일언어 사전과 한국어·영어 사전이 필요한 경우 살펴볼 계약 후보. | [OUP 갱신 안내](https://languages.oup.com/about-us/annual-updates/spring-2024-2/)는 한국어 단일언어 데이터에 약 1,270개, Korean–English 데이터에 약 800개 항목을 추가했다고 밝힌다. [OUP 사이트](https://languages.oup.com/)는 별도 언어 데이터셋과 셀프서비스 API를 구분해 소개하고, Naver 담당자의 인용문에서 English–Korean·English–English·English–Japanese 사전 제공 사례를 명시한다. | 공개 안내만으로 가격, 정확한 언어 방향별 제공 범위, 일한 자료, 앱 내 저장·캐싱·재배포 권한은 확인되지 않는다. 계약형 **데이터셋** 가능성이 셀프서비스 **API**에 같은 언어 방향이 있다는 뜻은 아니다. |

## EDRDG를 사용할 때 특히 중요한 조건

[EDRDG 공식 라이선스](https://www.edrdg.org/edrdg/licence.html)는 일반적인 CC BY-SA 표시 외에 앱 사용 방식을 구체적으로 적는다. 출처와 라이선스를 앱 문서·사이트 등에 표시해야 하며, 모바일 앱에서는 시작 화면만으로는 부족하고 메뉴에서 열 수 있는 `About`·`Sources` 같은 별도 화면이 허용된다. 라이선스와 데이터 문서의 사본 또는 링크도 제공해야 한다. 데이터를 최신판으로 **정기 갱신하는 절차**가 있어야 하고, 웹 사전은 적어도 매월 갱신하는 방식을 예로 든다. 상업적 판매는 허용되며, 데이터를 사용한 앱 전체를 오픈소스로 만들 의무는 없다고 명시한다. 다만 데이터에서 파생한 사전 콘텐츠에는 동일조건 라이선스가 적용될 수 있으므로 원천별 항목을 구분해 보관하는 편이 안전하다. 마지막 문장은 설계 제안이다.

JMdict의 [공식 배포 목록](https://www.edrdg.org/wiki/Main_Page.html)은 **다운로드 파일** 목록이지 앱에서 호출할 수 있는 공식 사전 조회 API 목록이 아니다. EDRDG의 WWWJDIC은 웹 사전 서버로 소개되지만, 이 조사에서 그 서버를 앱 백엔드 API로 쓰는 조건은 확인하지 않았다. 파일 배포와 API 사용을 혼동하지 않아야 한다. JMnedict는 고유명사 데이터이고, KANJIDIC2는 글자 단위 데이터이므로 한국어·일본어·영어 일반 어휘의 뜻풀이를 이 두 파일로 채울 수 없다. [JMnedict 설명](https://www.edrdg.org/wiki/Main_Page.html), [KANJIDIC2 필드 설명](https://www.edrdg.org/wiki/KANJIDIC_Project.html).

## Wiktionary·Wikimedia·Kaikki의 관계

**사용자 언어에 맞는 뜻풀이를 위해서는 판본도 구분해야 한다.** [Kaikki 일본어판](https://kaikki.org/jawiktionary/)은 일본어판 Wiktionary에서 추출하며 일본어·영어 등 표제어 분류를 제공한다. 일본어로 쓰인 사전 풀이의 후보로 검토할 수 있다. 반면 [영어판의 Japanese 목록](https://kaikki.org/dictionary/Japanese/)은 영어판 원문에서 일본어 표제어를 추린 것으로 일본어 뜻풀이 사전과 다르다. 한국어판·영어판도 같은 구분으로 선택해야 한다. 실제 풀이 언어와 누락률은 개별 항목을 검증한다. Kaikki는 기존 후처리 다운로드를 폐기 예정으로 표시하므로 구현 시 안내된 원시 데이터 배포 경로를 사용한다.

1. **Wiktionary**는 공동 편집 사전의 원문과 개별 항목이다. 영어판 항목의 [저작권 안내](https://en.wiktionary.org/wiki/Wiktionary:Copyrights)가 텍스트 재사용 조건을 설명한다. 개별 음성·사진·외부 인용은 항목별 표기를 확인해야 한다.
2. **Wikimedia**는 해당 프로젝트를 운영하고 [원문 덤프](https://dumps.wikimedia.org/enwiktionary/)와 [API](https://www.mediawiki.org/wiki/Wikimedia_APIs/Access_policy)를 제공한다. API는 접근 방식이고 콘텐츠 라이선스를 바꾸지 않는다. 공식 API 정책은 식별 가능한 User-Agent를 요구하며, 대량 데이터는 덤프로 받을 수 있다고 안내한다. [API 정책](https://www.mediawiki.org/wiki/Wikimedia_APIs/Access_policy).
3. **Kaikki**는 운영자가 [Wiktextract](https://github.com/tatuylonen/wiktextract)를 사용해 Wiktionary 덤프를 구조화한 편의 배포처다. [원시 JSONL 다운로드](https://kaikki.org/dictionary/rawdata.html)는 주기적으로 갱신된다고 설명하지만, 추출 지연·누락·파싱 오류 가능성이 있으므로 최신 단어의 유무를 단정할 근거로 삼기 어렵다. [Wiktextract의 MIT 라이선스](https://github.com/tatuylonen/wiktextract/blob/master/LICENSE)는 파서 코드에 관한 것이고, 사전 원문의 출처·동일조건은 계속 관리해야 한다.

Wiktionary 계열은 영어 단어의 뜻, 일본어 단어의 영어 뜻, 일부 번역 연결을 찾는 데 유용하다. 그러나 항목 구조와 번역 채움률이 일정하다는 공식 보장이 없어 **한·일·영 세 언어 간 모든 직접 번역**을 약속하는 단일 데이터베이스로 보지 않는다. 이 평가는 위 자료 구조를 바탕으로 한 추론이며, 실제 포함률은 샘플 단어 집합으로 검증해야 한다. 이 앱의 목표 자체도 모든 언어쌍 번역을 제공하는 것은 아니다.

## 최근 신조어의 탐지와 수록 권한은 별개

- 일본어: [산세이도 「올해의 신어 2026」](https://dictionary.sanseido-publ.co.jp/shingo/2026/selection_before.html)는 현재 쓰이는 말을 모집하고 향후 국어사전 수록 후보를 고르는 **탐지 신호**다. [2025년 선정 결과](https://dictionary.sanseido-publ.co.jp/shingo/2025/best10/)에는 출판사가 작성한 풀이도 실려 있다. 이 공개 발표가 그 풀이를 앱 사전 데이터로 복제·재배포할 허가는 아니다. 단어 후보를 발견한 뒤 재사용 가능한 자료에서 뜻을 확인하거나 독자적으로 서술해야 한다.
- 영어: [Oxford University Press의 2025 올해의 단어 발표](https://corp.oup.com/word-of-the-year/)는 `rage bait` 같은 동시대 표현의 탐지 신호다. [Cambridge의 신어 편입 설명](https://dictionary.cambridge.org/help/)은 사용 빈도·다양한 문맥·시간 경과를 검토한다고 한다. 어느 발표도 사전 풀이·예문·발음 파일의 앱 내 재배포 허가로 읽을 수 없다.
- `올해의 단어`와 `사전에 수록된 단어`도 같지 않다. 후보 선정은 문화적 주목도 또는 미래 수록 가능성을 보여줄 뿐이다. 최신성 기능에는 **발견일·검증일·출처·풀이 작성 주체**를 따로 기록하는 것이 좋다(앱 설계 제안).

## 작은 검증 범위 제안

우선 사용자의 언어에 맞는 사전의 **원래 뜻·품사·용례**를 기본으로 놓고, 요청 시 한국어 또는 영어로 작성된 별도 사전 풀이를 병렬로 보여주는 구성을 검증한다. JMdict의 일영 기본 검색과 Kaikki/Wiktionary의 영어·일본어 보완 데이터를 표제어 단위로 비교하고, 한국어 풀이가 필요한 항목은 권한이 명확한 한국어 사전 데이터 또는 직접 작성한 풀이를 별도로 연결한다. 기계번역을 중간 단계로 넣어 원 사전의 뜻을 바꾸는 방식은 이 요구에 맞지 않는다. 2025–2026년 유행어와 일반어를 각각 소수 선정해 **각 언어의 사전에서 실제로 무엇이 조회되는지** 확인하는 것이 다음 검증이다. 앱 구현·API 계약·데이터 다운로드는 이 조사 범위에 포함되지 않는다.
