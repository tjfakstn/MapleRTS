# 로비(방 목록) + 방별 게임 — 설계 (2026-10-05)

## 목표
접속 → **로비**(방 목록: 만들기·들어가기·나가기, 방장 시작) → 방 인원만 **진영 선택 대기실(map01)** → **게임(map02)** → 끝나면 **로비로 복귀**. 여러 방이 동시에 게임을 진행할 수 있다. 방 인원 1~4명(시작 최소 인원은 설정값), 방 설정은 이름만.

## MSW 구조 (공식 문서 "Creating Instance Map" 확인)
- 정적 룸(Static Room): 월드 인스턴스마다 1개. 정적 맵만 포함. → **로비 맵 `lobby`**(새로 만듦, map01 복제).
- 인스턴스 룸(Instance Room): 서버가 `RoomService:CreateInstanceRoom(key, mapNames)`로 동적으로 만든다. 인스턴스 맵만 포함. → **방마다 1개, `map01` + `map02` 사본**. 맵을 인스턴스 맵으로 쓰려면 `MapComponent.IsInstanceMap = true`.
- **"정적 룸과 인스턴스 룸은 서로 데이터에 접근할 수 없다. 그래서 Service와 Logic은 공간마다 따로 존재한다."** → `@Logic`·`_UserService`·`/maps/map02` 경로가 **룸마다 독립**. 기존 한 판짜리 코드(LobbyController 등)를 방마다 그대로 돌릴 수 있다.
- 이동: 정적 → 인스턴스 `MoveUsersToInstanceRoom(key, userIds, "map01")`, 인스턴스 → 정적 `MoveUsersToStaticRoom(userIds, "lobby")`. 인스턴스 룸 사이 직접 이동 불가. 방 삭제 API는 없어 게임마다 새 key를 쓴다.
- DataStorage는 공유(이번 작업에선 안 씀). 방 목록은 같은 월드 인스턴스(서버) 안에서만 보인다(SectorConfig maxUserNo 16).

## 구성
| 부분 | 내용 | 파일 |
|---|---|---|
| 로비 맵 | map01 복제, 정적 맵, 월드 시작 맵 | `map/lobby.map`, `Global/SectorConfig.config`(맨 앞) |
| 방 관리(서버) | 정적 룸에서만 동작. 방 표 `{id, name, host, members, state(대기/게임 중), key}`. 요청: 만들기/들어가기/나가기/시작. 시작 = 새 인스턴스 룸 생성 + 방 인원 이동. 게임 중 방은 인원이 모두 나가면(또는 룸 무효) 목록에서 제거. 방장이 나가면 다음 사람에게 넘김, 0명이면 방 삭제 | `RoomLobby/RoomLobbyLogic.mlua`(@Logic) |
| 로비 = 자유시장 광장 | 목록 화면 대신 **광장**: 캐릭터가 돌아다니고, 가운데 "FREE MARKET" 관문(메이플 리소스 `d4128e56`), 방마다 **노점**(A 무지개 천막 `76d57067`, 10-05 교체 — 예전 `659bdbe2`는 너무 어두움)이 자리(x = ±4, ±8, ±12, ±16)에 선다. 노점 머리 위 메이플 말풍선(ChatBalloon) "방 이름 / 2/4 · 대기 중", 아래 이름표(NameTag) "방장 ○○", **노점 클릭 = 입장**. 게임 중 노점은 어둡게 + "게임 중". 노점·관문은 서버가 스폰하며 스프라이트 크기를 재서 바닥(y=0)에 맞춘다 | `RoomLobby/RoomBooth.mlua`(신규), `Models/MapObjects/RoomBooth.model`·`LobbyDecor.model`(신규), `RoomLobbyLogic`(노점 관리) |
| 로비 UI(클라) | 화면은 최소: 위 안내 띠, 아래 바 하나가 번갈아 — 방 밖이면 "방 이름 + 방 만들기", 방 안이면 "내 방" 띠(방 이름·인원 칩 4개·방장 표시·게임 시작(방장)·방 나가기). 화면을 어둡게 덮지 않는다 | `ui/RoomLobbyGroup.ui`, `RoomLobby/RoomLobbyUI.mlua`, 도구 `build_room_lobby_ui.cjs` |
| 화면 전환 | lobby → 로비 UI / map01 → 대기실 UI / map02 → 게임 HUD | `SceneController` |
| 대기실(방 안) | 기존 그대로 + "로비로 나가기" 버튼. 경기 로직은 인스턴스 룸에서만 | `LobbyController`, `ui/LobbyGroup.ui` |
| 경기 종료 | 결과 표시 후 대기실이 아니라 **로비로** 복귀(항복자도 로비로) | `LobbyController.ReturnToLobby/RequestSurrender` |

## 광장 2층 (2026-10-06)
- 횡스크롤 광장: 1층 돌 바닥(x −8.93 ~ 8.03) 위 노점 4칸 + 같은 돌 바닥 2층(윗면 y 4.8) 위 노점 4칸, x ±3.4 · ±6.6(`BoothSlotsX`·`BoothSlotsY`, 1층부터). 관문 양옆 밧줄 사다리(x ±1.9). 발판 1층 34 + 2층 18. 노점·관문 배율 0.7.
- 장식: 구름 · 양 끝 큰 나무 · 1·2층 가로등 + 화단(x ±5). 미리보기 `Docs/preview/lobby_map_real.png`, 도구 `메이플RTS_tools/build_lobby_decor.cjs`.

## Maker에서 확인할 것 (이 Mac엔 Maker 없음)
1. map01·map02 MapComponent **InstanceMap 체크**가 켜져 있는지(파일로 켜 뒀지만 Maker가 맵을 다시 읽지 않으면 꺼진 채로 남는다 → 맵 열고 Property 창에서 직접 체크 후 저장). 꺼져 있으면 증상: ① 시작하자마자 map01(진영 선택)에 들어감 ② 방장이 "게임 시작"을 눌러도 이동 없이 노점만 "게임 중"이 됨. 이제 ②는 RequestStartRoom이 이동 0명이면 방을 "대기 중"으로 되돌리고 "InstanceMap 설정 확인" 토스트 + 경고 로그를 남긴다
2. **시작 맵 = lobby로 바꾸기(필수)**: Workspace → NativeScripts → Logic → **DefaultUserEnterLeaveLogic** 선택 → Property 창 **StartPoint**를 `/maps/map01` → `/maps/lobby`로 변경(lobby 맵 우클릭 → Copy Entry Path 값). 기본값이 map01이라 안 바꾸면 바로 진영 선택이 뜬다. 코드 안전망: RoomLobbyLogic.PullStraysToLobby가 정적 룸에서 로비 밖 맵에 들어온 유저를 0.25초 안에 로비로 순간이동시킨다(그래서 잠깐 진영 선택 화면이 비칠 수 있음 → 설정 변경 권장)
3. 여러 명 테스트: [Start] → Add a MultiPlayer로 2~3명 → 방 만들기/입장/시작 → 진영 선택 → 게임 → 로비 복귀, 방 2개 동시 진행
4. 로비 2층: 캐릭터가 1층 돌 바닥 윗면에 서는지, 사다리로 2층에 오르는지, 방 5개째부터 2층 노점이 서는지
