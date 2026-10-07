# 🍁 Maple RTS

**메이플스토리의 세 진영이 맞붙는 실시간 전략(RTS) 게임** — MapleStory Worlds(MSW)로 만들었습니다.

일꾼으로 자원을 모으고, 건물을 지어 유닛을 뽑고, 나만의 영웅과 함께 상대 기지를 무너뜨리세요.
스타크래프트식 조작(드래그 선택 · 우클릭 명령 · 어택땅 · 부대 지정)에 메이플스토리의 몬스터·직업·마을을 입혔습니다.

> *A real-time strategy game built on MapleStory Worlds. Three MapleStory factions — Adventurers, Cygnus Knights and Edelstein Resistance — gather resources, build bases, train armies and fight alongside their own hero.*

---

## ✨ 주요 특징

| | |
|---|---|
| ⚔️ **3진영 비대칭 플레이** | 모험가(물량·확장형) / 시그너스(정예형) / 에델슈타인(기계·전술형) — 진영마다 건설 방식부터 다름 |
| 🦸 **영웅 시스템** | 진영별 5개 직업, 총 15명의 영웅. 전직(2~5차)으로 스킬 W·E·R·T 해금, 쓰러지면 30초 뒤 부활 |
| 💰 **두 가지 자원** | 메소(일꾼 채집) + 에르다(에르다 몬스터 사냥 · 채집 건물) |
| 🏗️ **테크트리** | 선행 건물 조건, 업그레이드(공격·방어 3단계), 유닛 진화 |
| 🎮 **스타크래프트식 조작** | 드래그 선택, 어택땅(A), 위치 고수(H), 순찰(P), 부대 지정(Ctrl+숫자), 명령 칸 단축키 |
| 🌫️ **전장의 안개 · 은신/탐지** | 시야 밖은 안개, 본 적 있는 적 건물은 잔상으로 남음, 은신 유닛은 탐지기로만 드러남 |
| 👥 **멀티플레이** | 방 로비 → 진영·직업 선택 대기실 → 최대 4인 대전 → 결과표 |

---

## 🕹️ 게임 방법

### 승리 조건
상대 플레이어의 **본진을 모두 파괴**하면 승리, 내 본진이 파괴되면 패배합니다.

### 게임 흐름
1. 로비에서 방을 만들거나 들어갑니다.
2. 대기실에서 **진영**과 **영웅 직업**을 고르고 **준비 완료**.
3. 본진 1채 · 일꾼 4명 · 영웅 1명 · 메소 50으로 시작합니다.
4. 일꾼으로 메소를 캐고(일꾼 최대 20명), 건물을 지어 유닛을 생산합니다.
5. 에르다를 모아 상위 유닛·업그레이드·영웅 전직을 진행합니다.
6. 부대를 모아 상대 본진을 공격합니다.

### 조작법

| 입력 | 기능 |
|---|---|
| 좌클릭 / 드래그 | 유닛·건물 선택 |
| 우클릭 | 이동 · 공격 · 채집 |
| `A` + 클릭 | 어택땅 (가는 길의 적과 교전) |
| `M` / `S` / `H` / `P` | 이동 / 정지 / 위치 고수 / 순찰 |
| `Ctrl` + 숫자 / 숫자 | 부대 지정 / 부대 불러오기 |
| `Q` `W` `E` `R` `T` | 영웅 스킬 (커서 방향) |
| `X` (본진 선택 중) | 에르다 채집 건물 건설 |
| `Tab` / `Space` | 대표 유닛 종류 전환 / 카메라 고정 |
| 화면 가장자리 · 미니맵 클릭 | 카메라 이동 |
| `Esc` / `F10` | 명령 취소 / 설정(소리·감도·항복) |

---

## 🏰 진영

### 🍄 모험가 — 넓게 퍼지는 물량형
- 본진 **세계수**. 건물은 **건설 가능 영역** 안에만 지을 수 있고, 세계수의 뿌리를 마을 **전초지**로 바꿔 지역 테크를 엽니다.
- 헤네시스(버섯) · 페리온(보어) · 엘리니아(요정·눈알 마법) · 커닝시티(공중·은신)
- 영웅: 다크나이트 · 비숍 · 보우마스터 · 나이트로드 · 캡틴

### ⚔️ 시그너스 — 단단한 정예형
- 본진 **신수**. 신수와 **신수의 가호** 주변에만 건설, 신수가 무너지면 범위 안 건물이 멈춥니다.
- 일꾼(티노)은 건설을 시작하면 바로 다른 일을 할 수 있음
- 정식기사 → 상급기사 진화, 에인션트 골렘, 정령(공중)
- 영웅: 소울마스터 · 플레임위자드 · 나이트워커 · 스트라이커 · 윈드브레이커

### 🤖 에델슈타인 — 기계·전술형
- 본진 **레지스탕스 본부**. 일꾼(훈련로봇A)이 **곁에 있어야 건설이 진행**(테란식)
- 힐러(물도둑), 은신 저격(추적자), 시즈 모드 포병(방어시스템), 최종 병기 게오르크
- 영웅: 메카닉 · 와일드헌터 · 배틀메이지 · 제논 · 블래스터

---

## 🛠️ 기술 스택

- **엔진**: [MapleStory Worlds](https://maplestoryworlds.nexon.com/) (MSW Maker)
- **언어**: mLua (MSW 전용 Lua 확장 — `@Component`, `@Logic`, `@Sync`, `@ExecSpace`)
- **구조**: 서버 권위(Server-authoritative) — 생산·건설·전투·자원 판정은 모두 서버에서 검증
- **데이터**: 진영별 유닛·건물 스탯을 CSV 데이터셋으로 관리

---

## 📁 프로젝트 구조

```
MapleRTS/
├── map/                      # 맵 파일
│   ├── lobby.map             #   방 로비
│   ├── map01.map             #   진영·직업 선택 대기실
│   └── map02.map             #   게임 맵
├── ui/                       # UI 그룹 (.ui) — HUD, 명령 칸, 대기실, 결과표, 설정 등
├── Global/                   # 공용 모델(.model)·월드 설정
├── RootDesk/MyDesk/
│   ├── SetCampManager_Logic.mlua   # 진영 데이터셋 파싱
│   ├── RoomLobby/            # 방 로비 (방 만들기·입장·시작)
│   ├── WaitingMap/           # 대기실 흐름, 경기 시작·승패 판정·로비 복귀
│   ├── Hero/                 # 영웅 15종 — 데이터, 스킬, 이펙트, 부활
│   ├── Models/               # 유닛·건물 모델
│   └── PlayMap/              # 인게임 시스템
│       ├── Mouse_Keyboard_Command/   # 선택, 명령 칸, 단축키
│       ├── UnitComponent/            # 유닛 정보·이동·공격·상태(애니메이션)
│       ├── StructureComponent/       # 건물 정보·생산 대기열·건설 진행
│       ├── BuildComponent/           # 건설 미리보기, 건설 가능 영역
│       ├── Player_Scripts/           # 생산·건설 요청(서버), 플레이어 자원·인구
│       ├── Gather/ · Resource/       # 메소 채집, 에르다 몬스터·채집 건물
│       ├── Combat/                   # 시야·안개·은신 탐지, 힐러·지원 능력
│       ├── Ability/                  # 유닛 고유 능력(돌진·도발·시즈모드 등)
│       ├── Upgrade/ · JobAdvance/    # 업그레이드, 영웅 전직
│       ├── Camera/                   # RTS 카메라(가장자리 스크롤·고정)
│       ├── Stats/                    # 경기 기록·점수
│       ├── UI_Scripts/               # HUD, 미니맵, 오버레이(체력바·소유 색), 설정
│       ├── Unit_Stat_DataSet/        # 진영별 유닛 스탯 CSV
│       └── Structure_Stat_DataSet/   # 진영별 건물 스탯 CSV
└── Docs/                     # 설계·작업 문서
```

---

## ▶️ 실행 방법

1. [MSW Maker](https://maplestoryworlds.nexon.com/)를 설치합니다.
2. 이 저장소를 내려받아 MSW Maker에서 프로젝트 폴더로 엽니다.
3. **시작 맵을 로비로 설정**: Workspace → NativeScripts → Logic → `DefaultUserEnterLeaveLogic`의 **StartPoint**를 `lobby` 맵으로 지정합니다.
4. `map01`, `map02`의 MapComponent에서 **InstanceMap**이 켜져 있는지 확인합니다.
5. **Play** → 여러 명으로 테스트하려면 *Add a MultiPlayer*로 플레이어를 추가합니다.

> 자세한 설정은 [`Docs/Room-Lobby-20261005.md`](Docs/Room-Lobby-20261005.md)를 참고하세요.

---

## 📚 문서

| 문서 | 내용 |
|---|---|
| [`Docs/CampWar-TechTree.md`](Docs/CampWar-TechTree.md) | 진영별 테크트리 |
| [`Docs/Handoff-20261004.md`](Docs/Handoff-20261004.md) | 시스템 구현 이력(서버 권위·부활·승패·미니맵·시야 등) |
| [`Docs/Hero-JobAdvance-Design-20261005.md`](Docs/Hero-JobAdvance-Design-20261005.md) | 영웅 전직 설계 |
| [`Docs/FogOfWar-20261005.md`](Docs/FogOfWar-20261005.md) · [`Docs/Vision-Spec-20261004.md`](Docs/Vision-Spec-20261004.md) | 안개·시야 |
| [`Docs/InternalTest-Fixes-20261006.md`](Docs/InternalTest-Fixes-20261006.md) | 1차 내부 테스트 피드백 반영 |
| [`Docs/ResFeedback-Fixes-20261007.md`](Docs/ResFeedback-Fixes-20261007.md) | 진영별 피드백·밸런스 반영 |

---

## 👥 팀

| 이름 | 역할 |
|---|---|
| **설만수** | 기획 · 총괄 · 개발 |
| **문신혁** | 개발 리드 |
| **노승현** | 맵 디자인 · 개발 |
| **주형준** | 영웅 모델링 · 디자인 |

---

<sub>MapleStory는 NEXON Korea의 상표입니다. 이 프로젝트는 MapleStory Worlds 플랫폼에서 제작된 창작물입니다.</sub>
