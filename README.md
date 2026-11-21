# Shinji & Kaoru Mod (Psych Engine)

신지(플레이어) vs 카오루(상대) 3곡 위크 모드입니다.

## 설치 (Psych Engine 0.7.x 기준)
1. 이 폴더(`ShinjiKaoruMod`)를 통째로 Psych Engine의 `mods/` 폴더에 넣습니다.
2. 게임 실행 → Mods 메뉴에서 "Shinji & Kaoru Mod" 활성화 (재시작 필요할 수 있음).
3. Story Mode 또는 Freeplay에서 플레이.

## 메인 메뉴 배경
- Psych Engine 0.7.x 메인 메뉴 배경으로 `images/menuBG.png`를 포함합니다. 이 모드를 `mods/`에 넣고 활성화하면 기본 메인 메뉴 배경을 대체합니다.

## 수록곡
| 곡 | BPM | 내용 |
|---|---|---|
| Piano Duet | 96 | 오리지널 피아노 곡. 카오루가 부르면 신지가 따라 부르는 콜 앤 리스폰스 |
| Daiku | 126 | 베토벤 교향곡 9번(환희의 송가, 퍼블릭 도메인) 칩튠 리믹스 |
| Tabris | 156 | 최종곡. 붉은 밤 스테이지, 듀엣 구간 포함 |

난이도 Easy / Normal / Hard 모두 포함. 음악은 직접 합성한 칩튠 Inst이고 Voices 파일은 필요 없습니다.
듀엣(D) 구간은 양쪽 화살표에서 동시에 노트가 나옵니다.

## 구성
- `characters/` shinji, kaoru, shinji-dead (게임오버)
- `images/characters/` 정렬·크기 통일한 스프라이트 시트 (idle 4프레임 바운스, sing 2프레임, 신지는 miss 포함)
- `images/icons/` 체력바 아이콘 2종
- `stages/` nervroof(석양 옥상), lclnight(붉은 밤) + Lua
- `scripts/songcard.lua` 곡 시작 타이틀 카드
- `scripts/story_cutscene.lua` 스토리 모드 첫 곡(Piano Duet) 시작 전 한글 컷씬 (Enter 다음 / ESC 건너뛰기)
- `fonts/NotoSansKR-Medium.otf` 컷씬용 한글 폰트 (Noto Sans CJK KR 부분집합, SIL OFL 라이선스)
- `weeks/shinji-kaoru.json`, `songs/`, `data/`

## 문제 해결
- 신지의 좌/우 모션이 반대로 나오면 `characters/shinji.json`의 `"flip_x"` 값을 바꿔 보세요.
- 캐릭터 위치는 `stages/*.json`의 `boyfriend` / `opponent` 좌표로 조절합니다.
- 캐릭터 크기는 `characters/*.json`의 `"scale"` 로 조절합니다.
- 노트 속도는 `data/<곡>/<곡>.json`의 `"speed"` 값을 수정하세요.

## 추가: 신지 & 아스카 위크
- 캐릭터: `asuka` (신지 스프라이트 스타일, 주황 머리·파란 눈·빨간 플러그슈트, 상대 캐릭터)
- 위크: `weeks/shinji-asuka.json` (Story / Freeplay에 "Shinji & Asuka" 추가)
- 곡: Anta Baka (132BPM) / Hedgehog Dilemma (104BPM) / Sortie (172BPM), 난이도 Easy·Normal·Hard
- 스테이지: `redsky` (붉은 석양 옥상), `nervroof`, `lclnight` 재사용
- 스토리 모드에서 Anta Baka 시작 전에 한글 컷씬이 나옵니다.

## 추가: 아야나미 레이 / 보컬 트랙 / 카오루 생일곡
- 캐릭터 `rei` (아야나미 레이): 올려주신 `ReiMan` 이미지 기반, 상대 캐릭터로 사용할 수 있습니다 (`characters/rei.json`, 체력바 아이콘·메뉴 캐릭터 포함). 아직 레이가 나오는 곡/위크는 없습니다.
- 모든 곡(`songs/*/`)에 `Inst.ogg`(반주)와 `Voices.ogg`(보컬 멜로디)를 분리해 넣었습니다. 차트는 `needsVoices: true` 입니다. 노트를 놓치면 보컬이 끊깁니다.
- 카오루 생일 이스터에그: 메인 메뉴에서 `0913`(또는 `20000913`)을 입력하면 생일 축하곡(`music/kaoruBirthday.ogg`)이 나옵니다. ESC/Backspace로 중단.
  - `states/MainMenuState.hx` 는 메뉴 스크립트(HScript)를 지원하는 Psych Engine 1.0 이상에서 동작합니다.
  - 구버전(0.7.x)은 `source_patches/MainMenuState_birthday_patch.txt` 의 코드를 소스에 직접 넣어야 합니다.

## 추가: 신지 & 레이 위크 / 카오루 생일 파티
- 위크 `shinji-rei`: Unit Zero (98BPM) / Smile (112BPM) / Blue Moon (150BPM), 난이도 Easy·Normal·Hard. 스토리 모드 시작 시 Unit Zero 앞에 한글 컷씬이 나옵니다.
- 위크 `kaoru-birthday` (Freeplay 전용): **Birthday Party**
  - Freeplay에서 곡을 고르면 먼저 **생일 입력 전용 창**이 열립니다. 카오루의 생일 `0913`을 입력하면 파티가 시작됩니다. (틀리면 흔들리며 다시 입력, ESC로 나가기, Backspace로 지우기)
  - 파티 장면: 방 가운데에 카오루, 옆에서 신지·아스카·레이가 노래하고, 배경은 생일 현수막과 풍선이 달린 방, 앞에는 케이크(촛불)가 놓여 있습니다. 곡이 끝날 즈음 촛불이 꺼지고 카오루가 반응합니다.
  - 노래는 Happy Birthday 멜로디(3/4박자)이고 `Inst.ogg` + `Voices.ogg` 로 나뉘어 있습니다.
  - 레이는 게임 엔진의 캐릭터 슬롯(3명)이 모자라서 스테이지 스크립트(`stages/birthdayroom.lua`)로 추가한 보조 가수입니다. 아스카와 함께 상대 노트에 맞춰 노래합니다.
- 메인 메뉴에서 `0913` 입력(Psych 1.0 이상)하면 생일 축하곡이 나오는 기능은 그대로입니다.

## 추가: 컷씬 대사 음성
- 스토리 컷씬은 대사마다 `sounds/cutscene/<곡이름>_<번호>.ogg` 파일이 있으면 그 음성을 읽어 줍니다. (예: `piano-duet_1.ogg`, `anta-baka_3.ogg`, `unit-zero_2.ogg`) 다음 대사로 넘기거나 ESC로 건너뛰면 음성도 멈춥니다.
- 음성 파일이 없는 대사는 캐릭터별 말소리 효과음(`babble_*.ogg`)이 글자와 함께 재생됩니다.
- 실제 한국어 음성은 `tools/make_cutscene_voice.py` 로 만들 수 있습니다. (`pip install edge-tts` 와 ffmpeg 필요, 인터넷 연결 필요) 모드 폴더에서 `python tools/make_cutscene_voice.py` 를 실행하면 모든 대사가 캐릭터별 목소리로 `sounds/cutscene/` 에 저장됩니다. 대사를 고쳤다면 `--force` 로 다시 생성하세요.

## 에반게리온 풍 타이틀 화면
- 에셋만으로 적용됩니다(재빌드 불필요): `images/titleBG_eva.png`, `logoBumpin.png/xml`, `gfDanceTitle.png/xml/json`, `titleEnter.png/xml`, `data/introText.txt`
- 인트로 문구(NERV HEADQUARTERS 등)와 붉은 섬광 연출은 소스 수정이 필요해서 `source_patches/TitleState.hx`로 제공합니다. Psych Engine 소스의 `source/states/TitleState.hx`를 이 파일로 교체하고 다시 빌드하세요.
