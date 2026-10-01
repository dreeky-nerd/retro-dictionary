# retro-dictionary

전자사전의 외형과 조작감을 즐기면서 한국어·일본어·영어를 실제로 검색하는 레트로 사전 앱을 준비하는 프로젝트.

**현재 상태: 실제 기기 자료 기반 정적 시안과 조사 문서를 작성했다. 실행 가능한 앱은 아직 없다.**

👉 [스킨 비교·CASIO 사용 흐름·스킨 변경 상세 시안](docs/design/mockup-spec.md)

최신: 사용자는 키 모양·배열이 바뀐 6버튼 대체안을 거부했다. [한국어·일본어·영어 버튼 현지화 시안](docs/design/09-localized-all-buttons.png)과 [원형 자판·필기판 A/B 시안](docs/design/sol-ab-mockups.md)을 참고한다. 모두 정적 제안이며 실제 키 터치와 사전 데이터는 검증 전이다.

## 사용자에게 확인한 방향

- 옛날 전자사전의 인터페이스와 모양을 앱으로 구현하고 싶다.
- 일본의 대표 전자사전 모델을 조사해 참고한다.
- 가장 중요한 목적은 **전자사전의 외형과 조작감을 즐기는 것**이다.
- 실제 사전 기능은 필수다. 한국어·일본어·영어를 지원하고 최신 신조어·속어도 다룬다.
- 사용자 언어의 사전을 기본 제공하고, 요청 시 한국어·영어 사전 풀이를 함께 보여준다. 번역기가 아니라 출처가 있는 사전 서비스다.
- 애니·드라마 속 전자사전의 형태와 브랜드도 디자인 참고 자료로 조사한다.
- `ai-workspace`의 관련 스킬을 이 프로젝트에 포함한다.
- iOS 네이티브를 먼저 만들고, 이후 Android 네이티브를 제작한다.
- 사전 내용은 지속적으로 갱신한다. 후속 논의에서 MP3 같은 불필요한 기능을 제외하고 사전 중심으로 구성하기로 방향을 조정했다. 계산기·학습 메뉴의 세부 범위는 별도 결정한다.
- 언어별 초기 기기 추천, 교체 가능한 스킨, 터치로 여는 모션, 원래 버튼 소리와 디스플레이 질감을 지향한다.
- 첫 기준 기종은 CASIO XD-SW6400이다. SHARP RD-9100MP와 iriver D26을 후속 스킨으로 구성하고 D100은 후순위로 둔다.

## 문서

- [레트로 서비스 사례·작은 자판 해법 토론 종합](docs/research/retro-ux-synthesis.md)

- [기획 브리프와 제안](docs/project-brief.md)
- [현대적 레트로 콘셉트와 재현 범위](docs/modern-retro-concept.md)
- [일본·한국 재현 후보 비교와 추천](docs/research/device-comparison.md)
- [일본 대표 제품 조사](docs/research/japanese-models.md)
- [구형 전자사전과 조작 방식 조사](docs/research/retro-interaction.md)
- [애니·드라마 속 전자사전 조사](docs/research/screen-appearances.md)
- [한국어 사전과 신조어 데이터](docs/research/korean-data-and-slang.md)
- [일본어·영어 데이터](docs/research/japanese-english-data.md)
- [스킬 선정과 적용 상태](docs/skills.md)
- [프로젝트 작업 지침](AGENTS.md)

제조사 사진·설명서 사본은 공개 저장소에 포함하지 않았다. 조사 출처와 로컬 참고 자료의 구분은 [참고 자료 안내](docs/design/references/README.md)에 있다. 복사한 로컬 스킬의 출처·라이선스는 [스킬 기록](skills-lock.json)과 [제3자 라이선스](docs/licenses/README.md)를 참고한다.

## 준비된 구성

- `.agents/skills/`: 기획·리서치·디자인·개발·검증 스킬 10개.
- `skills-lock.json`: 복사한 스킬의 출처와 기존 메타데이터.
- `docs/research/`: Sol 에이전트의 공식 자료 조사.

## 다음에 결정할 것

1. CASIO XD-SW6400 시안의 정확한 키 배열·각인과 조작을 실제 자료에 대조해 제작.
2. 스킨별 현대적 편의의 배치와 실제 iPhone 터치 사용성 검증.
3. 사용자 언어별 사전 공급원과 추가 한국어·영어 풀이의 수록 범위, 신조어 편집 범위.

플랫폼은 iOS 네이티브 우선으로 결정했다. SwiftUI는 검토 후보이며 제품 코드는 아직 없다. 구현 시 라이브러리 문서를 Context7으로 먼저 확인한다.
