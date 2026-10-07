# 사운드 후보 목록 (2026-10-05) — 검토용

## ✅ 확정 목록 (갱신: 2026-10-05)

| 슬롯 | RUID | 이름 | 길이 | 비고 |
|---|---|---|---:|---|
| 모험가 인게임 BGM 1 | `a8d9d161381c4f7bab3b95f8871662eb` | sound-375 | 205.8 | 신비 도입 → 웅장·모험 |
| 모험가 인게임 BGM 2 | `7a8f657721f7432fa0804dfbf2b8aadc` | sound-255 | 260.3 | 긴장감 리듬, 던전·전투 |
| 모험가 인게임 BGM 3 | `00ae4af8800c4e2587cc3118c8b88beb` | sound-2 | 103.3 | 웅장·신비, 금관 |

| 시그너스 인게임 BGM 1 | `063f1dddbf8b4a1bb9067b0c7a196922` | sound-14 | 189.6 | 서정·신비, 피아노·현악 |
| 시그너스 인게임 BGM 2 | `ba8ce178a584420d98e6e9c9db792881` | sound-422 | 149.5 | 몽환적 피아노·현악, 평화로운 탐험 |
| 시그너스 인게임 BGM 3 | `8a81d1865d1f4152b4cbf800efed62af` | sound-296 | 125.6 | 웅장 오케 + 긴장 퍼커션 |

| 에델슈타인 인게임 BGM 1 | `bf1f1c64293943baa5ce66a2b6c8ce76` | sound-440 | 178.9 | 미스터리·산업 전자, 연구소 |
| 에델슈타인 인게임 BGM 2 | `af3acec8784a4f80a0a354479b2132ff` | sound-388 | 165.0 | 레트로 신스, 신비·긴장 리듬 |
| 에델슈타인 인게임 BGM 3 | `732c8aeac0624d21bdcfc89bc6244105` | sound-237 | 144.1 | 어두운 금속성 타격 + 낮은 신스 |

모험가 3곡 순환 합계 약 9.5분(375 → 255 → 2 순서 권장). 시그너스 3곡 합계 약 7.7분(14 → 422 → 296 권장: 서정 두 곡 뒤에 긴장곡). 에델슈타인 3곡(440 → 388 → 237, 합 약 8.1분) 확정. 긴박곡 추가는 하지 않기로 결정(10-05). **세 진영 BGM 모두 확정 → 코드 연결 진행.**

### 코드 연결 상태 (2026-10-05)

- `PlayMap/UI_Data/SoundResources.mlua`(신규 @Logic): BGM RUID 표. 진영별 목록은 `"RUID:길이초|RUID:길이초|..."` 문자열 프로퍼티(`BgmAdv`/`BgmCyg`/`BgmEde`). `BgmLobby`/`BgmVictory`/`BgmDefeat`는 아직 비어 있음(비면 무음/정지). Maker 인스펙터에서 바로 바꿀 수 있다.
- `WaitingMap/SceneFlow/BgmController.mlua`(신규 @Logic, 클라 전용): 0.5초마다 `SceneController.InGame`과 로컬 `PlayerInfo.SelectedCamp`를 보고 목록을 고른다. 인게임은 1번 곡부터 순서대로, 곡 길이(표)+0.2초가 지나면 `_SoundService:PlayBGM`으로 다음 곡. 1곡짜리 목록은 엔진 반복에 맡김. 경기 종료 시 `LobbyController.EndMatch`가 각 클라에 `PlayResult(승패)`를 보내 결과곡(없으면 정지)으로 바꾸고, 로비 복귀 때 대기실 곡으로 돌아간다.
- 효과음(UI/유닛/전투/영웅/알림)은 아직 ✅ 전이라 코드에 연결하지 않았다. 확정되면 `SoundResources`에 슬롯을 추가하고 호출 지점에 `_SoundService:PlaySound(_SoundResources.<슬롯>, vol)`을 넣는다.

- 출처: MSW 리소스 검색(https://maplestoryworlds-resourcesearch-new.nexon.com) `api/v3/search/resources` 의미 검색. 점수는 검색 유사도(0~1), 길이는 초.
- 각 행의 링크를 열면 사이트에서 바로 미리 들을 수 있다. **채택할 RUID에 ✅ 표시해 주면 코드에 연결한다.**
- 영웅 스킬은 리소스 설명이 직업명을 모르므로 "효과 성격"으로 검색했다. 결과가 약하면 기존 3명(비숍·보우마스터·다크나이트)이 쓰는 RUID 계열을 재사용하는 안도 아래에 적었다.


## BGM

### BGM 로비/진영선택  <sub>(bgm, 검색어: 평화롭고 밝은 마을 대기실 배경음악 모험을 준비하는 느낌)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `df68e970951740de8f8235d1e5316b23` | sound-535 | 120.1 | 0.837 | 경쾌한 피아노 선율과 현악기가 어우러져 모험의 설렘과 신비로운 분위기를 자아내는 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=df68e970951740de8f8235d1e5316b23) |
| ☐ | `8cb1d47fdcf44e6dbf9f513076526c8c` | sound-303 | 36.4 | 0.792 | 어쿠스틱 기타의 경쾌한 리듬이 돋보이는 밝고 활기찬 분위기의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8cb1d47fdcf44e6dbf9f513076526c8c) |
| ☐ | `a532a9d31a954885b558d77538aa0cca` | sound-368 | 130.1 | 0.79 | 어쿠스틱 기타와 플루트 선율이 돋보이는 경쾌하고 활기찬 모험 분위기의 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a532a9d31a954885b558d77538aa0cca) |
| ☐ | `2dd03c76b331416bbf9752f6a897988e` | sound-98 | 141.5 | 0.79 | 경쾌하고 밝은 분위기의 마을 배경음악으로 어쿠스틱 기타와 아코디언 연주가 돋보이는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2dd03c76b331416bbf9752f6a897988e) |
| ☐ | `387dee48e8064f9091b090f45a8d94cf` | sound-126 | 134.5 | 0.789 | 밝고 경쾌한 오케스트라 선율이 돋보이는 곡으로 모험의 시작을 알리는 마을이나 필드에 어울리는 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=387dee48e8064f9091b090f45a8d94cf) |
| ☐ | `87455f5f463441b4befc83a2c0b8b12a` | sound-285 | 122.3 | 0.787 | 피아노와 현악기가 어우러진 밝고 경쾌한 분위기의 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=87455f5f463441b4befc83a2c0b8b12a) |
| ☐ | `840d9bb3ee8244c689fa5eaa02063a89` | sound-279 | 125.8 | 0.786 | 통기타와 플루트 선율이 어우러진 밝고 평화로운 분위기의 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=840d9bb3ee8244c689fa5eaa02063a89) |
| ☐ | `a4b033c7fc8b48c99d398a912f837511` | sound-365 | 135.9 | 0.785 | 모험의 시작을 알리는 듯한 밝고 활기찬 오케스트라 풍의 게임 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a4b033c7fc8b48c99d398a912f837511) |
| ☐ | `3c7eac1135c54c06963e44aeea3306f7` | sound-135 | 122.3 | 0.778 | 피아노와 플루트, 신스음이 어우러진 밝고 경쾌한 분위기의 판타지 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3c7eac1135c54c06963e44aeea3306f7) |
| ☐ | `95bed36bb42e421aa6d8070f02dae80c` | sound-331 | 140.7 | 0.778 | 오케스트라와 피아노가 어우러진 서정적이면서도 경쾌한 분위기의 판타지 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=95bed36bb42e421aa6d8070f02dae80c) |
| ☐ | `c97353f4ebcd4af1b9c69a521fb1a635` | sound-470 | 169.8 | 0.778 | 밝고 경쾌한 마을 배경음악으로 피아노와 플루트가 어우러진 활기찬 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c97353f4ebcd4af1b9c69a521fb1a635) |
| ☐ | `7b302352b0614439861f89eda29fad3f` | sound-257 | 155 | 0.777 | 피아노와 목관악기가 어우러진 밝고 경쾌한 분위기의 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7b302352b0614439861f89eda29fad3f) |
| ☐ | `6ac20b63715b4701b318cbb5842ff1ff` | sound-214 | 126.1 | 0.777 | 활기차고 모험적인 분위기의 오케스트라 곡으로, 현악기와 목관악기가 어우러진 밝은 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6ac20b63715b4701b318cbb5842ff1ff) |
| ☐ | `bfb906b5891345d59fcf013bfec2b507` | sound-441 | 81.7 | 0.776 | 피아노와 플루트, 현악기가 어우러진 밝고 경쾌한 분위기의 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bfb906b5891345d59fcf013bfec2b507) |
| ☐ | `e08a91d5292e423ebbc511ff14df482c` | sound-537 | 146.9 | 0.774 | 경쾌한 피아노 선율과 오케스트라 악기들이 어우러진 밝고 활기찬 모험 분위기의 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e08a91d5292e423ebbc511ff14df482c) |
| ☐ | `b71c08c8bdbb4c8198ab577e17787fe8` | sound-413 | 89.6 | 0.773 | 피아노와 경쾌한 오케스트라 선율이 돋보이는 활기차고 희망찬 모험 테마곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b71c08c8bdbb4c8198ab577e17787fe8) |
| ☐ | `ad5ae4151d0f4adaa56922febbb43bcf` | sound-384 | 119.4 | 0.772 | 밝고 경쾌한 마을 배경음악으로 피아노와 플루트 선율이 조화롭게 어우러진 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ad5ae4151d0f4adaa56922febbb43bcf) |
| ☐ | `ade75165d86c409aa50a1115722ceb54` | sound-385 | 177.8 | 0.771 | 플루트와 어쿠스틱 기타가 어우러진 밝고 평화로운 분위기의 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ade75165d86c409aa50a1115722ceb54) |
| ☐ | `3dd2569b18b546568d356412c3bab8b5` | sound-138 | 170.1 | 0.77 | 활기차고 모험적인 분위기의 오케스트라 곡으로, 밝은 마을이나 필드 배경에 어울리는 경쾌한 음악입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3dd2569b18b546568d356412c3bab8b5) |
| ☐ | `1be6ad577d5a49978b1aac40a38aa996` | sound-58 | 128.3 | 0.769 | 바이올린 선율이 돋보이는 빠르고 경쾌한 오케스트라 곡으로, 활기찬 마을이나 모험의 시작에 어울리는 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1be6ad577d5a49978b1aac40a38aa996) |

### BGM 인게임 기본(공용)  <sub>(bgm, 검색어: 전략 게임 전투 준비 긴장감 있는 웅장한 오케스트라 배경음악)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `dd94f8153ab94cf8807de5327aa5c5f7` | sound-527 | 93.4 | 0.813 | 긴박하고 웅장한 오케스트라 사운드로 전투나 추격 장면에 어울리는 강렬한 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dd94f8153ab94cf8807de5327aa5c5f7) |
| ☐ | `e81c438b3fec4bf68a932323a4876975` | sound-649 | 95.1 | 0.811 | 웅장한 오케스트라 사운드와 긴박한 합창이 어우러진 드라마틱한 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e81c438b3fec4bf68a932323a4876975) |
| ☐ | `3b038b734432424ea4bea567997ea12d` | sound-132 | 32.5 | 0.808 | 웅장한 오케스트라 사운드와 합창이 어우러져 긴박함과 몰입감을 주는 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3b038b734432424ea4bea567997ea12d) |
| ☐ | `89a9b4312f894c3cbab274dd05fdd758` | sound-291 | 33.6 | 0.805 | 강렬한 오케스트라 연주와 긴박한 리듬이 돋보이는 웅장한 보스 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=89a9b4312f894c3cbab274dd05fdd758) |
| ☐ | `1d218b1555594e259e8dd37f205c9be0` | sound-62 | 98 | 0.802 | 강렬한 오케스트라 브라스와 일렉트릭 기타 사운드가 돋보이는 웅장하고 긴박한 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1d218b1555594e259e8dd37f205c9be0) |
| ☐ | `6329b911eb214276872ad605ba18e524` | sound-648 | 95.1 | 0.802 | 웅장한 오케스트라와 합창이 어우러진 긴박하고 강렬한 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6329b911eb214276872ad605ba18e524) |
| ☐ | `831aab90dc6045c88f5c73643c02f591` | sound-278 | 85.4 | 0.798 | 웅장한 오케스트라 사운드와 긴장감 넘치는 타악기가 어우러진 서사적인 분위기의 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=831aab90dc6045c88f5c73643c02f591) |
| ☐ | `1ab072bf95e24ddba7d758f21af04ad1` | sound-54 | 36.9 | 0.797 | 웅장한 오케스트라 사운드와 긴박한 리듬이 돋보이는 모험과 전투 테마의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1ab072bf95e24ddba7d758f21af04ad1) |
| ☐ | `7f73d3afe48a4d618dcda18f741731b5` | sound-646 | 150.8 | 0.785 | 웅장한 오케스트라 선율이 돋보이며 모험의 설렘과 긴장감을 동시에 담아낸 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7f73d3afe48a4d618dcda18f741731b5) |
| ☐ | `2a0257f832ee4a7c84c0a8efc9aa5bba` | sound-87 | 125.3 | 0.784 | 긴박하고 웅장한 오케스트라 사운드로 긴장감 넘치는 보스 전투나 극적인 장면에 어울리는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a0257f832ee4a7c84c0a8efc9aa5bba) |
| ☐ | `32330a23b78a4c9cbc56e9d05d985a06` | sound-112 | 92.2 | 0.779 | 강렬한 일렉 기타와 웅장한 오케스트라 사운드가 어우러진 긴박하고 에너제틱한 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=32330a23b78a4c9cbc56e9d05d985a06) |
| ☐ | `7d681eceb71d44f88a36b32422180d8c` | sound-262 | 134.5 | 0.773 | 긴박하고 웅장한 오케스트라 사운드로 긴장감 넘치는 전투나 보스전 상황에 어울리는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7d681eceb71d44f88a36b32422180d8c) |
| ☐ | `949ee1aace064a74bb72069f6126bfbd` | sound-327 | 98.1 | 0.77 | 웅장하고 긴박한 분위기의 오케스트라 곡으로 강렬한 금관 악기와 타악기가 조화를 이루어 전투나 보스전에 어울리는 음악입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=949ee1aace064a74bb72069f6126bfbd) |
| ☐ | `8a7aabed91c14684b0ff2214838762e1` | sound-295 | 127.1 | 0.769 | 강렬하고 긴박한 분위기의 오케스트라 전투 배경음악으로 빠른 현악기와 웅장한 금관악기가 돋보이는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8a7aabed91c14684b0ff2214838762e1) |
| ☐ | `636ff098ea254d3a82e29e311f5be712` | sound-204 | 86.3 | 0.766 | 긴박하고 웅장한 오케스트라 사운드와 강렬한 타악기 리듬이 돋보이는 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=636ff098ea254d3a82e29e311f5be712) |
| ☐ | `a66b9df2d3f742abb4f1da5c2dfb33a0` | sound-371 | 125.5 | 0.765 | 웅장한 오케스트라 사운드와 긴박한 리듬이 돋보이는 강렬한 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a66b9df2d3f742abb4f1da5c2dfb33a0) |
| ☐ | `4cb9a18f1ed540ada6f40e7cd1612a65` | sound-155 | 123.8 | 0.765 | 웅장하고 긴박한 분위기의 오케스트라 곡으로 강렬한 타악기와 금관악기가 어우러져 전투의 긴장감을 자아낸다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4cb9a18f1ed540ada6f40e7cd1612a65) |
| ☐ | `bf12afd2632644b19e8f6075339907d9` | sound-439 | 128.5 | 0.762 | 웅장한 오케스트라 사운드와 긴장감 넘치는 합창이 어우러진 강렬한 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bf12afd2632644b19e8f6075339907d9) |
| ☐ | `9539fc02cc6d451fa9f13e8db1136d58` | sound-329 | 128.1 | 0.761 | 긴박하고 웅장한 분위기의 오케스트라 곡으로, 강렬한 비트와 현악기 선율이 어우러진 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9539fc02cc6d451fa9f13e8db1136d58) |
| ☐ | `764aa2962eda4610ad5351a1fc2a3199` | sound-243 | 127.7 | 0.759 | 웅장한 오케스트라 사운드와 긴박한 리듬이 돋보이는 강렬한 보스 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=764aa2962eda4610ad5351a1fc2a3199) |

### BGM 진영-모험가  <sub>(bgm, 검색어: 밝고 모험적인 숲과 초원 분위기 오케스트라 플루트)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `7f73d3afe48a4d618dcda18f741731b5` | sound-646 | 150.8 | 0.779 | 웅장한 오케스트라 선율이 돋보이며 모험의 설렘과 긴장감을 동시에 담아낸 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7f73d3afe48a4d618dcda18f741731b5) |
| ☐ | `df68e970951740de8f8235d1e5316b23` | sound-535 | 120.1 | 0.772 | 경쾌한 피아노 선율과 현악기가 어우러져 모험의 설렘과 신비로운 분위기를 자아내는 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=df68e970951740de8f8235d1e5316b23) |
| ☐ | `3dd2569b18b546568d356412c3bab8b5` | sound-138 | 170.1 | 0.77 | 활기차고 모험적인 분위기의 오케스트라 곡으로, 밝은 마을이나 필드 배경에 어울리는 경쾌한 음악입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3dd2569b18b546568d356412c3bab8b5) |
| ☐ | `6ac20b63715b4701b318cbb5842ff1ff` | sound-214 | 126.1 | 0.767 | 활기차고 모험적인 분위기의 오케스트라 곡으로, 현악기와 목관악기가 어우러진 밝은 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6ac20b63715b4701b318cbb5842ff1ff) |
| ☐ | `a65afaec5a4b4c19a1e1a366c710508e` | sound-369 | 33.6 | 0.766 | 피아노와 현악기, 목관악기가 어우러져 통통 튀는 느낌을 주는 빠르고 경쾌한 분위기의 곡입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a65afaec5a4b4c19a1e1a366c710508e) |
| ☐ | `387dee48e8064f9091b090f45a8d94cf` | sound-126 | 134.5 | 0.766 | 밝고 경쾌한 오케스트라 선율이 돋보이는 곡으로 모험의 시작을 알리는 마을이나 필드에 어울리는 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=387dee48e8064f9091b090f45a8d94cf) |
| ☐ | `a8d9d161381c4f7bab3b95f8871662eb` | sound-375 | 205.8 | 0.762 | 신비롭고 긴장감 있는 분위기에서 점차 웅장하고 모험적인 느낌으로 변화하는 오케스트라 배경음악입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a8d9d161381c4f7bab3b95f8871662eb) |
| ☐ | `86c104bf5ff84f8693a471ef40105975` | sound-283 | 135.2 | 0.76 | 웅장한 오케스트라와 이국적인 타악기가 어우러져 모험과 탐험의 분위기를 자아내는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=86c104bf5ff84f8693a471ef40105975) |
| ☐ | `1ab072bf95e24ddba7d758f21af04ad1` | sound-54 | 36.9 | 0.758 | 웅장한 오케스트라 사운드와 긴박한 리듬이 돋보이는 모험과 전투 테마의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1ab072bf95e24ddba7d758f21af04ad1) |
| ☐ | `8b57ad3bb40742a1b4955390bf14b36d` | sound-300 | 99.2 | 0.754 | 밝고 경쾌한 분위기의 오케스트라 곡으로, 플루트와 현악기가 어우러져 평화로운 마을이나 모험의 시작을 연상시킵니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8b57ad3bb40742a1b4955390bf14b36d) |
| ☐ | `e29a9b42178c42baa50cc1eb6e130b2d` | sound-542 | 87.2 | 0.753 | 평화롭고 아기자기한 마을의 분위기를 담은 경쾌한 오케스트라 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e29a9b42178c42baa50cc1eb6e130b2d) |
| ☐ | `5d29291eb5e84b1a8669395f5672b65f` | sound-191 | 142.1 | 0.753 | 레트로한 8비트 사운드와 경쾌한 오케스트라 요소가 어우러진 밝고 활기찬 분위기의 게임 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5d29291eb5e84b1a8669395f5672b65f) |
| ☐ | `c97353f4ebcd4af1b9c69a521fb1a635` | sound-470 | 169.8 | 0.752 | 밝고 경쾌한 마을 배경음악으로 피아노와 플루트가 어우러진 활기찬 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c97353f4ebcd4af1b9c69a521fb1a635) |
| ☐ | `4fc7d1d6121d48f4b4051e98fff30a86` | sound-160 | 216.9 | 0.751 | 플루트와 현악기가 어우러진 밝고 희망찬 분위기의 모험 테마 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4fc7d1d6121d48f4b4051e98fff30a86) |
| ☐ | `87455f5f463441b4befc83a2c0b8b12a` | sound-285 | 122.3 | 0.751 | 피아노와 현악기가 어우러진 밝고 경쾌한 분위기의 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=87455f5f463441b4befc83a2c0b8b12a) |
| ☐ | `e08a91d5292e423ebbc511ff14df482c` | sound-537 | 146.9 | 0.749 | 경쾌한 피아노 선율과 오케스트라 악기들이 어우러진 밝고 활기찬 모험 분위기의 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e08a91d5292e423ebbc511ff14df482c) |
| ☐ | `3c7eac1135c54c06963e44aeea3306f7` | sound-135 | 122.3 | 0.748 | 피아노와 플루트, 신스음이 어우러진 밝고 경쾌한 분위기의 판타지 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3c7eac1135c54c06963e44aeea3306f7) |
| ☐ | `8228f7d5f8a04dfdb024acb1fd98b8ac` | sound-273 | 174.1 | 0.748 | 신비롭고 몽환적인 분위기의 오케스트라 곡으로 피아노와 스트링 선율이 조화를 이루며 모험을 떠나는 듯한 느낌을 주는 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8228f7d5f8a04dfdb024acb1fd98b8ac) |
| ☐ | `ba8ce178a584420d98e6e9c9db792881` | sound-422 | 149.5 | 0.748 | 신비롭고 몽환적인 분위기의 오케스트라 곡으로 피아노와 현악기가 어우러져 평화로운 탐험의 느낌을 줍니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ba8ce178a584420d98e6e9c9db792881) |
| ☐ | `b1f8adb645204bbf826e4c99248dfb68` | sound-399 | 124.5 | 0.747 | 신비롭고 모험적인 분위기의 곡으로, 스타카토 현악기와 목관악기가 어우러져 경쾌하면서도 호기심을 자극하는 배경음악입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b1f8adb645204bbf826e4c99248dfb68) |

### BGM 진영-시그너스  <sub>(bgm, 검색어: 신성하고 우아한 기사단 성가 합창 오케스트라 장엄)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `4c7aea4348314c8abc94341d42f0b2be` | sound-154 | 92.8 | 0.642 | 피아노와 현악기가 어우러져 우아하고 신비로운 분위기를 자아내는 왈츠풍의 오케스트라 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4c7aea4348314c8abc94341d42f0b2be) |
| ☐ | `e81c438b3fec4bf68a932323a4876975` | sound-649 | 95.1 | 0.634 | 웅장한 오케스트라 사운드와 긴박한 합창이 어우러진 드라마틱한 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e81c438b3fec4bf68a932323a4876975) |
| ☐ | `6329b911eb214276872ad605ba18e524` | sound-648 | 95.1 | 0.633 | 웅장한 오케스트라와 합창이 어우러진 긴박하고 강렬한 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6329b911eb214276872ad605ba18e524) |
| ☐ | `3b038b734432424ea4bea567997ea12d` | sound-132 | 32.5 | 0.627 | 웅장한 오케스트라 사운드와 합창이 어우러져 긴박함과 몰입감을 주는 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3b038b734432424ea4bea567997ea12d) |
| ☐ | `4392446bf405463ba944feb33c585f6e` | sound-145 | 102.5 | 0.626 | 피아노와 현악기, 애절한 보컬이 어우러져 감동적이고 서정적인 분위기를 자아내는 시네마틱한 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4392446bf405463ba944feb33c585f6e) |
| ☐ | `c386a7d316bd46b6a27098e7dc37b8ea` | sound-454 | 89.5 | 0.624 | 웅장한 합창과 현악기가 어우러져 신비롭고 긴장감 넘치는 분위기를 조성하는 시네마틱 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c386a7d316bd46b6a27098e7dc37b8ea) |
| ☐ | `4a48bbd4b74142a6a997d478e78ed870` | sound-150 | 207 | 0.621 | 웅장한 오케스트라 서곡으로 시작하여 강렬한 일렉 기타와 빠른 비트가 이어지는 박진감 넘치는 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4a48bbd4b74142a6a997d478e78ed870) |
| ☐ | `063f1dddbf8b4a1bb9067b0c7a196922` | sound-14 | 189.6 | 0.617 | 신비롭고 서정적인 분위기의 오케스트라 곡으로 피아노와 현악기가 어우러져 평화로운 느낌을 줍니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=063f1dddbf8b4a1bb9067b0c7a196922) |
| ☐ | `00ae4af8800c4e2587cc3118c8b88beb` | sound-2 | 103.3 | 0.617 | 웅장하고 신비로운 분위기의 오케스트라 곡으로, 긴박한 리듬과 강력한 금관 악기가 어우러져 모험이나 전투 장면에 어울리는 배경음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=00ae4af8800c4e2587cc3118c8b88beb) |
| ☐ | `7205b36f60e8463987bdfe95f9ef972b` | sound-231 | 91.6 | 0.615 | 웅장한 합창과 오케스트라가 어우러진 긴박하고 압도적인 분위기의 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7205b36f60e8463987bdfe95f9ef972b) |
| ☐ | `c78591fac73847b5be4dfc0143cc1241` | sound-461 | 95.8 | 0.611 | 웅장한 오케스트라와 합창이 어우러져 긴장감과 박진감을 주는 보스 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c78591fac73847b5be4dfc0143cc1241) |
| ☐ | `a3b78cba21f94f79851e38d2cd720f1a` | sound-362 | 96.1 | 0.611 | 웅장하고 어두운 분위기의 오케스트라 곡으로, 남성 합창과 강렬한 금관악기가 긴장감 넘치는 전투 장면을 연상시킵니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a3b78cba21f94f79851e38d2cd720f1a) |
| ☐ | `89a9b4312f894c3cbab274dd05fdd758` | sound-291 | 33.6 | 0.608 | 강렬한 오케스트라 연주와 긴박한 리듬이 돋보이는 웅장한 보스 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=89a9b4312f894c3cbab274dd05fdd758) |
| ☐ | `a3e1d64b93824ddd809a9b81a2ded673` | sound-363 | 102.4 | 0.604 | 웅장한 오케스트라와 합창이 어우러진 긴박하고 강렬한 분위기의 보스 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a3e1d64b93824ddd809a9b81a2ded673) |
| ☐ | `bf12afd2632644b19e8f6075339907d9` | sound-439 | 128.5 | 0.604 | 웅장한 오케스트라 사운드와 긴장감 넘치는 합창이 어우러진 강렬한 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bf12afd2632644b19e8f6075339907d9) |
| ☐ | `0e26468d34c2466f97ed8d0e8fd86764` | sound-29 | 101.5 | 0.603 | 웅장하고 긴박한 분위기의 오케스트라 곡으로, 강렬한 금관 악기와 현악기가 어우러진 보스전 배경음악. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0e26468d34c2466f97ed8d0e8fd86764) |
| ☐ | `8d37a92619014935bdec8487e65f4227` | sound-305 | 148.2 | 0.6 | 부드러운 피아노 선율과 은은한 현악기가 어우러진 평화롭고 따뜻한 분위기의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8d37a92619014935bdec8487e65f4227) |
| ☐ | `7f73d3afe48a4d618dcda18f741731b5` | sound-646 | 150.8 | 0.598 | 웅장한 오케스트라 선율이 돋보이며 모험의 설렘과 긴장감을 동시에 담아낸 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7f73d3afe48a4d618dcda18f741731b5) |
| ☐ | `949ee1aace064a74bb72069f6126bfbd` | sound-327 | 98.1 | 0.598 | 웅장하고 긴박한 분위기의 오케스트라 곡으로 강렬한 금관 악기와 타악기가 조화를 이루어 전투나 보스전에 어울리는 음악입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=949ee1aace064a74bb72069f6126bfbd) |
| ☐ | `2a0257f832ee4a7c84c0a8efc9aa5bba` | sound-87 | 125.3 | 0.596 | 긴박하고 웅장한 오케스트라 사운드로 긴장감 넘치는 보스 전투나 극적인 장면에 어울리는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a0257f832ee4a7c84c0a8efc9aa5bba) |

### BGM 진영-에델슈타인  <sub>(bgm, 검색어: 기계적이고 산업적인 전자음악 미래 도시 공장 분위기)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `bfa8c3e2a33f4e8d871e03df2737c304` | sound-442 | 327.4 | 0.756 | 긴장감 넘치는 분위기의 산업적인 배경음악으로, 금속성 타악기와 신시사이저가 어우러져 기계적인 느낌을 줍니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bfa8c3e2a33f4e8d871e03df2737c304) |
| ☐ | `8aeeed0861e242a7b1e17867cd560bb8` | sound-298 | 130.1 | 0.752 | 강렬한 일렉트릭 기타 리프와 비트가 긴장감을 조성하는 매우 빠르고 파워풀한 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8aeeed0861e242a7b1e17867cd560bb8) |
| ☐ | `bf1f1c64293943baa5ce66a2b6c8ce76` | sound-440 | 178.9 | 0.747 | 미스테리하고 산업적인 분위기의 전자 음악으로, 연구소나 미래적인 공간에 어울리는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bf1f1c64293943baa5ce66a2b6c8ce76) |
| ☐ | `2f6c3b7579d04d1297ff1f913a4788b9` | sound-103 | 112.5 | 0.738 | 세련된 비트와 몽환적인 신스 사운드가 어우러진 도시적인 분위기의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2f6c3b7579d04d1297ff1f913a4788b9) |
| ☐ | `2de176cd6a9f496caf8c2bd06e961838` | sound-99 | 113.7 | 0.723 | 그루비한 비트와 신비로운 분위기가 어우러진 일렉트로닉 배경음악으로, 도시나 던전 탐험에 어울리는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2de176cd6a9f496caf8c2bd06e961838) |
| ☐ | `82a6606e1a074934be368b8e4a642b45` | sound-275 | 130.5 | 0.721 | 빠르고 강렬한 비트와 신시사이저 사운드가 어우러진 긴박감 넘치는 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=82a6606e1a074934be368b8e4a642b45) |
| ☐ | `80a18b7f3e87412e8e8c487cdb8a065b` | sound-268 | 153.6 | 0.72 | 신비롭고 기묘한 분위기의 곡으로, 오케스트라 악기와 전자음이 어우러져 긴장감과 호기심을 자아냅니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=80a18b7f3e87412e8e8c487cdb8a065b) |
| ☐ | `563451bdf50146279f110e8dadb56875` | sound-176 | 45 | 0.715 | 강렬한 일렉 기타 리프와 드럼 비트가 어우러진 세련되고 에너지 넘치는 록 스타일의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=563451bdf50146279f110e8dadb56875) |
| ☐ | `a0d187258cd4485eb9860abd8dfacb99` | sound-355 | 104.6 | 0.709 | 레트로한 칩튠 사운드와 현대적인 신스팝이 결합된 빠르고 세련된 분위기의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a0d187258cd4485eb9860abd8dfacb99) |
| ☐ | `fbc4290f54894595a3e507c2cdad4117` | sound-605 | 40.9 | 0.7 | 오르골 소리가 중심이 되는 차분하고 몽환적인 분위기의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fbc4290f54894595a3e507c2cdad4117) |
| ☐ | `78e27b35f81c431ca80ef11c14a74ffc` | sound-251 | 124.2 | 0.699 | 강렬한 비트와 긴박한 신스 멜로디가 돋보이는 빠른 템포의 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=78e27b35f81c431ca80ef11c14a74ffc) |
| ☐ | `732c8aeac0624d21bdcfc89bc6244105` | sound-237 | 144.1 | 0.695 | 어둡고 긴장감 넘치는 분위기의 곡으로 금속성 타격음과 낮은 신스음이 조화를 이루어 공포나 보스전 도입부에 어울리는 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=732c8aeac0624d21bdcfc89bc6244105) |
| ☐ | `32330a23b78a4c9cbc56e9d05d985a06` | sound-112 | 92.2 | 0.693 | 강렬한 일렉 기타와 웅장한 오케스트라 사운드가 어우러진 긴박하고 에너제틱한 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=32330a23b78a4c9cbc56e9d05d985a06) |
| ☐ | `72cc8a13d806422caa3c9be5289ca98c` | sound-236 | 96 | 0.692 | 강렬한 일렉 기타와 웅장한 오케스트라 사운드가 어우러진 긴박하고 에너지 넘치는 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=72cc8a13d806422caa3c9be5289ca98c) |
| ☐ | `3379dfab54a84c4ca8ae1b77af2e7e3e` | sound-113 | 122.5 | 0.691 | 강렬한 일렉 기타와 웅장한 오케스트라가 조화를 이루는 빠르고 긴박한 전투 배경음악입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3379dfab54a84c4ca8ae1b77af2e7e3e) |
| ☐ | `3b8bb6a391be45e481a2a323e9f445dd` | sound-133 | 126.9 | 0.69 | 경쾌한 일렉트릭 피아노와 베이스 리듬이 돋보이는 그루비하고 활기찬 분위기의 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3b8bb6a391be45e481a2a323e9f445dd) |
| ☐ | `c1d0a02aca8f4f3fa0c20ba2186bc9ec` | sound-448 | 101 | 0.69 | 신비롭고 긴장감 넘치는 분위기의 오케스트라 곡으로 현악기와 목관악기가 조화를 이루는 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c1d0a02aca8f4f3fa0c20ba2186bc9ec) |
| ☐ | `f2677ea116ba4474bd80277b32545758` | sound-571 | 141.9 | 0.689 | 긴장감 넘치는 분위기와 빠른 비트의 신스 사운드가 어우러진 사이버펑크 스타일의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f2677ea116ba4474bd80277b32545758) |
| ☐ | `85ce3923fe4844d98b7823efad6a0976` | sound-282 | 87.7 | 0.689 | 긴장감 넘치는 신스 사운드와 빠른 비트가 어우러진 복고풍 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=85ce3923fe4844d98b7823efad6a0976) |
| ☐ | `efc990867e2a4a10af0d3a10a8d645f3` | sound-565 | 122 | 0.689 | 웅장한 오케스트라 선율과 강렬한 타악기 리듬이 돋보이는 긴박하고 에너지 넘치는 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=efc990867e2a4a10af0d3a10a8d645f3) |

### BGM 교전 전환  <sub>(bgm, 검색어: 긴박하고 빠른 템포의 보스 전투 배경음악 강렬한 타악기)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `89a9b4312f894c3cbab274dd05fdd758` | sound-291 | 33.6 | 0.874 | 강렬한 오케스트라 연주와 긴박한 리듬이 돋보이는 웅장한 보스 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=89a9b4312f894c3cbab274dd05fdd758) |
| ☐ | `6329b911eb214276872ad605ba18e524` | sound-648 | 95.1 | 0.865 | 웅장한 오케스트라와 합창이 어우러진 긴박하고 강렬한 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6329b911eb214276872ad605ba18e524) |
| ☐ | `32330a23b78a4c9cbc56e9d05d985a06` | sound-112 | 92.2 | 0.863 | 강렬한 일렉 기타와 웅장한 오케스트라 사운드가 어우러진 긴박하고 에너제틱한 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=32330a23b78a4c9cbc56e9d05d985a06) |
| ☐ | `dd94f8153ab94cf8807de5327aa5c5f7` | sound-527 | 93.4 | 0.859 | 긴박하고 웅장한 오케스트라 사운드로 전투나 추격 장면에 어울리는 강렬한 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dd94f8153ab94cf8807de5327aa5c5f7) |
| ☐ | `e81c438b3fec4bf68a932323a4876975` | sound-649 | 95.1 | 0.852 | 웅장한 오케스트라 사운드와 긴박한 합창이 어우러진 드라마틱한 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e81c438b3fec4bf68a932323a4876975) |
| ☐ | `1d218b1555594e259e8dd37f205c9be0` | sound-62 | 98 | 0.851 | 강렬한 오케스트라 브라스와 일렉트릭 기타 사운드가 돋보이는 웅장하고 긴박한 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1d218b1555594e259e8dd37f205c9be0) |
| ☐ | `3b038b734432424ea4bea567997ea12d` | sound-132 | 32.5 | 0.841 | 웅장한 오케스트라 사운드와 합창이 어우러져 긴박함과 몰입감을 주는 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3b038b734432424ea4bea567997ea12d) |
| ☐ | `1ab072bf95e24ddba7d758f21af04ad1` | sound-54 | 36.9 | 0.825 | 웅장한 오케스트라 사운드와 긴박한 리듬이 돋보이는 모험과 전투 테마의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1ab072bf95e24ddba7d758f21af04ad1) |
| ☐ | `82a6606e1a074934be368b8e4a642b45` | sound-275 | 130.5 | 0.824 | 빠르고 강렬한 비트와 신시사이저 사운드가 어우러진 긴박감 넘치는 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=82a6606e1a074934be368b8e4a642b45) |
| ☐ | `97a774405ab14f8c961d967ac49964cf` | sound-337 | 169.8 | 0.821 | 강렬한 일렉 기타와 오케스트라 사운드가 어우러진 긴박하고 웅장한 보스 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=97a774405ab14f8c961d967ac49964cf) |
| ☐ | `7743f93c29674b7a96bd6b644f8ba7a0` | sound-249 | 131.3 | 0.818 | 웅장한 오케스트라 사운드와 강렬한 타악기가 어우러진 긴박하고 박진감 넘치는 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7743f93c29674b7a96bd6b644f8ba7a0) |
| ☐ | `996682d36bad47ebaf3c635a17bec91c` | sound-340 | 90.1 | 0.814 | 강렬한 일렉 기타와 드럼 사운드가 긴박감을 조성하는 웅장한 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=996682d36bad47ebaf3c635a17bec91c) |
| ☐ | `52d138d2e77842769121c27e678cc22d` | sound-166 | 89.3 | 0.813 | 긴박한 오케스트라 선율과 강렬한 타악기가 어우러진 전투 및 보스전 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=52d138d2e77842769121c27e678cc22d) |
| ☐ | `be6f04a1b255467f92c9b31caef58258` | sound-436 | 133.8 | 0.81 | 웅장한 오케스트라 사운드와 긴박한 리듬이 돋보이는 강렬한 보스 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=be6f04a1b255467f92c9b31caef58258) |
| ☐ | `2a0257f832ee4a7c84c0a8efc9aa5bba` | sound-87 | 125.3 | 0.809 | 긴박하고 웅장한 오케스트라 사운드로 긴장감 넘치는 보스 전투나 극적인 장면에 어울리는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a0257f832ee4a7c84c0a8efc9aa5bba) |
| ☐ | `949ee1aace064a74bb72069f6126bfbd` | sound-327 | 98.1 | 0.808 | 웅장하고 긴박한 분위기의 오케스트라 곡으로 강렬한 금관 악기와 타악기가 조화를 이루어 전투나 보스전에 어울리는 음악입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=949ee1aace064a74bb72069f6126bfbd) |
| ☐ | `7255a7d897524806ba957fed6da67e8e` | sound-233 | 88.9 | 0.807 | 강렬한 일렉 기타와 웅장한 오케스트라 사운드가 어우러진 긴박하고 에너제틱한 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7255a7d897524806ba957fed6da67e8e) |
| ☐ | `764aa2962eda4610ad5351a1fc2a3199` | sound-243 | 127.7 | 0.806 | 웅장한 오케스트라 사운드와 긴박한 리듬이 돋보이는 강렬한 보스 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=764aa2962eda4610ad5351a1fc2a3199) |
| ☐ | `1c8b1c570bbd4e72b40f4e9114e4c097` | sound-61 | 132.9 | 0.805 | 강렬한 타악기 리듬과 긴박한 오케스트라 사운드가 어우러진 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1c8b1c570bbd4e72b40f4e9114e4c097) |
| ☐ | `8a7aabed91c14684b0ff2214838762e1` | sound-295 | 127.1 | 0.805 | 강렬하고 긴박한 분위기의 오케스트라 전투 배경음악으로 빠른 현악기와 웅장한 금관악기가 돋보이는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8a7aabed91c14684b0ff2214838762e1) |

### BGM 승리  <sub>(bgm, 검색어: 승리 축하 팡파르 짧은 음악)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `704d139895f5452b8ae131ea5e989758` | sound-225 | 34.3 | 0.78 | 금관 악기와 일렉 기타가 어우러진 활기차고 축제 분위기의 경쾌한 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=704d139895f5452b8ae131ea5e989758) |
| ☐ | `0428442a33fd48a193a1a39c1602cf0c` | sound-10 | 72 | 0.731 | 경쾌하고 에너지가 넘치는 레트로 풍의 승리 및 결과 화면 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0428442a33fd48a193a1a39c1602cf0c) |
| ☐ | `cd16b2b8ed6643a68e8aed1c12a8bc87` | sound-477 | 125.6 | 0.721 | 웅장한 브라스와 경쾌한 현악기가 어우러진 승리와 축제 분위기의 활기찬 오케스트라 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cd16b2b8ed6643a68e8aed1c12a8bc87) |
| ☐ | `9e89dc9de09d429d895d318cd704f7d9` | sound-350 | 125.4 | 0.714 | 강렬한 일렉 기타와 화려한 브라스 연주가 돋보이는 승리의 기쁨을 표현한 빠른 템포의 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9e89dc9de09d429d895d318cd704f7d9) |
| ☐ | `19e031d785ac465d95bf65e6f0cd21c3` | sound-603 | 129.2 | 0.707 | 경쾌한 바이올린과 아코디언 선율이 돋보이는 활기찬 마을 축제 분위기의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=19e031d785ac465d95bf65e6f0cd21c3) |
| ☐ | `a65afaec5a4b4c19a1e1a366c710508e` | sound-369 | 33.6 | 0.696 | 피아노와 현악기, 목관악기가 어우러져 통통 튀는 느낌을 주는 빠르고 경쾌한 분위기의 곡입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a65afaec5a4b4c19a1e1a366c710508e) |
| ☐ | `115207ca190f4273a415beb8a1a6aeae` | sound-32 | 120.9 | 0.693 | 화려한 브라스와 경쾌한 리듬이 돋보이는 축제 분위기의 밝고 에너지 넘치는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=115207ca190f4273a415beb8a1a6aeae) |
| ☐ | `ff5c0a90d4c8455faee0f6507055a075` | sound-647 | 86.5 | 0.692 | 빠르고 경쾌한 비트의 레트로풍 칩튠 음악으로, 아케이드 게임이나 미니게임에 어울리는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ff5c0a90d4c8455faee0f6507055a075) |
| ☐ | `531f8778dfc847c982d0b78ce6671df6` | sound-168 | 142.1 | 0.691 | 경쾌하고 빠른 템포의 8비트 칩튠 음악으로, 미니게임이나 활기찬 레트로풍 맵에 어울리는 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=531f8778dfc847c982d0b78ce6671df6) |
| ☐ | `58473c62e628465199f958781ee280f9` | sound-181 | 90.7 | 0.691 | 활기차고 경쾌한 분위기의 오케스트라 곡으로, 현악기와 목관악기가 어우러져 마을이나 상점 등에 어울리는 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58473c62e628465199f958781ee280f9) |
| ☐ | `bfb906b5891345d59fcf013bfec2b507` | sound-441 | 81.7 | 0.689 | 피아노와 플루트, 현악기가 어우러진 밝고 경쾌한 분위기의 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bfb906b5891345d59fcf013bfec2b507) |
| ☐ | `eb1e0480fcb44d7f8ca56adc7bcf78be` | sound-558 | 106.6 | 0.685 | 축제 분위기의 밝고 활기찬 오케스트라 풍의 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=eb1e0480fcb44d7f8ca56adc7bcf78be) |
| ☐ | `c059b03d2f6e420687dacd6545450cc2` | sound-445 | 86.5 | 0.683 | 아코디언과 브라스가 어우러진 활기차고 축제 분위기가 물씬 풍기는 경쾌한 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c059b03d2f6e420687dacd6545450cc2) |
| ☐ | `a4b033c7fc8b48c99d398a912f837511` | sound-365 | 135.9 | 0.682 | 모험의 시작을 알리는 듯한 밝고 활기찬 오케스트라 풍의 게임 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a4b033c7fc8b48c99d398a912f837511) |
| ☐ | `5d29291eb5e84b1a8669395f5672b65f` | sound-191 | 142.1 | 0.68 | 레트로한 8비트 사운드와 경쾌한 오케스트라 요소가 어우러진 밝고 활기찬 분위기의 게임 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5d29291eb5e84b1a8669395f5672b65f) |
| ☐ | `fb2ae50a8aeb49c29c04bc3db91e7e6a` | sound-584 | 115.3 | 0.679 | 밝고 경쾌한 신시사이저 사운드가 특징인 활기찬 분위기의 게임 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fb2ae50a8aeb49c29c04bc3db91e7e6a) |
| ☐ | `3b038b734432424ea4bea567997ea12d` | sound-132 | 32.5 | 0.678 | 웅장한 오케스트라 사운드와 합창이 어우러져 긴박함과 몰입감을 주는 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3b038b734432424ea4bea567997ea12d) |
| ☐ | `5935885b480a4f84ba880f71c97accbe` | sound-184 | 121.4 | 0.678 | 금관악기와 현악기가 어우러진 밝고 활기찬 축제 분위기의 마을 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5935885b480a4f84ba880f71c97accbe) |
| ☐ | `ab3383f554f64622b56e2f6e41b5a917` | sound-382 | 122.3 | 0.676 | 축제 분위기의 밝고 활기찬 오케스트라 곡으로, 경쾌한 리듬과 화려한 금관악기가 돋보이는 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ab3383f554f64622b56e2f6e41b5a917) |
| ☐ | `9eda2cba0a0d4348b994ab35ed764b8a` | sound-352 | 183.1 | 0.675 | 피아노와 오케스트라 선율이 어우러진 밝고 경쾌한 분위기의 모험 테마 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9eda2cba0a0d4348b994ab35ed764b8a) |

### BGM 패배  <sub>(bgm, 검색어: 패배 슬프고 침울한 짧은 음악)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `063f1dddbf8b4a1bb9067b0c7a196922` | sound-14 | 189.6 | 0.663 | 신비롭고 서정적인 분위기의 오케스트라 곡으로 피아노와 현악기가 어우러져 평화로운 느낌을 줍니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=063f1dddbf8b4a1bb9067b0c7a196922) |
| ☐ | `732c8aeac0624d21bdcfc89bc6244105` | sound-237 | 144.1 | 0.658 | 어둡고 긴장감 넘치는 분위기의 곡으로 금속성 타격음과 낮은 신스음이 조화를 이루어 공포나 보스전 도입부에 어울리는 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=732c8aeac0624d21bdcfc89bc6244105) |
| ☐ | `fc18e326825e4eb6aed5ccd70928692a` | sound-589 | 94.4 | 0.655 | 피아노와 현악기가 어우러진 서정적이고 평화로운 분위기의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fc18e326825e4eb6aed5ccd70928692a) |
| ☐ | `fbc4290f54894595a3e507c2cdad4117` | sound-605 | 40.9 | 0.654 | 오르골 소리가 중심이 되는 차분하고 몽환적인 분위기의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fbc4290f54894595a3e507c2cdad4117) |
| ☐ | `a3b78cba21f94f79851e38d2cd720f1a` | sound-362 | 96.1 | 0.648 | 웅장하고 어두운 분위기의 오케스트라 곡으로, 남성 합창과 강렬한 금관악기가 긴장감 넘치는 전투 장면을 연상시킵니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a3b78cba21f94f79851e38d2cd720f1a) |
| ☐ | `a4139e0733154eb1a2f1d785caf78c1e` | sound-364 | 149.9 | 0.648 | 피아노 선율이 중심이 되는 차분하고 신비로운 분위기의 곡으로 서정적인 느낌을 줍니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a4139e0733154eb1a2f1d785caf78c1e) |
| ☐ | `e26ce82e1f9c404dbab50ec6683b4fac` | sound-541 | 90.6 | 0.645 | 긴장감 넘치는 리듬으로 시작하여 웅장한 오케스트라 사운드로 전개되는 극적인 분위기의 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e26ce82e1f9c404dbab50ec6683b4fac) |
| ☐ | `fec06ea8a4a943279acfdba9a1f3a1f8` | sound-594 | 95 | 0.645 | 신비롭고 긴장감 넘치는 분위기의 앰비언트 곡으로, 신시사이저와 현악기가 어우러져 미지의 공간을 탐험하는 느낌을 줍니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fec06ea8a4a943279acfdba9a1f3a1f8) |
| ☐ | `a19fe95385bf47279f25655fc1032c98` | sound-356 | 92.2 | 0.645 | 신비롭고 기괴한 분위기를 자아내는 곡으로, 벨 소리와 현악기가 긴장감을 더하는 배경음악입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a19fe95385bf47279f25655fc1032c98) |
| ☐ | `e277da825c0f4ce5805d04617cab5cd3` | sound-540 | 130.1 | 0.644 | 피아노와 현악기가 어우러져 서정적이고 감동적인 분위기를 자아내는 오케스트라 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e277da825c0f4ce5805d04617cab5cd3) |
| ☐ | `a937f55ab20548c9a3cb7f7a3d701240` | sound-377 | 122.9 | 0.641 | 강렬한 일렉 기타와 오케스트라 사운드가 긴박함을 더하는 웅장한 보스 전투 배경음악입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a937f55ab20548c9a3cb7f7a3d701240) |
| ☐ | `7f12be7facb84f47b5a4bdbd79858d4a` | sound-266 | 113.7 | 0.639 | 웅장하고 서사적인 오케스트라 곡으로 신비로운 분위기에서 시작해 비장하고 감동적인 선율로 이어지는 배경음악입니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7f12be7facb84f47b5a4bdbd79858d4a) |
| ☐ | `8f12929a1da847c79c204595b319c7a5` | sound-312 | 10.1 | 0.638 | 웅장하고 긴장감 넘치는 분위기의 시네마틱 배경음악으로 어둡고 신비로운 느낌을 줍니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8f12929a1da847c79c204595b319c7a5) |
| ☐ | `6d7bf7e04ea8436da98f0ec156052ed7` | sound-222 | 97.1 | 0.636 | 피아노와 현악기가 어우러진 평화롭고 감성적인 분위기의 오케스트라 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6d7bf7e04ea8436da98f0ec156052ed7) |
| ☐ | `640ca5c09595461695c3a566999b59b6` | sound-207 | 122.3 | 0.636 | 사막이나 이국적인 배경의 전투 장면이 떠오르는, 플루트 선율과 긴박한 퍼커션이 조화를 이룬 에너제틱한 곡 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=640ca5c09595461695c3a566999b59b6) |
| ☐ | `190ac389eaf547e1b817baaca733a5d0` | sound-50 | 166.6 | 0.636 | 잔잔한 피아노 선율과 현악기가 어우러져 신비롭고 몽환적인 분위기를 자아내는 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=190ac389eaf547e1b817baaca733a5d0) |
| ☐ | `0c319c21fac3449f972215750e3f5515` | sound-23 | 95.6 | 0.636 | 웅장하고 긴장감 넘치는 분위기의 곡으로 무거운 타악기와 오케스트라 선율이 어우러져 위기 상황이나 보스전을 연상시킵니다. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0c319c21fac3449f972215750e3f5515) |
| ☐ | `1c8b1c570bbd4e72b40f4e9114e4c097` | sound-61 | 132.9 | 0.634 | 강렬한 타악기 리듬과 긴박한 오케스트라 사운드가 어우러진 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1c8b1c570bbd4e72b40f4e9114e4c097) |
| ☐ | `a3e1d64b93824ddd809a9b81a2ded673` | sound-363 | 102.4 | 0.633 | 웅장한 오케스트라와 합창이 어우러진 긴박하고 강렬한 분위기의 보스 전투 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a3e1d64b93824ddd809a9b81a2ded673) |
| ☐ | `bcc73825742745089f771fbb23c881e9` | sound-432 | 129.1 | 0.633 | 피아노와 현악기가 어우러져 평화롭고 신비로운 분위기를 연출하는 서정적인 배경음악 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bcc73825742745089f771fbb23c881e9) |


## UI

### UI 버튼 클릭  <sub>(effect, 검색어: UI 버튼을 클릭할 때 짧고 깔끔한 클릭음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `10f217ca7a1740e68d906405832d0ef5` | audioclip-2783 | 0.8 | 0.95 | UI 버튼을 클릭할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=10f217ca7a1740e68d906405832d0ef5) |
| ☐ | `16021cbacf884ddf92c4fcf6d0122586` | audioclip-40268 | 4.1 | 0.949 | UI 버튼을 클릭할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=16021cbacf884ddf92c4fcf6d0122586) |
| ☐ | `223a4a355e68494d8438f29946027a18` | audioclip-5516 | 2.2 | 0.948 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=223a4a355e68494d8438f29946027a18) |
| ☐ | `315e91f433f740e69fa2b97ef110325b` | audioclip-7863 | 0.7 | 0.948 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=315e91f433f740e69fa2b97ef110325b) |
| ☐ | `11abaa10cd9246e1af867b5ea0493fc4` | audioclip-2891 | 0.8 | 0.947 | UI 버튼을 클릭할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=11abaa10cd9246e1af867b5ea0493fc4) |
| ☐ | `0cb8e717c8724b9ca0e06d8ca90f239e` | audioclip-2074 | 0.3 | 0.946 | UI 버튼을 클릭하거나 메뉴를 선택할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0cb8e717c8724b9ca0e06d8ca90f239e) |
| ☐ | `50f3a8227bbc491894589f060b25ba68` | audioclip-41600 | 1 | 0.946 | UI 버튼을 클릭할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=50f3a8227bbc491894589f060b25ba68) |
| ☐ | `c4da48a2cdbf4320804a1b13a57bfb0e` | audioclip-30852 | 0.9 | 0.946 | UI 버튼을 클릭할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c4da48a2cdbf4320804a1b13a57bfb0e) |
| ☐ | `589c24bd648f4311a3550ded0f7c06d7` | audioclip-13993 | 1.7 | 0.946 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=589c24bd648f4311a3550ded0f7c06d7) |
| ☐ | `8890ad81f93240079816560cac360711` | audioclip-21418 | 0.7 | 0.946 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8890ad81f93240079816560cac360711) |
| ☐ | `7206adf461714e189bef46bf6c1e3732` | audioclip-61481 | 0.4 | 0.946 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7206adf461714e189bef46bf6c1e3732) |
| ☐ | `24bc2b02e819461f9335241f154311dd` | audioclip-5925 | 0.3 | 0.946 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=24bc2b02e819461f9335241f154311dd) |
| ☐ | `24c14eef01124c0c88440d230be1b2f9` | audioclip-5928 | 0.7 | 0.945 | UI 버튼을 클릭할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=24c14eef01124c0c88440d230be1b2f9) |
| ☐ | `2603c19462f14f38b98d94cc530da851` | audioclip-6127 | 0.5 | 0.945 | UI 버튼을 클릭할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2603c19462f14f38b98d94cc530da851) |
| ☐ | `02548ec668604954aa661d8383df901c` | audioclip-497 | 3.7 | 0.945 | UI 버튼을 클릭할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=02548ec668604954aa661d8383df901c) |
| ☐ | `e33cd20a69c94eec88a81c0488a64d40` | audioclip-43115 | 0.5 | 0.943 | 버튼을 누르거나 메뉴를 선택할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e33cd20a69c94eec88a81c0488a64d40) |
| ☐ | `7b2f8b990d9a436caedcdbb70a097fbd` | audioclip-19315 | 0.5 | 0.943 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7b2f8b990d9a436caedcdbb70a097fbd) |
| ☐ | `ac6de4a9949942a9bd02a56509788579` | audioclip-27030 | 0.4 | 0.943 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ac6de4a9949942a9bd02a56509788579) |
| ☐ | `3a265a8591f44f878ddd94d96e1d358f` | audioclip-9243 | 0.4 | 0.943 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3a265a8591f44f878ddd94d96e1d358f) |
| ☐ | `173a0a7f06474b628575a9c73345f0b1` | audioclip-3790 | 0.3 | 0.943 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=173a0a7f06474b628575a9c73345f0b1) |

### UI 버튼 호버  <sub>(effect, 검색어: UI 버튼 위에 마우스를 올릴 때 아주 짧고 가벼운 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `9653b09facc3434ca15566e0b55fbd3c` | audioclip-62077 | 0.4 | 0.938 | UI 버튼 위에 마우스를 올렸을 때 발생하는 짧고 부드러운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9653b09facc3434ca15566e0b55fbd3c) |
| ☐ | `5f9b242e69a246a59d35c256cd45c598` | audioclip-15070 | 0.6 | 0.93 | 마우스 커서를 버튼이나 아이콘 위에 올렸을 때 발생하는 짧은 인터페이스 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5f9b242e69a246a59d35c256cd45c598) |
| ☐ | `8ba4b8ed32704ee6bd9f5248541b6521` | audioclip-21886 | 0.4 | 0.904 | UI 버튼을 클릭할 때 발생하는 짧고 가벼운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8ba4b8ed32704ee6bd9f5248541b6521) |
| ☐ | `3f72854c673d45e9a2f9ce231a32693e` | audioclip-10039 | 0.6 | 0.892 | 인터페이스에서 버튼을 클릭할 때 발생하는 짧은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3f72854c673d45e9a2f9ce231a32693e) |
| ☐ | `0ba7a68d0d5f44c8a6f15e54a14ebb71` | audioclip-1922 | 0.6 | 0.89 | UI 버튼을 클릭할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0ba7a68d0d5f44c8a6f15e54a14ebb71) |
| ☐ | `09cd4fdb8b224b12bd7ece970ed12285` | audioclip-1631 | 0.7 | 0.888 | UI 버튼을 클릭할 때 발생하는 짧고 간결한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=09cd4fdb8b224b12bd7ece970ed12285) |
| ☐ | `b9b1a7a5287e4527a8e6695f9203679d` | audioclip-29109 | 0.3 | 0.884 | UI 인터페이스에서 버튼을 클릭하거나 항목을 선택할 때 발생하는 짧은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b9b1a7a5287e4527a8e6695f9203679d) |
| ☐ | `9702a571cd944e7292513d7dbbe48770` | audioclip-23597 | 1.1 | 0.882 | UI 요소를 클릭하거나 선택할 때 발생하는 짧은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9702a571cd944e7292513d7dbbe48770) |
| ☐ | `a21885d506484dc2b2b7b5d8fc84f705` | audioclip-25406 | 0.6 | 0.881 | UI 버튼을 클릭하거나 메뉴를 선택할 때 발생하는 짧고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a21885d506484dc2b2b7b5d8fc84f705) |
| ☐ | `3d629f714fdb43c2af11dfcc266ab777` | audioclip-62738 | 0.7 | 0.881 | UI 메뉴를 조작하거나 버튼을 누를 때 발생하는 짧은 클릭 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3d629f714fdb43c2af11dfcc266ab777) |
| ☐ | `c1cbcd9c442d42dea53e21ddfece4f68` | audioclip-30377 | 1 | 0.88 | UI 버튼을 클릭하거나 선택할 때 발생하는 짧고 간결한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c1cbcd9c442d42dea53e21ddfece4f68) |
| ☐ | `ef24c2d6376d446ca4a680abc6d970b0` | audioclip-37551 | 0.3 | 0.88 | UI 버튼을 클릭하거나 선택할 때 발생하는 짧고 깔끔한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ef24c2d6376d446ca4a680abc6d970b0) |
| ☐ | `06ae2eb272f54ad2a93540c0c388bf7a` | audioclip-1136 | 0.3 | 0.88 | UI 버튼을 클릭하거나 메뉴를 선택할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=06ae2eb272f54ad2a93540c0c388bf7a) |
| ☐ | `dc2d12280a0b4d67adf113fcd26db49c` | audioclip-34615 | 1.4 | 0.88 | UI 버튼을 클릭할 때 발생하는 짧고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dc2d12280a0b4d67adf113fcd26db49c) |
| ☐ | `4d5374482ee34e78a4fb3ccc1a376a74` | audioclip-12227 | 0.4 | 0.88 | UI 버튼을 클릭하거나 메뉴를 선택할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4d5374482ee34e78a4fb3ccc1a376a74) |
| ☐ | `0ebc2587223549b39f4b10b0f32985ca` | audioclip-2420 | 0.8 | 0.879 | UI 버튼을 클릭하거나 선택할 때 발생하는 짧고 깔끔한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0ebc2587223549b39f4b10b0f32985ca) |
| ☐ | `e006e78fffac4ba98c81f636a052b364` | audioclip-35193 | 1 | 0.879 | UI 인터페이스에서 버튼을 클릭하거나 항목을 선택할 때 들리는 짧은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e006e78fffac4ba98c81f636a052b364) |
| ☐ | `eb395fad0e874008a1b5c4e96211bb21` | audioclip-36942 | 1.3 | 0.879 | UI 버튼을 클릭하거나 메뉴를 선택할 때 발생하는 짧고 간결한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=eb395fad0e874008a1b5c4e96211bb21) |
| ☐ | `aa9c4ee77fc64ed8bdd5b58d67fae495` | audioclip-42522 | 0.7 | 0.879 | UI 버튼을 클릭할 때 발생하는 가볍고 짧은 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=aa9c4ee77fc64ed8bdd5b58d67fae495) |
| ☐ | `a3c33a84fed84d6b86776b07c193e5a5` | audioclip-61950 | 1.1 | 0.878 | 메뉴 선택이나 버튼 클릭 시 발생하는 짧고 깔끔한 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a3c33a84fed84d6b86776b07c193e5a5) |

### UI 불가/잠김  <sub>(effect, 검색어: 할 수 없음 오류 거부 버저 효과음 UI)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `174d501eccd04eadbd6c6411d4ade7e7` | audioclip-3801 | 0.9 | 0.787 | 짧고 날카로운 전자음으로, UI 오류나 경고 상황에 적합한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=174d501eccd04eadbd6c6411d4ade7e7) |
| ☐ | `e5389ea837dc46f49a97a69d21abbb79` | audioclip-36023 | 2.6 | 0.776 | 전기 기타의 왜곡된 소리를 이용한 실패 또는 오류 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e5389ea837dc46f49a97a69d21abbb79) |
| ☐ | `1bee698506af44c4a1f84b01be7373a2` | audioclip-41034 | 1 | 0.768 | 경고나 알림을 나타내는 날카롭고 반복적인 전자 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1bee698506af44c4a1f84b01be7373a2) |
| ☐ | `762421119c1148f18d592554cfde4d9c` | audioclip-18502 | 3.1 | 0.765 | 높은 톤으로 반복해서 울리는 전자식 경고음 또는 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=762421119c1148f18d592554cfde4d9c) |
| ☐ | `40fb4b84ca7b4df399b36fd7d0475d24` | audioclip-10277 | 1.2 | 0.765 | UI 알림이나 버튼 클릭 시 발생하는 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=40fb4b84ca7b4df399b36fd7d0475d24) |
| ☐ | `540ef7865b7943128cbca004ec5c10ae` | audioclip-13281 | 3.1 | 0.765 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=540ef7865b7943128cbca004ec5c10ae) |
| ☐ | `7adc4731e2d04522a411012f77351d6a` | audioclip-60047 | 12.1 | 0.765 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 알람 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7adc4731e2d04522a411012f77351d6a) |
| ☐ | `c7956414a0054d2fb44a8b653429a7da` | audioclip-31314 | 0.6 | 0.763 | 창을 닫거나 동작을 취소할 때 들리는 시스템 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c7956414a0054d2fb44a8b653429a7da) |
| ☐ | `e5397d34e85e4a3caf593748afbf030f` | audioclip-36024 | 4.8 | 0.757 | 비상 상황이나 시스템 경고를 알리는 날카로운 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e5397d34e85e4a3caf593748afbf030f) |
| ☐ | `9325d50a0b2d434f94edc6dbdfc1da17` | audioclip-23010 | 0.7 | 0.757 | UI에서 알림이나 버튼 클릭 시 발생하는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9325d50a0b2d434f94edc6dbdfc1da17) |
| ☐ | `652025e1107345aaa52a2e06681f284c` | audioclip-15911 | 4.1 | 0.756 | 전자적인 알람이나 경고를 나타내는 반복적인 고음의 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=652025e1107345aaa52a2e06681f284c) |
| ☐ | `15064f1b31974a629387d617746b0140` | audioclip-3452 | 0.8 | 0.755 | 메뉴 취소 또는 뒤로 가기 시 발생하는 시스템 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=15064f1b31974a629387d617746b0140) |
| ☐ | `81122a7025f84ffbb31b3989476ba080` | audioclip-20301 | 0.7 | 0.753 | 짧고 반복적인 전자음 형태의 UI 알림 또는 경고음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=81122a7025f84ffbb31b3989476ba080) |
| ☐ | `d54077cf43a144c2aa6ad0a17a2789a0` | audioclip-33491 | 10.7 | 0.752 | 긴박한 상황이나 경고를 알리는 반복적인 고음의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d54077cf43a144c2aa6ad0a17a2789a0) |
| ☐ | `a74d1652120942c9a5ca3afcdaedf33e` | audioclip-26214 | 1.9 | 0.751 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a74d1652120942c9a5ca3afcdaedf33e) |
| ☐ | `c15e945508d44dee8e805737d606e85e` | audioclip-30307 | 0.6 | 0.751 | UI에서 발생하는 짧고 높은 톤의 디지털 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c15e945508d44dee8e805737d606e85e) |
| ☐ | `98e9c05088db4dbc853dfb4e56734220` | audioclip-23888 | 1.9 | 0.751 | 경고나 비상 상황을 알리는 날카롭고 반복적인 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=98e9c05088db4dbc853dfb4e56734220) |
| ☐ | `29dd05164963439cbba85f26a4f3d5e6` | audioclip-6729 | 0.7 | 0.75 | UI 알림이나 시스템 메시지 출력 시 사용되는 짧고 명확한 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=29dd05164963439cbba85f26a4f3d5e6) |
| ☐ | `5d704b3c83504094b96febc1c936239f` | audioclip-14711 | 1.9 | 0.749 | 비상 상황이나 경고를 알리는 날카로운 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5d704b3c83504094b96febc1c936239f) |
| ☐ | `99cd886831b14d5e940d4e1bc21c295c` | audioclip-24036 | 1.1 | 0.749 | UI 메뉴를 조작하거나 알림이 발생할 때 들리는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=99cd886831b14d5e940d4e1bc21c295c) |

### UI 토스트 알림  <sub>(effect, 검색어: 알림 띵 짧은 벨 소리 UI 메시지)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `4836083d9d3643d0be18992420c9c7bf` | audioclip-11423 | 0.6 | 0.895 | UI 알림이나 시스템 메시지 등에 사용되는 짧고 맑은 금속성 벨 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4836083d9d3643d0be18992420c9c7bf) |
| ☐ | `165389842ce3415c90753bf79c0722a2` | audioclip-40967 | 0.7 | 0.889 | 메뉴 선택이나 알림 시 발생하는 짧고 맑은 금속성 벨 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=165389842ce3415c90753bf79c0722a2) |
| ☐ | `5a05741788d64295841c7e9bf4ec064c` | audioclip-14200 | 3.2 | 0.885 | UI 알림이나 특정 상호작용 시 발생하는 짧고 높은 톤의 금속성 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5a05741788d64295841c7e9bf4ec064c) |
| ☐ | `1a4105f0518740f6bf3fa13283f88995` | audioclip-4272 | 0.7 | 0.885 | UI 알림이나 아이템 획득 시 발생하는 짧고 맑은 금속성 벨 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1a4105f0518740f6bf3fa13283f88995) |
| ☐ | `9e7f2227b45445eab802e275fbdd7025` | audioclip-24795 | 1.4 | 0.883 | UI 메뉴 선택이나 알림 시 발생하는 짧고 경쾌한 전자음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9e7f2227b45445eab802e275fbdd7025) |
| ☐ | `c9ac15f88dd941e29c60c8bd7a612a70` | audioclip-31643 | 0.8 | 0.882 | UI 메뉴 선택이나 알림 시 발생하는 짧고 높은 톤의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c9ac15f88dd941e29c60c8bd7a612a70) |
| ☐ | `3ee9b64e6f0c4553acf863a0392993ee` | audioclip-41406 | 0.9 | 0.881 | UI 알림이나 아이템 획득 시 발생하는 짧고 높은 톤의 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3ee9b64e6f0c4553acf863a0392993ee) |
| ☐ | `917903a1b0da41c7a3a4018d5cd4ec35` | audioclip-22765 | 1.5 | 0.881 | UI 메뉴 선택이나 알림 시 발생하는 짧고 명쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=917903a1b0da41c7a3a4018d5cd4ec35) |
| ☐ | `896386ef8af14817bb898cfc1bca2db9` | audioclip-62637 | 0.6 | 0.881 | UI 알림이나 아이템 획득 시 발생하는 짧고 맑은 금속성 벨 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=896386ef8af14817bb898cfc1bca2db9) |
| ☐ | `7cb6cb8e83174d71afcb7a39c1a19b86` | audioclip-19590 | 1.1 | 0.88 | UI 알림이나 아이템 획득 시 발생하는 짧고 맑은 금속성 벨 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7cb6cb8e83174d71afcb7a39c1a19b86) |
| ☐ | `f939d19915ac419a97e283709e419553` | audioclip-39147 | 2.9 | 0.88 | UI 메뉴 선택이나 알림 시 발생하는 밝고 짧은 딩 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f939d19915ac419a97e283709e419553) |
| ☐ | `1f8b9a439dc54691b0ccf11114fdc6c4` | audioclip-61259 | 0.6 | 0.879 | UI에서 알림이나 확인을 나타내는 짧고 밝은 금속성 딩 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1f8b9a439dc54691b0ccf11114fdc6c4) |
| ☐ | `1f7f9d1e81fd44f284f045e8f38817f7` | audioclip-5062 | 1 | 0.879 | 짧고 높은 톤의 UI 알림 또는 선택 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1f7f9d1e81fd44f284f045e8f38817f7) |
| ☐ | `c38e29df47e44d4781b19449fed35eb3` | audioclip-62406 | 3 | 0.879 | UI 알림이나 버튼 클릭 시 발생하는 짧고 날카로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c38e29df47e44d4781b19449fed35eb3) |
| ☐ | `b106ff0151bb408ea23839b0fbb15af0` | audioclip-27770 | 0.6 | 0.878 | 높은 톤의 맑고 짧은 UI 알림음 또는 아이템 획득음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b106ff0151bb408ea23839b0fbb15af0) |
| ☐ | `74e82828f10441a3a185061333694521` | audioclip-18318 | 0.7 | 0.878 | UI에서 선택이나 알림 시 발생하는 높고 맑은 금속성 벨 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=74e82828f10441a3a185061333694521) |
| ☐ | `750075f4f0684f9ca3f6b7ecb1386c82` | audioclip-18329 | 0.9 | 0.878 | UI 메뉴 선택이나 알림 시 발생하는 짧고 높은 톤의 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=750075f4f0684f9ca3f6b7ecb1386c82) |
| ☐ | `438914e9386447208a6faf75c988a619` | audioclip-10697 | 0.2 | 0.878 | UI 메뉴 선택이나 알림 시 발생하는 짧고 높은 톤의 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=438914e9386447208a6faf75c988a619) |
| ☐ | `fa39a393bf5c4bc9b48768204e8f1fc1` | audioclip-39299 | 1.9 | 0.876 | UI에서 알림이나 선택 시 발생하는 짧고 높은 톤의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fa39a393bf5c4bc9b48768204e8f1fc1) |
| ☐ | `3e1802b362004017ba388b3d34071ca8` | audioclip-9835 | 1 | 0.876 | UI 알림이나 성공을 나타내는 짧고 높은 톤의 금속성 벨소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e1802b362004017ba388b3d34071ca8) |

### UI 팝업 열기  <sub>(effect, 검색어: 창이 열리는 UI 효과음 팝업 등장)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `3cabe0ad239047f2baf9599e97f47eff` | audioclip-9619 | 3.4 | 0.898 | 메뉴 창이 열리거나 UI 요소가 나타날 때 발생하는 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3cabe0ad239047f2baf9599e97f47eff) |
| ☐ | `3d1374f1ed0540c4a030d07b0d727c33` | audioclip-9679 | 1 | 0.873 | 짧고 깔끔한 UI 버튼 클릭 또는 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3d1374f1ed0540c4a030d07b0d727c33) |
| ☐ | `649dffcd1484432c9d45d7c6971cfa53` | audioclip-15818 | 0.8 | 0.86 | UI 버튼을 클릭하거나 팝업이 뜰 때 발생하는 짧고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=649dffcd1484432c9d45d7c6971cfa53) |
| ☐ | `cacde52756e94b18b3c3a0351cc37e76` | audioclip-31828 | 2.7 | 0.86 | UI 창이 열리거나 메뉴를 선택할 때 발생하는 짧고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cacde52756e94b18b3c3a0351cc37e76) |
| ☐ | `78eda980db9a4abdb191911ace283f35` | audioclip-18938 | 1.1 | 0.857 | 짧고 경쾌하게 클릭하거나 팝업이 뜨는 듯한 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=78eda980db9a4abdb191911ace283f35) |
| ☐ | `cb9ff9735c834a558cab88b31aa6500b` | audioclip-31948 | 0.3 | 0.855 | 깔끔하고 짧은 UI 버튼 클릭 또는 팝업 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cb9ff9735c834a558cab88b31aa6500b) |
| ☐ | `1d9714b6ce3547ee9f84b890a05df3e6` | audioclip-4801 | 2.2 | 0.854 | UI 버튼을 클릭할 때 발생하는 짧고 경쾌한 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1d9714b6ce3547ee9f84b890a05df3e6) |
| ☐ | `127364dd6b674c1fa948cc3747d135aa` | audioclip-62593 | 1.7 | 0.852 | UI 선택 시 발생하는 짧고 경쾌한 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=127364dd6b674c1fa948cc3747d135aa) |
| ☐ | `79c981558002470f8d97301e16bcce52` | audioclip-41991 | 0.4 | 0.851 | UI 창을 닫거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=79c981558002470f8d97301e16bcce52) |
| ☐ | `81f9aeb07f824b4cad56a7e83c827f02` | audioclip-42082 | 2.5 | 0.85 | UI 메뉴를 선택하거나 팝업이 뜰 때 발생하는 짧고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=81f9aeb07f824b4cad56a7e83c827f02) |
| ☐ | `d945b6f0bd384200b5fb687e25dfa2cd` | audioclip-34187 | 4.8 | 0.849 | UI 메뉴를 선택하거나 팝업이 뜰 때 발생하는 짧고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d945b6f0bd384200b5fb687e25dfa2cd) |
| ☐ | `7654f7cafe1d44b19b4f9fed64befda8` | audioclip-18533 | 1 | 0.848 | UI 선택 시 발생하는 짧고 가벼운 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7654f7cafe1d44b19b4f9fed64befda8) |
| ☐ | `6c92637cc45d41a08af3dc394832874b` | audioclip-17040 | 2.3 | 0.848 | UI 버튼을 누르거나 알림이 뜰 때 발생하는 짧고 가벼운 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6c92637cc45d41a08af3dc394832874b) |
| ☐ | `5099cf9ad7914c01948f47b333fa0fdd` | audioclip-12758 | 0.8 | 0.847 | UI 메뉴 선택이나 버튼 클릭 시 발생하는 짧고 깔끔한 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5099cf9ad7914c01948f47b333fa0fdd) |
| ☐ | `06e985dbc42c4511a38f8b8862623439` | audioclip-1173 | 0.6 | 0.846 | UI 버튼 클릭이나 알림 시 발생하는 짧고 경쾌한 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=06e985dbc42c4511a38f8b8862623439) |
| ☐ | `55c167f415cc492a83070c2a9030846b` | audioclip-13558 | 3 | 0.846 | UI 메뉴를 열거나 닫을 때 발생하는 짧고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=55c167f415cc492a83070c2a9030846b) |
| ☐ | `b90b0ba2e8fd4fdfa2df60387650826b` | audioclip-29015 | 2.8 | 0.846 | UI 메뉴 선택 시 발생하는 짧고 경쾌한 팝업 효과음. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b90b0ba2e8fd4fdfa2df60387650826b) |
| ☐ | `3e15605df17b43949d1453eeae8dbe0e` | audioclip-9832 | 0.3 | 0.846 | UI 메뉴를 조작하거나 버튼을 클릭할 때 발생하는 짧고 경쾌한 팝업 사운드 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e15605df17b43949d1453eeae8dbe0e) |
| ☐ | `bac254e0981b4bbaba9813498401a7e3` | audioclip-62698 | 0.3 | 0.843 | UI 메뉴 조작 시 발생하는 짧고 경쾌한 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bac254e0981b4bbaba9813498401a7e3) |
| ☐ | `9b32a7aa5f4d468bbfc7786945e7bda1` | audioclip-24279 | 1.3 | 0.843 | UI 메뉴를 클릭하거나 아이템을 획득할 때 발생하는 짧고 가벼운 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9b32a7aa5f4d468bbfc7786945e7bda1) |

### UI 팝업 닫기  <sub>(effect, 검색어: 창이 닫히는 UI 효과음 팝업 사라짐)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `c7956414a0054d2fb44a8b653429a7da` | audioclip-31314 | 0.6 | 0.829 | 창을 닫거나 동작을 취소할 때 들리는 시스템 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c7956414a0054d2fb44a8b653429a7da) |
| ☐ | `79c981558002470f8d97301e16bcce52` | audioclip-41991 | 0.4 | 0.822 | UI 창을 닫거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=79c981558002470f8d97301e16bcce52) |
| ☐ | `3d1374f1ed0540c4a030d07b0d727c33` | audioclip-9679 | 1 | 0.807 | 짧고 깔끔한 UI 버튼 클릭 또는 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3d1374f1ed0540c4a030d07b0d727c33) |
| ☐ | `cb9ff9735c834a558cab88b31aa6500b` | audioclip-31948 | 0.3 | 0.806 | 깔끔하고 짧은 UI 버튼 클릭 또는 팝업 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cb9ff9735c834a558cab88b31aa6500b) |
| ☐ | `5482fcdae53944f5a0600c0799f28b97` | audioclip-13360 | 1.3 | 0.797 | UI 메뉴를 선택하거나 아이템이 나타날 때 발생하는 짧고 높은 톤의 팝 사운드 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5482fcdae53944f5a0600c0799f28b97) |
| ☐ | `e5ec13307b074bf9ba49b10c60f3fb53` | audioclip-43147 | 0.2 | 0.795 | UI 요소를 선택하거나 클릭할 때 발생하는 짧고 높은 톤의 팝 사운드 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e5ec13307b074bf9ba49b10c60f3fb53) |
| ☐ | `1d9714b6ce3547ee9f84b890a05df3e6` | audioclip-4801 | 2.2 | 0.794 | UI 버튼을 클릭할 때 발생하는 짧고 경쾌한 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1d9714b6ce3547ee9f84b890a05df3e6) |
| ☐ | `7f4aa28bcd9148d5b022b6f9a86c848a` | audioclip-19996 | 0.8 | 0.793 | UI 버튼을 클릭할 때 발생하는 짧고 경쾌한 팝 사운드 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7f4aa28bcd9148d5b022b6f9a86c848a) |
| ☐ | `649dffcd1484432c9d45d7c6971cfa53` | audioclip-15818 | 0.8 | 0.789 | UI 버튼을 클릭하거나 팝업이 뜰 때 발생하는 짧고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=649dffcd1484432c9d45d7c6971cfa53) |
| ☐ | `b69f4eaeb3d34ce993b46e16abe216db` | audioclip-28658 | 1 | 0.789 | UI 버튼을 클릭하거나 알림이 뜰 때 발생하는 짧고 경쾌한 팝 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b69f4eaeb3d34ce993b46e16abe216db) |
| ☐ | `16021cbacf884ddf92c4fcf6d0122586` | audioclip-40268 | 4.1 | 0.787 | UI 버튼을 클릭할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=16021cbacf884ddf92c4fcf6d0122586) |
| ☐ | `6c92637cc45d41a08af3dc394832874b` | audioclip-17040 | 2.3 | 0.787 | UI 버튼을 누르거나 알림이 뜰 때 발생하는 짧고 가벼운 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6c92637cc45d41a08af3dc394832874b) |
| ☐ | `127364dd6b674c1fa948cc3747d135aa` | audioclip-62593 | 1.7 | 0.786 | UI 선택 시 발생하는 짧고 경쾌한 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=127364dd6b674c1fa948cc3747d135aa) |
| ☐ | `ba87de24dd2549128f6b95b3656f79c0` | audioclip-29236 | 0.8 | 0.786 | UI 버튼을 클릭할 때 발생하는 짧고 경쾌한 팝 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ba87de24dd2549128f6b95b3656f79c0) |
| ☐ | `5099cf9ad7914c01948f47b333fa0fdd` | audioclip-12758 | 0.8 | 0.785 | UI 메뉴 선택이나 버튼 클릭 시 발생하는 짧고 깔끔한 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5099cf9ad7914c01948f47b333fa0fdd) |
| ☐ | `f04cd4d673244a12b5c0df17be3e3c3d` | audioclip-37745 | 0.3 | 0.784 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧은 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f04cd4d673244a12b5c0df17be3e3c3d) |
| ☐ | `15064f1b31974a629387d617746b0140` | audioclip-3452 | 0.8 | 0.784 | 메뉴 취소 또는 뒤로 가기 시 발생하는 시스템 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=15064f1b31974a629387d617746b0140) |
| ☐ | `7654f7cafe1d44b19b4f9fed64befda8` | audioclip-18533 | 1 | 0.784 | UI 선택 시 발생하는 짧고 가벼운 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7654f7cafe1d44b19b4f9fed64befda8) |
| ☐ | `9b32a7aa5f4d468bbfc7786945e7bda1` | audioclip-24279 | 1.3 | 0.783 | UI 메뉴를 클릭하거나 아이템을 획득할 때 발생하는 짧고 가벼운 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9b32a7aa5f4d468bbfc7786945e7bda1) |
| ☐ | `b3b7e6eafae6454d8179f0ca38e4510a` | audioclip-28206 | 0.5 | 0.783 | UI 버튼을 클릭하거나 메뉴를 선택할 때 발생하는 짧고 깔끔한 팝업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b3b7e6eafae6454d8179f0ca38e4510a) |

### UI 부대 지정 확인  <sub>(effect, 검색어: 짧은 확인 삐 전자음 설정 완료)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `4db2253d10424e87a3b09478a2f65e6b` | audioclip-12294 | 7.1 | 0.796 | UI 알림이나 성공을 나타내는 고음의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4db2253d10424e87a3b09478a2f65e6b) |
| ☐ | `e66430c822664c1187dca889e1ebca27` | audioclip-36211 | 1.9 | 0.788 | 짧고 높은 톤의 전자식 UI 알림음 또는 선택음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e66430c822664c1187dca889e1ebca27) |
| ☐ | `eda3d33e84074f5f9f2096932fc2538e` | audioclip-37305 | 0.6 | 0.787 | 밝고 짧은 톤의 UI 알림 또는 확인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=eda3d33e84074f5f9f2096932fc2538e) |
| ☐ | `35875303bee44d50a535c9d3f3d6e62b` | audioclip-8509 | 1.1 | 0.786 | UI 알림이나 성공 시 발생하는 짧고 멜로디컬한 전자음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=35875303bee44d50a535c9d3f3d6e62b) |
| ☐ | `cfb824c8bc33486786d3d324c0a67792` | audioclip-32612 | 1.7 | 0.786 | 짧고 높은 톤의 디지털 알림음 또는 UI 선택음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cfb824c8bc33486786d3d324c0a67792) |
| ☐ | `88462bb46e034ecd95ebb5f5020f303e` | audioclip-21368 | 0.6 | 0.786 | 짧고 높은 톤의 디지털 알림음 또는 UI 선택음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=88462bb46e034ecd95ebb5f5020f303e) |
| ☐ | `be6978ecc0f54501934f986beb6e28a3` | audioclip-29844 | 0.8 | 0.786 | 짧고 높은 톤의 디지털 UI 알림음 또는 선택음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=be6978ecc0f54501934f986beb6e28a3) |
| ☐ | `805deb8f76034300917c44526a5a7500` | audioclip-42058 | 1.7 | 0.786 | 짧고 높은 톤의 디지털 알림음 또는 시스템 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=805deb8f76034300917c44526a5a7500) |
| ☐ | `44ddd2b6e81e4c0ea51cd3367333bf83` | audioclip-10920 | 1 | 0.785 | UI 알림이나 전자 기기 조작 시 발생하는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=44ddd2b6e81e4c0ea51cd3367333bf83) |
| ☐ | `e35d980959fe4cd3b8302331cfa742c3` | audioclip-35734 | 4.5 | 0.784 | 짧고 명료한 전자음 형태의 UI 알림 또는 선택 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e35d980959fe4cd3b8302331cfa742c3) |
| ☐ | `258bad569a8f4a748bfbba7dea9dc426` | audioclip-6048 | 4.5 | 0.784 | UI에서 알림이나 선택 시 발생하는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=258bad569a8f4a748bfbba7dea9dc426) |
| ☐ | `966c1ce9101f4e1ca943de28c89e1a37` | audioclip-23495 | 0.7 | 0.784 | UI 상호작용이나 알림 시 발생하는 높고 경쾌한 전자음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=966c1ce9101f4e1ca943de28c89e1a37) |
| ☐ | `2a6e08ec10bd4ea0be6f967e592e04c1` | audioclip-6809 | 0.7 | 0.783 | 짧고 높은 톤의 디지털 비프음으로, UI 알림이나 선택 시 발생하는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a6e08ec10bd4ea0be6f967e592e04c1) |
| ☐ | `90dbb64402f04f40982ff665c254126e` | audioclip-22666 | 3.2 | 0.783 | 짧고 높은 톤의 디지털 알림음 또는 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=90dbb64402f04f40982ff665c254126e) |
| ☐ | `15bfa9917087411d9cde87092e4eb7f0` | audioclip-3570 | 1.6 | 0.783 | UI 메뉴 선택이나 알림에 사용되는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=15bfa9917087411d9cde87092e4eb7f0) |
| ☐ | `7cefc4d240454f129fa2d144dd684a41` | audioclip-19628 | 0.6 | 0.783 | UI에서 성공이나 확인을 나타내는 밝고 짧은 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7cefc4d240454f129fa2d144dd684a41) |
| ☐ | `85bbbdf1e5974a13a9e3eb1af17abf58` | audioclip-20997 | 1.1 | 0.782 | UI에서 무언가를 선택하거나 성공했을 때 들리는 짧고 경쾌한 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=85bbbdf1e5974a13a9e3eb1af17abf58) |
| ☐ | `e2ff9fc16355406c801dd053a4aee4ec` | audioclip-35676 | 2.1 | 0.782 | 짧고 높은 톤의 전자식 알림음 또는 UI 선택음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e2ff9fc16355406c801dd053a4aee4ec) |
| ☐ | `a1ee58d11da14d74a18b63e31e1cfd25` | audioclip-25397 | 0.7 | 0.782 | UI에서 발생하는 짧고 경쾌한 디지털 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a1ee58d11da14d74a18b63e31e1cfd25) |
| ☐ | `769bb45980804bcfaf5d5d0657ea3aa7` | audioclip-18574 | 1.5 | 0.782 | 짧고 높은 톤의 디지털 비프음으로, UI 알림이나 전자 기기 상호작용에 적합한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=769bb45980804bcfaf5d5d0657ea3aa7) |

### UI 진영 선택 확정  <sub>(effect, 검색어: 선택 확정 결정 효과음 UI 묵직한 확인)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `699dce87c0f844ea98f8be13282d8af5` | audioclip-16587 | 1.1 | 0.904 | 무겁고 임팩트 있는 UI 선택 또는 확인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=699dce87c0f844ea98f8be13282d8af5) |
| ☐ | `8ccdd81a9b844227ada9e13d517f8593` | audioclip-22057 | 1.8 | 0.901 | 무겁고 단호한 느낌의 UI 선택 또는 확인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8ccdd81a9b844227ada9e13d517f8593) |
| ☐ | `814ad61de0f54c198816f9b75ed8529f` | audioclip-20332 | 2 | 0.882 | UI 메뉴 선택이나 확인 시 발생하는 임팩트 있는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=814ad61de0f54c198816f9b75ed8529f) |
| ☐ | `10ef000382cf4424839b2949c73482a6` | audioclip-2781 | 3.4 | 0.878 | 기계적인 조작감이 느껴지는 묵직한 UI 선택 또는 확인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=10ef000382cf4424839b2949c73482a6) |
| ☐ | `bb48cf1eb1ab483999b0076a46b0a6ff` | audioclip-29369 | 4.9 | 0.878 | 무게감이 느껴지는 짧고 묵직한 UI 선택 또는 확인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bb48cf1eb1ab483999b0076a46b0a6ff) |
| ☐ | `110e8a69eb8a49e8b2dc35655c3641ad` | audioclip-2804 | 3.1 | 0.873 | 메뉴 선택이나 확인 시 발생하는 짧고 명확한 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=110e8a69eb8a49e8b2dc35655c3641ad) |
| ☐ | `66c16eb0fa77469bbf29af1bd02c02c9` | audioclip-16151 | 3.4 | 0.871 | 묵직하고 기계적인 느낌의 UI 버튼 클릭 또는 선택 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=66c16eb0fa77469bbf29af1bd02c02c9) |
| ☐ | `5b3bbae65de34506baa100aa15ae950f` | audioclip-14375 | 3.8 | 0.868 | UI 메뉴를 선택하거나 확인을 누를 때 발생하는 날카롭고 짧은 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5b3bbae65de34506baa100aa15ae950f) |
| ☐ | `2fb28fc36ac44c20a737f92c9c7678e7` | audioclip-7601 | 2.5 | 0.868 | 짧고 명확한 타격감이 느껴지는 UI 선택 또는 확인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2fb28fc36ac44c20a737f92c9c7678e7) |
| ☐ | `45f0467eef6b4b37ac0e52afebe9acf0` | audioclip-11077 | 1.4 | 0.868 | 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 묵직한 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=45f0467eef6b4b37ac0e52afebe9acf0) |
| ☐ | `1272203ca66545ffb0a86ab056f0ae36` | audioclip-3024 | 6.1 | 0.868 | UI 메뉴에서 선택이나 확인을 할 때 발생하는 디지털 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1272203ca66545ffb0a86ab056f0ae36) |
| ☐ | `1099c6c300f44cc38e1a9e52da666d1a` | audioclip-2712 | 3 | 0.867 | UI 메뉴를 선택하거나 확인 버튼을 누를 때 발생하는 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1099c6c300f44cc38e1a9e52da666d1a) |
| ☐ | `3e6ed01151294003a9178d1a137df3eb` | audioclip-60883 | 3.3 | 0.866 | UI 메뉴 선택이나 버튼 클릭 시 발생하는 묵직한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e6ed01151294003a9178d1a137df3eb) |
| ☐ | `f500360465754c0c9b1447c4a4ae7eb1` | audioclip-38540 | 2.2 | 0.865 | 짧고 강한 타격감이 느껴지는 UI 선택 또는 확인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f500360465754c0c9b1447c4a4ae7eb1) |
| ☐ | `2a34c2e95dce418d9c29f40dc3c0061a` | audioclip-6766 | 1.7 | 0.865 | UI 메뉴에서 선택하거나 확인 버튼을 누를 때 발생하는 짧고 깔끔한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a34c2e95dce418d9c29f40dc3c0061a) |
| ☐ | `0c71e606fe784d6cae444b35a059e8cf` | audioclip-2025 | 2.6 | 0.864 | 메뉴를 선택하거나 버튼을 누를 때 발생하는 깔끔한 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0c71e606fe784d6cae444b35a059e8cf) |
| ☐ | `167a06b0822547f7a845f0f6102b29cf` | audioclip-3676 | 0.7 | 0.864 | UI 메뉴를 선택하거나 확인 버튼을 누를 때 발생하는 짧고 깔끔한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=167a06b0822547f7a845f0f6102b29cf) |
| ☐ | `c9834919318544aa9db9a56ceb016d1d` | audioclip-31607 | 2 | 0.863 | 웅장하고 임팩트 있는 UI 확인 또는 시작 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c9834919318544aa9db9a56ceb016d1d) |
| ☐ | `4f82afe26e844a30aeff37a2c616e133` | audioclip-12574 | 1 | 0.862 | 짧고 날카로운 느낌의 UI 선택 또는 확인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4f82afe26e844a30aeff37a2c616e133) |
| ☐ | `40f0b77905404e41887d9a0c5d45848e` | audioclip-10275 | 3.1 | 0.862 | UI 메뉴를 선택하거나 확인 버튼을 누를 때 발생하는 묵직하고 짧은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=40f0b77905404e41887d9a0c5d45848e) |

### UI 카운트다운 틱  <sub>(effect, 검색어: 카운트다운 시계 틱 초읽기 비프)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `671fbecafebd44e2918fb6881afdeddf` | audioclip-16215 | 4.9 | 0.821 | 카운트다운이나 타이머의 종료를 알리는 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=671fbecafebd44e2918fb6881afdeddf) |
| ☐ | `839d3d38f22e4e87bf0a87076761a6a8` | audioclip-20685 | 10.7 | 0.812 | 일정한 간격으로 반복되는 디지털 타이머 또는 경고 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=839d3d38f22e4e87bf0a87076761a6a8) |
| ☐ | `778160a185c4464ea829b609d7afeea1` | audioclip-18706 | 2.1 | 0.803 | 카운트다운이나 알림에 사용되는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=778160a185c4464ea829b609d7afeea1) |
| ☐ | `0501b711b2a2460d9032149ada6b3e22` | audioclip-870 | 6.1 | 0.789 | 시스템 알림이나 카운트다운에 사용되는 규칙적인 전자 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0501b711b2a2460d9032149ada6b3e22) |
| ☐ | `1551cd3bb726497a8daf6b189e908fbd` | audioclip-3494 | 0.8 | 0.772 | 시계가 빠르게 째깍거리는 소리 또는 기계적인 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1551cd3bb726497a8daf6b189e908fbd) |
| ☐ | `98c91ad88cf046d0a1a54d415a6bf25b` | audioclip-23869 | 1.8 | 0.764 | 빠르게 반복되는 기계적인 클릭음 또는 타이머 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=98c91ad88cf046d0a1a54d415a6bf25b) |
| ☐ | `ef338f6a831c4dd4ab55ec5142e6d567` | audioclip-37564 | 0.4 | 0.754 | 시계 바늘이 움직이는 듯한 짧고 명확한 기계적 째깍 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ef338f6a831c4dd4ab55ec5142e6d567) |
| ☐ | `171d678023fa4abf87289e83d5e9de88` | audioclip-3777 | 0.9 | 0.739 | 시계 바늘이 일정하게 움직이며 내는 기계적인 째깍거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=171d678023fa4abf87289e83d5e9de88) |
| ☐ | `4296a09811cb465db196450fd8eb73ad` | audioclip-10556 | 1.2 | 0.733 | 짧고 리듬감 있는 디지털 비프음으로 UI 알림이나 카운트다운에 적합한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4296a09811cb465db196450fd8eb73ad) |
| ☐ | `e6d0f68f49e346c49be5869550d9137f` | audioclip-36293 | 12.7 | 0.732 | 타이머가 작동하며 일정 간격으로 클릭 소리가 나다가 종료되는 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e6d0f68f49e346c49be5869550d9137f) |
| ☐ | `028d6e56690a4e188ea749423e807b8e` | audioclip-500 | 2.6 | 0.727 | 빠르게 똑딱거리는 기계적인 타이머 또는 카운트다운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=028d6e56690a4e188ea749423e807b8e) |
| ☐ | `d54077cf43a144c2aa6ad0a17a2789a0` | audioclip-33491 | 10.7 | 0.721 | 긴박한 상황이나 경고를 알리는 반복적인 고음의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d54077cf43a144c2aa6ad0a17a2789a0) |
| ☐ | `29dd05164963439cbba85f26a4f3d5e6` | audioclip-6729 | 0.7 | 0.721 | UI 알림이나 시스템 메시지 출력 시 사용되는 짧고 명확한 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=29dd05164963439cbba85f26a4f3d5e6) |
| ☐ | `652025e1107345aaa52a2e06681f284c` | audioclip-15911 | 4.1 | 0.719 | 전자적인 알람이나 경고를 나타내는 반복적인 고음의 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=652025e1107345aaa52a2e06681f284c) |
| ☐ | `54482ea3aed549cebf93c27e8e1aef22` | audioclip-13329 | 1.1 | 0.714 | UI 메뉴를 조작하거나 버튼을 클릭할 때 발생하는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=54482ea3aed549cebf93c27e8e1aef22) |
| ☐ | `c0d7360d9e0c4a4aa06555b51975a8ab` | audioclip-30223 | 1.1 | 0.714 | UI 알림이나 버튼 클릭 시 발생하는 짧고 명확한 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c0d7360d9e0c4a4aa06555b51975a8ab) |
| ☐ | `64d64691dd264453824c42cbbb96ccaf` | audioclip-15858 | 2 | 0.714 | 반복되는 고음의 디지털 알림음 또는 기계적인 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=64d64691dd264453824c42cbbb96ccaf) |
| ☐ | `81122a7025f84ffbb31b3989476ba080` | audioclip-20301 | 0.7 | 0.711 | 짧고 반복적인 전자음 형태의 UI 알림 또는 경고음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=81122a7025f84ffbb31b3989476ba080) |
| ☐ | `87ea23cc09774fd3b0d42ef7c7e074f5` | audioclip-21313 | 1 | 0.71 | UI 메뉴를 클릭하거나 알림이 발생할 때 들리는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=87ea23cc09774fd3b0d42ef7c7e074f5) |
| ☐ | `15bfa9917087411d9cde87092e4eb7f0` | audioclip-3570 | 1.6 | 0.71 | UI 메뉴 선택이나 알림에 사용되는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=15bfa9917087411d9cde87092e4eb7f0) |


## 선택

### 선택 유닛-모험가(버섯)  <sub>(effect, 검색어: 버섯 몬스터가 귀엽게 우는 소리)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `de530e2743cc45ada65f06ede376fa7a` | audioclip-34918 | 1.3 | 0.828 | 작은 몬스터나 생명체가 서럽게 우는 귀여운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=de530e2743cc45ada65f06ede376fa7a) |
| ☐ | `401aa2c1c3c54ee3a22339a99c4fa013` | audioclip-10157 | 1.4 | 0.822 | 작은 몬스터가 내는 높은 톤의 귀여운 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=401aa2c1c3c54ee3a22339a99c4fa013) |
| ☐ | `39ec7b2700bf41d898d75e56db451d66` | audioclip-9199 | 1.2 | 0.819 | 작고 귀여운 몬스터가 내는 짧고 부드러운 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=39ec7b2700bf41d898d75e56db451d66) |
| ☐ | `dac38d12552044f499969a226914b92a` | audioclip-34399 | 2.6 | 0.812 | 귀여운 몬스터가 짧게 내뱉는 높은 톤의 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dac38d12552044f499969a226914b92a) |
| ☐ | `05497607145a47cba22c7f8e4c4318d6` | audioclip-908 | 1.2 | 0.811 | 작은 몬스터가 끼기기 소리를 내며 우는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=05497607145a47cba22c7f8e4c4318d6) |
| ☐ | `646f385ac9a849ebbaef096e925dff8f` | audioclip-15788 | 0.7 | 0.811 | 작고 귀여운 몬스터가 내는 짧고 높은 톤의 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=646f385ac9a849ebbaef096e925dff8f) |
| ☐ | `e2b0ebd3f3ce4265a5c016a3760f0df3` | audioclip-35623 | 0.8 | 0.809 | 작고 귀여운 몬스터가 짧고 날카롭게 내뱉는 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e2b0ebd3f3ce4265a5c016a3760f0df3) |
| ☐ | `9e0057aa063e46d19efe94eac5151687` | audioclip-24702 | 2.4 | 0.808 | 작고 귀여운 몬스터가 내는 높은 톤의 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9e0057aa063e46d19efe94eac5151687) |
| ☐ | `00f8efdea1fe47748fd218c61c7e08c0` | audioclip-246 | 2.2 | 0.808 | 작고 귀여운 몬스터가 내는 짧고 높은 톤의 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=00f8efdea1fe47748fd218c61c7e08c0) |
| ☐ | `8b0c68b650aa41e98d4013a7d2062e82` | audioclip-21795 | 2.2 | 0.807 | 작고 귀여운 몬스터가 내는 짧고 높은 톤의 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8b0c68b650aa41e98d4013a7d2062e82) |
| ☐ | `55a8af0df722458cbe3af47e519a0d11` | audioclip-13546 | 1.3 | 0.807 | 작고 귀여운 몬스터가 내는 짧고 높은 톤의 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=55a8af0df722458cbe3af47e519a0d11) |
| ☐ | `7dfabece349c4f7482bea41ab7af7acb` | audioclip-19817 | 0.3 | 0.807 | 작고 귀여운 몬스터가 내는 짧고 높은 톤의 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7dfabece349c4f7482bea41ab7af7acb) |
| ☐ | `0f9d7515b9084f57ba51d91c0f984ed6` | audioclip-2562 | 0.7 | 0.807 | 작고 귀여운 몬스터가 내는 높은 톤의 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0f9d7515b9084f57ba51d91c0f984ed6) |
| ☐ | `cfcaa8fc8b514fa2a863f2f93650531b` | audioclip-32628 | 1.3 | 0.806 | 작은 몬스터가 내는 고음의 끽끽거리는 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cfcaa8fc8b514fa2a863f2f93650531b) |
| ☐ | `7e580a7a1a354fe0b0964cd602316210` | audioclip-19876 | 1.1 | 0.806 | 작은 몬스터가 내는 높은 톤의 짧은 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7e580a7a1a354fe0b0964cd602316210) |
| ☐ | `663a88f7e35141f6ac4f7fbb65925183` | audioclip-16082 | 0.6 | 0.806 | 작고 귀여운 몬스터가 내는 짧고 높은 톤의 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=663a88f7e35141f6ac4f7fbb65925183) |
| ☐ | `3c99aa99e2ff4e8b8e29382062028e1b` | audioclip-41362 | 0.9 | 0.805 | 작고 귀여운 몬스터가 내는 고음의 끽끽거리는 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3c99aa99e2ff4e8b8e29382062028e1b) |
| ☐ | `6c4ba6501b384a44b5fc2c61addb4905` | audioclip-16995 | 0.9 | 0.805 | 작은 몬스터가 짧게 내는 비명 또는 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6c4ba6501b384a44b5fc2c61addb4905) |
| ☐ | `53f6c66425ec4cd887f52651106deff2` | audioclip-13266 | 2.3 | 0.805 | 작고 귀여운 몬스터가 내는 짧고 높은 톤의 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=53f6c66425ec4cd887f52651106deff2) |
| ☐ | `9e15e71a127c4958baa6d46aff26655e` | audioclip-24709 | 0.7 | 0.803 | 작고 귀여운 몬스터가 내는 짧은 울음소리 또는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9e15e71a127c4958baa6d46aff26655e) |

### 선택 유닛-시그너스(기사)  <sub>(effect, 검색어: 기사가 칼을 뽑는 금속 소리 검집)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `fcbda4f33f0c40e196d89f2116edfade` | audioclip-39706 | 1.4 | 0.851 | 검을 뽑거나 휘두를 때 발생하는 날카로운 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fcbda4f33f0c40e196d89f2116edfade) |
| ☐ | `66a5b9ff00154ca39833ba69d7d3f310` | audioclip-16138 | 1 | 0.843 | 검을 뽑거나 휘두를 때 발생하는 날카로운 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=66a5b9ff00154ca39833ba69d7d3f310) |
| ☐ | `5cf128c409a540e7a3fc17d286cdced4` | audioclip-14630 | 3.6 | 0.843 | 검을 뽑거나 휘두를 때 발생하는 날카로운 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5cf128c409a540e7a3fc17d286cdced4) |
| ☐ | `d4becf80c2f44549b1a96583fc9503e3` | audioclip-33404 | 0.9 | 0.841 | 검을 뽑거나 금속 재질의 무기가 부딪히는 날카로운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d4becf80c2f44549b1a96583fc9503e3) |
| ☐ | `4971306a274541c2bb105ce746ecaddb` | audioclip-41530 | 0.6 | 0.84 | 검을 뽑거나 금속이 부딪히는 날카로운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4971306a274541c2bb105ce746ecaddb) |
| ☐ | `9c4c5b5b7206419fa1518b4e4c87aad2` | audioclip-42391 | 0.3 | 0.84 | 검을 뽑거나 휘두를 때 발생하는 날카로운 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9c4c5b5b7206419fa1518b4e4c87aad2) |
| ☐ | `aaed7f30ab9040409b9b380afbbe91df` | audioclip-26786 | 0.5 | 0.839 | 검을 뽑거나 휘두를 때 발생하는 날카로운 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=aaed7f30ab9040409b9b380afbbe91df) |
| ☐ | `2229497718cf42f4a1ae0426f0c05767` | audioclip-5511 | 1.6 | 0.836 | 검을 뽑거나 금속 무기가 부딪힐 때 발생하는 날카로운 금속음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2229497718cf42f4a1ae0426f0c05767) |
| ☐ | `567f3b55937f40cea6bc62b9c5c64105` | audioclip-41657 | 0.2 | 0.832 | 검을 휘두르거나 뽑을 때 발생하는 날카로운 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=567f3b55937f40cea6bc62b9c5c64105) |
| ☐ | `f2248307523540f5863c74601d9e8bee` | audioclip-38044 | 1.3 | 0.832 | 검을 뽑거나 휘두를 때 발생하는 날카로운 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f2248307523540f5863c74601d9e8bee) |
| ☐ | `cf81ba33557d48089baae540394c69e8` | audioclip-32586 | 1.3 | 0.831 | 검을 뽑거나 금속 재질의 무기가 부딪힐 때 발생하는 날카로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cf81ba33557d48089baae540394c69e8) |
| ☐ | `fdb4717a2f34419e8fdb8ca6c2c0da54` | audioclip-43390 | 2.1 | 0.831 | 검을 휘두르거나 뽑을 때 발생하는 날카로운 금속성 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fdb4717a2f34419e8fdb8ca6c2c0da54) |
| ☐ | `36f5cd9e6c19469788dba5d00b817512` | audioclip-8737 | 0.4 | 0.829 | 검을 뽑거나 금속이 부딪히는 날카롭고 짧은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=36f5cd9e6c19469788dba5d00b817512) |
| ☐ | `998406a344a1403daf2bacf3c44b1d80` | audioclip-42359 | 0.9 | 0.828 | 검을 휘두르거나 뽑을 때 발생하는 날카롭고 빠른 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=998406a344a1403daf2bacf3c44b1d80) |
| ☐ | `01c71ca2b8b44f08ad63a0d3a50bcbbb` | audioclip-382 | 1.8 | 0.828 | 검을 휘두르거나 뽑을 때 발생하는 날카롭고 빠른 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=01c71ca2b8b44f08ad63a0d3a50bcbbb) |
| ☐ | `572ff078721c474685e85a8829545cf1` | audioclip-13767 | 0.9 | 0.828 | 검을 휘두르거나 뽑을 때 발생하는 날카롭고 빠른 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=572ff078721c474685e85a8829545cf1) |
| ☐ | `db00aab689fb4b4f8e428ede40b007e6` | audioclip-34443 | 1.3 | 0.827 | 검을 뽑거나 휘두를 때 발생하는 날카로운 금속성 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=db00aab689fb4b4f8e428ede40b007e6) |
| ☐ | `0584e7c4f94d4737bbe6f487bc4904d5` | audioclip-61094 | 1.1 | 0.826 | 검을 휘두르거나 뽑을 때 발생하는 날카롭고 빠른 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0584e7c4f94d4737bbe6f487bc4904d5) |
| ☐ | `192ac417da3c4879ae4c63b37cc732d2` | audioclip-4102 | 1.8 | 0.825 | 검을 뽑거나 금속이 부딪힐 때 발생하는 날카로운 금속음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=192ac417da3c4879ae4c63b37cc732d2) |
| ☐ | `3a6b7b3c8e3140d29a2c70f52db7c410` | audioclip-9285 | 1.3 | 0.824 | 검을 뽑거나 휘두를 때 발생하는 날카롭고 매끄러운 금속 마찰음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3a6b7b3c8e3140d29a2c70f52db7c410) |

### 선택 유닛-에델슈타인(로봇)  <sub>(effect, 검색어: 로봇 기계 작동 비프 전자음 안드로이드)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `630ffcd759624653a0213b41d77439cd` | audioclip-15568 | 0.3 | 0.802 | 짧고 기계적인 느낌의 UI 알림 또는 디지털 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=630ffcd759624653a0213b41d77439cd) |
| ☐ | `fd6da1c5984244328ce30e08037d5ac9` | audioclip-39825 | 5.6 | 0.799 | 기계 생명체가 내는 듯한 빠르고 날카로운 디지털 전자음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fd6da1c5984244328ce30e08037d5ac9) |
| ☐ | `29dd05164963439cbba85f26a4f3d5e6` | audioclip-6729 | 0.7 | 0.798 | UI 알림이나 시스템 메시지 출력 시 사용되는 짧고 명확한 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=29dd05164963439cbba85f26a4f3d5e6) |
| ☐ | `5ada95fab40e4d7d96f2a7c0acb938fb` | audioclip-14318 | 1.5 | 0.795 | 높은 피치의 디지털 비프음 또는 기계적인 알림 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5ada95fab40e4d7d96f2a7c0acb938fb) |
| ☐ | `174bd555e24849728de5448fb3beed2f` | audioclip-3802 | 6.9 | 0.793 | 메뉴를 열거나 알림이 울릴 때 발생하는 디지털 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=174bd555e24849728de5448fb3beed2f) |
| ☐ | `0dc99e83905746639700b7b3df6b7374` | audioclip-2254 | 5.8 | 0.791 | 기계가 스캔하거나 작동하는 듯한 미래지향적인 디지털 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0dc99e83905746639700b7b3df6b7374) |
| ☐ | `44ddd2b6e81e4c0ea51cd3367333bf83` | audioclip-10920 | 1 | 0.791 | UI 알림이나 전자 기기 조작 시 발생하는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=44ddd2b6e81e4c0ea51cd3367333bf83) |
| ☐ | `470358406e9540629a7a42d5a9c511f5` | audioclip-11256 | 6.2 | 0.791 | 로봇이나 기계 장치가 움직이며 내는 금속성 기계음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=470358406e9540629a7a42d5a9c511f5) |
| ☐ | `baf72e3dc03c49278fb95548e2efc94a` | audioclip-29307 | 4.3 | 0.79 | 컴퓨터 인터페이스나 디지털 기기가 작동하는 듯한 전자음. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=baf72e3dc03c49278fb95548e2efc94a) |
| ☐ | `87ea23cc09774fd3b0d42ef7c7e074f5` | audioclip-21313 | 1 | 0.789 | UI 메뉴를 클릭하거나 알림이 발생할 때 들리는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=87ea23cc09774fd3b0d42ef7c7e074f5) |
| ☐ | `156c596a34bf4fa48c58e76a58bd79f8` | audioclip-40960 | 1.9 | 0.789 | 밝고 경쾌한 고음의 디지털 알림음 또는 기계적인 생명체의 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=156c596a34bf4fa48c58e76a58bd79f8) |
| ☐ | `971111baddd84de3b697603846c1825d` | audioclip-23604 | 0.7 | 0.787 | UI 알림이나 시스템 메시지 등에 사용될 법한 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=971111baddd84de3b697603846c1825d) |
| ☐ | `8ddb96db520d432bbbbdf6780a9f1e2f` | audioclip-22228 | 2.1 | 0.786 | 데이터를 스캔하거나 기계가 작동하는 듯한 전자적인 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8ddb96db520d432bbbbdf6780a9f1e2f) |
| ☐ | `e1b6e6ec22364a288947b51f98aa81e0` | audioclip-35475 | 1 | 0.785 | 컴퓨터가 데이터를 처리하거나 스캔하는 듯한 전자 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e1b6e6ec22364a288947b51f98aa81e0) |
| ☐ | `fe18f922026943a3b08b7678c8ef9312` | audioclip-60421 | 3.5 | 0.783 | 미래지향적인 느낌의 SF 스타일 UI 알림음 또는 시스템 활성화 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fe18f922026943a3b08b7678c8ef9312) |
| ☐ | `99cd886831b14d5e940d4e1bc21c295c` | audioclip-24036 | 1.1 | 0.782 | UI 메뉴를 조작하거나 알림이 발생할 때 들리는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=99cd886831b14d5e940d4e1bc21c295c) |
| ☐ | `769bb45980804bcfaf5d5d0657ea3aa7` | audioclip-18574 | 1.5 | 0.782 | 짧고 높은 톤의 디지털 비프음으로, UI 알림이나 전자 기기 상호작용에 적합한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=769bb45980804bcfaf5d5d0657ea3aa7) |
| ☐ | `652025e1107345aaa52a2e06681f284c` | audioclip-15911 | 4.1 | 0.782 | 전자적인 알람이나 경고를 나타내는 반복적인 고음의 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=652025e1107345aaa52a2e06681f284c) |
| ☐ | `6c67a9b025ae4be98648e5d43956cb1d` | audioclip-60815 | 3.8 | 0.782 | 로봇 몬스터가 내는 기계적인 울음소리와 디지털 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6c67a9b025ae4be98648e5d43956cb1d) |
| ☐ | `15bfa9917087411d9cde87092e4eb7f0` | audioclip-3570 | 1.6 | 0.781 | UI 메뉴 선택이나 알림에 사용되는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=15bfa9917087411d9cde87092e4eb7f0) |


## 명령

### 명령 수락-이동  <sub>(effect, 검색어: 짧은 확인 응답 효과음 명령 수락)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `110e8a69eb8a49e8b2dc35655c3641ad` | audioclip-2804 | 3.1 | 0.815 | 메뉴 선택이나 확인 시 발생하는 짧고 명확한 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=110e8a69eb8a49e8b2dc35655c3641ad) |
| ☐ | `6366a5f880ba4b29939146e67ff64e71` | audioclip-15620 | 6 | 0.815 | UI 메뉴에서 항목을 선택하거나 버튼을 누를 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6366a5f880ba4b29939146e67ff64e71) |
| ☐ | `814ad61de0f54c198816f9b75ed8529f` | audioclip-20332 | 2 | 0.813 | UI 메뉴 선택이나 확인 시 발생하는 임팩트 있는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=814ad61de0f54c198816f9b75ed8529f) |
| ☐ | `a52e4d298cb74672b48c181984b82389` | audioclip-25881 | 3.9 | 0.808 | UI 메뉴 선택이나 확인 시 발생하는 짧고 경쾌한 디지털 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a52e4d298cb74672b48c181984b82389) |
| ☐ | `73ff7d03761a4a61afb84454a3f817a8` | audioclip-18164 | 1.5 | 0.807 | 인터페이스에서 버튼을 클릭하거나 항목을 선택할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=73ff7d03761a4a61afb84454a3f817a8) |
| ☐ | `1099c6c300f44cc38e1a9e52da666d1a` | audioclip-2712 | 3 | 0.806 | UI 메뉴를 선택하거나 확인 버튼을 누를 때 발생하는 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1099c6c300f44cc38e1a9e52da666d1a) |
| ☐ | `34e810dafd40497f914fdcd9f32ff55f` | audioclip-8414 | 0.5 | 0.805 | UI 버튼을 클릭하거나 메뉴를 선택할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=34e810dafd40497f914fdcd9f32ff55f) |
| ☐ | `de3a02f48c054f7db5a9ded7d3667a80` | audioclip-62423 | 3 | 0.803 | UI 버튼을 클릭하거나 확인을 누를 때 발생하는 밝고 짧은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=de3a02f48c054f7db5a9ded7d3667a80) |
| ☐ | `2a34c2e95dce418d9c29f40dc3c0061a` | audioclip-6766 | 1.7 | 0.803 | UI 메뉴에서 선택하거나 확인 버튼을 누를 때 발생하는 짧고 깔끔한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a34c2e95dce418d9c29f40dc3c0061a) |
| ☐ | `06ae2eb272f54ad2a93540c0c388bf7a` | audioclip-1136 | 0.3 | 0.803 | UI 버튼을 클릭하거나 메뉴를 선택할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=06ae2eb272f54ad2a93540c0c388bf7a) |
| ☐ | `1658585b6d274007a3e1a3f12f7ba388` | audioclip-3656 | 0.7 | 0.803 | UI 요소를 클릭하거나 선택할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1658585b6d274007a3e1a3f12f7ba388) |
| ☐ | `4d5374482ee34e78a4fb3ccc1a376a74` | audioclip-12227 | 0.4 | 0.802 | UI 버튼을 클릭하거나 메뉴를 선택할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4d5374482ee34e78a4fb3ccc1a376a74) |
| ☐ | `a2ecead8d03d4a61b6de52b233a5c2bb` | audioclip-62671 | 0.3 | 0.802 | UI 버튼을 클릭하거나 메뉴를 선택할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a2ecead8d03d4a61b6de52b233a5c2bb) |
| ☐ | `0ba7a68d0d5f44c8a6f15e54a14ebb71` | audioclip-1922 | 0.6 | 0.802 | UI 버튼을 클릭할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0ba7a68d0d5f44c8a6f15e54a14ebb71) |
| ☐ | `45d59649c7d147cb88a30ba4698f82bb` | audioclip-11058 | 0.4 | 0.802 | UI 인터페이스에서 버튼을 클릭하거나 항목을 선택할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=45d59649c7d147cb88a30ba4698f82bb) |
| ☐ | `3f72854c673d45e9a2f9ce231a32693e` | audioclip-10039 | 0.6 | 0.802 | 인터페이스에서 버튼을 클릭할 때 발생하는 짧은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3f72854c673d45e9a2f9ce231a32693e) |
| ☐ | `961c331b75d2451ba7d868434c80a955` | audioclip-42312 | 2.7 | 0.801 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=961c331b75d2451ba7d868434c80a955) |
| ☐ | `eda3d33e84074f5f9f2096932fc2538e` | audioclip-37305 | 0.6 | 0.801 | 밝고 짧은 톤의 UI 알림 또는 확인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=eda3d33e84074f5f9f2096932fc2538e) |
| ☐ | `167a06b0822547f7a845f0f6102b29cf` | audioclip-3676 | 0.7 | 0.8 | UI 메뉴를 선택하거나 확인 버튼을 누를 때 발생하는 짧고 깔끔한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=167a06b0822547f7a845f0f6102b29cf) |
| ☐ | `c1cbcd9c442d42dea53e21ddfece4f68` | audioclip-30377 | 1 | 0.799 | UI 버튼을 클릭하거나 선택할 때 발생하는 짧고 간결한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c1cbcd9c442d42dea53e21ddfece4f68) |

### 명령 수락-공격  <sub>(effect, 검색어: 전투 함성 짧은 기합 공격 시작)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `655c74418f4c4d65932641a375e7a4f5` | audioclip-62477 | 1.3 | 0.833 | 몬스터가 짧고 힘차게 내뱉는 기합 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=655c74418f4c4d65932641a375e7a4f5) |
| ☐ | `b161460c116b40e49740719b38e059aa` | audioclip-27818 | 1.9 | 0.832 | 몬스터나 캐릭터가 짧고 강하게 내뱉는 기합 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b161460c116b40e49740719b38e059aa) |
| ☐ | `1417b3bf96d24ab28395dd8fca214581` | audioclip-3305 | 2 | 0.83 | 몬스터가 짧고 힘차게 기합을 내지르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1417b3bf96d24ab28395dd8fca214581) |
| ☐ | `3854def18b46424cae3f12c7ec2b9a60` | audioclip-8967 | 2.4 | 0.827 | 몬스터가 기합을 내지르며 공격하는 짧고 날카로운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3854def18b46424cae3f12c7ec2b9a60) |
| ☐ | `26434de954e94b28b7dc90cdbd3e26bd` | audioclip-6160 | 2.9 | 0.82 | 몬스터가 공격할 때 내는 짧고 날카로운 기합 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=26434de954e94b28b7dc90cdbd3e26bd) |
| ☐ | `135af0eef1ab4467ac4836d6b2b56c6f` | audioclip-3190 | 2.2 | 0.818 | 몬스터가 기합을 내지르며 공격하는 짧고 활기찬 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=135af0eef1ab4467ac4836d6b2b56c6f) |
| ☐ | `916531afac6f436fb323197fc92a9c51` | audioclip-22747 | 1.3 | 0.817 | 작은 몬스터가 기합을 넣으며 공격할 때 내는 짧고 활기찬 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=916531afac6f436fb323197fc92a9c51) |
| ☐ | `87c92c799ed34e7eab69a5b1aadfef9a` | audioclip-21293 | 2.1 | 0.817 | 몬스터가 짧고 날카롭게 내뱉는 공격적인 기합 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=87c92c799ed34e7eab69a5b1aadfef9a) |
| ☐ | `dbe481dae68a4592af2c14970b32bd98` | audioclip-34575 | 3 | 0.816 | 몬스터가 짧고 강하게 내뱉는 공격적인 기합 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dbe481dae68a4592af2c14970b32bd98) |
| ☐ | `142cb10b60614c8a9345d699a13e1139` | audioclip-3314 | 0.7 | 0.814 | 몬스터가 내는 짧고 날카로운 기합 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=142cb10b60614c8a9345d699a13e1139) |
| ☐ | `2e5c08335e0140459b0e196ce95343d1` | audioclip-7398 | 1.6 | 0.809 | 몬스터가 공격할 때 내는 짧고 강한 기합 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2e5c08335e0140459b0e196ce95343d1) |
| ☐ | `28a618eb7bae43d09f878b2f194299b4` | audioclip-6528 | 2.4 | 0.803 | 몬스터가 공격하거나 기합을 넣는 듯한 짧고 높은 톤의 괴성 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=28a618eb7bae43d09f878b2f194299b4) |
| ☐ | `4a2079328fb84281a9fa0225d7effc76` | audioclip-11739 | 1.1 | 0.801 | 몬스터가 공격하거나 기합을 넣는 듯한 짧은 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4a2079328fb84281a9fa0225d7effc76) |
| ☐ | `641ceadc30404bb39b34e2f5d9232fe1` | audioclip-15736 | 1.5 | 0.799 | 몬스터가 공격하거나 위협할 때 내는 짧고 거친 기합 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=641ceadc30404bb39b34e2f5d9232fe1) |
| ☐ | `d3af3e8226c54091a69091ae99ebfe97` | audioclip-33230 | 1.3 | 0.797 | 작고 활기찬 몬스터가 내는 짧은 기합 소리 또는 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d3af3e8226c54091a69091ae99ebfe97) |
| ☐ | `4727baae31b34b07bc9f40479fe8b7e1` | audioclip-11276 | 0.8 | 0.795 | 작은 몬스터가 내는 짧고 날카로운 기합 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4727baae31b34b07bc9f40479fe8b7e1) |
| ☐ | `cca356b247b3424d97408800fecdaa26` | audioclip-32120 | 2.8 | 0.792 | 작은 몬스터가 기합을 내지르며 공격하는 듯한 짧고 높은 톤의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cca356b247b3424d97408800fecdaa26) |
| ☐ | `1b6ba880fed1438ba4eacb24a9ec7ae3` | audioclip-4449 | 4.3 | 0.792 | 작고 귀여운 몬스터가 기합을 내지르며 공격하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1b6ba880fed1438ba4eacb24a9ec7ae3) |
| ☐ | `1892ec69da33411eb436e1ad40577594` | audioclip-4011 | 1.6 | 0.791 | 몬스터가 기합을 내지르며 공격하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1892ec69da33411eb436e1ad40577594) |
| ☐ | `240864ec89224ca386cfef54c8b2c5e0` | audioclip-5809 | 3.3 | 0.791 | 작은 몬스터가 기합을 넣으며 공격하는 듯한 짧고 귀여운 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=240864ec89224ca386cfef54c8b2c5e0) |


## 위치

### 위치 지정 대기 진입  <sub>(effect, 검색어: 조준 모드 진입 클릭 타겟 선택 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `efa32a1a651646f7868c5cae86c611a2` | audioclip-37647 | 0.3 | 0.813 | UI 메뉴를 클릭하거나 선택할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=efa32a1a651646f7868c5cae86c611a2) |
| ☐ | `d994edad91414ad1a4a6daf6f41cbfc8` | audioclip-34224 | 0.7 | 0.813 | UI 버튼을 클릭하거나 선택할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d994edad91414ad1a4a6daf6f41cbfc8) |
| ☐ | `5873f227d7604a63997546a92824c135` | audioclip-13971 | 0.4 | 0.813 | 짧고 명확하게 들리는 클릭 또는 선택 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5873f227d7604a63997546a92824c135) |
| ☐ | `3d629f714fdb43c2af11dfcc266ab777` | audioclip-62738 | 0.7 | 0.812 | UI 메뉴를 조작하거나 버튼을 누를 때 발생하는 짧은 클릭 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3d629f714fdb43c2af11dfcc266ab777) |
| ☐ | `26e422277f244cf29d076689ec0f025b` | audioclip-6254 | 0.3 | 0.812 | UI 선택 시 발생하는 짧고 명확한 금속성 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=26e422277f244cf29d076689ec0f025b) |
| ☐ | `3afa0f6018194be7a6c4e6a549fa8333` | audioclip-9363 | 1 | 0.812 | UI 버튼을 클릭하거나 선택할 때 발생하는 짧고 날카로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3afa0f6018194be7a6c4e6a549fa8333) |
| ☐ | `cc0be61d8a104aee81a4b177a9f79706` | audioclip-32029 | 0.7 | 0.812 | UI 메뉴 선택 시 발생하는 짧고 날카로운 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cc0be61d8a104aee81a4b177a9f79706) |
| ☐ | `6edbb88eba664485bc3b77d73fc79735` | audioclip-17376 | 1.5 | 0.812 | UI 메뉴 선택 시 발생하는 짧고 날카로운 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6edbb88eba664485bc3b77d73fc79735) |
| ☐ | `c9adc34434f744b1ad5b108dd6c85a92` | audioclip-31646 | 1.1 | 0.811 | UI 메뉴 선택 시 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c9adc34434f744b1ad5b108dd6c85a92) |
| ☐ | `3e92c72918e144019a767e653716ee1f` | audioclip-61013 | 2.2 | 0.809 | UI 버튼을 클릭하거나 선택할 때 발생하는 짧고 명확한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e92c72918e144019a767e653716ee1f) |
| ☐ | `fcbd94b35ea447618a90f5a165735f13` | audioclip-39705 | 2.1 | 0.809 | UI 메뉴 선택이나 클릭 시 발생하는 짧고 날카로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fcbd94b35ea447618a90f5a165735f13) |
| ☐ | `457e478dfeae448bb02dd02fbe614855` | audioclip-11004 | 0.3 | 0.809 | UI 요소를 클릭하거나 선택할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=457e478dfeae448bb02dd02fbe614855) |
| ☐ | `628c059ae00848928c810f878d3c67b2` | audioclip-15513 | 1.4 | 0.809 | UI 메뉴를 선택하거나 클릭할 때 발생하는 짧고 날카로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=628c059ae00848928c810f878d3c67b2) |
| ☐ | `3e4ff08f0d4642ed866b05df10ef0ed8` | audioclip-9864 | 1 | 0.809 | 짧고 날카로운 UI 클릭 또는 선택 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e4ff08f0d4642ed866b05df10ef0ed8) |
| ☐ | `0da162fd85c94121893f89d986ef3a09` | audioclip-2226 | 1.1 | 0.809 | 짧고 날카로운 UI 클릭 또는 선택 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0da162fd85c94121893f89d986ef3a09) |
| ☐ | `06178bf25d1844b2b3236fca60ac6b24` | audioclip-40799 | 0.4 | 0.808 | UI 메뉴를 선택하거나 클릭할 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=06178bf25d1844b2b3236fca60ac6b24) |
| ☐ | `97796c8c687a47ec99d1ed1dd53cae62` | audioclip-23668 | 2.3 | 0.808 | 날카롭고 짧은 금속성 UI 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=97796c8c687a47ec99d1ed1dd53cae62) |
| ☐ | `24bc2b02e819461f9335241f154311dd` | audioclip-5925 | 0.3 | 0.808 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=24bc2b02e819461f9335241f154311dd) |
| ☐ | `589c24bd648f4311a3550ded0f7c06d7` | audioclip-13993 | 1.7 | 0.808 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=589c24bd648f4311a3550ded0f7c06d7) |
| ☐ | `8890ad81f93240079816560cac360711` | audioclip-21418 | 0.7 | 0.808 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8890ad81f93240079816560cac360711) |


## 건물 선택

### 건물 선택음  <sub>(effect, 검색어: 묵직하고 둔탁한 UI 선택 효과음 건물)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `66c16eb0fa77469bbf29af1bd02c02c9` | audioclip-16151 | 3.4 | 0.899 | 묵직하고 기계적인 느낌의 UI 버튼 클릭 또는 선택 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=66c16eb0fa77469bbf29af1bd02c02c9) |
| ☐ | `64cb803b256640bc929187dccff40e71` | audioclip-15847 | 3.4 | 0.891 | 무겁고 타격감이 느껴지는 UI 선택 또는 전환 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=64cb803b256640bc929187dccff40e71) |
| ☐ | `85b7666671cd4bada0948693de995580` | audioclip-20994 | 1.4 | 0.889 | 묵직하고 낮은 톤의 UI 버튼 클릭 또는 선택 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=85b7666671cd4bada0948693de995580) |
| ☐ | `699dce87c0f844ea98f8be13282d8af5` | audioclip-16587 | 1.1 | 0.887 | 무겁고 임팩트 있는 UI 선택 또는 확인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=699dce87c0f844ea98f8be13282d8af5) |
| ☐ | `3e6ed01151294003a9178d1a137df3eb` | audioclip-60883 | 3.3 | 0.887 | UI 메뉴 선택이나 버튼 클릭 시 발생하는 묵직한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e6ed01151294003a9178d1a137df3eb) |
| ☐ | `6c33204e5ef3496ab28e86b7c9d0df78` | audioclip-16979 | 0.3 | 0.886 | 짧고 둔탁한 느낌의 UI 버튼 클릭 또는 선택 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6c33204e5ef3496ab28e86b7c9d0df78) |
| ☐ | `c905974a708b411dbc7ed7487ec85158` | audioclip-31533 | 0.6 | 0.886 | 무겁고 낮은 톤의 기계적인 버튼 클릭 또는 UI 선택음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c905974a708b411dbc7ed7487ec85158) |
| ☐ | `67f5fc9f86f54ca39303e2634bbd380a` | audioclip-16354 | 3.3 | 0.884 | 묵직하고 낮은 톤의 UI 선택 또는 임팩트 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=67f5fc9f86f54ca39303e2634bbd380a) |
| ☐ | `fee1938003084661af1ff48aa188ca58` | audioclip-40065 | 0.3 | 0.883 | UI 버튼을 클릭하거나 선택할 때 발생하는 짧고 둔탁한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fee1938003084661af1ff48aa188ca58) |
| ☐ | `010ca3f49d2e49db858370d9f6af5393` | audioclip-257 | 1.4 | 0.882 | 금속 재질의 묵직하고 날카로운 UI 클릭 또는 선택 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=010ca3f49d2e49db858370d9f6af5393) |
| ☐ | `15a062b0e99d44c181c415041557d34e` | audioclip-3551 | 0.3 | 0.881 | UI 메뉴를 클릭하거나 버튼을 누를 때 발생하는 짧고 둔탁한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=15a062b0e99d44c181c415041557d34e) |
| ☐ | `8a95c17048564777bfaa9b3c2f4cbf63` | audioclip-21714 | 1 | 0.878 | UI 버튼을 클릭하거나 짧게 선택할 때 발생하는 둔탁한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8a95c17048564777bfaa9b3c2f4cbf63) |
| ☐ | `bf99166e6fe749a2ad84b50329abab2d` | audioclip-30007 | 2.6 | 0.878 | 묵직한 느낌의 UI 버튼 클릭 또는 메뉴 선택 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bf99166e6fe749a2ad84b50329abab2d) |
| ☐ | `fd8365d26b9f4cbeadc436aa0f3fd2cb` | audioclip-39837 | 1.2 | 0.878 | 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 둔탁한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fd8365d26b9f4cbeadc436aa0f3fd2cb) |
| ☐ | `eba87ce9533a4fd98580804c74c023c9` | audioclip-61577 | 0.6 | 0.878 | 무겁고 기계적인 느낌의 UI 클릭 또는 버튼 조작음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=eba87ce9533a4fd98580804c74c023c9) |
| ☐ | `b8e8bc7afbb84652a6142f37349fb012` | audioclip-28997 | 0.7 | 0.877 | 짧고 묵직하게 들리는 UI 선택음 또는 타격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b8e8bc7afbb84652a6142f37349fb012) |
| ☐ | `10ef000382cf4424839b2949c73482a6` | audioclip-2781 | 3.4 | 0.877 | 기계적인 조작감이 느껴지는 묵직한 UI 선택 또는 확인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=10ef000382cf4424839b2949c73482a6) |
| ☐ | `d1870460b7b94b37a083d18739dd53c5` | audioclip-32891 | 0.6 | 0.877 | 묵직하고 짧은 타격음 또는 UI 선택 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d1870460b7b94b37a083d18739dd53c5) |
| ☐ | `de00a63e8d6f45e3b5f1df4a8d9a405a` | audioclip-34869 | 1.5 | 0.877 | 짧고 둔탁한 느낌의 UI 선택음 또는 타격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=de00a63e8d6f45e3b5f1df4a8d9a405a) |
| ☐ | `bb48cf1eb1ab483999b0076a46b0a6ff` | audioclip-29369 | 4.9 | 0.877 | 무게감이 느껴지는 짧고 묵직한 UI 선택 또는 확인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bb48cf1eb1ab483999b0076a46b0a6ff) |


## 생산

### 생산 시작  <sub>(effect, 검색어: 기계가 작동을 시작하는 효과음 생산 가동)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `0b88df5ee7dd4e0cacdc946d0c43fa7d` | audioclip-1898 | 3.4 | 0.81 | 기계가 작동하거나 회전하는 듯한 공상과학 스타일의 기계음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0b88df5ee7dd4e0cacdc946d0c43fa7d) |
| ☐ | `247795a81c7e4e60925e2d71cdd62725` | audioclip-5875 | 2.8 | 0.8 | 기계 장치나 모터가 빠르게 회전하며 작동하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=247795a81c7e4e60925e2d71cdd62725) |
| ☐ | `90381babf33b48db9bd1cc988877d424` | audioclip-22581 | 2.1 | 0.796 | 기계가 작동을 시작하며 회전수가 올라가는 듯한 기계음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=90381babf33b48db9bd1cc988877d424) |
| ☐ | `247cd312d13849bfa8707de93c089b98` | audioclip-5879 | 1.8 | 0.794 | 공장이나 기계 장치에서 발생하는 반복적이고 리드미컬한 기계 작동음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=247cd312d13849bfa8707de93c089b98) |
| ☐ | `a17ef76bb7374282b2424cd1eb07ccc3` | audioclip-25296 | 16.3 | 0.79 | 기계가 작동하며 무겁게 돌아가는 소리와 금속성 타격음이 섞인 산업용 기계 작동음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a17ef76bb7374282b2424cd1eb07ccc3) |
| ☐ | `5aac03f3ebe54cf5aaac5994e82cb307` | audioclip-14278 | 4.7 | 0.788 | 무거운 기계 장치가 작동하거나 거대한 금속 물체가 움직이는 육중한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5aac03f3ebe54cf5aaac5994e82cb307) |
| ☐ | `9d40d4d28c204afda869459f1a3a38a0` | audioclip-24591 | 9.7 | 0.784 | 공장이나 기계 장치가 작동하는 무겁고 규칙적인 산업용 기계음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9d40d4d28c204afda869459f1a3a38a0) |
| ☐ | `716fbe4c14af4f3cad4f315d6d86f84a` | audioclip-17780 | 1 | 0.784 | 기계 장치나 로봇이 움직일 때 발생하는 규칙적인 금속성 구동음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=716fbe4c14af4f3cad4f315d6d86f84a) |
| ☐ | `1d78cb06d3aa419f8b5aa990c1a59027` | audioclip-61080 | 1.3 | 0.78 | 기계 장치가 규칙적으로 작동하며 무거운 물체가 미끄러지는 듯한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1d78cb06d3aa419f8b5aa990c1a59027) |
| ☐ | `ec8c9451c0f4492db81e9f4d992af392` | audioclip-37125 | 1.5 | 0.78 | 산업용 기계나 대형 엔진이 지속적으로 돌아가는 육중한 기계 작동음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ec8c9451c0f4492db81e9f4d992af392) |
| ☐ | `210304f9cf0f49849baa828f33b89839` | audioclip-5315 | 2.3 | 0.78 | 기계 장치가 짧게 작동하거나 로봇이 움직이는 듯한 금속성 기계음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=210304f9cf0f49849baa828f33b89839) |
| ☐ | `cf2bac00cbbb4fcc92d4a166b1f77a0a` | audioclip-32532 | 4.9 | 0.779 | 기계 장치가 가속하며 빠르게 지나가는 듯한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cf2bac00cbbb4fcc92d4a166b1f77a0a) |
| ☐ | `8f16088c9c564c7f8df9886c928eadf9` | audioclip-22404 | 2.6 | 0.778 | 무거운 금속 기계 장치가 움직이거나 맞물리는 육중한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8f16088c9c564c7f8df9886c928eadf9) |
| ☐ | `907a3b9e66a14bb89de2f3f07662c4b2` | audioclip-22628 | 5.5 | 0.778 | 거대한 기계 장치나 탈것이 굉음을 내며 빠르게 지나가는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=907a3b9e66a14bb89de2f3f07662c4b2) |
| ☐ | `c21031dd4ae04ec4bedf1489a8ad07fb` | audioclip-30421 | 4.2 | 0.778 | 기계가 작동하거나 엔진이 돌아가는 듯한 웅웅거리는 기계음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c21031dd4ae04ec4bedf1489a8ad07fb) |
| ☐ | `9ec9ad3eb917448cb55f2857f00e4107` | audioclip-42410 | 9.9 | 0.778 | 우주선이나 기계가 가속하며 이륙하는 듯한 SF 스타일의 기계음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9ec9ad3eb917448cb55f2857f00e4107) |
| ☐ | `baffef66f8a24dd48fcc7072192441da` | audioclip-29314 | 2.7 | 0.777 | 기계가 작동하거나 엔진이 돌아가는 듯한 무겁고 반복적인 기계음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=baffef66f8a24dd48fcc7072192441da) |
| ☐ | `ad50e9a827a146a2b59f45f15fcbd3de` | audioclip-27195 | 1.3 | 0.777 | 산업 현장이나 대형 기계가 작동하는 듯한 웅장하고 지속적인 기계 소음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ad50e9a827a146a2b59f45f15fcbd3de) |
| ☐ | `94b1b5fcef684cf58e5d4e70cd84e665` | audioclip-23225 | 2.8 | 0.776 | 무거운 기계 장치가 작동하거나 육중한 금속 물체가 부딪히는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=94b1b5fcef684cf58e5d4e70cd84e665) |
| ☐ | `55431cfe269a4bd9ab19be8e4c8f2984` | audioclip-13478 | 4.2 | 0.776 | 무겁고 지속적인 기계 장치 또는 엔진의 가동 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=55431cfe269a4bd9ab19be8e4c8f2984) |

### 생산 완료(유닛 준비됨)  <sub>(effect, 검색어: 완료 알림 띠링 성공 효과음 유닛 준비)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `a5427847c1ff40dc86c951d72ad2b16f` | audioclip-25895 | 2.7 | 0.823 | 성공이나 알림을 나타내는 맑고 높은 톤의 금속성 벨 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a5427847c1ff40dc86c951d72ad2b16f) |
| ☐ | `c190c3e2bb934dbcab5ba3335398bb6b` | audioclip-30351 | 1 | 0.823 | UI 알림이나 성공을 나타내는 짧고 높은 톤의 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c190c3e2bb934dbcab5ba3335398bb6b) |
| ☐ | `d52229d0398c452e84de821c6fbb2ecf` | audioclip-33460 | 3.4 | 0.822 | UI 알림이나 성공을 나타내는 짧고 높은 톤의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d52229d0398c452e84de821c6fbb2ecf) |
| ☐ | `a72a3986004e40119f3bbf33ab265590` | audioclip-26194 | 0.5 | 0.821 | 밝고 높은 톤의 금속성 UI 알림음 또는 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a72a3986004e40119f3bbf33ab265590) |
| ☐ | `819d229ebc834eed97bba53cbc8e214e` | audioclip-20382 | 1.5 | 0.821 | 알림이나 성공을 나타내는 짧고 높은 톤의 금속성 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=819d229ebc834eed97bba53cbc8e214e) |
| ☐ | `a64a30bed96848779bc7f36457cd0e3b` | audioclip-26048 | 0.6 | 0.82 | 밝고 맑은 톤의 UI 알림 또는 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a64a30bed96848779bc7f36457cd0e3b) |
| ☐ | `a0846e52c0e7469c970826b61a026044` | audioclip-25109 | 2.6 | 0.82 | 밝고 높은 톤의 알림음 또는 UI 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a0846e52c0e7469c970826b61a026044) |
| ☐ | `e02aa4ea84f142578c2ab1b09d0b2d8d` | audioclip-35220 | 3 | 0.82 | 무언가 완료되거나 알림이 뜰 때 발생하는 짧고 경쾌한 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e02aa4ea84f142578c2ab1b09d0b2d8d) |
| ☐ | `f35eac1d24224721b8e2205b71634eb1` | audioclip-38279 | 2.7 | 0.82 | UI에서 무언가 완료되거나 알림이 뜰 때 발생하는 맑고 높은 금속성 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f35eac1d24224721b8e2205b71634eb1) |
| ☐ | `f6e922a46a07487da673e1b7da5ca041` | audioclip-61108 | 1.5 | 0.819 | 성공이나 알림을 나타내는 짧고 높은 톤의 금속성 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f6e922a46a07487da673e1b7da5ca041) |
| ☐ | `e7a4c6ace6b640f383256849a597964a` | audioclip-36412 | 0.5 | 0.819 | 밝고 경쾌한 느낌의 UI 알림 또는 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e7a4c6ace6b640f383256849a597964a) |
| ☐ | `fad074e5ff984d9aa6d3d649994b76e1` | audioclip-39389 | 1.4 | 0.819 | 밝고 높은 톤의 UI 알림음 또는 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fad074e5ff984d9aa6d3d649994b76e1) |
| ☐ | `121bcc627499496182f01b8e622ab0ab` | audioclip-2945 | 1.2 | 0.819 | 무언가 완료되거나 알림이 뜰 때 들리는 맑고 높은 톤의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=121bcc627499496182f01b8e622ab0ab) |
| ☐ | `3e1802b362004017ba388b3d34071ca8` | audioclip-9835 | 1 | 0.819 | UI 알림이나 성공을 나타내는 짧고 높은 톤의 금속성 벨소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e1802b362004017ba388b3d34071ca8) |
| ☐ | `1e46799f903f49ebae142a9831210d9b` | audioclip-4891 | 0.5 | 0.819 | UI 알림이나 성공을 나타내는 짧고 높은 톤의 금속성 벨소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1e46799f903f49ebae142a9831210d9b) |
| ☐ | `b4b3b42e91794e36b68fd3d0d59aaa83` | audioclip-28358 | 2.7 | 0.818 | 성공이나 알림을 나타내는 짧고 높은 톤의 금속성 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b4b3b42e91794e36b68fd3d0d59aaa83) |
| ☐ | `bd50a941c46e4a1fa8e11ad4fb70871a` | audioclip-29662 | 0.6 | 0.818 | UI 알림이나 성공 시 발생하는 짧고 높은 톤의 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bd50a941c46e4a1fa8e11ad4fb70871a) |
| ☐ | `9e2f885b03b74832b650ac27585680b8` | audioclip-42406 | 2.3 | 0.818 | 밝고 경쾌한 톤의 UI 알림 또는 작업 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9e2f885b03b74832b650ac27585680b8) |
| ☐ | `a33f450bf4b540099985d06531b71588` | audioclip-25593 | 2 | 0.818 | UI에서 무언가 완료되었거나 알림이 뜰 때 발생하는 맑고 높은 금속성 알림음. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a33f450bf4b540099985d06531b71588) |
| ☐ | `09b80d0714ac4b8cb5111fc2fcae3773` | audioclip-1618 | 1.6 | 0.817 | 밝고 높은 톤의 UI 알림음 또는 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=09b80d0714ac4b8cb5111fc2fcae3773) |

### 생산 취소/환불  <sub>(effect, 검색어: 취소 효과음 되돌리기 UI)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `15064f1b31974a629387d617746b0140` | audioclip-3452 | 0.8 | 0.861 | 메뉴 취소 또는 뒤로 가기 시 발생하는 시스템 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=15064f1b31974a629387d617746b0140) |
| ☐ | `c7956414a0054d2fb44a8b653429a7da` | audioclip-31314 | 0.6 | 0.821 | 창을 닫거나 동작을 취소할 때 들리는 시스템 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c7956414a0054d2fb44a8b653429a7da) |
| ☐ | `cb07b96d4ad34dbf9b918e65edb527bf` | audioclip-31855 | 0.8 | 0.802 | UI 메뉴를 닫거나 취소할 때 발생하는 짧고 뭉툭한 클릭 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cb07b96d4ad34dbf9b918e65edb527bf) |
| ☐ | `e48e4c49fa4641ce9a456a0e309fa93d` | audioclip-35925 | 3.1 | 0.797 | 메뉴를 닫거나 뒤로 가기 버튼을 누를 때 발생하는 짧고 깔끔한 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e48e4c49fa4641ce9a456a0e309fa93d) |
| ☐ | `0e34e099be104f6eab1361d1b3cce61c` | audioclip-40899 | 1.1 | 0.794 | UI 인터페이스에서 버튼을 누르거나 취소할 때 발생하는 짧고 기계적인 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0e34e099be104f6eab1361d1b3cce61c) |
| ☐ | `1cc27894b265460aacca7bd9ee2fa353` | audioclip-4668 | 3 | 0.792 | UI 메뉴를 닫거나 취소할 때 발생하는 짧고 깔끔한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1cc27894b265460aacca7bd9ee2fa353) |
| ☐ | `6dc981c7759c49958159fa43076f199f` | audioclip-17215 | 1.9 | 0.787 | 창을 닫거나 동작을 취소할 때 발생하는 짧고 깔끔한 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6dc981c7759c49958159fa43076f199f) |
| ☐ | `2fbc565c1b0643ed903f4e2cb1b67386` | audioclip-7606 | 3.9 | 0.768 | UI 메뉴에서 뒤로 가기나 취소 시 발생하는 짧고 깔끔한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2fbc565c1b0643ed903f4e2cb1b67386) |
| ☐ | `5b07744e843b4b36b64b0067610331aa` | audioclip-41695 | 0.7 | 0.766 | UI 버튼을 누르거나 창을 닫을 때 발생하는 짧고 간결한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5b07744e843b4b36b64b0067610331aa) |
| ☐ | `2c79656363ba450e95cec1b1c02d91cb` | audioclip-7107 | 1.3 | 0.762 | UI 메뉴를 닫거나 취소할 때 발생하는 날카롭고 금속적인 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2c79656363ba450e95cec1b1c02d91cb) |
| ☐ | `738302986e0242999bf0cccb87c3327e` | audioclip-18103 | 0.3 | 0.757 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 뭉툭한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=738302986e0242999bf0cccb87c3327e) |
| ☐ | `79c981558002470f8d97301e16bcce52` | audioclip-41991 | 0.4 | 0.756 | UI 창을 닫거나 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=79c981558002470f8d97301e16bcce52) |
| ☐ | `b5c8f07c6fe740f381e1e1c579f34905` | audioclip-28521 | 0.8 | 0.754 | UI 메뉴 선택 시 발생하는 날카롭고 금속적인 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b5c8f07c6fe740f381e1e1c579f34905) |
| ☐ | `16021cbacf884ddf92c4fcf6d0122586` | audioclip-40268 | 4.1 | 0.754 | UI 버튼을 클릭할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=16021cbacf884ddf92c4fcf6d0122586) |
| ☐ | `ad895897d7574f4299123b716b6aaf01` | audioclip-42547 | 0.4 | 0.749 | UI 버튼을 클릭하거나 항목을 선택할 때 발생하는 짧고 뭉툭한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ad895897d7574f4299123b716b6aaf01) |
| ☐ | `09854793d42349ecbd91143002507858` | audioclip-1580 | 1.1 | 0.749 | UI 버튼을 클릭할 때 발생하는 짧고 기계적인 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=09854793d42349ecbd91143002507858) |
| ☐ | `10f217ca7a1740e68d906405832d0ef5` | audioclip-2783 | 0.8 | 0.748 | UI 버튼을 클릭할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=10f217ca7a1740e68d906405832d0ef5) |
| ☐ | `c8b7f79a74464f089c27ff03701c010b` | audioclip-31478 | 0.6 | 0.747 | UI 메뉴 선택이나 버튼 클릭 시 발생하는 짧은 기계적 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c8b7f79a74464f089c27ff03701c010b) |
| ☐ | `2dc9286ee38e423fa02c99949d49254a` | audioclip-7300 | 1.6 | 0.747 | UI 버튼을 누를 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2dc9286ee38e423fa02c99949d49254a) |
| ☐ | `efedc7734f4a406eb8f881b07301baf9` | audioclip-37692 | 0.3 | 0.746 | UI 버튼을 클릭할 때 발생하는 짧고 깔끔한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=efedc7734f4a406eb8f881b07301baf9) |


## 기타

### 건물 배치 확정  <sub>(effect, 검색어: 무거운 물체를 땅에 내려놓는 쿵 배치 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `c5faf1a9b70a4294be3434c4561afe08` | audioclip-42810 | 0.4 | 0.839 | 무거운 물체나 캐릭터가 바닥에 착지할 때 발생하는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c5faf1a9b70a4294be3434c4561afe08) |
| ☐ | `69012a1a741d47eb89221caaeed91186` | audioclip-16490 | 1.6 | 0.836 | 무거운 물체나 캐릭터가 바닥에 착지할 때 발생하는 묵직한 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=69012a1a741d47eb89221caaeed91186) |
| ☐ | `4168a36006a44f919035607df526b5de` | audioclip-10360 | 2.1 | 0.829 | 무거운 금속성 물체가 바닥에 부딪히며 나는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4168a36006a44f919035607df526b5de) |
| ☐ | `65f9a99aad6449369d1c0b7f5371c1e4` | audioclip-41808 | 2.5 | 0.823 | 캐릭터가 점프 후 지면에 묵직하게 착지하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=65f9a99aad6449369d1c0b7f5371c1e4) |
| ☐ | `b89b487980754fedad952fa742cf187e` | audioclip-28956 | 0.9 | 0.819 | 무거운 둔기로 타격하는 듯한 묵직한 물리적 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b89b487980754fedad952fa742cf187e) |
| ☐ | `5615c4e2a2434cd4b2862fc406cabce5` | audioclip-13603 | 1 | 0.818 | 캐릭터가 착지하거나 물체가 바닥에 부딪히는 짧고 둔탁한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5615c4e2a2434cd4b2862fc406cabce5) |
| ☐ | `f69c517faf5443cc9558ef4f7284a19c` | audioclip-38771 | 0.5 | 0.818 | 무거운 금속 물체가 바닥에 떨어지거나 부딪히는 묵직한 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f69c517faf5443cc9558ef4f7284a19c) |
| ☐ | `38c63c3a0fa2479d94db8572b7885ef2` | audioclip-9032 | 0.5 | 0.816 | 무거운 발걸음이나 착지 시 발생하는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=38c63c3a0fa2479d94db8572b7885ef2) |
| ☐ | `007b93653d5643a0a3c8b9dfba6d5965` | audioclip-167 | 0.9 | 0.816 | 무거운 물체가 바닥에 떨어지거나 착지할 때 발생하는 둔탁하고 묵직한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=007b93653d5643a0a3c8b9dfba6d5965) |
| ☐ | `b3aa1cad5e0f4a24b9a11f9a824cf03d` | audioclip-28190 | 0.3 | 0.815 | 캐릭터가 착지하거나 무거운 물체가 바닥에 부딪힐 때 발생하는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b3aa1cad5e0f4a24b9a11f9a824cf03d) |
| ☐ | `f5dffaa3600647a79d22d123c51b44df` | audioclip-38666 | 0.9 | 0.815 | 무거운 금속 물체가 부딪히거나 닫히는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f5dffaa3600647a79d22d123c51b44df) |
| ☐ | `9438aab5f47e40b7ba3b761232a076c4` | audioclip-23160 | 3.1 | 0.815 | 무거운 물체로 타격하는 둔탁한 물리적 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9438aab5f47e40b7ba3b761232a076c4) |
| ☐ | `1f791ff2ea1846dba04097d14352f755` | audioclip-5064 | 2 | 0.814 | 캐릭터나 몬스터가 점프 후 바닥에 착지할 때 발생하는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1f791ff2ea1846dba04097d14352f755) |
| ☐ | `49aee67ced7142a386a6a0cd3a320261` | audioclip-62725 | 0.7 | 0.813 | 캐릭터가 바닥에 착지할 때 발생하는 짧고 둔탁한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=49aee67ced7142a386a6a0cd3a320261) |
| ☐ | `912519c0592c40f3a5a9285d51afce42` | audioclip-22701 | 0.5 | 0.812 | 무거운 물체가 바닥에 떨어지거나 착지할 때 발생하는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=912519c0592c40f3a5a9285d51afce42) |
| ☐ | `42d5c111b0bb49d1b4e5039d0d5b9c36` | audioclip-10598 | 0.5 | 0.812 | 무거운 생명체나 물체가 바닥에 떨어지며 발생하는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=42d5c111b0bb49d1b4e5039d0d5b9c36) |
| ☐ | `400cfa18fd35438283bba55af6dd1c78` | audioclip-10150 | 2.6 | 0.811 | 무거운 물체로 타격하는 듯한 묵직한 물리적 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=400cfa18fd35438283bba55af6dd1c78) |
| ☐ | `dc159f9272e34e8e961ebb7fcb61c3a6` | audioclip-34597 | 2 | 0.811 | 무거운 물체로 무언가를 강하게 타격하는 물리적인 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dc159f9272e34e8e961ebb7fcb61c3a6) |
| ☐ | `5be3859e6b414fd0a70213c3ecab27f5` | audioclip-14491 | 1.1 | 0.811 | 무언가 강하게 타격하거나 부딪히는 묵직한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5be3859e6b414fd0a70213c3ecab27f5) |
| ☐ | `d54d4ba7b9f047019a7f7b273e42e7a5` | audioclip-33485 | 0.9 | 0.811 | 무거운 물체가 바닥에 떨어지거나 착지할 때 발생하는 묵직한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d54d4ba7b9f047019a7f7b273e42e7a5) |

### 건물 배치 불가  <sub>(effect, 검색어: 배치 불가 오류 경고음 UI 거부)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `762421119c1148f18d592554cfde4d9c` | audioclip-18502 | 3.1 | 0.734 | 높은 톤으로 반복해서 울리는 전자식 경고음 또는 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=762421119c1148f18d592554cfde4d9c) |
| ☐ | `1bee698506af44c4a1f84b01be7373a2` | audioclip-41034 | 1 | 0.732 | 경고나 알림을 나타내는 날카롭고 반복적인 전자 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1bee698506af44c4a1f84b01be7373a2) |
| ☐ | `7adc4731e2d04522a411012f77351d6a` | audioclip-60047 | 12.1 | 0.732 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 알람 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7adc4731e2d04522a411012f77351d6a) |
| ☐ | `540ef7865b7943128cbca004ec5c10ae` | audioclip-13281 | 3.1 | 0.728 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=540ef7865b7943128cbca004ec5c10ae) |
| ☐ | `40fb4b84ca7b4df399b36fd7d0475d24` | audioclip-10277 | 1.2 | 0.725 | UI 알림이나 버튼 클릭 시 발생하는 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=40fb4b84ca7b4df399b36fd7d0475d24) |
| ☐ | `e5389ea837dc46f49a97a69d21abbb79` | audioclip-36023 | 2.6 | 0.724 | 전기 기타의 왜곡된 소리를 이용한 실패 또는 오류 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e5389ea837dc46f49a97a69d21abbb79) |
| ☐ | `5d704b3c83504094b96febc1c936239f` | audioclip-14711 | 1.9 | 0.722 | 비상 상황이나 경고를 알리는 날카로운 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5d704b3c83504094b96febc1c936239f) |
| ☐ | `e5397d34e85e4a3caf593748afbf030f` | audioclip-36024 | 4.8 | 0.72 | 비상 상황이나 시스템 경고를 알리는 날카로운 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e5397d34e85e4a3caf593748afbf030f) |
| ☐ | `98e9c05088db4dbc853dfb4e56734220` | audioclip-23888 | 1.9 | 0.72 | 경고나 비상 상황을 알리는 날카롭고 반복적인 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=98e9c05088db4dbc853dfb4e56734220) |
| ☐ | `81122a7025f84ffbb31b3989476ba080` | audioclip-20301 | 0.7 | 0.718 | 짧고 반복적인 전자음 형태의 UI 알림 또는 경고음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=81122a7025f84ffbb31b3989476ba080) |
| ☐ | `15064f1b31974a629387d617746b0140` | audioclip-3452 | 0.8 | 0.718 | 메뉴 취소 또는 뒤로 가기 시 발생하는 시스템 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=15064f1b31974a629387d617746b0140) |
| ☐ | `d54077cf43a144c2aa6ad0a17a2789a0` | audioclip-33491 | 10.7 | 0.716 | 긴박한 상황이나 경고를 알리는 반복적인 고음의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d54077cf43a144c2aa6ad0a17a2789a0) |
| ☐ | `652025e1107345aaa52a2e06681f284c` | audioclip-15911 | 4.1 | 0.715 | 전자적인 알람이나 경고를 나타내는 반복적인 고음의 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=652025e1107345aaa52a2e06681f284c) |
| ☐ | `c7956414a0054d2fb44a8b653429a7da` | audioclip-31314 | 0.6 | 0.714 | 창을 닫거나 동작을 취소할 때 들리는 시스템 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c7956414a0054d2fb44a8b653429a7da) |
| ☐ | `a74d1652120942c9a5ca3afcdaedf33e` | audioclip-26214 | 1.9 | 0.713 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a74d1652120942c9a5ca3afcdaedf33e) |
| ☐ | `9325d50a0b2d434f94edc6dbdfc1da17` | audioclip-23010 | 0.7 | 0.709 | UI에서 알림이나 버튼 클릭 시 발생하는 짧고 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9325d50a0b2d434f94edc6dbdfc1da17) |
| ☐ | `c15e945508d44dee8e805737d606e85e` | audioclip-30307 | 0.6 | 0.708 | UI에서 발생하는 짧고 높은 톤의 디지털 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c15e945508d44dee8e805737d606e85e) |
| ☐ | `041034e6ef4e4570b8677a62c90512a0` | audioclip-718 | 7.6 | 0.707 | 메뉴 선택이나 시스템 알림 시 발생하는 고음의 디지털 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=041034e6ef4e4570b8677a62c90512a0) |
| ☐ | `174d501eccd04eadbd6c6411d4ade7e7` | audioclip-3801 | 0.9 | 0.707 | 짧고 날카로운 전자음으로, UI 오류나 경고 상황에 적합한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=174d501eccd04eadbd6c6411d4ade7e7) |
| ☐ | `431281324cc8407da50ed8d53390be67` | audioclip-10627 | 3.6 | 0.702 | 높은 톤의 디지털 비프음이 반복되는 알림 또는 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=431281324cc8407da50ed8d53390be67) |


## 건설

### 건설 시작  <sub>(effect, 검색어: 공사 시작 건설 효과음 톱질 망치)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `0005a690863742eca3347ca5fa0fc7be` | audioclip-105 | 4.4 | 0.81 | 망치나 둔기로 나무를 두드리는 듯한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0005a690863742eca3347ca5fa0fc7be) |
| ☐ | `a6f7d49a8a5d4fe3a2695351cdde8bbe` | audioclip-26151 | 1.7 | 0.803 | 나무를 망치로 두드리는 듯한 규칙적인 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a6f7d49a8a5d4fe3a2695351cdde8bbe) |
| ☐ | `fce5b39404274086b7d0c112d8cb3723` | audioclip-39730 | 0.9 | 0.791 | 무거운 나무나 망치로 무언가를 강하게 내리치는 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fce5b39404274086b7d0c112d8cb3723) |
| ☐ | `c38272c85206476eb98768a03eb5097a` | audioclip-30640 | 1.8 | 0.776 | 무거운 금속 물체나 망치로 단단한 표면을 내리치는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c38272c85206476eb98768a03eb5097a) |
| ☐ | `4d1ea044426d4985bc9ba8c70999af3d` | audioclip-12201 | 2.8 | 0.775 | 나무를 톱질하는 규칙적이고 거친 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4d1ea044426d4985bc9ba8c70999af3d) |
| ☐ | `630b133a2e8a457fa431c8aa27a28c51` | audioclip-41774 | 2.5 | 0.765 | 금속을 반복적으로 두드리는 규칙적인 망치질 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=630b133a2e8a457fa431c8aa27a28c51) |
| ☐ | `6dc40825bdbd4184a1bac3d0868389b2` | audioclip-17211 | 0.6 | 0.759 | 망치로 무언가를 세게 내리치는 듯한 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6dc40825bdbd4184a1bac3d0868389b2) |
| ☐ | `1868a31d1c3742d294426a232bbbef52` | audioclip-3987 | 1.1 | 0.752 | 무언가 부서지거나 강하게 타격하는 날카로운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1868a31d1c3742d294426a232bbbef52) |
| ☐ | `96dcdef321bb4a4596a6cc4dfa54a94a` | audioclip-23566 | 1.8 | 0.751 | 나무 상자나 물체가 부서지는 듯한 연속적인 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=96dcdef321bb4a4596a6cc4dfa54a94a) |
| ☐ | `91432c6802154843b161baa0864ec556` | audioclip-62113 | 0.7 | 0.75 | 무언가 강하게 부서지거나 타격하는 묵직한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=91432c6802154843b161baa0864ec556) |
| ☐ | `b70188f3d9f94d25874a2e88dd618def` | audioclip-28713 | 5.8 | 0.748 | 회전하는 톱날이 무언가를 자르는 듯한 기계적인 소음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b70188f3d9f94d25874a2e88dd618def) |
| ☐ | `12c9b2bdbe5641eab552432edc68d93d` | audioclip-3096 | 1.9 | 0.746 | 나무 상자나 물체가 부서지는 듯한 날카로운 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=12c9b2bdbe5641eab552432edc68d93d) |
| ☐ | `6abe61ee35f2440c8e045035e420372a` | audioclip-16745 | 1 | 0.746 | 나무나 단단한 물체가 부서지는 날카로운 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6abe61ee35f2440c8e045035e420372a) |
| ☐ | `da197a8131e14a85b1e269359113ee24` | audioclip-34300 | 0.4 | 0.746 | 무언가 부서지거나 강하게 타격하는 날카로운 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=da197a8131e14a85b1e269359113ee24) |
| ☐ | `3c57fe7b25c6488b918e7f5af761db2f` | audioclip-9561 | 1.8 | 0.746 | 목재나 물체가 부서지는 듯한 날카로운 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3c57fe7b25c6488b918e7f5af761db2f) |
| ☐ | `d8383cb8a89445f4b45c2ec1d6ee48a5` | audioclip-60257 | 1.6 | 0.745 | 무거운 물체가 부서지거나 파괴되는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d8383cb8a89445f4b45c2ec1d6ee48a5) |
| ☐ | `9f8c3d551e9b4a3fbd11160d20334183` | audioclip-24962 | 1 | 0.745 | 목재나 단단한 물체가 부서지는 날카로운 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9f8c3d551e9b4a3fbd11160d20334183) |
| ☐ | `28a43c547124422ea380483af2b32e37` | audioclip-6525 | 1.2 | 0.744 | 나무나 상자가 부서지는 듯한 둔탁한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=28a43c547124422ea380483af2b32e37) |
| ☐ | `58957f5d41bb4ebc8db053a4c25001fb` | audioclip-13982 | 0.7 | 0.744 | 나무나 물체가 부서지는 듯한 둔탁한 타격음과 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58957f5d41bb4ebc8db053a4c25001fb) |
| ☐ | `7f61308d96cf4ca3a926f04dc88dc346` | audioclip-20032 | 1.5 | 0.744 | 무거운 목재나 구조물이 부서지는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7f61308d96cf4ca3a926f04dc88dc346) |

### 건설 진행 루프(망치질)  <sub>(effect, 검색어: 망치로 두드리는 소리 반복 공사)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `a6f7d49a8a5d4fe3a2695351cdde8bbe` | audioclip-26151 | 1.7 | 0.852 | 나무를 망치로 두드리는 듯한 규칙적인 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a6f7d49a8a5d4fe3a2695351cdde8bbe) |
| ☐ | `630b133a2e8a457fa431c8aa27a28c51` | audioclip-41774 | 2.5 | 0.826 | 금속을 반복적으로 두드리는 규칙적인 망치질 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=630b133a2e8a457fa431c8aa27a28c51) |
| ☐ | `0005a690863742eca3347ca5fa0fc7be` | audioclip-105 | 4.4 | 0.815 | 망치나 둔기로 나무를 두드리는 듯한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0005a690863742eca3347ca5fa0fc7be) |
| ☐ | `fce5b39404274086b7d0c112d8cb3723` | audioclip-39730 | 0.9 | 0.788 | 무거운 나무나 망치로 무언가를 강하게 내리치는 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fce5b39404274086b7d0c112d8cb3723) |
| ☐ | `c38272c85206476eb98768a03eb5097a` | audioclip-30640 | 1.8 | 0.785 | 무거운 금속 물체나 망치로 단단한 표면을 내리치는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c38272c85206476eb98768a03eb5097a) |
| ☐ | `6dc40825bdbd4184a1bac3d0868389b2` | audioclip-17211 | 0.6 | 0.783 | 망치로 무언가를 세게 내리치는 듯한 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6dc40825bdbd4184a1bac3d0868389b2) |
| ☐ | `7061e14116b4474f8ab07ac2996ce292` | audioclip-17624 | 3.8 | 0.778 | 무거운 금속 물체를 여러 번 강하게 내리치는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7061e14116b4474f8ab07ac2996ce292) |
| ☐ | `a43cb696894542b6a28ae8580ed90484` | audioclip-25731 | 2.6 | 0.778 | 금속을 망치로 두드리는 듯한 규칙적인 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a43cb696894542b6a28ae8580ed90484) |
| ☐ | `0e328b92f77243bfada87a43581e29c0` | audioclip-2329 | 1.8 | 0.771 | 대장간에서 망치로 금속을 두드리는 규칙적인 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0e328b92f77243bfada87a43581e29c0) |
| ☐ | `9f3ff1369b234ed0aa15d80e965caa81` | audioclip-24928 | 3.1 | 0.763 | 무거운 둔기로 여러 번 타격하는 묵직한 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9f3ff1369b234ed0aa15d80e965caa81) |
| ☐ | `4613038676d8496fb40f153f4b8ed123` | audioclip-11100 | 2.4 | 0.763 | 무거운 둔기나 망치로 금속을 강하게 내리치는 여러 번의 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4613038676d8496fb40f153f4b8ed123) |
| ☐ | `040018c3821c4674984f7e81129baf64` | audioclip-724 | 3.4 | 0.758 | 대장장이가 모루를 망치로 두드리는 금속성 작업음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=040018c3821c4674984f7e81129baf64) |
| ☐ | `646cea67fb8a461f9fa33d3010ce7354` | audioclip-15785 | 1.9 | 0.757 | 무거운 금속 무기로 여러 번 타격하는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=646cea67fb8a461f9fa33d3010ce7354) |
| ☐ | `bdedec300aec4e9789e2242f69b96a71` | audioclip-29770 | 2.8 | 0.751 | 무겁고 강력한 기계적 폭발음 또는 타격음이 연속적으로 발생하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bdedec300aec4e9789e2242f69b96a71) |
| ☐ | `38c0fbc9ab634fefaba4fc4c25fd6aa4` | audioclip-9028 | 3.3 | 0.75 | 무거운 물체로 바닥이나 벽을 강하게 내리치는 육중한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=38c0fbc9ab634fefaba4fc4c25fd6aa4) |
| ☐ | `96dcdef321bb4a4596a6cc4dfa54a94a` | audioclip-23566 | 1.8 | 0.749 | 나무 상자나 물체가 부서지는 듯한 연속적인 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=96dcdef321bb4a4596a6cc4dfa54a94a) |
| ☐ | `6027db37ff3d41f9a456942d7ddbc849` | audioclip-15155 | 0.8 | 0.748 | 둔탁한 타격음과 함께 미세한 금속성 울림이 느껴지는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6027db37ff3d41f9a456942d7ddbc849) |
| ☐ | `63be9417034044edbcb595a86899d66b` | audioclip-15681 | 2.8 | 0.744 | 여러 번 반복되는 둔탁한 물리적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=63be9417034044edbcb595a86899d66b) |
| ☐ | `4172dbf8ede14dd989a4f9ef7fd3728f` | audioclip-10369 | 2.8 | 0.741 | 대장간에서 망치로 금속을 두드리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4172dbf8ede14dd989a4f9ef7fd3728f) |
| ☐ | `86772003148a480a84ce5a0e93b33267` | audioclip-62223 | 1.3 | 0.74 | 빠르게 반복되는 규칙적인 기계적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=86772003148a480a84ce5a0e93b33267) |

### 건설 완료  <sub>(effect, 검색어: 완성 팡파르 짧은 건물 완공 축하)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `2194bc42a2b14ecd85bc62cd2ab1872f` | audioclip-5408 | 7 | 0.743 | 승리나 스테이지 클리어를 축하하는 밝고 경쾌한 금관악기 팡파르 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2194bc42a2b14ecd85bc62cd2ab1872f) |
| ☐ | `d0809e566e704b97aa8371e5a8557363` | audioclip-32731 | 12 | 0.741 | 성취감이나 승리를 나타내는 경쾌하고 웅장한 오케스트라풍의 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d0809e566e704b97aa8371e5a8557363) |
| ☐ | `8d2a61033e874dd5bf4444232bb37663` | audioclip-22119 | 2.4 | 0.741 | 레벨 업이나 퀘스트 완료 시 사용하기 좋은 웅장하고 짧은 오케스트라 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8d2a61033e874dd5bf4444232bb37663) |
| ☐ | `655fec4efe3643d88eac1c686e5af922` | audioclip-15941 | 3.9 | 0.734 | 레벨 업이나 퀘스트 완료 시 재생되는 밝고 경쾌한 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=655fec4efe3643d88eac1c686e5af922) |
| ☐ | `a95fafcab2634b6f8be44f5833456440` | audioclip-26553 | 9.8 | 0.731 | 레벨 업이나 업적 달성 시 재생되는 밝고 경쾌한 축하 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a95fafcab2634b6f8be44f5833456440) |
| ☐ | `84a187fe4d514e6a9376069c89ceafe3` | audioclip-20821 | 2.4 | 0.727 | 퀘스트 완료나 레벨 업 시 사용될 법한 웅장하고 짧은 오케스트라 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=84a187fe4d514e6a9376069c89ceafe3) |
| ☐ | `ff2b8b75dfa84471b3b5d0f0566cdf74` | audioclip-40105 | 2.4 | 0.724 | 밝고 경쾌한 느낌의 짧은 팡파르 UI 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ff2b8b75dfa84471b3b5d0f0566cdf74) |
| ☐ | `612db5a626d04ae194a4de97b6846c52` | audioclip-15309 | 3.2 | 0.723 | 퀘스트 완료나 레벨 업 시 들리는 밝고 경쾌한 오케스트라 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=612db5a626d04ae194a4de97b6846c52) |
| ☐ | `538f8e6c766c4c01b73245f32974f59a` | audioclip-13203 | 24 | 0.723 | 승리나 레벨 업을 축하하는 웅장하고 화려한 오케스트라 팡파르 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=538f8e6c766c4c01b73245f32974f59a) |
| ☐ | `5d41290792d347cba393232249f27b21` | audioclip-14679 | 3 | 0.723 | 퀘스트 완료나 레벨 업 시 들릴 법한 밝고 경쾌한 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5d41290792d347cba393232249f27b21) |
| ☐ | `0ec9de7090264d85ae9a03d5f6f59093` | audioclip-2431 | 19.3 | 0.718 | 레벨업이나 퀘스트 완료 시 사용되는 웅장하고 경쾌한 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0ec9de7090264d85ae9a03d5f6f59093) |
| ☐ | `e5f4c86da12444e8bf34e12accefa817` | audioclip-36148 | 8.7 | 0.718 | 스테이지 클리어나 성공을 알리는 밝고 웅장한 오케스트라 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e5f4c86da12444e8bf34e12accefa817) |
| ☐ | `a245b6b409cb40ef895f1595b307df34` | audioclip-25441 | 2.4 | 0.717 | 퀘스트 완료나 레벨 업 시 들릴 법한 짧고 웅장한 브라스 풍의 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a245b6b409cb40ef895f1595b307df34) |
| ☐ | `54e6731a8e0c4572855c761c9391d58d` | audioclip-13434 | 12.1 | 0.717 | 레벨 업이나 퀘스트 완료 시 재생되는 밝고 경쾌한 금관악기 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=54e6731a8e0c4572855c761c9391d58d) |
| ☐ | `ed6f2ed374ec4dbc85c322963c4a9ba0` | audioclip-37268 | 10.2 | 0.717 | 성공이나 레벨 업을 축하하는 밝고 경쾌한 금관 악기 풍의 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ed6f2ed374ec4dbc85c322963c4a9ba0) |
| ☐ | `13841c274e5d44f8b405b8cd9fe221ef` | audioclip-3195 | 10.2 | 0.716 | 성공이나 레벨 업을 알리는 밝고 경쾌한 금관악기 풍의 팡파르 사운드 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=13841c274e5d44f8b405b8cd9fe221ef) |
| ☐ | `3816ac2e3f58475db603cc442df0c51e` | audioclip-8922 | 2.4 | 0.716 | 승리나 레벨업을 축하하는 듯한 밝고 웅장한 오케스트라 팡파르 사운드 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3816ac2e3f58475db603cc442df0c51e) |
| ☐ | `8f8a22b409cc4e4ca5a26e331d74474b` | audioclip-22478 | 12.6 | 0.716 | 레벨 업이나 퀘스트 완료 시 들릴 법한 밝고 경쾌한 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8f8a22b409cc4e4ca5a26e331d74474b) |
| ☐ | `20b32ab54bab4fada882247b81cb7225` | audioclip-5264 | 4.9 | 0.714 | 레벨 업이나 퀘스트 완료 시 재생되는 밝고 웅장한 오케스트라 풍의 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=20b32ab54bab4fada882247b81cb7225) |
| ☐ | `43d1aef974a9473aaf2efdb6edb18477` | audioclip-10742 | 2.4 | 0.706 | 레벨 업이나 퀘스트 완료 시 사용되는 밝고 웅장한 오케스트라 팡파르 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=43d1aef974a9473aaf2efdb6edb18477) |


## 기타

### 건물 파괴  <sub>(effect, 검색어: 건물이 무너지는 붕괴 폭발 소리 돌 무너짐)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `83882bc70b014c54ba9bdda1c287c302` | audioclip-20675 | 56.1 | 0.902 | 건물이 무너지거나 대규모 폭발이 일어나는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=83882bc70b014c54ba9bdda1c287c302) |
| ☐ | `c6d9aca9ac434209bcbb4002924910af` | audioclip-31198 | 3.7 | 0.897 | 무거운 돌이나 건물이 무너져 내리는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c6d9aca9ac434209bcbb4002924910af) |
| ☐ | `7e691679210d464eb705507188643bf3` | audioclip-19886 | 5.5 | 0.895 | 무거운 돌이나 건물이 무너져 내리는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7e691679210d464eb705507188643bf3) |
| ☐ | `23ed527a974143c98d81759845b8301d` | audioclip-5784 | 1.4 | 0.893 | 무거운 돌이나 건물이 무너져 내리는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=23ed527a974143c98d81759845b8301d) |
| ☐ | `ded1acf020d143ca9c2ab29b7c6407fa` | audioclip-43064 | 3 | 0.892 | 무거운 돌이나 건물이 무너지는 듯한 파괴음과 파편 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ded1acf020d143ca9c2ab29b7c6407fa) |
| ☐ | `b3a77c8691294cd4a8c3dfbbbf11b8a7` | audioclip-28193 | 1.9 | 0.891 | 무거운 돌이나 구조물이 무너져 내리는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b3a77c8691294cd4a8c3dfbbbf11b8a7) |
| ☐ | `6c54f9d67bab48ca93a2733734abc944` | audioclip-17002 | 2.5 | 0.891 | 무거운 돌이나 건물이 무너지며 파괴되는 웅장한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6c54f9d67bab48ca93a2733734abc944) |
| ☐ | `e2113941cdd943268195ca393fcfbee6` | audioclip-35528 | 3.7 | 0.891 | 무거운 돌덩이나 건물이 무너져 내리는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e2113941cdd943268195ca393fcfbee6) |
| ☐ | `2e113e32078c4a7792453e2be089b101` | audioclip-7351 | 4.2 | 0.891 | 무거운 돌이나 구조물이 무너지며 발생하는 파편 소리와 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2e113e32078c4a7792453e2be089b101) |
| ☐ | `e3a9a602c1c849d19968845b5408223e` | audioclip-35777 | 3.1 | 0.89 | 무거운 물체가 부서지거나 건물이 붕괴하며 잔해가 떨어지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e3a9a602c1c849d19968845b5408223e) |
| ☐ | `f5075b1b81ac40ffb440ebbc0c6422f7` | audioclip-38547 | 3.8 | 0.889 | 무거운 돌이나 구조물이 파괴되어 무너지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f5075b1b81ac40ffb440ebbc0c6422f7) |
| ☐ | `cfaed20951a144da830cc12b1e71d7e4` | audioclip-42911 | 3 | 0.888 | 무거운 물체가 부서지거나 건물이 무너지는 듯한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cfaed20951a144da830cc12b1e71d7e4) |
| ☐ | `7805a8996f0942929e7f37c5494b7c43` | audioclip-18789 | 2.9 | 0.888 | 무거운 바위나 구조물이 무너지며 발생하는 파괴음과 잔해 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7805a8996f0942929e7f37c5494b7c43) |
| ☐ | `4e352f6d1a2e4fd6890078545474cd39` | audioclip-12386 | 3.7 | 0.888 | 무거운 돌이나 건물이 무너져 내리는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4e352f6d1a2e4fd6890078545474cd39) |
| ☐ | `865686aae0074c0f8735303ec308cb2a` | audioclip-21080 | 6.9 | 0.888 | 무언가 크게 폭발하고 잔해가 무너져 내리는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=865686aae0074c0f8735303ec308cb2a) |
| ☐ | `4038c19ec5de413e816f8d3100a33f21` | audioclip-10180 | 3.5 | 0.887 | 무거운 돌이나 건물이 무너져 내리는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4038c19ec5de413e816f8d3100a33f21) |
| ☐ | `7984a5c1df754f069ae709cc2966b875` | audioclip-19044 | 3.8 | 0.887 | 무거운 돌이나 구조물이 무너져 내리는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7984a5c1df754f069ae709cc2966b875) |
| ☐ | `0e0200b6c78a45e0bd88b72ab6f33725` | audioclip-2292 | 3.9 | 0.886 | 무언가 폭발하며 무너져 내리는 묵직한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0e0200b6c78a45e0bd88b72ab6f33725) |
| ☐ | `346e522a22e949619d6e5936fbd5e8bc` | audioclip-8327 | 1.8 | 0.886 | 무거운 구조물이 무너지며 발생하는 거대한 파괴음과 파편 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=346e522a22e949619d6e5936fbd5e8bc) |
| ☐ | `8578a15512034b01b98b4983ae9ff824` | audioclip-20956 | 4.3 | 0.886 | 거대한 구조물이 파괴되며 발생하는 묵직한 폭발음과 잔해 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8578a15512034b01b98b4983ae9ff824) |


## 메소

### 메소 채집(곡괭이)  <sub>(effect, 검색어: 곡괭이로 바위를 캐는 소리 채굴)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `2af9c467e550455ca3ddd1ebf7ec46d6` | audioclip-6888 | 2.5 | 0.773 | 무거운 돌이나 바위가 부서지며 발생하는 강력한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2af9c467e550455ca3ddd1ebf7ec46d6) |
| ☐ | `228a6f4cdecc4a22abefb8bf7ef5f4f1` | audioclip-5569 | 2.4 | 0.769 | 무거운 바위가 부서지는 듯한 묵직하고 강력한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=228a6f4cdecc4a22abefb8bf7ef5f4f1) |
| ☐ | `3ebb8a6391bd4af1be906c000d346cbf` | audioclip-9923 | 2.9 | 0.761 | 돌이나 바위가 부서지는 묵직한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3ebb8a6391bd4af1be906c000d346cbf) |
| ☐ | `93b1f5aae2ff496ea026ae5f01e4f811` | audioclip-23100 | 0.3 | 0.758 | 돌이나 바위가 부서지는 날카로운 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=93b1f5aae2ff496ea026ae5f01e4f811) |
| ☐ | `22d2ca56cc7e4f1480c0b997507a25b0` | audioclip-5616 | 2.4 | 0.758 | 무거운 돌이나 바위가 부서지며 발생하는 묵직한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=22d2ca56cc7e4f1480c0b997507a25b0) |
| ☐ | `a9aeaadebf5b46e397cda37e8013079d` | audioclip-26601 | 1.9 | 0.757 | 무거운 돌이나 바위가 부서지며 발생하는 파편 소리와 강한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a9aeaadebf5b46e397cda37e8013079d) |
| ☐ | `4eb0fa43dff345efb6bbb4c142d50419` | audioclip-12448 | 1.1 | 0.755 | 육중한 기계가 작동하며 무언가를 갈거나 뚫는 듯한 산업용 드릴 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4eb0fa43dff345efb6bbb4c142d50419) |
| ☐ | `0005a690863742eca3347ca5fa0fc7be` | audioclip-105 | 4.4 | 0.753 | 망치나 둔기로 나무를 두드리는 듯한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0005a690863742eca3347ca5fa0fc7be) |
| ☐ | `629eb3863487464ba06e781f1fe5ee21` | audioclip-62674 | 1 | 0.749 | 돌이나 단단한 물체가 부서지는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=629eb3863487464ba06e781f1fe5ee21) |
| ☐ | `1aab5ab5047346caa23f5188f9bbffec` | audioclip-4337 | 2.7 | 0.749 | 무거운 돌이나 바위가 강력한 충격으로 인해 부서지는 묵직한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1aab5ab5047346caa23f5188f9bbffec) |
| ☐ | `4d0326325afa406998366b33d8389efa` | audioclip-12185 | 3.5 | 0.747 | 무거운 물체나 돌이 부서지는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4d0326325afa406998366b33d8389efa) |
| ☐ | `0cc525061fa544d4b7957501a6cb0acf` | audioclip-2078 | 3.7 | 0.746 | 무거운 돌이나 바위가 부서지며 무너지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0cc525061fa544d4b7957501a6cb0acf) |
| ☐ | `7805a8996f0942929e7f37c5494b7c43` | audioclip-18789 | 2.9 | 0.746 | 무거운 바위나 구조물이 무너지며 발생하는 파괴음과 잔해 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7805a8996f0942929e7f37c5494b7c43) |
| ☐ | `a7e410b1ea8f487c960127d1d62fa9be` | audioclip-26317 | 2.7 | 0.745 | 무거운 돌이나 바위가 부서지며 흩어지는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a7e410b1ea8f487c960127d1d62fa9be) |
| ☐ | `c77bc683a6ed48968c9d52beb327f8de` | audioclip-31290 | 2.7 | 0.744 | 무거운 물체가 부서지거나 바위가 깨지는 듯한 묵직한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c77bc683a6ed48968c9d52beb327f8de) |
| ☐ | `6ff1118187f447c38fd716785df69f4e` | audioclip-17543 | 3.1 | 0.743 | 무거운 돌덩이가 부서지거나 묵직하게 충돌하며 발생하는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6ff1118187f447c38fd716785df69f4e) |
| ☐ | `5f08be1c60fe4292bb6a361177c40707` | audioclip-14973 | 2.3 | 0.743 | 무거운 돌덩이가 바닥에 긁히며 밀리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5f08be1c60fe4292bb6a361177c40707) |
| ☐ | `d67616d0ea1e4659ab9ba7fd25cd7643` | audioclip-33693 | 2.8 | 0.742 | 무거운 돌덩이가 부서지거나 무너지는 육중한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d67616d0ea1e4659ab9ba7fd25cd7643) |
| ☐ | `33d976f365f74dc497541d81364cd904` | audioclip-41270 | 7.3 | 0.742 | 기계가 작동하거나 무언가를 뚫는 듯한 날카로운 금속성 마찰음과 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=33d976f365f74dc497541d81364cd904) |
| ☐ | `1e16222a5f3b4023a5a99e6f5873f403` | audioclip-4867 | 2.4 | 0.742 | 무거운 돌이나 벽이 부서지며 파편이 튀는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1e16222a5f3b4023a5a99e6f5873f403) |


## 자원

### 자원 반환(동전)  <sub>(effect, 검색어: 동전이 짤랑거리는 소리 메소 획득)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `acb0f70275b7422dbcc8a395cbbd9d28` | audioclip-27074 | 1 | 0.866 | 동전이나 금속 조각이 부딪히며 나는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=acb0f70275b7422dbcc8a395cbbd9d28) |
| ☐ | `218160d405824f1c86b679c018eaacbb` | audioclip-5386 | 1.1 | 0.811 | 동전이나 작은 금속 물체를 획득할 때 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=218160d405824f1c86b679c018eaacbb) |
| ☐ | `acc4991b0aef42d2942cb2094d871a75` | audioclip-27087 | 0.6 | 0.808 | 동전이나 작은 금속 물체를 획득할 때 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=acc4991b0aef42d2942cb2094d871a75) |
| ☐ | `541944fd38bb4e2c9a2d04a1282706b9` | audioclip-13299 | 0.6 | 0.807 | 동전이나 금속 조각을 획득할 때 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=541944fd38bb4e2c9a2d04a1282706b9) |
| ☐ | `427008dc85b143038dea58712bff7e16` | audioclip-10536 | 2.6 | 0.807 | 동전이나 금속 조각을 획득할 때 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=427008dc85b143038dea58712bff7e16) |
| ☐ | `19fa97e093ab4d98b892fc00c3153478` | audioclip-4240 | 1.5 | 0.806 | 동전이나 작은 금속 아이템을 획득할 때 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=19fa97e093ab4d98b892fc00c3153478) |
| ☐ | `4851b3bc08534a768c26c703efd10c2a` | audioclip-61245 | 1.9 | 0.804 | 작은 동전이나 금속 조각들이 부딪히며 나는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4851b3bc08534a768c26c703efd10c2a) |
| ☐ | `d692ea90e288429c8a39f03cbe9dc6fc` | audioclip-33712 | 4 | 0.803 | 동전이나 작은 금속 물체가 부딪히며 나는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d692ea90e288429c8a39f03cbe9dc6fc) |
| ☐ | `3a7d2cff5a744e25b45ce525ed426bab` | audioclip-62316 | 0.7 | 0.803 | 동전이나 작은 금속 아이템을 획득할 때 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3a7d2cff5a744e25b45ce525ed426bab) |
| ☐ | `09ecbff8403c45a89b1d51921ac7ac17` | audioclip-1656 | 1.2 | 0.802 | 동전이나 작은 금속 아이템을 획득할 때 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=09ecbff8403c45a89b1d51921ac7ac17) |
| ☐ | `8e315aea162244f18b5a08cefd21a3fd` | audioclip-22285 | 0.7 | 0.8 | 동전이나 금속 아이템을 획득할 때 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8e315aea162244f18b5a08cefd21a3fd) |
| ☐ | `dbfaab34d3d844c19e8ee77b48156c5e` | audioclip-34590 | 0.6 | 0.8 | 동전이나 작은 금속 아이템을 획득할 때 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dbfaab34d3d844c19e8ee77b48156c5e) |
| ☐ | `8c19f98ce6f44f208a82eba8f012bcd3` | audioclip-21961 | 1.4 | 0.8 | 동전이나 작은 금속 아이템을 획득할 때 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8c19f98ce6f44f208a82eba8f012bcd3) |
| ☐ | `3e60904a80e24a7eb78c07f184273ca0` | audioclip-9866 | 0.8 | 0.8 | 동전이나 작은 금속 아이템을 획득할 때 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e60904a80e24a7eb78c07f184273ca0) |
| ☐ | `ac3c30b518b34905b80195a783979e29` | audioclip-26994 | 1.8 | 0.8 | 동전이나 금화를 획득할 때 발생하는 짤랑거리는 금속음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ac3c30b518b34905b80195a783979e29) |
| ☐ | `f464d1104047450e80011e252be77224` | audioclip-38433 | 1.5 | 0.799 | 동전이나 금화를 획득할 때 발생하는 짤랑거리는 금속음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f464d1104047450e80011e252be77224) |
| ☐ | `06ad6556a8ae4df1b6e881892509bee8` | audioclip-1137 | 1.7 | 0.799 | 동전이나 작은 금속 아이템을 획득할 때 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=06ad6556a8ae4df1b6e881892509bee8) |
| ☐ | `1be5f6cd5841462c8dad511abc74a8be` | audioclip-4532 | 2 | 0.798 | 동전이나 작은 금속 물체가 부딪히는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1be5f6cd5841462c8dad511abc74a8be) |
| ☐ | `cb7097a0c69a4b5a88d0b865ffe12be4` | audioclip-31914 | 0.5 | 0.798 | 동전이나 작은 금속 물체가 부딪히는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cb7097a0c69a4b5a88d0b865ffe12be4) |
| ☐ | `19f45ea4d8eb46b1ba4aed7c006c0b69` | audioclip-4227 | 0.9 | 0.798 | 동전이나 금속 조각이 부딪히며 발생하는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=19f45ea4d8eb46b1ba4aed7c006c0b69) |


## 에르다

### 에르다 획득  <sub>(effect, 검색어: 반짝이는 마법 아이템 획득 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `daba7d3fcf88417091c6bf987e9f2314` | audioclip-34390 | 1.3 | 0.886 | 마법적이고 반짝이는 느낌의 UI 효과음 또는 아이템 획득음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=daba7d3fcf88417091c6bf987e9f2314) |
| ☐ | `128bb92077ca45c7bcf9e27c79d43700` | audioclip-3039 | 0.5 | 0.882 | 반짝이는 마법 효과음 또는 아이템 획득 시 발생하는 밝은 톤의 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=128bb92077ca45c7bcf9e27c79d43700) |
| ☐ | `9674cf39456b4f5f993cfd26437efb5e` | audioclip-23502 | 1.1 | 0.882 | 반짝이는 마법 효과음이나 아이템 획득 시 발생하는 밝고 경쾌한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9674cf39456b4f5f993cfd26437efb5e) |
| ☐ | `d4445e60704a48bbb19f290e2e3e424b` | audioclip-33325 | 2.1 | 0.881 | 밝고 반짝이는 느낌의 마법적인 UI 효과음 또는 아이템 획득 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d4445e60704a48bbb19f290e2e3e424b) |
| ☐ | `8a09334b1891479d93dc41fcfc2fe5d7` | audioclip-21639 | 0.4 | 0.88 | 마법이 발동되거나 아이템을 획득할 때 들리는 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8a09334b1891479d93dc41fcfc2fe5d7) |
| ☐ | `2a53d01240cf4a7892a920b7f51d0316` | audioclip-41187 | 0.4 | 0.88 | 반짝이는 느낌의 마법적인 UI 알림음 또는 아이템 획득 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a53d01240cf4a7892a920b7f51d0316) |
| ☐ | `77a8c358ae674971993ebf685ee937fd` | audioclip-18734 | 0.8 | 0.878 | 반짝이는 마법 효과음이나 아이템 획득 시 들리는 신비로운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=77a8c358ae674971993ebf685ee937fd) |
| ☐ | `ca4d64daa3884efd80db0f76acb0ccf0` | audioclip-60312 | 0.5 | 0.873 | 마법적이고 반짝이는 느낌의 효과음으로, 성공이나 아이템 획득 시 사용하기 적합한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ca4d64daa3884efd80db0f76acb0ccf0) |
| ☐ | `33c8b46a0316464b936e78f982c20ad3` | audioclip-61936 | 0.7 | 0.872 | 반짝이는 마법 효과음으로, 버프 부여나 아이템 획득 시 사용하기 적합한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=33c8b46a0316464b936e78f982c20ad3) |
| ☐ | `06c9e0c97df549ea9dca84d3cd79d1f4` | audioclip-1154 | 0.4 | 0.872 | 반짝이는 느낌의 마법 같은 UI 알림음 또는 아이템 획득 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=06c9e0c97df549ea9dca84d3cd79d1f4) |
| ☐ | `3eae29a2f12747e8bc271f73956e3e32` | audioclip-9915 | 1.1 | 0.87 | 마법이 발동되거나 신비로운 아이템을 획득할 때 들릴 법한 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3eae29a2f12747e8bc271f73956e3e32) |
| ☐ | `e8dab55e47dd40659ded6cbd8f57ff36` | audioclip-43179 | 2.1 | 0.868 | 반짝이는 느낌의 마법적인 UI 효과음 또는 아이템 획득음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e8dab55e47dd40659ded6cbd8f57ff36) |
| ☐ | `40b70e7052e4452c9237996c917d6422` | audioclip-61991 | 3 | 0.867 | 반짝이는 느낌의 밝고 경쾌한 UI 알림음 또는 아이템 획득 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=40b70e7052e4452c9237996c917d6422) |
| ☐ | `996e02e598d9489e8a59e9d3aee1470d` | audioclip-23973 | 1.2 | 0.867 | 반짝이는 느낌의 마법적인 UI 효과음 또는 아이템 획득음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=996e02e598d9489e8a59e9d3aee1470d) |
| ☐ | `7ddd3105e8744005b185c4e8e6853219` | audioclip-19793 | 1 | 0.866 | 반짝이는 느낌의 마법적인 UI 알림음 또는 아이템 획득 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7ddd3105e8744005b185c4e8e6853219) |
| ☐ | `78f7f660e6004cae831f29528e56ef33` | audioclip-18947 | 0.5 | 0.866 | 반짝이는 느낌의 마법적인 UI 알림 또는 아이템 획득 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=78f7f660e6004cae831f29528e56ef33) |
| ☐ | `8bbc2030ac9042c08887e7b5eb451c84` | audioclip-21904 | 1.7 | 0.865 | 마법적인 느낌의 반짝이는 효과음으로, 스킬 사용이나 아이템 획득 시 적합한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8bbc2030ac9042c08887e7b5eb451c84) |
| ☐ | `bb67a125a4104e258c6da68a22f26c94` | audioclip-29388 | 0.5 | 0.864 | 밝고 반짝이는 느낌의 마법적인 UI 알림음 또는 아이템 획득 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bb67a125a4104e258c6da68a22f26c94) |
| ☐ | `bc1c11b535a34a29a11b1f1552ae3f70` | audioclip-29489 | 1.9 | 0.864 | 마법적인 느낌의 반짝이는 효과음으로, 버프 획득이나 아이템 생성 시 사용하기 적합한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bc1c11b535a34a29a11b1f1552ae3f70) |
| ☐ | `767b7de0d1e9447b91edbaeed49e7c2b` | audioclip-18554 | 2.7 | 0.864 | 마법이 발동되거나 아이템이 빛나는 듯한 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=767b7de0d1e9447b91edbaeed49e7c2b) |


## 인구

### 인구 한도 경고  <sub>(effect, 검색어: 경고음 한도 도달 알림 UI 경고)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `762421119c1148f18d592554cfde4d9c` | audioclip-18502 | 3.1 | 0.804 | 높은 톤으로 반복해서 울리는 전자식 경고음 또는 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=762421119c1148f18d592554cfde4d9c) |
| ☐ | `7adc4731e2d04522a411012f77351d6a` | audioclip-60047 | 12.1 | 0.799 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 알람 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7adc4731e2d04522a411012f77351d6a) |
| ☐ | `5d704b3c83504094b96febc1c936239f` | audioclip-14711 | 1.9 | 0.798 | 비상 상황이나 경고를 알리는 날카로운 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5d704b3c83504094b96febc1c936239f) |
| ☐ | `1bee698506af44c4a1f84b01be7373a2` | audioclip-41034 | 1 | 0.797 | 경고나 알림을 나타내는 날카롭고 반복적인 전자 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1bee698506af44c4a1f84b01be7373a2) |
| ☐ | `98e9c05088db4dbc853dfb4e56734220` | audioclip-23888 | 1.9 | 0.796 | 경고나 비상 상황을 알리는 날카롭고 반복적인 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=98e9c05088db4dbc853dfb4e56734220) |
| ☐ | `540ef7865b7943128cbca004ec5c10ae` | audioclip-13281 | 3.1 | 0.792 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=540ef7865b7943128cbca004ec5c10ae) |
| ☐ | `e5397d34e85e4a3caf593748afbf030f` | audioclip-36024 | 4.8 | 0.787 | 비상 상황이나 시스템 경고를 알리는 날카로운 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e5397d34e85e4a3caf593748afbf030f) |
| ☐ | `a74d1652120942c9a5ca3afcdaedf33e` | audioclip-26214 | 1.9 | 0.785 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a74d1652120942c9a5ca3afcdaedf33e) |
| ☐ | `652025e1107345aaa52a2e06681f284c` | audioclip-15911 | 4.1 | 0.782 | 전자적인 알람이나 경고를 나타내는 반복적인 고음의 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=652025e1107345aaa52a2e06681f284c) |
| ☐ | `d54077cf43a144c2aa6ad0a17a2789a0` | audioclip-33491 | 10.7 | 0.778 | 긴박한 상황이나 경고를 알리는 반복적인 고음의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d54077cf43a144c2aa6ad0a17a2789a0) |
| ☐ | `81122a7025f84ffbb31b3989476ba080` | audioclip-20301 | 0.7 | 0.775 | 짧고 반복적인 전자음 형태의 UI 알림 또는 경고음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=81122a7025f84ffbb31b3989476ba080) |
| ☐ | `40fb4b84ca7b4df399b36fd7d0475d24` | audioclip-10277 | 1.2 | 0.767 | UI 알림이나 버튼 클릭 시 발생하는 높은 톤의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=40fb4b84ca7b4df399b36fd7d0475d24) |
| ☐ | `839d3d38f22e4e87bf0a87076761a6a8` | audioclip-20685 | 10.7 | 0.767 | 일정한 간격으로 반복되는 디지털 타이머 또는 경고 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=839d3d38f22e4e87bf0a87076761a6a8) |
| ☐ | `c8bee68c2cdb44d0951aabfcd1d05858` | audioclip-31490 | 1.5 | 0.765 | UI 알림이나 아이템 획득 시 발생하는 짧고 높은 톤의 딩 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c8bee68c2cdb44d0951aabfcd1d05858) |
| ☐ | `dd35ce28ffb843d2b87f38e7b01258e0` | audioclip-34753 | 0.6 | 0.765 | 퀘스트 알림이나 새로운 정보가 나타날 때 발생하는 맑은 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dd35ce28ffb843d2b87f38e7b01258e0) |
| ☐ | `20937b2af6df495b9eb6730aa67e2d51` | audioclip-5251 | 1 | 0.764 | UI 알림이나 아이템 획득 시 발생하는 짧고 높은 톤의 금속성 딩 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=20937b2af6df495b9eb6730aa67e2d51) |
| ☐ | `69d03b948a624872b2aad80dc8f5238c` | audioclip-16606 | 0.8 | 0.759 | UI 알림이나 아이템 획득 시 발생하는 짧고 높은 톤의 금속성 핑 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=69d03b948a624872b2aad80dc8f5238c) |
| ☐ | `0501b711b2a2460d9032149ada6b3e22` | audioclip-870 | 6.1 | 0.758 | 시스템 알림이나 카운트다운에 사용되는 규칙적인 전자 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0501b711b2a2460d9032149ada6b3e22) |
| ☐ | `5407688385eb42ac9d308f413c469bdd` | audioclip-13277 | 1.5 | 0.757 | 높은 음의 디지털 비프음이 연속적으로 발생하는 UI 알림 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5407688385eb42ac9d308f413c469bdd) |
| ☐ | `f939d19915ac419a97e283709e419553` | audioclip-39147 | 2.9 | 0.756 | UI 메뉴 선택이나 알림 시 발생하는 밝고 짧은 딩 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f939d19915ac419a97e283709e419553) |


## 근접

### 근접-버섯 통통  <sub>(effect, 검색어: 통통 튀는 귀여운 타격음 슬라임 버섯)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `6e4f704a85e64fc3a7485c8d1a15e650` | audioclip-17297 | 0.7 | 0.843 | 슬라임 같은 작고 귀여운 몬스터가 점프하거나 움직일 때 나는 통통 튀는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6e4f704a85e64fc3a7485c8d1a15e650) |
| ☐ | `059d6fce824247e08fa4e6c59ee39d0d` | audioclip-40792 | 0.5 | 0.838 | 슬라임과 같은 작은 몬스터가 공격을 받았을 때 나는 귀여운 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=059d6fce824247e08fa4e6c59ee39d0d) |
| ☐ | `81976af07e8e4cef9014498978f3157f` | audioclip-20377 | 1 | 0.825 | 슬라임이나 작은 몬스터가 통통 튀며 점프하는 귀여운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=81976af07e8e4cef9014498978f3157f) |
| ☐ | `fa933e320c2c49f195ae039f3eb8692b` | audioclip-39353 | 0.6 | 0.818 | 슬라임이나 작은 생명체가 통통 튀어 오르는 듯한 귀엽고 익살스러운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fa933e320c2c49f195ae039f3eb8692b) |
| ☐ | `731c1fef91e94ecfb932f9170ca81a23` | audioclip-18034 | 4.9 | 0.815 | 슬라임이나 귀여운 생명체가 통통 튀며 점프하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=731c1fef91e94ecfb932f9170ca81a23) |
| ☐ | `c966fde4a0204b1fa9aba5b0ad9d7ad1` | audioclip-42849 | 0.4 | 0.812 | 슬라임이나 생명체가 무언가를 때리거나 부딪힐 때 발생하는 끈적하고 젖은 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c966fde4a0204b1fa9aba5b0ad9d7ad1) |
| ☐ | `710b6250b8d7415580cd4db255d83bd0` | audioclip-17723 | 1 | 0.808 | 슬라임이나 작은 몬스터가 움직이거나 소리를 내는 귀엽고 톡 쏘는 듯한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=710b6250b8d7415580cd4db255d83bd0) |
| ☐ | `58d56b4524964cb495e2aaf2e372a40e` | audioclip-14031 | 0.8 | 0.805 | 슬라임이나 액체 형태의 몬스터가 피격되거나 터지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58d56b4524964cb495e2aaf2e372a40e) |
| ☐ | `f333783b12634fe2a1564563c3db6c3e` | audioclip-38241 | 0.7 | 0.804 | 슬라임과 같은 생명체가 움직이거나 착지할 때 발생하는 끈적하고 말랑한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f333783b12634fe2a1564563c3db6c3e) |
| ☐ | `61013b1ef2c14903bd3a1d455145c2ec` | audioclip-15278 | 2.3 | 0.803 | 몬스터가 피격되거나 쓰러질 때 발생하는 익살스럽고 귀여운 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=61013b1ef2c14903bd3a1d455145c2ec) |
| ☐ | `41ed805d0730492188763926af4ab0b3` | audioclip-10448 | 1.1 | 0.8 | 슬라임과 같은 작고 귀여운 몬스터가 점프하거나 튀어 오를 때 나는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=41ed805d0730492188763926af4ab0b3) |
| ☐ | `4ebb1ed8b79f4141bc27b559fecad738` | audioclip-12465 | 2.5 | 0.797 | 작은 생명체나 캐릭터가 가볍게 점프할 때 발생하는 탄력 있는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4ebb1ed8b79f4141bc27b559fecad738) |
| ☐ | `9f994160319642388032e3b45cb18cb2` | audioclip-24973 | 0.7 | 0.796 | 슬라임 같은 몬스터가 점프하거나 움직일 때 나는 끈적하고 귀여운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9f994160319642388032e3b45cb18cb2) |
| ☐ | `129626cd0447441099aa0c678722a299` | audioclip-3043 | 0.8 | 0.795 | 슬라임이나 액체 형태의 몬스터가 내는 끈적하고 축축한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=129626cd0447441099aa0c678722a299) |
| ☐ | `6c6a3cc85fef4860aafa0328e0514dde` | audioclip-17019 | 1.2 | 0.793 | 몬스터가 타격을 받거나 터지는 듯한 유기적인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6c6a3cc85fef4860aafa0328e0514dde) |
| ☐ | `98c4029ea6af4a50b49eb2ee4cab92e1` | audioclip-23864 | 0.6 | 0.793 | 몬스터가 피격되었을 때 발생하는 짧고 말랑한 느낌의 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=98c4029ea6af4a50b49eb2ee4cab92e1) |
| ☐ | `c224d69715004904a67fa49cd83ff23f` | audioclip-30434 | 1.2 | 0.79 | 몬스터가 피격되거나 터질 때 발생하는 축축하고 유기적인 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c224d69715004904a67fa49cd83ff23f) |
| ☐ | `09adb86113c44c8e8ced9443f79f2601` | audioclip-1610 | 0.9 | 0.789 | 작은 생명체가 통통 튀거나 착지할 때 발생하는 귀엽고 쫀득한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=09adb86113c44c8e8ced9443f79f2601) |
| ☐ | `2b83d579cb1a4a3eb23fc4ba03972916` | audioclip-6973 | 1.9 | 0.789 | 액체가 튀거나 슬라임 같은 생명체가 부딪힐 때 발생하는 젖은 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2b83d579cb1a4a3eb23fc4ba03972916) |
| ☐ | `837d859bb6ed478f97142e79527dc7ca` | audioclip-20660 | 0.5 | 0.786 | 슬라임이나 작은 생명체가 움직이거나 점프할 때 발생하는 끈적하고 가벼운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=837d859bb6ed478f97142e79527dc7ca) |

### 근접-멧돼지 돌진  <sub>(effect, 검색어: 멧돼지 돌진 충돌 쿵 타격)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `f95b26592eda4a058391cdf0270b8a5e` | audioclip-39165 | 1.9 | 0.772 | 묵직하고 강력한 타격음 또는 충돌음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f95b26592eda4a058391cdf0270b8a5e) |
| ☐ | `2a9355c1cd4b4f57b9a4ab4c115c4e73` | audioclip-6815 | 2.4 | 0.771 | 무언가에 강하게 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a9355c1cd4b4f57b9a4ab4c115c4e73) |
| ☐ | `aef113052d92476480ad2df107cd58da` | audioclip-27446 | 1.2 | 0.77 | 무겁고 둔탁한 타격음 또는 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=aef113052d92476480ad2df107cd58da) |
| ☐ | `0e0bd72b3e034e2dbc90fa4c52622792` | audioclip-2294 | 0.7 | 0.768 | 무언가에 강하게 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0e0bd72b3e034e2dbc90fa4c52622792) |
| ☐ | `67aecfb8f0264fc09c5327c940b4b438` | audioclip-16297 | 0.9 | 0.768 | 무언가에 강하게 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=67aecfb8f0264fc09c5327c940b4b438) |
| ☐ | `67330b670aad4ea6b52ae8038380a777` | audioclip-16220 | 0.9 | 0.768 | 무언가에 강하게 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=67330b670aad4ea6b52ae8038380a777) |
| ☐ | `1f83b022221b4b23b130311e9e56379d` | audioclip-5071 | 1.4 | 0.767 | 무거운 물체가 부딪히거나 타격할 때 발생하는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1f83b022221b4b23b130311e9e56379d) |
| ☐ | `d335ae253ce74d4a8845a22123ece5b5` | audioclip-33143 | 0.5 | 0.767 | 무겁고 둔탁한 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d335ae253ce74d4a8845a22123ece5b5) |
| ☐ | `0ddf78bd1f174768bc74b133ac199cf5` | audioclip-2273 | 0.8 | 0.767 | 무언가에 강하게 부딪히거나 타격하는 둔탁한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0ddf78bd1f174768bc74b133ac199cf5) |
| ☐ | `9aba0400aaf84e989baa3cbfb147b241` | audioclip-24190 | 0.6 | 0.767 | 묵직하고 둔탁한 느낌의 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9aba0400aaf84e989baa3cbfb147b241) |
| ☐ | `a9d79a821e584ee5a967b22fd5d3ca20` | audioclip-26634 | 3.1 | 0.766 | 무거운 물체가 강하게 부딪히는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a9d79a821e584ee5a967b22fd5d3ca20) |
| ☐ | `3f4bc1588e5a4b2da28cf92b63994f06` | audioclip-10016 | 0.9 | 0.766 | 무언가에 강하게 부딪히는 둔탁하고 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3f4bc1588e5a4b2da28cf92b63994f06) |
| ☐ | `200c2bb0806a4a2fa298d36b07673ab2` | audioclip-5165 | 1.2 | 0.765 | 무겁고 둔탁한 타격음 또는 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=200c2bb0806a4a2fa298d36b07673ab2) |
| ☐ | `1e233afcc42b4d3580174f0bdb2b7ac0` | audioclip-4872 | 1.9 | 0.765 | 무겁고 둔탁한 타격음 또는 무언가 강하게 부딪히는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1e233afcc42b4d3580174f0bdb2b7ac0) |
| ☐ | `efab85c6cfa247c285d612fa5c652f5f` | audioclip-37657 | 0.8 | 0.765 | 무언가를 강하게 때리는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=efab85c6cfa247c285d612fa5c652f5f) |
| ☐ | `3d9f064a69a9436a8639ad66d2a16a1b` | audioclip-9762 | 0.9 | 0.765 | 무거운 물체가 강하게 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3d9f064a69a9436a8639ad66d2a16a1b) |
| ☐ | `62ee1d268500430caee76a322d976722` | audioclip-15553 | 3.7 | 0.765 | 무거운 물체가 강하게 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=62ee1d268500430caee76a322d976722) |
| ☐ | `61a02acf5838469f9a800e39f4f32b4b` | audioclip-15370 | 2.1 | 0.764 | 묵직하고 강한 타격음 또는 무거운 물체가 부딪히는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=61a02acf5838469f9a800e39f4f32b4b) |
| ☐ | `c85fcf78a5024aa7a14d830d551e6add` | audioclip-31436 | 0.5 | 0.764 | 무언가를 강하게 때리거나 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c85fcf78a5024aa7a14d830d551e6add) |
| ☐ | `d15b6ab16b63435ba5289244fd37bc9e` | audioclip-32866 | 1 | 0.764 | 무언가를 강하게 때리거나 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d15b6ab16b63435ba5289244fd37bc9e) |

### 근접-기사 검격  <sub>(effect, 검색어: 검으로 베는 소리 칼날 휘두르기)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `0777dcc92e734fcc935d1c31f056f8c8` | audioclip-1270 | 4.6 | 0.888 | 검을 휘둘러 공기를 가르며 날카롭게 베는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0777dcc92e734fcc935d1c31f056f8c8) |
| ☐ | `2667330e586c4342ba2ba26730e94a1e` | audioclip-41146 | 1.3 | 0.886 | 검을 휘두르거나 날카로운 무기로 베는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2667330e586c4342ba2ba26730e94a1e) |
| ☐ | `7698a45502f4455ab9027204e17fc341` | audioclip-18582 | 2.7 | 0.883 | 검을 휘둘러 공기를 가르거나 금속 물체를 베는 날카로운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7698a45502f4455ab9027204e17fc341) |
| ☐ | `dc9a1465d9cc44c3b374fdf73ad0201f` | audioclip-34665 | 2.5 | 0.881 | 날카로운 금속 칼날이 공기를 가르며 베는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dc9a1465d9cc44c3b374fdf73ad0201f) |
| ☐ | `7830e3e31c9b40df956395ff78d6b4a9` | audioclip-18816 | 2.2 | 0.881 | 검을 휘둘러 공기를 가르거나 적을 베는 날카로운 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7830e3e31c9b40df956395ff78d6b4a9) |
| ☐ | `5dfa3163f82349709954d9e5d6d7a523` | audioclip-14800 | 1.1 | 0.88 | 검을 휘둘러 공기를 가르거나 적을 베는 날카로운 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5dfa3163f82349709954d9e5d6d7a523) |
| ☐ | `8c560e52723d442093b681fc2cb93251` | audioclip-21990 | 2.6 | 0.88 | 검을 휘둘러 공기를 가르거나 적을 베는 날카로운 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8c560e52723d442093b681fc2cb93251) |
| ☐ | `6936fa0e2fbd4b1a8c30520da606f34a` | audioclip-16532 | 2.6 | 0.88 | 검을 휘둘러 공기를 가르거나 적을 베는 날카로운 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6936fa0e2fbd4b1a8c30520da606f34a) |
| ☐ | `2c29dd92f9d3475f8bf7f269fb112f1c` | audioclip-7065 | 1.9 | 0.879 | 날카로운 칼날로 무언가를 빠르게 베는 듯한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2c29dd92f9d3475f8bf7f269fb112f1c) |
| ☐ | `4c4fe6e804d248339cb011e4956ec0df` | audioclip-12071 | 0.8 | 0.879 | 검을 휘둘러 공기를 가르거나 적을 베는 날카로운 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4c4fe6e804d248339cb011e4956ec0df) |
| ☐ | `427cfda7ac0b4dccb8456e45cff30226` | audioclip-10542 | 2 | 0.878 | 날카로운 칼날로 무언가를 베는 듯한 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=427cfda7ac0b4dccb8456e45cff30226) |
| ☐ | `d119ae57826a4b44ae0b77d7e15c4faf` | audioclip-32823 | 1.1 | 0.877 | 검을 휘둘러 공기를 가르는 날카로운 공격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d119ae57826a4b44ae0b77d7e15c4faf) |
| ☐ | `cf6999111dc246fe9dcf7c626d61c03a` | audioclip-62514 | 1 | 0.876 | 검을 휘둘러 공기를 가르거나 적을 베는 날카로운 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cf6999111dc246fe9dcf7c626d61c03a) |
| ☐ | `3bd715819c3143f9942110fa43640243` | audioclip-9496 | 1.3 | 0.876 | 검을 휘둘러 공기를 가르거나 적을 베는 날카로운 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3bd715819c3143f9942110fa43640243) |
| ☐ | `d25280ddda8a454cb3a8420899fd965d` | audioclip-33009 | 3.1 | 0.876 | 검을 휘둘러 공기를 가르며 날카롭게 베는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d25280ddda8a454cb3a8420899fd965d) |
| ☐ | `62b11e6ad5ae41eaa50e1d78b0822fd1` | audioclip-15521 | 3.4 | 0.876 | 검을 휘둘러 공기를 가르며 날카롭게 베는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=62b11e6ad5ae41eaa50e1d78b0822fd1) |
| ☐ | `88bacb3230f547ef9d49578ba41455c1` | audioclip-21443 | 1.6 | 0.875 | 검을 휘둘러 공기를 가르거나 적을 베는 날카로운 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=88bacb3230f547ef9d49578ba41455c1) |
| ☐ | `58c9263ac62c40b38bf8e2cb7a6a008d` | audioclip-14018 | 1.4 | 0.875 | 검을 휘둘러 공기를 가르거나 적을 베는 날카로운 물리 공격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58c9263ac62c40b38bf8e2cb7a6a008d) |
| ☐ | `75dcad7217ae4faf86800698edc6dc5b` | audioclip-18474 | 1.8 | 0.875 | 검으로 공기를 가르거나 적을 베는 날카로운 휘두름 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=75dcad7217ae4faf86800698edc6dc5b) |
| ☐ | `25f528fa3391460293021cbb808f92ce` | audioclip-6116 | 1.4 | 0.874 | 검이나 날카로운 무기를 빠르게 휘두르는 날카로운 베기 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=25f528fa3391460293021cbb808f92ce) |

### 근접-골렘 강타  <sub>(effect, 검색어: 거대한 바위 주먹 묵직한 충격 강타)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `fa2a319550d042e5a4d0520ffe8088f3` | audioclip-39290 | 3.5 | 0.815 | 무거운 물체가 지면을 강하게 내리쳐 파괴되는 듯한 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fa2a319550d042e5a4d0520ffe8088f3) |
| ☐ | `228a6f4cdecc4a22abefb8bf7ef5f4f1` | audioclip-5569 | 2.4 | 0.812 | 무거운 바위가 부서지는 듯한 묵직하고 강력한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=228a6f4cdecc4a22abefb8bf7ef5f4f1) |
| ☐ | `83861dd485be41b483b435323080704a` | audioclip-20664 | 2.7 | 0.806 | 강력한 충격과 함께 바닥이 파괴되는 듯한 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=83861dd485be41b483b435323080704a) |
| ☐ | `2af9c467e550455ca3ddd1ebf7ec46d6` | audioclip-6888 | 2.5 | 0.806 | 무거운 돌이나 바위가 부서지며 발생하는 강력한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2af9c467e550455ca3ddd1ebf7ec46d6) |
| ☐ | `dfd1aaacbb714df2aab1f35f26d8a4c0` | audioclip-35149 | 3.8 | 0.805 | 무거운 물체가 바닥에 강하게 부딪히는 묵직한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dfd1aaacbb714df2aab1f35f26d8a4c0) |
| ☐ | `59f05857f9ac476b994c7c5786812704` | audioclip-14187 | 1.6 | 0.798 | 강력한 물리적 충격이나 폭발을 연상시키는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=59f05857f9ac476b994c7c5786812704) |
| ☐ | `17cd617103834422a722f52aba8a32de` | audioclip-3879 | 1.7 | 0.794 | 무거운 물체나 주먹으로 강하게 타격하는 묵직한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=17cd617103834422a722f52aba8a32de) |
| ☐ | `1b593f96181946cfbc3d2624dae40bb1` | audioclip-4444 | 2.1 | 0.785 | 강력한 힘으로 지면을 강타하거나 폭발하는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1b593f96181946cfbc3d2624dae40bb1) |
| ☐ | `3a5d1aae2212450195cd4cfcba263754` | audioclip-9269 | 3.5 | 0.785 | 강한 힘으로 내려치거나 주먹으로 때리는 듯한 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3a5d1aae2212450195cd4cfcba263754) |
| ☐ | `6eb7cb18fd2143d38741c64aba7c346b` | audioclip-17348 | 2.1 | 0.782 | 무거운 물체가 부서지거나 강하게 충돌하는 묵직한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6eb7cb18fd2143d38741c64aba7c346b) |
| ☐ | `86017faf48ba4a2391412d9cc977005e` | audioclip-21036 | 2.6 | 0.782 | 무거운 물체가 강하게 부딪히거나 파괴되는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=86017faf48ba4a2391412d9cc977005e) |
| ☐ | `0042633e9f754d1b9333ee3dad4e614d` | audioclip-134 | 1.6 | 0.782 | 무거운 물체가 강하게 부딪히거나 부서지는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0042633e9f754d1b9333ee3dad4e614d) |
| ☐ | `d334a0b9f0234bfaba8b2a16d3614151` | audioclip-33142 | 1.5 | 0.781 | 무겁고 둔탁한 물리적 충격음 또는 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d334a0b9f0234bfaba8b2a16d3614151) |
| ☐ | `19f7056153a74b14b88d0a14239b7fc1` | audioclip-60809 | 3.3 | 0.781 | 강력한 폭발과 함께 잔해가 흩어지는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=19f7056153a74b14b88d0a14239b7fc1) |
| ☐ | `dfd8b1454ae9417c961a41c916a25ce2` | audioclip-35151 | 2.7 | 0.78 | 거대한 괴물이나 기계가 바닥을 내리치는 듯한 묵직하고 강력한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dfd8b1454ae9417c961a41c916a25ce2) |
| ☐ | `d1a995196026434ea156329a843b7465` | audioclip-32907 | 3 | 0.779 | 무거운 돌이나 바위가 지면에 강하게 충돌하며 부서지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d1a995196026434ea156329a843b7465) |
| ☐ | `079d1a8e691c4681ae81afcddd5330e6` | audioclip-1276 | 2.4 | 0.779 | 강력한 힘으로 지면을 내리치거나 폭발하는 듯한 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=079d1a8e691c4681ae81afcddd5330e6) |
| ☐ | `7194ca2cd57e4947876208ed73c5cb44` | audioclip-17796 | 4.5 | 0.779 | 무거운 바위나 물체가 지면에 강하게 충돌하며 발생하는 묵직한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7194ca2cd57e4947876208ed73c5cb44) |
| ☐ | `6604374ce6f5459ab361bd6eec99c52d` | audioclip-16043 | 1.7 | 0.778 | 무거운 금속 물체가 강하게 부딪히는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6604374ce6f5459ab361bd6eec99c52d) |
| ☐ | `fe746e6543ce40219af5b1d5f8fd7beb` | audioclip-39992 | 0.4 | 0.777 | 주먹으로 치는 듯한 짧고 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fe746e6543ce40219af5b1d5f8fd7beb) |


## 원거리

### 원거리-투척  <sub>(effect, 검색어: 물체를 휙 던지는 소리 투척)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `66c54ce7c4cf40d48b22c4cd942a01c9` | audioclip-16157 | 2.7 | 0.787 | 무언가를 빠르게 던지거나 발사할 때 발생하는 바람을 가르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=66c54ce7c4cf40d48b22c4cd942a01c9) |
| ☐ | `d241be0f5d4d429ba2ce750b3d02eab9` | audioclip-33000 | 3.5 | 0.782 | 날카로운 물체가 공기를 가르며 빠르게 날아가는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d241be0f5d4d429ba2ce750b3d02eab9) |
| ☐ | `2b378c682b7d4f34b0366972061b899c` | audioclip-6918 | 1.8 | 0.775 | 표창이나 작은 칼날을 빠르게 던지는 날카로운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2b378c682b7d4f34b0366972061b899c) |
| ☐ | `58778cf5b5de43fb831b90c1677ead4d` | audioclip-62334 | 1.8 | 0.767 | 무언가를 빠르게 던지거나 발사할 때 발생하는 마법적인 투사체 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58778cf5b5de43fb831b90c1677ead4d) |
| ☐ | `ca4c49b20de341d4bb9dea4c1c9c68fc` | audioclip-75 | 0.5 | 0.766 | 금속 무기가 부딪히거나 단단한 물체에 타격되는 날카로운 금속음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ca4c49b20de341d4bb9dea4c1c9c68fc) |
| ☐ | `6a232f2ea9334280a85c544bdb15551f` | audioclip-16656 | 1.4 | 0.765 | 검을 휘둘러 공기를 가르는 날카롭고 빠른 금속성 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6a232f2ea9334280a85c544bdb15551f) |
| ☐ | `41a8b196ad864ae1844abdcdbbdd69fa` | audioclip-10405 | 1.1 | 0.764 | 마법 투사체가 날아가서 가볍게 부딪히는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=41a8b196ad864ae1844abdcdbbdd69fa) |
| ☐ | `e5d0f4debb894e9fb9e6fb27f0d75760` | audioclip-36121 | 3.2 | 0.758 | 표창이나 작은 발사체를 빠르게 던질 때 나는 날카로운 바람 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e5d0f4debb894e9fb9e6fb27f0d75760) |
| ☐ | `b19660fd48724dc99038b965a23ec6fb` | audioclip-27849 | 2.4 | 0.756 | 무언가를 빠르게 발사하거나 던질 때 발생하는 날카로운 투사체 발사음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b19660fd48724dc99038b965a23ec6fb) |
| ☐ | `5b6b777f0e564b84aa09fe68c9115535` | audioclip-14407 | 1.1 | 0.75 | 검으로 무언가를 날카롭게 베거나 타격하는 금속성 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5b6b777f0e564b84aa09fe68c9115535) |
| ☐ | `6dcf25bc078c4814b47adb6b374afe63` | audioclip-17218 | 1.5 | 0.748 | 무언가를 빠르게 던지거나 발사하는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6dcf25bc078c4814b47adb6b374afe63) |
| ☐ | `7777128da0904a0dbf7eba19cd68db4d` | audioclip-18699 | 1.7 | 0.738 | 나무 상자나 물체가 부서지는 듯한 묵직한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7777128da0904a0dbf7eba19cd68db4d) |
| ☐ | `8c04cf239d704b8b8f7d3b404a160bbe` | audioclip-21948 | 8.1 | 0.738 | 빠르게 발사되는 마법 에너지 투사체 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8c04cf239d704b8b8f7d3b404a160bbe) |
| ☐ | `4e591e5199b7413b9771f2e67cec45cd` | audioclip-12398 | 1.8 | 0.734 | 빠르고 가볍게 움직이는 듯한 휙 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4e591e5199b7413b9771f2e67cec45cd) |
| ☐ | `1e3bb2243eb94b32bd83856dbeb57cae` | audioclip-4887 | 2 | 0.731 | 빠르고 가벼운 움직임이나 휘두르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1e3bb2243eb94b32bd83856dbeb57cae) |
| ☐ | `a523193ad9fd4fc888c6903d87ea3ce1` | audioclip-25870 | 2.6 | 0.731 | 마법 에너지가 빠르게 날아가는 듯한 휘두르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a523193ad9fd4fc888c6903d87ea3ce1) |
| ☐ | `9925041d48474aeeab6df6e0c4368097` | audioclip-23925 | 0.4 | 0.731 | UI 메뉴를 클릭하거나 아이템을 선택할 때 발생하는 짧고 명확한 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9925041d48474aeeab6df6e0c4368097) |
| ☐ | `b36e3f3626b54ddabf78667f57e3b05e` | audioclip-28150 | 0.8 | 0.73 | 동전이나 작은 금속 물체가 부딪히는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b36e3f3626b54ddabf78667f57e3b05e) |
| ☐ | `f83d4313597a410dabd037622c45e2cc` | audioclip-39000 | 0.9 | 0.729 | 빠르고 날카롭게 휘두르거나 움직이는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f83d4313597a410dabd037622c45e2cc) |
| ☐ | `6897f591af3e4d45a1e702360fd654e1` | audioclip-16446 | 0.9 | 0.728 | 작은 물체가 공중을 가르는 빠르고 날카로운 휘두르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6897f591af3e4d45a1e702360fd654e1) |

### 원거리-마법 광선  <sub>(effect, 검색어: 마법 광선 빔 발사 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `2a549edd63ad41fb86fa2b02bd6c8f52` | audioclip-6788 | 4 | 0.869 | 강력한 마법 에너지나 빔을 발사하여 타격하는 화려한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a549edd63ad41fb86fa2b02bd6c8f52) |
| ☐ | `f93486e5f11f435bbdaf898fad2188ef` | audioclip-39143 | 4.1 | 0.868 | 강력한 마법 에너지가 방출되며 지속적으로 타격하는 마법 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f93486e5f11f435bbdaf898fad2188ef) |
| ☐ | `013b83da7a174d859b0d233b27956b08` | audioclip-287 | 2.9 | 0.855 | 강력한 마법 에너지가 방출되며 울려 퍼지는 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=013b83da7a174d859b0d233b27956b08) |
| ☐ | `c5a24b9388c746238e6dd3d793119793` | audioclip-60422 | 4.2 | 0.854 | 강력한 마법 에너지나 빔이 발사되어 폭발하는 듯한 웅장한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c5a24b9388c746238e6dd3d793119793) |
| ☐ | `423b282b0a304fb9a76215fd99af89f8` | audioclip-62374 | 3.4 | 0.85 | 강력한 에너지 빔이나 마법 기술이 발동되어 폭발하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=423b282b0a304fb9a76215fd99af89f8) |
| ☐ | `e890e6b1e8834d7594b597e1f55dfc95` | audioclip-36562 | 2.9 | 0.85 | 강력한 마법 에너지나 레이저 빔을 발사하는 화려한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e890e6b1e8834d7594b597e1f55dfc95) |
| ☐ | `0ab31646b1594dc3874642849dae0d56` | audioclip-1761 | 4.9 | 0.848 | 강력한 에너지 빔이 발사되어 폭발하는 공상과학 스타일의 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0ab31646b1594dc3874642849dae0d56) |
| ☐ | `e6386d6de1c841c4a92df8b1b91af3fb` | audioclip-36181 | 4.1 | 0.847 | 미래지향적인 레이저나 에너지 빔이 발사되는 날카로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e6386d6de1c841c4a92df8b1b91af3fb) |
| ☐ | `bbec8c990c284026af92b8956b7f2704` | audioclip-29466 | 3.6 | 0.844 | 강력한 마법 에너지가 방출되어 폭발하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bbec8c990c284026af92b8956b7f2704) |
| ☐ | `50133ed1238f40118a752d2592df8147` | audioclip-12666 | 13.1 | 0.839 | 남성의 기합 소리와 함께 강력한 에너지 빔이 발사되어 지속되는 마법 스킬 사운드 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=50133ed1238f40118a752d2592df8147) |
| ☐ | `82281eb943b0401082839edeae68ae1f` | audioclip-20461 | 16.2 | 0.831 | 강한 기합 소리와 함께 에너지를 방출하는 강력한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=82281eb943b0401082839edeae68ae1f) |
| ☐ | `56b3ff8e53b5460e8b162c7d56df6857` | audioclip-13702 | 10.8 | 0.826 | 강력한 에너지 빔이 발사되어 폭발하는 미래적인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=56b3ff8e53b5460e8b162c7d56df6857) |
| ☐ | `4086ce8af5dc47669cda7aeab3c65bf1` | audioclip-41431 | 7 | 0.822 | 에너지를 충전한 뒤 강력한 레이저 빔을 발사하는 공상과학 스타일의 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4086ce8af5dc47669cda7aeab3c65bf1) |
| ☐ | `1acf456b17154bf4a5fd0c2708946cfe` | audioclip-4356 | 2.4 | 0.822 | 마법 에너지가 빠르게 날아가는 듯한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1acf456b17154bf4a5fd0c2708946cfe) |
| ☐ | `13f039c3fbd64502aa2ced8c86406cf1` | audioclip-3271 | 6.3 | 0.821 | 빠르게 연속으로 발사되는 에너지 탄환 또는 마법 투사체 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=13f039c3fbd64502aa2ced8c86406cf1) |
| ☐ | `34fa0485182e46d2ada6543214da030c` | audioclip-8423 | 5.7 | 0.819 | 마법 에너지가 빠르게 날아가는 듯한 신비로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=34fa0485182e46d2ada6543214da030c) |
| ☐ | `266d91ab162048069c0f1dc90eb5304e` | audioclip-62756 | 4.1 | 0.817 | 마법 에너지가 빠르게 날아가는 듯한 신비로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=266d91ab162048069c0f1dc90eb5304e) |
| ☐ | `2994cd6fc9504b23a2e0d77cc1e1b21c` | audioclip-6689 | 3.4 | 0.817 | 마법 에너지가 발사되어 흩어지는 듯한 신비로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2994cd6fc9504b23a2e0d77cc1e1b21c) |
| ☐ | `9346f44a8890443cbfff059c2d7f6689` | audioclip-23033 | 4.7 | 0.816 | 여러 번의 강력한 마법 에너지 투사체 발사 후 발생하는 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9346f44a8890443cbfff059c2d7f6689) |
| ☐ | `b07190103c1945eca86959243afed890` | audioclip-27678 | 3.3 | 0.816 | 강력한 마법 에너지나 전기가 방출된 후 폭발하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b07190103c1945eca86959243afed890) |

### 원거리-화살  <sub>(effect, 검색어: 활시위를 당겨 화살을 쏘는 소리)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `8c04cf239d704b8b8f7d3b404a160bbe` | audioclip-21948 | 8.1 | 0.757 | 빠르게 발사되는 마법 에너지 투사체 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8c04cf239d704b8b8f7d3b404a160bbe) |
| ☐ | `94019b350018445f84169f906b13b212` | audioclip-23146 | 1.7 | 0.756 | UI 메뉴를 선택하거나 알림이 뜰 때 발생하는 밝고 날카로운 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=94019b350018445f84169f906b13b212) |
| ☐ | `eb0b86e533f7420a8e97cb7b97c745f3` | audioclip-36912 | 1.6 | 0.756 | 검을 휘두를 때 발생하는 날카롭고 빠른 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=eb0b86e533f7420a8e97cb7b97c745f3) |
| ☐ | `e01294d012d247c1a5bc07949484778b` | audioclip-35204 | 1.1 | 0.755 | 검이 부딪히는 날카로운 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e01294d012d247c1a5bc07949484778b) |
| ☐ | `d241be0f5d4d429ba2ce750b3d02eab9` | audioclip-33000 | 3.5 | 0.752 | 날카로운 물체가 공기를 가르며 빠르게 날아가는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d241be0f5d4d429ba2ce750b3d02eab9) |
| ☐ | `1cbdba6cbf6f44be96303453c441ca58` | audioclip-4660 | 1.1 | 0.751 | 검을 휘둘러 공기를 가르는 날카롭고 빠른 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1cbdba6cbf6f44be96303453c441ca58) |
| ☐ | `72f38c79a086471392f827ae911cfd08` | audioclip-18013 | 0.8 | 0.75 | 무기를 빠르게 휘두르는 날카로운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=72f38c79a086471392f827ae911cfd08) |
| ☐ | `fa83bfb724964467910feda763f4bf36` | audioclip-39342 | 2.3 | 0.744 | 여러 번 빠르게 휘두르는 듯한 마법 공격 또는 에너지 스킬 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fa83bfb724964467910feda763f4bf36) |
| ☐ | `48755505f27e4581af747a1e13e3df4b` | audioclip-11469 | 2.2 | 0.743 | 권총이나 소총에서 발사되는 날카롭고 강력한 총성 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=48755505f27e4581af747a1e13e3df4b) |
| ☐ | `a523193ad9fd4fc888c6903d87ea3ce1` | audioclip-25870 | 2.6 | 0.743 | 마법 에너지가 빠르게 날아가는 듯한 휘두르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a523193ad9fd4fc888c6903d87ea3ce1) |
| ☐ | `e105123e73f149c1ae907b8bdffca395` | audioclip-35363 | 1.4 | 0.743 | 검을 휘둘러 공기를 가르는 날카롭고 빠른 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e105123e73f149c1ae907b8bdffca395) |
| ☐ | `1cc3f499b44a43cda9749b17d3a26201` | audioclip-4667 | 1.6 | 0.74 | 검을 휘두를 때 발생하는 날카롭고 빠른 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1cc3f499b44a43cda9749b17d3a26201) |
| ☐ | `5c127e4b02da4e65b4f46d30f885390c` | audioclip-14515 | 0.5 | 0.738 | 권총이나 소형 화기를 발사할 때 발생하는 날카로운 총성 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5c127e4b02da4e65b4f46d30f885390c) |
| ☐ | `bd8707172fb745bc85936f98036c2177` | audioclip-29696 | 3.4 | 0.738 | 마법 에너지가 빠르게 날아가는 듯한 투사체 발사 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bd8707172fb745bc85936f98036c2177) |
| ☐ | `ca4c49b20de341d4bb9dea4c1c9c68fc` | audioclip-75 | 0.5 | 0.737 | 금속 무기가 부딪히거나 단단한 물체에 타격되는 날카로운 금속음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ca4c49b20de341d4bb9dea4c1c9c68fc) |
| ☐ | `58778cf5b5de43fb831b90c1677ead4d` | audioclip-62334 | 1.8 | 0.737 | 무언가를 빠르게 던지거나 발사할 때 발생하는 마법적인 투사체 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58778cf5b5de43fb831b90c1677ead4d) |
| ☐ | `a4c452b41ae8405aa3e959a2509970b1` | audioclip-25820 | 3.7 | 0.737 | 에너지가 담긴 투사체가 빠르게 날아가는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a4c452b41ae8405aa3e959a2509970b1) |
| ☐ | `eb30252f067e48f8acf42ef684bce86a` | audioclip-36937 | 1.9 | 0.737 | 소총이나 권총을 발사할 때 발생하는 날카롭고 묵직한 총성 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=eb30252f067e48f8acf42ef684bce86a) |
| ☐ | `2413d415e7044d5ca5be8c5e0914adc2` | audioclip-5806 | 1.9 | 0.736 | 기관총이나 자동소총으로 빠르게 연사하는 총기 발사음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2413d415e7044d5ca5be8c5e0914adc2) |
| ☐ | `6dcf25bc078c4814b47adb6b374afe63` | audioclip-17218 | 1.5 | 0.736 | 무언가를 빠르게 던지거나 발사하는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6dcf25bc078c4814b47adb6b374afe63) |

### 원거리-총격  <sub>(effect, 검색어: 총 발사 소리 사격 레이저 건)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `c359649e15de431ba7d9f9b14f082358` | audioclip-30615 | 6.3 | 0.796 | 빠르게 연속으로 발사되는 레이저 또는 에너지 탄환의 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c359649e15de431ba7d9f9b14f082358) |
| ☐ | `13f039c3fbd64502aa2ced8c86406cf1` | audioclip-3271 | 6.3 | 0.793 | 빠르게 연속으로 발사되는 에너지 탄환 또는 마법 투사체 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=13f039c3fbd64502aa2ced8c86406cf1) |
| ☐ | `e4eeb402b9374355bb2483bf390bcd0f` | audioclip-35976 | 1.6 | 0.782 | 에너지 무기나 레이저 기관총이 빠르게 연사되는 SF 스타일의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e4eeb402b9374355bb2483bf390bcd0f) |
| ☐ | `462bab718e984714933f0c8027959965` | audioclip-11112 | 4 | 0.781 | 강력한 에너지 레이저가 발사되는 기계적인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=462bab718e984714933f0c8027959965) |
| ☐ | `48755505f27e4581af747a1e13e3df4b` | audioclip-11469 | 2.2 | 0.776 | 권총이나 소총에서 발사되는 날카롭고 강력한 총성 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=48755505f27e4581af747a1e13e3df4b) |
| ☐ | `2de9c6b1b5f54115bbabe6dff72e3d90` | audioclip-7327 | 2.4 | 0.774 | 자동 화기나 머신건으로 빠르게 연사하는 총기 발사 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2de9c6b1b5f54115bbabe6dff72e3d90) |
| ☐ | `017e5313a3d344acbb7d0498853fbae0` | audioclip-61790 | 1.5 | 0.773 | 권총을 세 번 연속으로 발사하는 날카로운 총성 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=017e5313a3d344acbb7d0498853fbae0) |
| ☐ | `09dc22f880ee446691d7686ee5a4b90f` | audioclip-1645 | 2.6 | 0.773 | 머신건이나 자동소총으로 빠르게 연사하는 총기 발사음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=09dc22f880ee446691d7686ee5a4b90f) |
| ☐ | `2413d415e7044d5ca5be8c5e0914adc2` | audioclip-5806 | 1.9 | 0.772 | 기관총이나 자동소총으로 빠르게 연사하는 총기 발사음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2413d415e7044d5ca5be8c5e0914adc2) |
| ☐ | `eb30252f067e48f8acf42ef684bce86a` | audioclip-36937 | 1.9 | 0.769 | 소총이나 권총을 발사할 때 발생하는 날카롭고 묵직한 총성 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=eb30252f067e48f8acf42ef684bce86a) |
| ☐ | `e6386d6de1c841c4a92df8b1b91af3fb` | audioclip-36181 | 4.1 | 0.769 | 미래지향적인 레이저나 에너지 빔이 발사되는 날카로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e6386d6de1c841c4a92df8b1b91af3fb) |
| ☐ | `afed106592164af18aec37352a6e6c41` | audioclip-27623 | 1.3 | 0.769 | 기관총이나 자동 소총으로 빠르게 연사하는 총기 발사 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=afed106592164af18aec37352a6e6c41) |
| ☐ | `e0fc34aeccdb4dcc9316562e83fab18e` | audioclip-35374 | 2.4 | 0.769 | 기계적인 느낌의 빠른 연사음 또는 머신건 발사 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e0fc34aeccdb4dcc9316562e83fab18e) |
| ☐ | `516433a1b4b4426ebe5400ea4f82c6a3` | audioclip-12873 | 2.2 | 0.768 | 기관총이나 자동 소총으로 빠르게 연사하는 총기 발사음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=516433a1b4b4426ebe5400ea4f82c6a3) |
| ☐ | `5ca9efe9b69e435682b2ee6d7185d8e2` | audioclip-14595 | 2.2 | 0.768 | 기관총이나 자동 소총으로 빠르게 연사하는 총기 발사음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5ca9efe9b69e435682b2ee6d7185d8e2) |
| ☐ | `41edbde25d7c4bc0b61dd0db7c42a168` | audioclip-10451 | 6.3 | 0.768 | 빠르게 연속적으로 발사되는 디지털 느낌의 레이저 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=41edbde25d7c4bc0b61dd0db7c42a168) |
| ☐ | `d6b46d9d41da40db92c41ac8cb78e440` | audioclip-33734 | 2.6 | 0.768 | 기관총이나 개틀링건으로 빠르게 연사하는 묵직한 발사음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d6b46d9d41da40db92c41ac8cb78e440) |
| ☐ | `f6c51c9fd2bc4113acff98f21f249466` | audioclip-38805 | 2.4 | 0.767 | 자동 화기나 기관총으로 빠르게 연사하는 총기 격발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f6c51c9fd2bc4113acff98f21f249466) |
| ☐ | `f91f37239ee3447486cbb9c40da4fc82` | audioclip-39136 | 4.9 | 0.766 | 강력한 에너지 레이저를 발사하는 기계적인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f91f37239ee3447486cbb9c40da4fc82) |
| ☐ | `9451d1ab93184c53ba6f9c69ae471c2e` | audioclip-23175 | 2.2 | 0.765 | 자동 소총이나 기관총으로 빠르게 연사하는 총기 발사음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9451d1ab93184c53ba6f9c69ae471c2e) |

### 원거리-포격  <sub>(effect, 검색어: 대포 발사 포격 폭음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `b5575654331543098c14cc438790a922` | audioclip-28453 | 3 | 0.827 | 강력하고 웅장한 폭발음 또는 대포 발사 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b5575654331543098c14cc438790a922) |
| ☐ | `543cd8a807de48a183c3edf744dcf34e` | audioclip-13319 | 1 | 0.795 | 검이 부딪히는 날카로운 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=543cd8a807de48a183c3edf744dcf34e) |
| ☐ | `9c03238612df480b8972a59d7aa09c3c` | audioclip-24410 | 3.5 | 0.795 | 폭죽이 발사되어 공중에서 크게 터지는 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9c03238612df480b8972a59d7aa09c3c) |
| ☐ | `18f5c872c1154f83bc88d9510a3cd1ea` | audioclip-4067 | 1 | 0.794 | 무거운 금속 물체가 강하게 충돌하거나 파괴되는 웅장한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=18f5c872c1154f83bc88d9510a3cd1ea) |
| ☐ | `4e890374a5414732949038f1313138a0` | audioclip-12425 | 1.4 | 0.794 | 강력한 총기 발사음 또는 폭발음. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4e890374a5414732949038f1313138a0) |
| ☐ | `1b5c9a886acd4e68937c6a78179aad21` | audioclip-4441 | 1.4 | 0.777 | 강력한 총기 발사음 또는 폭발적인 타격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1b5c9a886acd4e68937c6a78179aad21) |
| ☐ | `8859f59a2f3d42a59e34b2273bddb5e1` | audioclip-21377 | 3.7 | 0.776 | 강력한 화염 폭발이나 대규모 타격이 발생하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8859f59a2f3d42a59e34b2273bddb5e1) |
| ☐ | `d61dd1fddcf74c5e9e5400e7a8a3871d` | audioclip-33631 | 4.2 | 0.774 | 기합 소리와 함께 발생하는 묵직한 폭발 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d61dd1fddcf74c5e9e5400e7a8a3871d) |
| ☐ | `4cea08aebbd24e24907ee15b45a9d6ab` | audioclip-12169 | 2.2 | 0.774 | 강력하고 웅장한 폭발 또는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4cea08aebbd24e24907ee15b45a9d6ab) |
| ☐ | `5a9770b97bb54db29577c59ae853caa0` | audioclip-14269 | 3 | 0.773 | 강력한 폭발이나 무거운 타격이 발생하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5a9770b97bb54db29577c59ae853caa0) |
| ☐ | `09b94aa5be5b4bbab9f7715d7c907c1e` | audioclip-1619 | 1.6 | 0.773 | 강력한 폭발이나 무거운 타격이 발생하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=09b94aa5be5b4bbab9f7715d7c907c1e) |
| ☐ | `53ae296bff124bacaa50901f6f6e130a` | audioclip-13220 | 2 | 0.772 | 강력한 폭발음과 함께 발생하는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=53ae296bff124bacaa50901f6f6e130a) |
| ☐ | `5574b1866a1747c3832e07a75e4e3508` | audioclip-13509 | 1.7 | 0.772 | 무언가 크게 폭발하거나 파괴될 때 발생하는 강력한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5574b1866a1747c3832e07a75e4e3508) |
| ☐ | `0b10ddec4a0e4ccc92d55f506b38b88b` | audioclip-1821 | 8.1 | 0.77 | 연속적으로 발생하는 강력하고 거대한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0b10ddec4a0e4ccc92d55f506b38b88b) |
| ☐ | `30c634dc5e7e4e6db29c03627b76a19a` | audioclip-7781 | 1 | 0.77 | 검이 공기를 가르는 날카롭고 빠른 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=30c634dc5e7e4e6db29c03627b76a19a) |
| ☐ | `2974257d2a374868a582d9ee17030fd5` | audioclip-6704 | 14.4 | 0.769 | 연속적으로 발생하는 강력하고 웅장한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2974257d2a374868a582d9ee17030fd5) |
| ☐ | `f6b60aa60bf744f8aff378afdd54ea79` | audioclip-38794 | 4.6 | 0.768 | 강력한 폭발음과 함께 발생하는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f6b60aa60bf744f8aff378afdd54ea79) |
| ☐ | `3a3f66f191a444b08ec4ad50068bdd44` | audioclip-60895 | 3.3 | 0.767 | 강력한 폭발음과 함께 발생하는 묵직한 타격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3a3f66f191a444b08ec4ad50068bdd44) |
| ☐ | `d08e3b7814524e6184eb01fd9d8123d7` | audioclip-32736 | 2.1 | 0.767 | 강력한 폭발음과 함께 발생하는 묵직한 타격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d08e3b7814524e6184eb01fd9d8123d7) |
| ☐ | `3061ab35833445938d370c766ae1ce42` | audioclip-7711 | 2.8 | 0.767 | 강력한 폭발음과 함께 발생하는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3061ab35833445938d370c766ae1ce42) |


## 광역

### 광역-샹들리에 낙하  <sub>(effect, 검색어: 무거운 물체가 떨어지며 쾅 부딪히는 소리 추락 충격)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `2755ae6387604400bfeb2d1338b31530` | audioclip-6312 | 1.1 | 0.871 | 무거운 물체가 바닥에 떨어지며 발생하는 묵직한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2755ae6387604400bfeb2d1338b31530) |
| ☐ | `1c7efd2f570d4becb6a1698d5c3811fb` | audioclip-4632 | 1 | 0.871 | 무겁고 단단한 물체가 바닥에 떨어지며 발생하는 묵직한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1c7efd2f570d4becb6a1698d5c3811fb) |
| ☐ | `58fd0094f65c41cdb897941a2b2bda5e` | audioclip-14056 | 4.3 | 0.869 | 무거운 물체가 추락하여 파괴되는 웅장한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58fd0094f65c41cdb897941a2b2bda5e) |
| ☐ | `3927d16114d5431daf8ff32256cdbf29` | audioclip-9100 | 2.6 | 0.866 | 무거운 돌이나 구조물이 무너지며 발생하는 육중한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3927d16114d5431daf8ff32256cdbf29) |
| ☐ | `d3c8bb77cf5047e88d91dd9faffb0960` | audioclip-33237 | 3.2 | 0.862 | 무거운 물체가 바닥에 떨어지거나 부딪히는 묵직한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d3c8bb77cf5047e88d91dd9faffb0960) |
| ☐ | `fe960abf3df1427fa4184e4587123dd4` | audioclip-40017 | 3.7 | 0.861 | 무거운 물체가 바닥에 떨어지며 발생하는 묵직하고 강한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fe960abf3df1427fa4184e4587123dd4) |
| ☐ | `a8cbaf1c3b1b4af6bbbc736a0c8de8f7` | audioclip-26473 | 1.4 | 0.861 | 무거운 물체가 바닥에 떨어지며 발생하는 묵직하고 강한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a8cbaf1c3b1b4af6bbbc736a0c8de8f7) |
| ☐ | `4dc6eea106dd4d7dacb70a70ee105206` | audioclip-12311 | 5.7 | 0.861 | 무거운 물체가 바닥에 떨어지거나 부딪히는 묵직한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4dc6eea106dd4d7dacb70a70ee105206) |
| ☐ | `dac755d2e09744289ec3404b98704b43` | audioclip-34402 | 1.6 | 0.86 | 무거운 금속 물체가 바닥에 떨어지며 발생하는 묵직하고 강한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dac755d2e09744289ec3404b98704b43) |
| ☐ | `b0062241384d4c8daa40db205f5a811e` | audioclip-27616 | 2.5 | 0.859 | 무거운 물체가 바닥에 떨어지며 발생하는 묵직한 충격과 파편 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b0062241384d4c8daa40db205f5a811e) |
| ☐ | `464f5f1319b6440e942ab502d4ba7438` | audioclip-11141 | 2.6 | 0.858 | 무거운 금속 물체가 바닥에 떨어지며 발생하는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=464f5f1319b6440e942ab502d4ba7438) |
| ☐ | `e39a13587cc7445d8ec0a20819a410b7` | audioclip-61543 | 1.6 | 0.858 | 무거운 물체가 바닥에 떨어지거나 부딪히는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e39a13587cc7445d8ec0a20819a410b7) |
| ☐ | `ee2a3db8d83a40bb9afecbf81ceccffd` | audioclip-62926 | 3.1 | 0.858 | 무거운 물체가 떨어지거나 파괴될 때 발생하는 강력한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ee2a3db8d83a40bb9afecbf81ceccffd) |
| ☐ | `d54d4ba7b9f047019a7f7b273e42e7a5` | audioclip-33485 | 0.9 | 0.858 | 무거운 물체가 바닥에 떨어지거나 착지할 때 발생하는 묵직한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d54d4ba7b9f047019a7f7b273e42e7a5) |
| ☐ | `c70eab3080ca4e7ebaf0e2bd2ea1055c` | audioclip-31220 | 0.9 | 0.857 | 무거운 물체가 바닥에 떨어지거나 부딪히는 묵직한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c70eab3080ca4e7ebaf0e2bd2ea1055c) |
| ☐ | `8b5f7df6761b42e886d18a5c932996bd` | audioclip-21856 | 1.6 | 0.857 | 무거운 물체가 부딪히거나 떨어질 때 발생하는 둔탁하고 강한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8b5f7df6761b42e886d18a5c932996bd) |
| ☐ | `875a7e94feab4178aa588d72bdb92a30` | audioclip-21236 | 2.7 | 0.856 | 무거운 물체가 부딪히거나 파괴될 때 발생하는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=875a7e94feab4178aa588d72bdb92a30) |
| ☐ | `3a5914e718004375be538088acf5dec8` | audioclip-9272 | 1.4 | 0.855 | 무거운 물체가 바닥에 떨어지거나 파괴될 때 발생하는 둔탁하고 강한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3a5914e718004375be538088acf5dec8) |
| ☐ | `5a2d7c84b74347b6a64b8580c1f0ab34` | audioclip-14216 | 3.3 | 0.854 | 무거운 물체가 파괴되거나 폭발하는 강력한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5a2d7c84b74347b6a64b8580c1f0ab34) |
| ☐ | `230548e1a4884a81a93e6674abf9aed7` | audioclip-5651 | 2.6 | 0.854 | 무거운 물체가 바닥에 떨어지거나 강하게 부딪히는 묵직한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=230548e1a4884a81a93e6674abf9aed7) |

### 광역-화염 스플래시  <sub>(effect, 검색어: 불길이 터지는 화염 폭발 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `6034c63dc99b4e349e6335174a1b735b` | audioclip-15163 | 3.4 | 0.874 | 강력한 폭발과 함께 불길이 타오르는 화염 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6034c63dc99b4e349e6335174a1b735b) |
| ☐ | `7b1ff8f8c6f345eaa9fbd1d9ae56bcec` | audioclip-42000 | 1.5 | 0.866 | 강력한 불꽃이 폭발하듯 뿜어져 나오는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7b1ff8f8c6f345eaa9fbd1d9ae56bcec) |
| ☐ | `48eabf3f4675470c986319b1ff852ac7` | audioclip-11544 | 3 | 0.864 | 강력한 화염 마법이 폭발하며 번지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=48eabf3f4675470c986319b1ff852ac7) |
| ☐ | `524b08c78e0b497aa5627b95ec219382` | audioclip-13024 | 3.4 | 0.861 | 강력한 화염 마법이 폭발하며 타오르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=524b08c78e0b497aa5627b95ec219382) |
| ☐ | `43ebe9309f3644b584c7a84dc57b5b55` | audioclip-10757 | 2.8 | 0.859 | 강력한 불꽃이 폭발하며 번지는 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=43ebe9309f3644b584c7a84dc57b5b55) |
| ☐ | `cecc2c8817e0434bb210acec299e2731` | audioclip-32463 | 4 | 0.858 | 불꽃이 폭발하며 타오르는 듯한 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cecc2c8817e0434bb210acec299e2731) |
| ☐ | `64e056d673434784b38a780b9c143e09` | audioclip-15872 | 0.6 | 0.857 | 강력한 화염 폭발이 일어나는 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=64e056d673434784b38a780b9c143e09) |
| ☐ | `d8ec056693214a0a8e3f1ee372d45193` | audioclip-34125 | 5 | 0.857 | 강력한 폭발과 함께 불길이 치솟는 듯한 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d8ec056693214a0a8e3f1ee372d45193) |
| ☐ | `dc40cead5b0946bebe49e6ce46713ed7` | audioclip-60427 | 4.2 | 0.856 | 강력한 화염 마법이나 스킬이 폭발하며 발생하는 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dc40cead5b0946bebe49e6ce46713ed7) |
| ☐ | `2a43df614a0f41409adaf86a8e5f2dfd` | audioclip-6774 | 3 | 0.856 | 강력한 마법 폭발이나 스킬 사용 시 발생하는 화염 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a43df614a0f41409adaf86a8e5f2dfd) |
| ☐ | `73fa9fbd48594ea7a95a198349449eb7` | audioclip-18169 | 2 | 0.856 | 강력한 화염 마법이나 폭발 스킬의 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=73fa9fbd48594ea7a95a198349449eb7) |
| ☐ | `ed90fcdcceac437aa8b82259b8082bb4` | audioclip-37297 | 2.9 | 0.855 | 강렬한 불꽃이 터지거나 화염 마법을 사용하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ed90fcdcceac437aa8b82259b8082bb4) |
| ☐ | `4fb384a2bcfa456f87e96a1d2a7e002d` | audioclip-12606 | 16.3 | 0.854 | 강력한 화염 마법이 폭발하며 지속적으로 타오르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4fb384a2bcfa456f87e96a1d2a7e002d) |
| ☐ | `6fc0530c9c634c2e90f5a15ccea2975d` | audioclip-17506 | 3.4 | 0.853 | 강력한 화염 마법이 폭발하며 주변을 불태우는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6fc0530c9c634c2e90f5a15ccea2975d) |
| ☐ | `9cf09802f13d4d838e284e2f1214acea` | audioclip-24549 | 2.2 | 0.852 | 강력한 화염 마법이나 폭발이 일어나는 웅장한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9cf09802f13d4d838e284e2f1214acea) |
| ☐ | `82acc098c1ec47cebe2fa27194145ac8` | audioclip-20552 | 1.7 | 0.85 | 강력한 폭발음과 함께 화염이 터지는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=82acc098c1ec47cebe2fa27194145ac8) |
| ☐ | `56446062a2cb481aa77252884629f70a` | audioclip-13637 | 4.6 | 0.85 | 강력한 화염 폭발과 함께 타오르는 소리가 담긴 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=56446062a2cb481aa77252884629f70a) |
| ☐ | `dccd705bd3e149138ba7879b46443a5d` | audioclip-34687 | 3.4 | 0.85 | 강력한 화염 마법이 폭발하며 주변을 휩쓰는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dccd705bd3e149138ba7879b46443a5d) |
| ☐ | `14c9097916fe47df9a5917dd69b825d9` | audioclip-3413 | 3.2 | 0.85 | 강력한 화염 마법이 폭발하며 주변을 휩쓰는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=14c9097916fe47df9a5917dd69b825d9) |
| ☐ | `a5dd1b7c2fa441d580e818942c73b257` | audioclip-25984 | 3.7 | 0.85 | 강력한 불길이 솟구치며 타오르는 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a5dd1b7c2fa441d580e818942c73b257) |

### 광역-믹스골렘 폭발  <sub>(effect, 검색어: 큰 폭발 소리 폭탄 터짐)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `5574b1866a1747c3832e07a75e4e3508` | audioclip-13509 | 1.7 | 0.86 | 무언가 크게 폭발하거나 파괴될 때 발생하는 강력한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5574b1866a1747c3832e07a75e4e3508) |
| ☐ | `f7f74c990e3a430582498aac810d6f9c` | audioclip-38961 | 4.5 | 0.851 | 무언가 크게 폭발하거나 파괴될 때 발생하는 웅장하고 묵직한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f7f74c990e3a430582498aac810d6f9c) |
| ☐ | `f58538ad35464d75a2114dfe91458a25` | audioclip-38613 | 4.6 | 0.848 | 무언가 크게 폭발하거나 파괴될 때 발생하는 웅장하고 묵직한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f58538ad35464d75a2114dfe91458a25) |
| ☐ | `8147bb05959a4dcc86c76ef9a627ca0d` | audioclip-20331 | 2.2 | 0.848 | 무언가 크게 폭발하거나 파괴되는 웅장하고 강력한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8147bb05959a4dcc86c76ef9a627ca0d) |
| ☐ | `b5575654331543098c14cc438790a922` | audioclip-28453 | 3 | 0.847 | 강력하고 웅장한 폭발음 또는 대포 발사 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b5575654331543098c14cc438790a922) |
| ☐ | `09b94aa5be5b4bbab9f7715d7c907c1e` | audioclip-1619 | 1.6 | 0.847 | 강력한 폭발이나 무거운 타격이 발생하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=09b94aa5be5b4bbab9f7715d7c907c1e) |
| ☐ | `5a9770b97bb54db29577c59ae853caa0` | audioclip-14269 | 3 | 0.847 | 강력한 폭발이나 무거운 타격이 발생하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5a9770b97bb54db29577c59ae853caa0) |
| ☐ | `9c03238612df480b8972a59d7aa09c3c` | audioclip-24410 | 3.5 | 0.846 | 폭죽이 발사되어 공중에서 크게 터지는 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9c03238612df480b8972a59d7aa09c3c) |
| ☐ | `8f2f716b909a4fb68a5e7ceced6fee2d` | audioclip-22419 | 3.6 | 0.846 | 강력하고 웅장한 폭발음 또는 거대한 물체가 파괴되는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8f2f716b909a4fb68a5e7ceced6fee2d) |
| ☐ | `24aeda4f0a354cf9afa6a941ce5ac6d5` | audioclip-5907 | 3.9 | 0.846 | 강력하고 웅장한 폭발음 또는 무언가 파괴되는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=24aeda4f0a354cf9afa6a941ce5ac6d5) |
| ☐ | `836f0b6205c24deba6b3b17bab81153d` | audioclip-20653 | 4.6 | 0.846 | 강력하고 묵직한 폭발음 또는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=836f0b6205c24deba6b3b17bab81153d) |
| ☐ | `9cdb83cca4fd4bc8a0bf45b418052370` | audioclip-24541 | 3.6 | 0.845 | 무겁고 강력한 폭발음 또는 무언가 파괴되는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9cdb83cca4fd4bc8a0bf45b418052370) |
| ☐ | `564caad7e54a40c8aced59089f66e4ee` | audioclip-13640 | 1.6 | 0.845 | 강력하고 묵직한 폭발음 또는 무언가 파괴되는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=564caad7e54a40c8aced59089f66e4ee) |
| ☐ | `fbd92fb8b13c473da29a813e5a540ce0` | audioclip-39555 | 2.4 | 0.845 | 강력한 폭발이나 무거운 물체가 파괴될 때 발생하는 웅장한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fbd92fb8b13c473da29a813e5a540ce0) |
| ☐ | `04114fdd4d4c4cf188b03565a3855413` | audioclip-735 | 1.8 | 0.845 | 강력하고 웅장한 폭발음 또는 무언가 파괴되는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=04114fdd4d4c4cf188b03565a3855413) |
| ☐ | `b06cd1fa3c9b4ee58338b829ade99405` | audioclip-27677 | 2.2 | 0.845 | 무언가 크게 폭발하거나 파괴될 때 발생하는 웅장하고 묵직한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b06cd1fa3c9b4ee58338b829ade99405) |
| ☐ | `d7a533e1d84f4863afbde2769b4c55b9` | audioclip-33879 | 2.7 | 0.845 | 무언가 크게 폭발하거나 파괴될 때 발생하는 웅장하고 묵직한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d7a533e1d84f4863afbde2769b4c55b9) |
| ☐ | `b2a27b2c68254dcba07d6121477d1d29` | audioclip-28021 | 4.3 | 0.843 | 무언가 크게 폭발하며 파편이 튀는 듯한 강력한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b2a27b2c68254dcba07d6121477d1d29) |
| ☐ | `58a97dfbaa6149bbbc3a3c854a854112` | audioclip-13996 | 3.2 | 0.843 | 강력한 폭발과 함께 무언가 파괴되는 듯한 웅장한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58a97dfbaa6149bbbc3a3c854a854112) |
| ☐ | `6c6066a9bef74198b14b0c5e581c9f62` | audioclip-17010 | 1.6 | 0.843 | 강력하고 묵직한 폭발 또는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6c6066a9bef74198b14b0c5e581c9f62) |


## 공중

### 공중-레이스류 공격  <sub>(effect, 검색어: 유령이 공격하는 으스스한 소리)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `d47c69b51608487aaf2beda2bf881d5c` | audioclip-33369 | 20.1 | 0.807 | 유령이나 영혼들이 비명을 지르는 듯한 으스스하고 기괴한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d47c69b51608487aaf2beda2bf881d5c) |
| ☐ | `2d0bf75cc4424748b070683f0364a011` | audioclip-7202 | 5.5 | 0.798 | 괴물이나 유령이 깊게 숨을 내뱉는 듯한 으스스한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2d0bf75cc4424748b070683f0364a011) |
| ☐ | `db429f2ce82e4306a36d1f4cf118dcaf` | audioclip-34486 | 5.5 | 0.793 | 괴물이나 유령이 깊게 숨을 내뱉는 듯한 으스스한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=db429f2ce82e4306a36d1f4cf118dcaf) |
| ☐ | `3b19f6df63274dfda4a36aa4c70cc2f1` | audioclip-9385 | 5.5 | 0.787 | 괴물이나 유령이 깊게 숨을 내뱉는 듯한 으스스한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3b19f6df63274dfda4a36aa4c70cc2f1) |
| ☐ | `536a0aac7b7d421c88bc3fb357da51f5` | audioclip-13182 | 6 | 0.785 | 몬스터나 유령이 깊게 숨을 내뱉는 듯한 어둡고 으스스한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=536a0aac7b7d421c88bc3fb357da51f5) |
| ☐ | `dbd58d73f3394c39975e89402d9fe205` | audioclip-61622 | 3.8 | 0.785 | 괴생명체가 날카롭게 비명을 지르며 공격하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dbd58d73f3394c39975e89402d9fe205) |
| ☐ | `11bb6a81eae1436e8838d5be9ed38aec` | audioclip-2902 | 6 | 0.782 | 괴물이나 유령이 깊게 숨을 내뱉는 듯한 어둡고 으스스한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=11bb6a81eae1436e8838d5be9ed38aec) |
| ☐ | `a3a3ddae88074ba1800fed05f9c29f5e` | audioclip-25649 | 5.5 | 0.778 | 몬스터나 유령이 깊게 숨을 내뱉는 듯한 으스스하고 위협적인 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a3a3ddae88074ba1800fed05f9c29f5e) |
| ☐ | `c5ce1894bb7f4d74a79d31d1e43c57e9` | audioclip-61638 | 3.9 | 0.777 | 몬스터가 기괴하게 웃은 뒤 날카롭게 공격하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c5ce1894bb7f4d74a79d31d1e43c57e9) |
| ☐ | `591585096d7a40f082f9bf24cfe42e2a` | audioclip-14080 | 3.2 | 0.774 | 몬스터가 날카롭게 울부짖으며 공격하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=591585096d7a40f082f9bf24cfe42e2a) |
| ☐ | `d6c9187d52ab447fb1534bdd27ef8d07` | audioclip-33749 | 2.9 | 0.774 | 몬스터가 비명을 지르며 공격하는 날카로운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d6c9187d52ab447fb1534bdd27ef8d07) |
| ☐ | `007e81a16e1045809212d86a2954db20` | audioclip-173 | 2.1 | 0.773 | 몬스터가 공격하거나 기합을 넣는 듯한 짧고 공격적인 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=007e81a16e1045809212d86a2954db20) |
| ☐ | `a7314db4c90e402f9ba12f66974e3605` | audioclip-61433 | 5.5 | 0.768 | 심연의 생명체나 유령이 깊게 숨을 내뱉는 듯한 으스스한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a7314db4c90e402f9ba12f66974e3605) |
| ☐ | `975eb7110fec4ec79525980fbc707b9a` | audioclip-23645 | 1.3 | 0.768 | 몬스터가 공격하거나 피해를 입을 때 발생하는 짧고 날카로운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=975eb7110fec4ec79525980fbc707b9a) |
| ☐ | `4b1a51a1bac546b083b67207b3601326` | audioclip-11885 | 1.8 | 0.765 | 몬스터가 짧고 날카롭게 내뱉는 공격 또는 피격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4b1a51a1bac546b083b67207b3601326) |
| ☐ | `05ce5fd82759440a8c3debf19a5ac0e9` | audioclip-1001 | 3.5 | 0.765 | 몬스터가 날카롭게 소리를 지르며 공격하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=05ce5fd82759440a8c3debf19a5ac0e9) |
| ☐ | `6f170ac179254affb47ba9c478794be9` | audioclip-41903 | 0.8 | 0.764 | 몬스터가 짧고 날카롭게 내는 공격 또는 행동 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6f170ac179254affb47ba9c478794be9) |
| ☐ | `686bf9d71d31454483080f3e74f9c914` | audioclip-16417 | 0.8 | 0.761 | 몬스터가 짧고 날카롭게 내는 울음소리 또는 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=686bf9d71d31454483080f3e74f9c914) |
| ☐ | `d9cafef885884c66becbf2d9e1a76f3a` | audioclip-34257 | 1.3 | 0.758 | 몬스터가 빠르게 공격하거나 움직일 때 발생하는 날카로운 휘두르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d9cafef885884c66becbf2d9e1a76f3a) |
| ☐ | `029c52462440450384b4dccc1c57e00c` | audioclip-510 | 3.6 | 0.758 | 어둡고 으스스한 분위기를 자아내는 낮은 저음의 환경음 또는 포탈 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=029c52462440450384b4dccc1c57e00c) |

### 공중-정령류 공격  <sub>(effect, 검색어: 정령의 마법 공격 바람 번개 불꽃 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `c591695ca285470ebedf9523c622f09a` | audioclip-30988 | 1.9 | 0.852 | 마법 에너지가 방출되며 반짝이는 소리가 나는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c591695ca285470ebedf9523c622f09a) |
| ☐ | `ef39a94ca4a14a38af9af5ef410375e6` | audioclip-37571 | 1.9 | 0.846 | 마법 에너지가 폭발하며 발생하는 화려하고 강력한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ef39a94ca4a14a38af9af5ef410375e6) |
| ☐ | `431e60421b0847568e3f9ac314ec28dd` | audioclip-10635 | 2.8 | 0.841 | 강력한 마법 에너지가 방출되며 빠르게 휘감기는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=431e60421b0847568e3f9ac314ec28dd) |
| ☐ | `dfda3f7d17f94b9e8c1ff9fe5e877d6e` | audioclip-35154 | 3.2 | 0.84 | 강력한 마법 에너지가 폭발하며 퍼져나가는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dfda3f7d17f94b9e8c1ff9fe5e877d6e) |
| ☐ | `93ccc866143144138edba64e7cb05002` | audioclip-23119 | 2 | 0.84 | 바람이 휘몰아치며 마법 에너지가 폭발하는 듯한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=93ccc866143144138edba64e7cb05002) |
| ☐ | `5fc52ff3cbc8488fba1b25e91af7a1cc` | audioclip-15100 | 4.4 | 0.833 | 불꽃이나 바람 속성의 마법 기술이 빠르게 발동되는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5fc52ff3cbc8488fba1b25e91af7a1cc) |
| ☐ | `0b1324dd7d41431dac969d6829acbbe6` | audioclip-1814 | 3.4 | 0.83 | 마법 에너지가 방출되며 퍼져나가는 날카롭고 신비로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0b1324dd7d41431dac969d6829acbbe6) |
| ☐ | `d253578f058342e1b6a47fbe2a45a304` | audioclip-60420 | 4.2 | 0.827 | 마법 에너지가 방출되며 폭발하는 강력한 마법 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d253578f058342e1b6a47fbe2a45a304) |
| ☐ | `2d68615d7ac84fb3a376480e354b7a07` | audioclip-7254 | 3.4 | 0.826 | 강력한 마법 폭발이나 화염 속성의 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2d68615d7ac84fb3a376480e354b7a07) |
| ☐ | `cecc2c8817e0434bb210acec299e2731` | audioclip-32463 | 4 | 0.826 | 불꽃이 폭발하며 타오르는 듯한 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cecc2c8817e0434bb210acec299e2731) |
| ☐ | `da33cdec988242ad8f2dd9711d3ecf8d` | audioclip-34318 | 2.5 | 0.826 | 강한 바람이나 마법 에너지가 휘몰아치며 공격하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=da33cdec988242ad8f2dd9711d3ecf8d) |
| ☐ | `da1ccc4c66964fafb29ec5d6f4e9d58f` | audioclip-61788 | 2.6 | 0.825 | 바람이나 마법 에너지가 빠르게 방출되는 듯한 스킬 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=da1ccc4c66964fafb29ec5d6f4e9d58f) |
| ☐ | `cc1b31c5af6b46a281f3db6819966086` | audioclip-32044 | 7.8 | 0.825 | 빠르고 날카로운 바람 소리와 함께 마법 에너지가 발산되는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cc1b31c5af6b46a281f3db6819966086) |
| ☐ | `2cc66b1ee06846e0ade4972f855015e6` | audioclip-7156 | 3.2 | 0.825 | 강력한 마법 에너지가 방출되며 폭발하는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2cc66b1ee06846e0ade4972f855015e6) |
| ☐ | `1a53f69e216a4f178b66070546ec4235` | audioclip-60667 | 7 | 0.825 | 강력한 바람이나 마법 에너지가 휘몰아치며 폭발하는 듯한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1a53f69e216a4f178b66070546ec4235) |
| ☐ | `88bbac885a3542b3a14e8d33c9bffc86` | audioclip-21444 | 3.7 | 0.825 | 강력한 마법 에너지가 방출되며 얼음이나 바람 속성의 타격을 가하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=88bbac885a3542b3a14e8d33c9bffc86) |
| ☐ | `d07a3ca6054a47109f205b2aa5cb5e82` | audioclip-32722 | 4.9 | 0.824 | 강력한 마법 에너지가 폭발하며 발생하는 화염 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d07a3ca6054a47109f205b2aa5cb5e82) |
| ☐ | `3234da689f2946a1a83e70a9ecf4ddd0` | audioclip-7996 | 3 | 0.824 | 바람이 휘감기며 마법 투사체가 날아가는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3234da689f2946a1a83e70a9ecf4ddd0) |
| ☐ | `c4536e622ce940a8abd138f3e7bc184d` | audioclip-30759 | 2.9 | 0.824 | 마법 에너지가 방출되거나 폭발하는 화려한 마법 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c4536e622ce940a8abd138f3e7bc184d) |
| ☐ | `43ebe9309f3644b584c7a84dc57b5b55` | audioclip-10757 | 2.8 | 0.823 | 강력한 불꽃이 폭발하며 번지는 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=43ebe9309f3644b584c7a84dc57b5b55) |


## 투사체

### 투사체 명중  <sub>(effect, 검색어: 투사체가 명중하는 타격 임팩트 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `5aacfda92ef246ec93ab46c59dfb53e3` | audioclip-14281 | 2 | 0.891 | 물체나 적을 타격할 때 발생하는 물리적인 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5aacfda92ef246ec93ab46c59dfb53e3) |
| ☐ | `fa651b7ce58240a1b9b88cc0a94a2eb2` | audioclip-39330 | 0.6 | 0.884 | 무언가 강하게 타격하는 물리적인 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fa651b7ce58240a1b9b88cc0a94a2eb2) |
| ☐ | `1f075f56e7f34d348153e2432a032691` | audioclip-4994 | 2.1 | 0.882 | 적을 타격할 때 발생하는 둔탁하고 강한 물리적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1f075f56e7f34d348153e2432a032691) |
| ☐ | `65b5c0ac0964495c8cf0b0c5ca374d8e` | audioclip-15995 | 2 | 0.881 | 무언가를 강하게 타격하는 묵직한 물리적 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=65b5c0ac0964495c8cf0b0c5ca374d8e) |
| ☐ | `a647fdbf0e5748f2811494bc20f25e18` | audioclip-26046 | 0.9 | 0.88 | 무언가에 강하게 부딪히거나 타격하는 물리적인 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a647fdbf0e5748f2811494bc20f25e18) |
| ☐ | `05f4bdbfd9e8406986375fbaddc18e41` | audioclip-62385 | 2.5 | 0.877 | 무언가에 강하게 부딪히거나 타격하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=05f4bdbfd9e8406986375fbaddc18e41) |
| ☐ | `d50162cf31954078812108b35ba38fb0` | audioclip-33441 | 0.6 | 0.876 | 무언가를 강하게 타격하는 물리적인 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d50162cf31954078812108b35ba38fb0) |
| ☐ | `39b70915ec704c28b46a7bf0a8d922c6` | audioclip-1 | 0.6 | 0.876 | 무언가에 강하게 부딪히거나 타격하는 물리적인 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=39b70915ec704c28b46a7bf0a8d922c6) |
| ☐ | `8ba37b1bb18143689347f56850fb216a` | audioclip-21884 | 0.5 | 0.875 | 물리적인 타격이나 공격 시 발생하는 짧고 강한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8ba37b1bb18143689347f56850fb216a) |
| ☐ | `ac4f215b2d494bcc8ef63e98e6602da6` | audioclip-27007 | 1.5 | 0.874 | 무언가를 타격하는 둔탁하고 강한 물리적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ac4f215b2d494bcc8ef63e98e6602da6) |
| ☐ | `0f1eed31d05645518c7b79a016b91ded` | audioclip-2468 | 3.4 | 0.874 | 강한 타격감이 느껴지는 물리적인 공격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0f1eed31d05645518c7b79a016b91ded) |
| ☐ | `cd4f5282e55943b5bc95566e5ee1ae6e` | audioclip-32227 | 0.9 | 0.873 | 물리적인 타격감이 느껴지는 둔탁한 피격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cd4f5282e55943b5bc95566e5ee1ae6e) |
| ☐ | `4c4772ec80cb43098a49bb84e8f38426` | audioclip-12062 | 0.8 | 0.872 | 무언가를 강하게 때리는 물리적인 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4c4772ec80cb43098a49bb84e8f38426) |
| ☐ | `3b73889d6be34b8fa8a752dbb75c77dc` | audioclip-9420 | 1 | 0.872 | 무언가를 강하게 타격하는 묵직한 물리적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3b73889d6be34b8fa8a752dbb75c77dc) |
| ☐ | `8a0748a1ab9544d9a60000691ed86244` | audioclip-21636 | 0.4 | 0.871 | 무언가에 강하게 부딪히거나 타격하는 물리적인 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8a0748a1ab9544d9a60000691ed86244) |
| ☐ | `c5f3fc1564694e29809313c056305113` | audioclip-31056 | 0.4 | 0.871 | 주먹이나 둔기로 대상을 강하게 타격하는 물리적인 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c5f3fc1564694e29809313c056305113) |
| ☐ | `6252096b8f5c4319a3a3efaf37e7f39b` | audioclip-15479 | 0.8 | 0.871 | 무언가를 강하게 때리는 듯한 둔탁한 물리적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6252096b8f5c4319a3a3efaf37e7f39b) |
| ☐ | `0a58ad8078ec4565b99784fe011bdfdc` | audioclip-1705 | 0.7 | 0.87 | 무언가를 강하게 때리는 듯한 둔탁하고 날카로운 물리적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0a58ad8078ec4565b99784fe011bdfdc) |
| ☐ | `5be3859e6b414fd0a70213c3ecab27f5` | audioclip-14491 | 1.1 | 0.87 | 무언가 강하게 타격하거나 부딪히는 묵직한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5be3859e6b414fd0a70213c3ecab27f5) |
| ☐ | `8d1bc67aaf2d4142866c8197873add8f` | audioclip-22112 | 0.8 | 0.87 | 무언가를 강하게 타격하는 둔탁한 물리적 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8d1bc67aaf2d4142866c8197873add8f) |


## 피격

### 피격-일반  <sub>(effect, 검색어: 살을 때리는 타격음 피격 퍽)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `cd4f5282e55943b5bc95566e5ee1ae6e` | audioclip-32227 | 0.9 | 0.83 | 물리적인 타격감이 느껴지는 둔탁한 피격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cd4f5282e55943b5bc95566e5ee1ae6e) |
| ☐ | `7a9220eb76ae4bb08a22db3631722206` | audioclip-41996 | 0.5 | 0.826 | 무언가에 물리적으로 부딪히거나 타격하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7a9220eb76ae4bb08a22db3631722206) |
| ☐ | `ed7ebda170e34ee9b6c9cb2da573aa49` | audioclip-37282 | 2 | 0.824 | 신체적 타격이나 둔탁한 공격이 명중하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ed7ebda170e34ee9b6c9cb2da573aa49) |
| ☐ | `a04ee3be3e9c4d7dbd8264c811c152cc` | audioclip-25082 | 1.3 | 0.822 | 주먹이나 둔기로 대상을 타격할 때 발생하는 묵직하고 날카로운 물리적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a04ee3be3e9c4d7dbd8264c811c152cc) |
| ☐ | `15d8f000508044ae9282464d6e4b4aac` | audioclip-3582 | 0.4 | 0.82 | 주먹으로 때리는 듯한 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=15d8f000508044ae9282464d6e4b4aac) |
| ☐ | `d260b4ce39b043c2ba61d1b46b2d9844` | audioclip-33018 | 1.3 | 0.82 | 주먹이나 둔기로 대상을 강하게 타격하는 물리적인 공격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d260b4ce39b043c2ba61d1b46b2d9844) |
| ☐ | `367e58ab488a4d6ea3a1b93bc1c467ad` | audioclip-8670 | 0.4 | 0.82 | 무언가를 타격하는 둔탁하고 짧은 물리적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=367e58ab488a4d6ea3a1b93bc1c467ad) |
| ☐ | `7f8a57cd87ae4b3aaaa48fb2bd7c6761` | audioclip-20056 | 0.7 | 0.82 | 무언가를 타격하는 둔탁하고 짧은 물리적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7f8a57cd87ae4b3aaaa48fb2bd7c6761) |
| ☐ | `e50a699bdb824b7aa97c5ef97018cd9b` | audioclip-35995 | 3.8 | 0.819 | 무언가를 강하게 타격할 때 발생하는 둔탁한 물리적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e50a699bdb824b7aa97c5ef97018cd9b) |
| ☐ | `efab85c6cfa247c285d612fa5c652f5f` | audioclip-37657 | 0.8 | 0.819 | 무언가를 강하게 때리는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=efab85c6cfa247c285d612fa5c652f5f) |
| ☐ | `a2d812d65b824c799d9359a5c34c5153` | audioclip-25527 | 0.5 | 0.819 | 무언가를 강하게 때리거나 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a2d812d65b824c799d9359a5c34c5153) |
| ☐ | `d15b6ab16b63435ba5289244fd37bc9e` | audioclip-32866 | 1 | 0.819 | 무언가를 강하게 때리거나 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d15b6ab16b63435ba5289244fd37bc9e) |
| ☐ | `c85fcf78a5024aa7a14d830d551e6add` | audioclip-31436 | 0.5 | 0.819 | 무언가를 강하게 때리거나 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c85fcf78a5024aa7a14d830d551e6add) |
| ☐ | `fa651b7ce58240a1b9b88cc0a94a2eb2` | audioclip-39330 | 0.6 | 0.819 | 무언가 강하게 타격하는 물리적인 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fa651b7ce58240a1b9b88cc0a94a2eb2) |
| ☐ | `5aacfda92ef246ec93ab46c59dfb53e3` | audioclip-14281 | 2 | 0.819 | 물체나 적을 타격할 때 발생하는 물리적인 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5aacfda92ef246ec93ab46c59dfb53e3) |
| ☐ | `05f4bdbfd9e8406986375fbaddc18e41` | audioclip-62385 | 2.5 | 0.818 | 무언가에 강하게 부딪히거나 타격하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=05f4bdbfd9e8406986375fbaddc18e41) |
| ☐ | `89d574a93f9d4a1cb4c70b6c80354a68` | audioclip-21609 | 0.7 | 0.818 | 무언가를 강하게 때리거나 찰싹 소리가 나는 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=89d574a93f9d4a1cb4c70b6c80354a68) |
| ☐ | `5ffc25df80354177bb93acd1b1414e5d` | audioclip-15127 | 1.3 | 0.817 | 무언가를 둔탁하게 타격하는 물리적인 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5ffc25df80354177bb93acd1b1414e5d) |
| ☐ | `fe276fc8c8a7449a98705f53a973f556` | audioclip-39942 | 0.5 | 0.817 | 뺨을 때리거나 주먹으로 치는 듯한 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fe276fc8c8a7449a98705f53a973f556) |
| ☐ | `0a58ad8078ec4565b99784fe011bdfdc` | audioclip-1705 | 0.7 | 0.817 | 무언가를 강하게 때리는 듯한 둔탁하고 날카로운 물리적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0a58ad8078ec4565b99784fe011bdfdc) |

### 피격-중장갑 막힘  <sub>(effect, 검색어: 금속 갑옷에 튕기는 소리 막힘 챙)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `acbc478e4de1417b937d0d5731f00f71` | audioclip-27081 | 2.6 | 0.8 | 무거운 갑옷을 입고 움직일 때 발생하는 금속성 마찰음 및 달그락거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=acbc478e4de1417b937d0d5731f00f71) |
| ☐ | `1483db35b2164d6e98ef07d961296956` | audioclip-40348 | 0.8 | 0.788 | 갑옷이나 금속 장비가 움직일 때 발생하는 짤랑거리는 금속음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1483db35b2164d6e98ef07d961296956) |
| ☐ | `96fe28218f2b4af8a19d9512899d7112` | audioclip-23593 | 2.9 | 0.776 | 금속 재질의 무겁고 강한 타격음 또는 방패로 공격을 막는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=96fe28218f2b4af8a19d9512899d7112) |
| ☐ | `45e4c2d559cc40e3a62936194378f60d` | audioclip-11070 | 0.5 | 0.776 | 금속 재질의 장비나 물건이 부딪히며 발생하는 쇳소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=45e4c2d559cc40e3a62936194378f60d) |
| ☐ | `3b49df6589394c21be39b4e722e83afb` | audioclip-9408 | 1.5 | 0.774 | 무거운 금속 물체가 부딪히거나 바닥에 떨어질 때 발생하는 둔탁한 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3b49df6589394c21be39b4e722e83afb) |
| ☐ | `aa00256eb2f94074aab76d4d568d98ca` | audioclip-26657 | 0.4 | 0.767 | 금속 재질의 무기나 장비를 다룰 때 발생하는 날카로운 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=aa00256eb2f94074aab76d4d568d98ca) |
| ☐ | `f70a1a99a3ec4a12a08aadcb4d246943` | audioclip-62101 | 2.5 | 0.766 | 검이 방패나 다른 금속에 부딪히는 날카로운 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f70a1a99a3ec4a12a08aadcb4d246943) |
| ☐ | `73b4deaf414847df84f4e35a810c9f9d` | audioclip-18133 | 0.6 | 0.765 | 금속 사슬이나 장비가 부딪히며 나는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=73b4deaf414847df84f4e35a810c9f9d) |
| ☐ | `ac6cd7ac0feb416f9b6dc5282c0b5831` | audioclip-42538 | 0.9 | 0.765 | 금속 사슬이나 장비가 부딪히며 나는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ac6cd7ac0feb416f9b6dc5282c0b5831) |
| ☐ | `37ac460072084ec898932302a8cbee44` | audioclip-8850 | 0.4 | 0.765 | 금속 사슬이나 장비가 부딪히며 나는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=37ac460072084ec898932302a8cbee44) |
| ☐ | `cd5f48d71f1c4378a2613a2be380504a` | audioclip-32240 | 0.6 | 0.765 | 금속 재질의 바닥을 걷거나 갑옷을 입고 이동할 때 발생하는 쇳소리 섞인 발소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cd5f48d71f1c4378a2613a2be380504a) |
| ☐ | `cb74fe7c22784549961214121ca2cf1e` | audioclip-31915 | 0.8 | 0.765 | 사슬이나 금속 장비가 부딪히며 나는 달그락거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cb74fe7c22784549961214121ca2cf1e) |
| ☐ | `758af40fb904494e987b67070da871d0` | audioclip-18412 | 0.9 | 0.764 | 금속 사슬이나 장비가 부딪히며 달그락거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=758af40fb904494e987b67070da871d0) |
| ☐ | `406d56b5cbfd456db1ba1b20c9cba8d4` | audioclip-62565 | 1.4 | 0.764 | 금속 사슬이나 장비가 서로 부딪히며 나는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=406d56b5cbfd456db1ba1b20c9cba8d4) |
| ☐ | `59315d325d514655ad872ef53dce0b41` | audioclip-62136 | 0.5 | 0.763 | 금속 사슬이나 장비가 서로 부딪히며 나는 짤랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=59315d325d514655ad872ef53dce0b41) |
| ☐ | `24bbeb94a3604eb88a55a23e2658195a` | audioclip-5923 | 2.5 | 0.763 | 무거운 금속 물체가 부딪히는 묵직하고 날카로운 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=24bbeb94a3604eb88a55a23e2658195a) |
| ☐ | `322cc4393bb9426ea728342d93b670a9` | audioclip-7989 | 2.5 | 0.762 | 방패나 금속 갑옷에 무기가 부딪히는 묵직한 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=322cc4393bb9426ea728342d93b670a9) |
| ☐ | `a059fce022a94ebc945eea005f56c813` | audioclip-25089 | 2.4 | 0.762 | 금속이 부딪히는 날카롭고 짧은 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a059fce022a94ebc945eea005f56c813) |
| ☐ | `ba389f19b1164975a83e193e85be4896` | audioclip-60288 | 1 | 0.762 | 금속 재질의 방패나 무기가 부딪히는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ba389f19b1164975a83e193e85be4896) |
| ☐ | `3d4a41de581347d9aae7e292a47b3dc4` | audioclip-9710 | 0.4 | 0.761 | 금속 사슬이나 갑옷이 부딪히며 달랑거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3d4a41de581347d9aae7e292a47b3dc4) |

### 피격-건물  <sub>(effect, 검색어: 돌벽에 부딪히는 타격 건물 피격 둔탁)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `2a9355c1cd4b4f57b9a4ab4c115c4e73` | audioclip-6815 | 2.4 | 0.818 | 무언가에 강하게 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a9355c1cd4b4f57b9a4ab4c115c4e73) |
| ☐ | `20b7e7ef49c34c3b86a8e91a9a2c727f` | audioclip-5269 | 1.1 | 0.812 | 무언가에 강하게 부딪히거나 타격하는 둔탁한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=20b7e7ef49c34c3b86a8e91a9a2c727f) |
| ☐ | `89a122adba0542888cf2f509bf9a3e91` | audioclip-21579 | 1.7 | 0.811 | 무언가에 강하게 부딪히거나 타격을 입었을 때 발생하는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=89a122adba0542888cf2f509bf9a3e91) |
| ☐ | `20d2fd686b654f8e9b9d0fd9c88d7313` | audioclip-5293 | 1 | 0.811 | 무언가에 강하게 부딪히거나 타격을 입었을 때 발생하는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=20d2fd686b654f8e9b9d0fd9c88d7313) |
| ☐ | `a926b6c804fd483e819c41821843853c` | audioclip-26523 | 0.3 | 0.808 | 무언가에 강하게 부딪히거나 타격할 때 발생하는 둔탁한 물리적 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a926b6c804fd483e819c41821843853c) |
| ☐ | `ad5884aea6a24b31a26c596699673ccd` | audioclip-27197 | 0.6 | 0.808 | 무언가 강하게 부딪히거나 파괴되는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ad5884aea6a24b31a26c596699673ccd) |
| ☐ | `545243f1d90d4f2f8282589d5e7dc7d4` | audioclip-13334 | 0.8 | 0.807 | 무언가에 강하게 부딪히거나 타격하는 둔탁한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=545243f1d90d4f2f8282589d5e7dc7d4) |
| ☐ | `5dac1868ac5842a283dc1329c1350a33` | audioclip-14761 | 0.9 | 0.807 | 무언가에 강하게 부딪히거나 타격하는 둔탁한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5dac1868ac5842a283dc1329c1350a33) |
| ☐ | `5f0c2e9b04ee4a3a9d493a863b8a1379` | audioclip-14974 | 0.3 | 0.805 | 단단한 물체를 짧게 타격하는 둔탁한 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5f0c2e9b04ee4a3a9d493a863b8a1379) |
| ☐ | `efab85c6cfa247c285d612fa5c652f5f` | audioclip-37657 | 0.8 | 0.804 | 무언가를 강하게 때리는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=efab85c6cfa247c285d612fa5c652f5f) |
| ☐ | `a2d812d65b824c799d9359a5c34c5153` | audioclip-25527 | 0.5 | 0.802 | 무언가를 강하게 때리거나 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a2d812d65b824c799d9359a5c34c5153) |
| ☐ | `c85fcf78a5024aa7a14d830d551e6add` | audioclip-31436 | 0.5 | 0.802 | 무언가를 강하게 때리거나 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c85fcf78a5024aa7a14d830d551e6add) |
| ☐ | `d15b6ab16b63435ba5289244fd37bc9e` | audioclip-32866 | 1 | 0.802 | 무언가를 강하게 때리거나 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d15b6ab16b63435ba5289244fd37bc9e) |
| ☐ | `7525ab3df27044e08aa328df2ed8f285` | audioclip-18352 | 1 | 0.802 | 무거운 물체가 강하게 부딪히거나 타격하는 둔탁한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7525ab3df27044e08aa328df2ed8f285) |
| ☐ | `3d10e4720dbf43e783b43f8f74e27dd8` | audioclip-9674 | 1.1 | 0.802 | 무언가를 강하게 타격할 때 발생하는 둔탁한 물리적 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3d10e4720dbf43e783b43f8f74e27dd8) |
| ☐ | `05f4bdbfd9e8406986375fbaddc18e41` | audioclip-62385 | 2.5 | 0.802 | 무언가에 강하게 부딪히거나 타격하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=05f4bdbfd9e8406986375fbaddc18e41) |
| ☐ | `e50a699bdb824b7aa97c5ef97018cd9b` | audioclip-35995 | 3.8 | 0.801 | 무언가를 강하게 타격할 때 발생하는 둔탁한 물리적 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e50a699bdb824b7aa97c5ef97018cd9b) |
| ☐ | `178cf11ac14b474db7a0b3f8f4312af5` | audioclip-3850 | 3 | 0.8 | 물체나 생명체를 타격할 때 발생하는 둔탁한 물리적 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=178cf11ac14b474db7a0b3f8f4312af5) |
| ☐ | `ac984a6134ef43e08d07a28a7035b19f` | audioclip-27062 | 3.1 | 0.8 | 무언가에 강하게 부딪히는 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ac984a6134ef43e08d07a28a7035b19f) |
| ☐ | `ed8d48f147054e15ada730ea9285b298` | audioclip-37295 | 1.3 | 0.799 | 무언가에 강하게 부딪히거나 주먹으로 때리는 듯한 둔탁한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ed8d48f147054e15ada730ea9285b298) |


## 사망

### 사망-버섯/몬스터  <sub>(effect, 검색어: 몬스터가 쓰러지며 죽는 소리 귀여운 몬스터 사망)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `3e5f10c5cb474365b501c40994067602` | audioclip-62059 | 0.8 | 0.898 | 작은 몬스터가 쓰러지거나 타격을 입었을 때 발생하는 짧고 귀여운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e5f10c5cb474365b501c40994067602) |
| ☐ | `91c9bd697673466f89eed8807dfa04e6` | audioclip-22801 | 1 | 0.892 | 작은 몬스터가 쓰러지거나 패배할 때 내는 귀엽고 높은 톤의 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=91c9bd697673466f89eed8807dfa04e6) |
| ☐ | `e0291e01149b402bbae6afa0dbe8601a` | audioclip-35217 | 0.7 | 0.887 | 몬스터가 공격을 받거나 죽을 때 내는 귀엽고 높은 톤의 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e0291e01149b402bbae6afa0dbe8601a) |
| ☐ | `59dbbe3b71664e3fa84bffdce8c9f2e5` | audioclip-14178 | 3.1 | 0.88 | 작고 귀여운 몬스터가 내는 짧고 높은 톤의 신음 소리 또는 사망 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=59dbbe3b71664e3fa84bffdce8c9f2e5) |
| ☐ | `02dc8ffa533246449577f65674e60ce7` | audioclip-40758 | 0.3 | 0.873 | 작고 귀여운 몬스터가 내는 짧고 높은 톤의 피격 또는 사망 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=02dc8ffa533246449577f65674e60ce7) |
| ☐ | `b05fc3e97a1547a6b3951b97c02ba004` | audioclip-27666 | 3.1 | 0.872 | 작은 몬스터가 죽으면서 연기와 함께 사라지는 듯한 귀엽고 짧은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b05fc3e97a1547a6b3951b97c02ba004) |
| ☐ | `3f970229ffde4240b129112a59925f93` | audioclip-62460 | 2.2 | 0.869 | 작은 몬스터나 생명체가 내는 귀엽고 짧은 비명 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3f970229ffde4240b129112a59925f93) |
| ☐ | `3ee3a15c8fe94c25b1a8b549ec02702d` | audioclip-9953 | 2.4 | 0.869 | 몬스터가 공격을 받아 쓰러지며 소멸하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3ee3a15c8fe94c25b1a8b549ec02702d) |
| ☐ | `568186642d68458382cf09a1b48340b6` | audioclip-13661 | 0.9 | 0.868 | 작고 귀여운 몬스터가 짧게 비명을 지르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=568186642d68458382cf09a1b48340b6) |
| ☐ | `fc8065ce3278419da877aba5a85c951d` | audioclip-60568 | 1.5 | 0.866 | 작고 귀여운 몬스터가 내는 높은 톤의 비명 소리 또는 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fc8065ce3278419da877aba5a85c951d) |
| ☐ | `b5347e9f652e4819960688e30d18febc` | audioclip-42623 | 0.8 | 0.862 | 작은 몬스터가 사라지거나 처치될 때 발생하는 귀엽고 높은 톤의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b5347e9f652e4819960688e30d18febc) |
| ☐ | `fd0e7008a86c45e4ae0d65f9c614b9c9` | audioclip-60046 | 3.3 | 0.861 | 귀여운 몬스터가 피격되거나 사라질 때 발생하는 짧은 비명과 마법적인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fd0e7008a86c45e4ae0d65f9c614b9c9) |
| ☐ | `7b760724ee2a49d7a2108bd3f18e7393` | audioclip-19362 | 0.6 | 0.86 | 작은 몬스터가 공격을 받거나 죽을 때 내는 짧고 높은 비명 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7b760724ee2a49d7a2108bd3f18e7393) |
| ☐ | `520776021603496ea2f03c587e741543` | audioclip-12974 | 0.3 | 0.859 | 작고 귀여운 몬스터가 내는 짧고 높은 톤의 비명 또는 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=520776021603496ea2f03c587e741543) |
| ☐ | `61013b1ef2c14903bd3a1d455145c2ec` | audioclip-15278 | 2.3 | 0.855 | 몬스터가 피격되거나 쓰러질 때 발생하는 익살스럽고 귀여운 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=61013b1ef2c14903bd3a1d455145c2ec) |
| ☐ | `547aa30b35ec4063914fb8c1d00a6a5f` | audioclip-13356 | 1.4 | 0.853 | 작은 몬스터가 피격당하거나 쓰러질 때 내는 짧고 높은 톤의 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=547aa30b35ec4063914fb8c1d00a6a5f) |
| ☐ | `60e2526f078d405d906f67a8d77505a7` | audioclip-15246 | 1.3 | 0.853 | 작은 몬스터가 죽거나 피해를 입을 때 내는 짧고 높은 톤의 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=60e2526f078d405d906f67a8d77505a7) |
| ☐ | `97dd2ad1279c49c6b66dd07a64c0b49a` | audioclip-23735 | 0.4 | 0.853 | 작은 몬스터가 내는 고음의 비명 또는 사망 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=97dd2ad1279c49c6b66dd07a64c0b49a) |
| ☐ | `ae7eaba52459412082057e2b932f1c1e` | audioclip-27381 | 1.1 | 0.853 | 작고 귀여운 몬스터가 내는 고음의 비명 또는 사망 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ae7eaba52459412082057e2b932f1c1e) |
| ☐ | `a9801d1846e94165bc105cda0965a02b` | audioclip-26573 | 0.6 | 0.852 | 작은 몬스터가 내는 고음의 비명 또는 사망 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a9801d1846e94165bc105cda0965a02b) |

### 사망-기계(레지스탕스)  <sub>(effect, 검색어: 로봇이 파괴되며 폭발하는 기계 고장 소리)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `a6142533f6f346c89df39643135d20d2` | audioclip-26013 | 1.7 | 0.906 | 기계나 로봇이 파괴되면서 발생하는 금속성 파편 소리와 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a6142533f6f346c89df39643135d20d2) |
| ☐ | `1cf6afc7dc5b4264b4f6018c11c46ab5` | audioclip-4696 | 4.2 | 0.897 | 거대한 기계나 로봇이 파괴되면서 발생하는 묵직한 금속성 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1cf6afc7dc5b4264b4f6018c11c46ab5) |
| ☐ | `06835c7073e44b00b0879257e832f798` | audioclip-1105 | 3 | 0.893 | 기계 장치나 로봇이 파괴되면서 발생하는 묵직한 금속성 파편 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=06835c7073e44b00b0879257e832f798) |
| ☐ | `90a873fffc75468f96eab1534a87c524` | audioclip-22637 | 2.4 | 0.884 | 거대한 기계나 로봇이 파괴되며 발생하는 묵직한 금속성 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=90a873fffc75468f96eab1534a87c524) |
| ☐ | `edd30a346bd940f49df442e6a0a0f04f` | audioclip-62890 | 3.4 | 0.883 | 거대한 로봇이나 기계 장치가 파괴되면서 발생하는 웅장한 금속성 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=edd30a346bd940f49df442e6a0a0f04f) |
| ☐ | `8582cd44c6404ea4a9c0eb566c0ff635` | audioclip-20965 | 6.7 | 0.876 | 거대한 기계 장치가 무너지거나 폭발하며 발생하는 육중한 금속 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8582cd44c6404ea4a9c0eb566c0ff635) |
| ☐ | `3efc931ab1d047e991147acad6c6921f` | audioclip-60124 | 1.6 | 0.872 | 거대한 기계나 로봇이 파괴되면서 발생하는 웅장하고 날카로운 금속성 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3efc931ab1d047e991147acad6c6921f) |
| ☐ | `41a75b650c0f49aeb756dcc09e66aeba` | audioclip-10403 | 4.8 | 0.867 | 무거운 기계 장치가 폭발하며 잔해들이 흩어지는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=41a75b650c0f49aeb756dcc09e66aeba) |
| ☐ | `1e0eb23729ea49518eed1218cb0e197d` | audioclip-4861 | 3.7 | 0.856 | 무거운 기계나 구조물이 파괴되며 발생하는 폭발음과 금속 파편이 흩어지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1e0eb23729ea49518eed1218cb0e197d) |
| ☐ | `a238844f65304bd3881084678c097e39` | audioclip-25434 | 0.6 | 0.855 | 금속성 기계 장치가 파괴되거나 무너지는 묵직한 폭발음과 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a238844f65304bd3881084678c097e39) |
| ☐ | `a3454564b92542c79a62d9c12b1e684a` | audioclip-25598 | 4.5 | 0.851 | 기계 장치가 작동한 후 무겁게 충돌하거나 파괴되는 금속성 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a3454564b92542c79a62d9c12b1e684a) |
| ☐ | `14fcf8ebcf494b739794fb2b586b0c11` | audioclip-3443 | 2.9 | 0.85 | 거대한 기계나 금속 구조물이 파괴되며 무너지는 묵직한 폭발음과 잔해 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=14fcf8ebcf494b739794fb2b586b0c11) |
| ☐ | `1aa049ad28364608b1ba365813e8a212` | audioclip-4330 | 0.7 | 0.848 | 무거운 기계나 거대 생명체가 파괴되며 무너지는 웅장한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1aa049ad28364608b1ba365813e8a212) |
| ☐ | `31c89b41618a428c9c007752fe8901c8` | audioclip-7927 | 2.6 | 0.848 | 거대한 기계 장치가 파괴되거나 폭발하며 발생하는 무겁고 날카로운 금속성 파편 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=31c89b41618a428c9c007752fe8901c8) |
| ☐ | `0704cf785dbe4c4db6b0d0cc00bf8199` | audioclip-1188 | 1.8 | 0.847 | 무거운 물체가 파괴되거나 폭발하며 잔해가 떨어지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0704cf785dbe4c4db6b0d0cc00bf8199) |
| ☐ | `50dfc1e7117e458f9532b17778166cdc` | audioclip-12794 | 6.3 | 0.846 | 금속성 기계가 파괴되거나 강력한 타격을 가할 때 발생하는 무겁고 폭발적인 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=50dfc1e7117e458f9532b17778166cdc) |
| ☐ | `ccc73c5a95db439d8ee44a60cc69e385` | audioclip-32145 | 4.9 | 0.846 | 무겁고 거대한 기계 장치나 구조물이 파괴되는 강력한 폭발음과 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ccc73c5a95db439d8ee44a60cc69e385) |
| ☐ | `3d696b34bdb74f1ab3c4ab0ae832de48` | audioclip-9727 | 6 | 0.846 | 거대한 기계 장치나 구조물이 파괴되며 무너지는 웅장하고 묵직한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3d696b34bdb74f1ab3c4ab0ae832de48) |
| ☐ | `a7713015038c475a83a61dcda9883ee5` | audioclip-26238 | 2.1 | 0.843 | 거대한 기계 생명체가 움직이다가 강력하게 타격하거나 폭발하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a7713015038c475a83a61dcda9883ee5) |
| ☐ | `8c0b92d87191416183ed21cc62b55b2b` | audioclip-21951 | 2.6 | 0.842 | 무거운 금속 물체가 부서지거나 파괴되는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8c0b92d87191416183ed21cc62b55b2b) |

### 사망-기사/정령(시그너스)  <sub>(effect, 검색어: 전사가 쓰러지는 신음 기사 사망)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `f10ce91969e2454a99186b594f9de6a8` | audioclip-61951 | 1.1 | 0.742 | 생명체가 타격을 입고 바닥으로 쓰러지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f10ce91969e2454a99186b594f9de6a8) |
| ☐ | `3e9b2499798d406aaa06053cb000f532` | audioclip-9900 | 1.9 | 0.735 | 몬스터가 고통을 느끼거나 쓰러질 때 내는 깊고 거친 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e9b2499798d406aaa06053cb000f532) |
| ☐ | `e82454a7210c4c6da3e89a5d0bef9593` | audioclip-36487 | 0.9 | 0.734 | 몬스터가 고통을 느끼거나 쓰러질 때 내는 괴성 또는 신음 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e82454a7210c4c6da3e89a5d0bef9593) |
| ☐ | `d59f1c67762c4a769ac1748598aa6915` | audioclip-42974 | 1.7 | 0.732 | 몬스터가 고통스러워하거나 쓰러질 때 내는 신음 섞인 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d59f1c67762c4a769ac1748598aa6915) |
| ☐ | `c56ec9a053f9494092632e2bc0809c5d` | audioclip-30955 | 1.1 | 0.73 | 몬스터가 쓰러지거나 고통을 느낄 때 내는 낮고 굵은 신음 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c56ec9a053f9494092632e2bc0809c5d) |
| ☐ | `44a3c21284434f8cb1733e5a80dee974` | audioclip-10873 | 0.7 | 0.729 | 몬스터가 쓰러지거나 고통을 느낄 때 내는 낮고 굵은 신음 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=44a3c21284434f8cb1733e5a80dee974) |
| ☐ | `4be8734c531f48e899db39e140c600ba` | audioclip-12001 | 1.8 | 0.729 | 몬스터가 죽으면서 내는 비명 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4be8734c531f48e899db39e140c600ba) |
| ☐ | `84e817065afb4b28970449a0e65d9c7e` | audioclip-20867 | 0.9 | 0.729 | 몬스터가 공격을 받거나 쓰러질 때 내는 짧고 거친 괴성 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=84e817065afb4b28970449a0e65d9c7e) |
| ☐ | `d9e1910ecb6044679889e9cff45b8c1f` | audioclip-34270 | 0.9 | 0.728 | 몬스터가 짧게 신음하거나 쓰러질 때 발생하는 괴물 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d9e1910ecb6044679889e9cff45b8c1f) |
| ☐ | `29723f446bff4bc88455b14f73ebb2ba` | audioclip-6670 | 1.3 | 0.728 | 몬스터가 고통스러워하거나 쓰러질 때 내는 낮고 굵은 울음소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=29723f446bff4bc88455b14f73ebb2ba) |
| ☐ | `ba0338a3b0984eaf96ed796729d7d094` | audioclip-29166 | 3.3 | 0.727 | 거대한 괴물이 신음을 내뱉으며 바닥에 쓰러지는 묵직한 사망 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ba0338a3b0984eaf96ed796729d7d094) |
| ☐ | `6e7f33630287400eb458d108daf911b3` | audioclip-41894 | 1.1 | 0.726 | 작은 몬스터가 고통을 느끼거나 쓰러질 때 내는 짧은 신음 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6e7f33630287400eb458d108daf911b3) |
| ☐ | `7a87f3bbb5684629baeec4e26841cd11` | audioclip-19208 | 1.9 | 0.726 | 몬스터가 고통스러워하거나 쓰러질 때 내는 굵고 낮은 비명 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7a87f3bbb5684629baeec4e26841cd11) |
| ☐ | `a3c50ff73fda47c3a3d01f204b056801` | audioclip-25664 | 4.3 | 0.725 | 몬스터가 공격을 받아 비명을 지르며 쓰러지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a3c50ff73fda47c3a3d01f204b056801) |
| ☐ | `a4e24be2940841818fdaca10dbe7dc61` | audioclip-25838 | 1.3 | 0.724 | 몬스터가 죽거나 고통스러워하며 내는 낮은 톤의 신음 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a4e24be2940841818fdaca10dbe7dc61) |
| ☐ | `b68341c1300e442882c17d5ff63ff58b` | audioclip-28634 | 2 | 0.723 | 몬스터가 고통을 느끼거나 쓰러질 때 내는 거친 신음 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b68341c1300e442882c17d5ff63ff58b) |
| ☐ | `3c294c93d8ff43249163109860e50ec1` | audioclip-9542 | 0.7 | 0.72 | 몬스터가 죽으면서 내는 거칠고 낮은 괴성 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3c294c93d8ff43249163109860e50ec1) |
| ☐ | `3aa50248112c434db401406c128256e8` | audioclip-9320 | 1.3 | 0.719 | 몬스터가 고통스러워하거나 쓰러질 때 내는 낮고 거친 신음 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3aa50248112c434db401406c128256e8) |
| ☐ | `7a70711ed2784fb08c4543508b7adbe8` | audioclip-19193 | 1.3 | 0.719 | 몬스터가 고통스러워하거나 쓰러질 때 내는 낮고 굵은 신음 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7a70711ed2784fb08c4543508b7adbe8) |
| ☐ | `6602e7427f9a4e3ba0efd85c0b3a37bf` | audioclip-16044 | 1.2 | 0.719 | 몬스터가 고통스러워하거나 쓰러질 때 내는 낮고 굵은 신음 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6602e7427f9a4e3ba0efd85c0b3a37bf) |

### 사망-정령 소멸  <sub>(effect, 검색어: 정령이 사라지는 신비로운 소멸 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `a6ddb23645f9475487c817f5c7738927` | audioclip-26142 | 0.4 | 0.818 | 무언가 사라지거나 나타날 때 들리는 가벼운 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a6ddb23645f9475487c817f5c7738927) |
| ☐ | `c591695ca285470ebedf9523c622f09a` | audioclip-30988 | 1.9 | 0.812 | 마법 에너지가 방출되며 반짝이는 소리가 나는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c591695ca285470ebedf9523c622f09a) |
| ☐ | `ef39a94ca4a14a38af9af5ef410375e6` | audioclip-37571 | 1.9 | 0.806 | 마법 에너지가 폭발하며 발생하는 화려하고 강력한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ef39a94ca4a14a38af9af5ef410375e6) |
| ☐ | `3ee3a15c8fe94c25b1a8b549ec02702d` | audioclip-9953 | 2.4 | 0.803 | 몬스터가 공격을 받아 쓰러지며 소멸하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3ee3a15c8fe94c25b1a8b549ec02702d) |
| ☐ | `7053276ac2fb42f8b45101d979c03414` | audioclip-17607 | 3.4 | 0.8 | 몬스터가 포효하며 마법적인 기운과 함께 사라지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7053276ac2fb42f8b45101d979c03414) |
| ☐ | `69934328d6f04bf0b457ab6399b61954` | audioclip-41838 | 0.3 | 0.792 | 무언가 사라지거나 나타날 때 발생하는 짧은 마법 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=69934328d6f04bf0b457ab6399b61954) |
| ☐ | `2fe5601dc9304269bf37a6f0f3c151a7` | audioclip-7624 | 0.8 | 0.788 | UI 알림이나 마법 효과로 사용하기 좋은 맑고 높은 톤의 띵 하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2fe5601dc9304269bf37a6f0f3c151a7) |
| ☐ | `b05fc3e97a1547a6b3951b97c02ba004` | audioclip-27666 | 3.1 | 0.783 | 작은 몬스터가 죽으면서 연기와 함께 사라지는 듯한 귀엽고 짧은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b05fc3e97a1547a6b3951b97c02ba004) |
| ☐ | `4592ef3cf3e047dfb4cb40b640cf5f01` | audioclip-60529 | 3.7 | 0.782 | 신비롭고 반짝이는 느낌의 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4592ef3cf3e047dfb4cb40b640cf5f01) |
| ☐ | `b5347e9f652e4819960688e30d18febc` | audioclip-42623 | 0.8 | 0.782 | 작은 몬스터가 사라지거나 처치될 때 발생하는 귀엽고 높은 톤의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b5347e9f652e4819960688e30d18febc) |
| ☐ | `f152396c480b4a6686d4a3314b7ea096` | audioclip-37914 | 2.4 | 0.782 | 몬스터가 타격을 입고 비명을 지르며 폭발하듯 소멸하는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f152396c480b4a6686d4a3314b7ea096) |
| ☐ | `1f4a844305164a6483e6b9a79227ae90` | audioclip-5038 | 5.2 | 0.781 | 마법 에너지가 방출되며 신비로운 잔향을 남기는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1f4a844305164a6483e6b9a79227ae90) |
| ☐ | `fc1e7f7b017e451d9cd0e2522ffef63f` | audioclip-39605 | 3.9 | 0.778 | 신비롭고 영롱한 느낌의 마법 효과음 또는 포탈 활성화 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fc1e7f7b017e451d9cd0e2522ffef63f) |
| ☐ | `ab3f4f67106141148973e4fa3a420c3d` | audioclip-26837 | 4.3 | 0.778 | 마법적인 에너지가 터지거나 흩어지는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ab3f4f67106141148973e4fa3a420c3d) |
| ☐ | `452beac8f22941a7b7f9d4bfe9632ade` | audioclip-10957 | 2.8 | 0.777 | 신비로운 느낌의 마법 효과음 또는 스킬 발동 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=452beac8f22941a7b7f9d4bfe9632ade) |
| ☐ | `c4bea62181cf46d98a99f9d695823249` | audioclip-30826 | 3.2 | 0.777 | 유리나 크리스탈이 깨지면서 마법적인 잔향이 남는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c4bea62181cf46d98a99f9d695823249) |
| ☐ | `44c8a3d4261949afb64af7ee4c24544e` | audioclip-10894 | 3.9 | 0.776 | 신비로운 분위기를 자아내는 마법적인 바람 소리와 잔향 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=44c8a3d4261949afb64af7ee4c24544e) |
| ☐ | `6fdbc3a1d599476dac75aedf719a6b9d` | audioclip-17536 | 0.7 | 0.776 | 마법 에너지가 폭발하거나 흩어지는 듯한 신비로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6fdbc3a1d599476dac75aedf719a6b9d) |
| ☐ | `92b9bfeb33cb42548f569be17dcb61ea` | audioclip-22949 | 3.7 | 0.775 | 신비롭고 반짝이는 느낌의 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=92b9bfeb33cb42548f569be17dcb61ea) |
| ☐ | `e9092afab4f84c63840d837033d52c11` | audioclip-36626 | 1.5 | 0.775 | 유리나 크리스탈이 깨지는 듯한 소리와 마법적인 잔향이 섞인 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e9092afab4f84c63840d837033d52c11) |


## 상태

### 상태-독  <sub>(effect, 검색어: 독 중독 효과음 보글보글 녹색 연기)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `36fc9491e2244be5a0a375ead8390062` | audioclip-8742 | 1.2 | 0.748 | 액체가 보글보글 끓어오르는 마법적인 분위기의 환경음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=36fc9491e2244be5a0a375ead8390062) |
| ☐ | `1d88e852d83b42fca9307f7767fe73b0` | audioclip-4793 | 14.1 | 0.736 | 물이 끓거나 보글거리는 소리가 반복되는 환경음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1d88e852d83b42fca9307f7767fe73b0) |
| ☐ | `6a22834ef8414c809131155793933637` | audioclip-16655 | 2.1 | 0.734 | 물이 보글보글 끓거나 거품이 일어나는 액체의 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6a22834ef8414c809131155793933637) |
| ☐ | `bb3518e616e044fe85b50b297c023cb5` | audioclip-29346 | 1.2 | 0.716 | 물이나 포션을 마시는 듯한 액체 소리와 꿀꺽하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bb3518e616e044fe85b50b297c023cb5) |
| ☐ | `70ef48370f5c42ac8c1cd8ec0933abce` | audioclip-17703 | 0.2 | 0.713 | UI 버튼을 클릭하거나 아이템을 선택할 때 발생하는 짧고 깔끔한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=70ef48370f5c42ac8c1cd8ec0933abce) |
| ☐ | `78aa66c8dbd141ac82bff057e73c7d66` | audioclip-18900 | 0.2 | 0.711 | UI 메뉴를 선택하거나 버튼을 누를 때 발생하는 짧고 기계적인 클릭음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=78aa66c8dbd141ac82bff057e73c7d66) |
| ☐ | `fbc82c9f2524497c81aea0a647043ab9` | audioclip-39548 | 0.5 | 0.71 | UI 알림이나 마법 효과에 어울리는 반짝이는 느낌의 짧은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fbc82c9f2524497c81aea0a647043ab9) |
| ☐ | `85a547add7f74168b5a51eaaaafbfd03` | audioclip-20986 | 1.2 | 0.707 | 나무 상자나 물체가 부서지는 날카로운 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=85a547add7f74168b5a51eaaaafbfd03) |
| ☐ | `28d533ac6531424e806cfa3a98becf10` | audioclip-6553 | 6 | 0.704 | 몬스터가 거칠게 숨을 내뱉거나 쓰러질 때 발생하는 어두운 분위기의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=28d533ac6531424e806cfa3a98becf10) |
| ☐ | `f73ef7ffd6e64bd08e6f73e5a13d0746` | audioclip-38862 | 2.3 | 0.704 | 무거운 금속 기계 장치가 작동하거나 육중한 문이 열리는 듯한 기계음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f73ef7ffd6e64bd08e6f73e5a13d0746) |
| ☐ | `eb7f504670a14802a48cc94f4eb66848` | audioclip-36985 | 2.6 | 0.704 | 밝고 경쾌한 느낌의 마법적인 UI 효과음 또는 아이템 획득 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=eb7f504670a14802a48cc94f4eb66848) |
| ☐ | `b05fc3e97a1547a6b3951b97c02ba004` | audioclip-27666 | 3.1 | 0.704 | 작은 몬스터가 죽으면서 연기와 함께 사라지는 듯한 귀엽고 짧은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b05fc3e97a1547a6b3951b97c02ba004) |
| ☐ | `0cb1b8dc79d64442a4414266cde1ae36` | audioclip-2072 | 1.1 | 0.702 | 무언가 부서지거나 파괴되는 날카로운 충격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0cb1b8dc79d64442a4414266cde1ae36) |
| ☐ | `b16805edc528469995a48e29a738dfe6` | audioclip-27822 | 1.8 | 0.701 | 액체가 보글거리거나 쏟아지는 듯한 물 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b16805edc528469995a48e29a738dfe6) |
| ☐ | `0bd54abbd7724e3f855723bca5989d31` | audioclip-1942 | 2.8 | 0.7 | 물이 튀는 듯한 첨벙거리는 소리와 액체 반응음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0bd54abbd7724e3f855723bca5989d31) |
| ☐ | `ef0eef70a3fd49ae95ea296b2b1eb263` | audioclip-37535 | 1.3 | 0.7 | 슬라임이나 생명체가 움직이거나 소리를 내는 끈적하고 젖은 느낌의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ef0eef70a3fd49ae95ea296b2b1eb263) |
| ☐ | `65034254e014410ca1ea0805484c7094` | audioclip-15898 | 1.6 | 0.696 | 무거운 금속 물체가 떨어지며 발생하는 육중한 충격음과 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=65034254e014410ca1ea0805484c7094) |
| ☐ | `ad3fde2e53314fe29ec759886bc88e04` | audioclip-42545 | 2.3 | 0.695 | 물이나 포션을 따르거나 흔들 때 발생하는 액체 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ad3fde2e53314fe29ec759886bc88e04) |
| ☐ | `51c7d5c3360a4d33a5185f4e6be7689b` | audioclip-41609 | 2 | 0.694 | 아이템을 먹거나 마실 때 발생하는 아삭거리는 소리와 삼키는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=51c7d5c3360a4d33a5185f4e6be7689b) |
| ☐ | `f152396c480b4a6686d4a3314b7ea096` | audioclip-37914 | 2.4 | 0.693 | 몬스터가 타격을 입고 비명을 지르며 폭발하듯 소멸하는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f152396c480b4a6686d4a3314b7ea096) |

### 상태-냉기(감속)  <sub>(effect, 검색어: 얼음 결빙 차가운 효과음 얼어붙음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `e3cd1b75d711469496dbd3421b912866` | audioclip-60392 | 5.7 | 0.818 | 기합 소리와 함께 얼음 파편이 튀는 듯한 강력한 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e3cd1b75d711469496dbd3421b912866) |
| ☐ | `8f5f0945ced5413eb33dd2a7b191d198` | audioclip-22449 | 3.4 | 0.817 | 얼음이나 마법 에너지가 날카롭게 타격하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8f5f0945ced5413eb33dd2a7b191d198) |
| ☐ | `44a9ca3e82514bebbec48f7a05533e47` | audioclip-60746 | 1.8 | 0.817 | 얼음이나 유리가 산산조각 나며 부서지는 날카롭고 강한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=44a9ca3e82514bebbec48f7a05533e47) |
| ☐ | `2ea1dc61e3124bafb89c2c0c894d3566` | audioclip-7435 | 2.9 | 0.815 | 얼음이 깨지는 듯한 날카로운 타격음이 포함된 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2ea1dc61e3124bafb89c2c0c894d3566) |
| ☐ | `2151c37d1df940acb176aace7c748737` | audioclip-5362 | 2.5 | 0.811 | 얼음 조각이 부서지는 듯한 날카로운 타격음과 마법적인 잔향이 포함된 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2151c37d1df940acb176aace7c748737) |
| ☐ | `d5d5249bee0c49239cf4a82a8bee7c25` | audioclip-33587 | 4.5 | 0.811 | 마법 에너지가 폭발하며 얼음 파편이 튀는 듯한 날카로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d5d5249bee0c49239cf4a82a8bee7c25) |
| ☐ | `7644fcded89e4ce0915f4018ffb13196` | audioclip-18530 | 3.2 | 0.807 | 얼음 파편이 튀는 듯한 날카롭고 신비로운 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7644fcded89e4ce0915f4018ffb13196) |
| ☐ | `17a7db410475410291fde72bbda1103f` | audioclip-3863 | 3 | 0.806 | 강력한 얼음 마법이 폭발하며 주변을 얼리는 듯한 날카롭고 웅장한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=17a7db410475410291fde72bbda1103f) |
| ☐ | `5080bc200e7741ee834a59b7ef2feec5` | audioclip-12743 | 4.1 | 0.792 | 여러 번의 타격음과 함께 얼음이나 유리가 깨지는 듯한 강력한 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5080bc200e7741ee834a59b7ef2feec5) |
| ☐ | `1427847ba8e0443cb1db27d5407fa750` | audioclip-40947 | 0.9 | 0.785 | 유리나 얼음이 날카롭게 깨지는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1427847ba8e0443cb1db27d5407fa750) |
| ☐ | `1718ed6e31af403f99b042403e771e6b` | audioclip-3774 | 3.1 | 0.783 | 유리나 얼음 조각이 날카롭게 깨지는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1718ed6e31af403f99b042403e771e6b) |
| ☐ | `ebfc7ec070324eb1b1af6edd082a3266` | audioclip-37059 | 2.4 | 0.781 | 강력한 마법 에너지가 폭발하며 얼음이 깨지는 듯한 화려한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ebfc7ec070324eb1b1af6edd082a3266) |
| ☐ | `9df3b3409a864115b242d0ae60dceb88` | audioclip-24687 | 3.4 | 0.78 | 마법 에너지가 방출된 후 얼음이나 결정체가 부서지는 듯한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9df3b3409a864115b242d0ae60dceb88) |
| ☐ | `8541efcc979b4d48bd46fac2d5e85b06` | audioclip-20927 | 4.5 | 0.778 | 유리나 얼음이 날카롭게 깨지는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8541efcc979b4d48bd46fac2d5e85b06) |
| ☐ | `89b21f0d8203428fbaa27ce435df437b` | audioclip-21595 | 3.2 | 0.778 | 유리나 얼음이 날카롭게 깨지는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=89b21f0d8203428fbaa27ce435df437b) |
| ☐ | `d7f7a6f817a5410ead5f0966468540ac` | audioclip-33941 | 1.4 | 0.778 | 유리나 얼음이 날카롭게 깨지는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d7f7a6f817a5410ead5f0966468540ac) |
| ☐ | `0e97d39a68ad4a978268579a606e64fc` | audioclip-2393 | 0.9 | 0.777 | 유리나 얼음 같은 물체가 날카롭게 깨지는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0e97d39a68ad4a978268579a606e64fc) |
| ☐ | `27e9cf2757f24aae99a1cee78f33c959` | audioclip-6407 | 0.9 | 0.775 | 나무나 상자가 부서지는 듯한 날카로운 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=27e9cf2757f24aae99a1cee78f33c959) |
| ☐ | `35e6af7a2ebd437eb23203e70f473110` | audioclip-8580 | 1.9 | 0.775 | 무거운 물체가 부서지거나 얼음 또는 유리가 산산조각 나는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=35e6af7a2ebd437eb23203e70f473110) |
| ☐ | `efe97472bc874bb68e027cb8d3cacfbe` | audioclip-37683 | 4.5 | 0.773 | 유리나 얼음 같은 단단한 물체가 산산조각 나며 부서지는 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=efe97472bc874bb68e027cb8d3cacfbe) |

### 상태-저주  <sub>(effect, 검색어: 어둠의 저주 음산한 마법 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `f9165961f1264db98c48fd4bb3bba0a7` | audioclip-39131 | 1.7 | 0.83 | 어둡고 신비로운 분위기의 낮고 웅장한 마법 공명음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f9165961f1264db98c48fd4bb3bba0a7) |
| ☐ | `9fc0a82bbf62442daa37294f6d873f2b` | audioclip-25002 | 1 | 0.829 | 어둡고 신비로운 느낌의 저음 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9fc0a82bbf62442daa37294f6d873f2b) |
| ☐ | `13c63fa45ad543c8889003b5b9bc7a63` | audioclip-3248 | 1 | 0.827 | 어둡고 신비로운 분위기의 저음 마법 파동 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=13c63fa45ad543c8889003b5b9bc7a63) |
| ☐ | `5522ad3f293a4ad5a28ff3137ab54d02` | audioclip-13483 | 6 | 0.823 | 어둡고 강력한 마법 에너지가 폭발하며 울려 퍼지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5522ad3f293a4ad5a28ff3137ab54d02) |
| ☐ | `75d9d05cf1524d48adab89d1d0846745` | audioclip-18471 | 6 | 0.822 | 강력하고 어두운 마법 에너지가 폭발하며 울려 퍼지는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=75d9d05cf1524d48adab89d1d0846745) |
| ☐ | `cd790a500e8d47fe9cb694d501a07432` | audioclip-32266 | 6 | 0.821 | 강력하고 어두운 마법 에너지가 폭발하는 듯한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cd790a500e8d47fe9cb694d501a07432) |
| ☐ | `2a45bfaa3c4e4920b4851584e698510c` | audioclip-6777 | 7.7 | 0.817 | 낮고 웅장하게 울리는 마법 효과음 또는 무거운 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a45bfaa3c4e4920b4851584e698510c) |
| ☐ | `e3c0333d0c514cd88cb535f23e1b9206` | audioclip-43126 | 5.8 | 0.813 | 어둠의 마법 에너지가 폭발하며 발생하는 웅장하고 강력한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e3c0333d0c514cd88cb535f23e1b9206) |
| ☐ | `ef43c9e459534cd79e11f477e906eed4` | audioclip-60446 | 6 | 0.812 | 강력하고 어두운 분위기의 마법 폭발 또는 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ef43c9e459534cd79e11f477e906eed4) |
| ☐ | `f319b1cb847747a98c19d05f51f024a7` | audioclip-38223 | 3.9 | 0.807 | 어둡고 웅장한 느낌의 마법 효과음 또는 강력한 스킬 시전 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f319b1cb847747a98c19d05f51f024a7) |
| ☐ | `9d2aa08329ae4cbfa275a8ebdce80157` | audioclip-62909 | 7 | 0.807 | 어둡고 강력한 마법 에너지가 방출되거나 포탈이 열리는 듯한 신비로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9d2aa08329ae4cbfa275a8ebdce80157) |
| ☐ | `f79cd8baed714394a46076bdaaee430e` | audioclip-38914 | 3.5 | 0.805 | 강력한 마법 에너지가 폭발하며 퍼지는 묵직한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f79cd8baed714394a46076bdaaee430e) |
| ☐ | `c84d0ce343904731aa95cea9da09d2a6` | audioclip-31419 | 5.3 | 0.801 | 강력한 마법 에너지가 방출되며 폭발하는 웅장하고 어두운 느낌의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c84d0ce343904731aa95cea9da09d2a6) |
| ☐ | `ad1d72a567e741c699b6a8eadda26fa2` | audioclip-27146 | 2.3 | 0.8 | 낮고 웅장하게 울리는 마법적인 에너지 또는 환경적인 진동음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ad1d72a567e741c699b6a8eadda26fa2) |
| ☐ | `d72b8c9b578a4800a47ebc9eb3ac3f56` | audioclip-33811 | 5.7 | 0.8 | 몬스터의 낮은 으르렁거림과 함께 어두운 마법 에너지가 방출되는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d72b8c9b578a4800a47ebc9eb3ac3f56) |
| ☐ | `5b32d6ca97d8427ba4b77796c0620703` | audioclip-14370 | 2.7 | 0.799 | 강력한 마법 폭발이나 무거운 타격이 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5b32d6ca97d8427ba4b77796c0620703) |
| ☐ | `f9585f0794bc4e8ea762e6885b2c2326` | audioclip-39166 | 5.2 | 0.793 | 강력한 마법이나 기술이 폭발하며 발생하는 무겁고 웅장한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f9585f0794bc4e8ea762e6885b2c2326) |
| ☐ | `54dc385f33cd4006aba1e2d636a65eb9` | audioclip-13414 | 5.3 | 0.793 | 어둠의 마법 에너지가 폭발하며 여러 번 타격하는 강력한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=54dc385f33cd4006aba1e2d636a65eb9) |
| ☐ | `89fa051abb37429e9857d549d50f791d` | audioclip-62886 | 7 | 0.793 | 강력한 마법 폭발이나 에너지 파동이 연속적으로 발생하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=89fa051abb37429e9857d549d50f791d) |
| ☐ | `df72552e23304b9293918c58fc09887c` | audioclip-35090 | 5.7 | 0.793 | 몬스터의 낮은 으르렁거림과 함께 발생하는 어둡고 강력한 마법 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=df72552e23304b9293918c58fc09887c) |

### 상태-화상  <sub>(effect, 검색어: 불타는 화상 지글지글 불꽃 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `524b08c78e0b497aa5627b95ec219382` | audioclip-13024 | 3.4 | 0.834 | 강력한 화염 마법이 폭발하며 타오르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=524b08c78e0b497aa5627b95ec219382) |
| ☐ | `cecc2c8817e0434bb210acec299e2731` | audioclip-32463 | 4 | 0.832 | 불꽃이 폭발하며 타오르는 듯한 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cecc2c8817e0434bb210acec299e2731) |
| ☐ | `73fa9fbd48594ea7a95a198349449eb7` | audioclip-18169 | 2 | 0.831 | 강력한 화염 마법이나 폭발 스킬의 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=73fa9fbd48594ea7a95a198349449eb7) |
| ☐ | `b602decaf6b244a0a70e92ac2fdcd245` | audioclip-61050 | 1.1 | 0.829 | 불이 활활 타오르며 무언가 타는 듯한 강렬한 화염 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b602decaf6b244a0a70e92ac2fdcd245) |
| ☐ | `4fb384a2bcfa456f87e96a1d2a7e002d` | audioclip-12606 | 16.3 | 0.828 | 강력한 화염 마법이 폭발하며 지속적으로 타오르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4fb384a2bcfa456f87e96a1d2a7e002d) |
| ☐ | `6034c63dc99b4e349e6335174a1b735b` | audioclip-15163 | 3.4 | 0.828 | 강력한 폭발과 함께 불길이 타오르는 화염 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6034c63dc99b4e349e6335174a1b735b) |
| ☐ | `ec8e3cae38944ea2b30124dd31a6bb22` | audioclip-37135 | 1.6 | 0.826 | 거세게 타오르는 불길과 장작이 타는 듯한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ec8e3cae38944ea2b30124dd31a6bb22) |
| ☐ | `6fc0530c9c634c2e90f5a15ccea2975d` | audioclip-17506 | 3.4 | 0.825 | 강력한 화염 마법이 폭발하며 주변을 불태우는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6fc0530c9c634c2e90f5a15ccea2975d) |
| ☐ | `6eda7181fcde474582637ee058da934a` | audioclip-17375 | 7.3 | 0.823 | 강력한 화염 마법이 폭발하며 주변을 태우는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6eda7181fcde474582637ee058da934a) |
| ☐ | `a0cda3bb612a454bb115f3fa1f7c8ecb` | audioclip-25158 | 3 | 0.823 | 강력한 불길이 뿜어져 나오며 타오르는 마법 공격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a0cda3bb612a454bb115f3fa1f7c8ecb) |
| ☐ | `97c8ba01250944cf851e4186459f76bc` | audioclip-23726 | 3.8 | 0.822 | 강렬하게 타오르는 불꽃이나 화염 마법의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=97c8ba01250944cf851e4186459f76bc) |
| ☐ | `0b253c5fcf224ac09916b223579aa536` | audioclip-1825 | 3.6 | 0.821 | 강력한 화염 마법이 여러 번 폭발하며 적을 타격하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0b253c5fcf224ac09916b223579aa536) |
| ☐ | `56446062a2cb481aa77252884629f70a` | audioclip-13637 | 4.6 | 0.818 | 강력한 화염 폭발과 함께 타오르는 소리가 담긴 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=56446062a2cb481aa77252884629f70a) |
| ☐ | `dccd705bd3e149138ba7879b46443a5d` | audioclip-34687 | 3.4 | 0.818 | 강력한 화염 마법이 폭발하며 주변을 휩쓰는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dccd705bd3e149138ba7879b46443a5d) |
| ☐ | `14c9097916fe47df9a5917dd69b825d9` | audioclip-3413 | 3.2 | 0.818 | 강력한 화염 마법이 폭발하며 주변을 휩쓰는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=14c9097916fe47df9a5917dd69b825d9) |
| ☐ | `a5dd1b7c2fa441d580e818942c73b257` | audioclip-25984 | 3.7 | 0.817 | 강력한 불길이 솟구치며 타오르는 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a5dd1b7c2fa441d580e818942c73b257) |
| ☐ | `ed90fcdcceac437aa8b82259b8082bb4` | audioclip-37297 | 2.9 | 0.817 | 강렬한 불꽃이 터지거나 화염 마법을 사용하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ed90fcdcceac437aa8b82259b8082bb4) |
| ☐ | `bc7f68aaff344206b359fd945efcf70d` | audioclip-29548 | 6.1 | 0.816 | 강력한 불길이 지속적으로 타오르며 에너지를 내뿜는 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bc7f68aaff344206b359fd945efcf70d) |
| ☐ | `fbc480fa78cb4ce1a15dab977db82ecc` | audioclip-39544 | 1.6 | 0.816 | 거세게 타오르는 불길과 장작이 타는 듯한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fbc480fa78cb4ce1a15dab977db82ecc) |
| ☐ | `f3499946e86c4a1ca6f92000ab641d5f` | audioclip-38262 | 3.4 | 0.811 | 강력한 화염이 폭발하며 거세게 타오르는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f3499946e86c4a1ca6f92000ab641d5f) |


## 치유

### 치유(힐)  <sub>(effect, 검색어: 치유 회복 마법 반짝이는 힐 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `52b846955ca840db97ebfe104d779edd` | audioclip-13081 | 1.5 | 0.855 | 밝고 반짝이는 느낌의 UI 성공 또는 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=52b846955ca840db97ebfe104d779edd) |
| ☐ | `c1158dc120ca4e1b8751d814994b1f5a` | audioclip-30261 | 1.2 | 0.85 | 마법적인 느낌의 반짝이는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c1158dc120ca4e1b8751d814994b1f5a) |
| ☐ | `efb3e0b05b9746e8a59068f41f66f226` | audioclip-37655 | 1.2 | 0.849 | 마법적인 느낌의 반짝이는 스킬 효과음 또는 버프 적용 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=efb3e0b05b9746e8a59068f41f66f226) |
| ☐ | `b777c54d0ec0461f83ebce87596581bd` | audioclip-28778 | 0.9 | 0.847 | 마법 효과음으로, 반짝이는 소리와 함께 버프나 스킬이 적용되는 듯한 밝은 느낌의 사운드 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b777c54d0ec0461f83ebce87596581bd) |
| ☐ | `f631a021cdd54282850b11703eea7d14` | audioclip-38707 | 2.9 | 0.847 | 신비롭고 반짝이는 느낌의 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f631a021cdd54282850b11703eea7d14) |
| ☐ | `f541cc5e9de6478aa686a9e54a29c977` | audioclip-38569 | 2.2 | 0.846 | 반짝이는 느낌의 밝고 신비로운 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f541cc5e9de6478aa686a9e54a29c977) |
| ☐ | `faf1c3b2748f47d5beca2475dcac915e` | audioclip-39416 | 2.9 | 0.846 | 신비롭고 반짝이는 느낌의 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=faf1c3b2748f47d5beca2475dcac915e) |
| ☐ | `3f093139b1bf4804baee2549865e06e9` | audioclip-9981 | 0.5 | 0.845 | 마법적인 느낌의 반짝이는 효과음 또는 스킬 사용음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3f093139b1bf4804baee2549865e06e9) |
| ☐ | `591817cda69b47aba2b3eaccb06535bb` | audioclip-14074 | 2.6 | 0.845 | 마법 효과음으로, 반짝이는 소리와 함께 스킬을 사용하거나 버프를 받는 듯한 밝은 느낌의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=591817cda69b47aba2b3eaccb06535bb) |
| ☐ | `e46fd230851541c880db8e148e740a23` | audioclip-35902 | 1.2 | 0.844 | 마법 기술이나 버프 효과에 어울리는 반짝이는 느낌의 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e46fd230851541c880db8e148e740a23) |
| ☐ | `c8a932a8c547433c9ec4691651ce92b6` | audioclip-31486 | 1.1 | 0.844 | 신비롭고 반짝이는 느낌의 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c8a932a8c547433c9ec4691651ce92b6) |
| ☐ | `c40625d1d1ba44199d9fe3a33d1710d1` | audioclip-30704 | 2.1 | 0.843 | 마법적인 느낌의 반짝이는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c40625d1d1ba44199d9fe3a33d1710d1) |
| ☐ | `811987ef77084c8a811c70c1d5d4f7de` | audioclip-20306 | 1.1 | 0.843 | 마법 효과음으로 반짝이는 듯한 밝고 경쾌한 스킬 발동 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=811987ef77084c8a811c70c1d5d4f7de) |
| ☐ | `2d5171102eab4257b99a4fbcd7e7a732` | audioclip-61608 | 2.4 | 0.843 | 마법 스킬을 시전하거나 버프를 적용할 때 발생하는 반짝이는 느낌의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2d5171102eab4257b99a4fbcd7e7a732) |
| ☐ | `3e5859abd81b4dd8a78d477b31e0a259` | audioclip-9867 | 1.3 | 0.843 | 마법이 발동되거나 버프가 적용될 때 들리는 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e5859abd81b4dd8a78d477b31e0a259) |
| ☐ | `5bd82e92a40d4c2aa55da388e2b2793e` | audioclip-60647 | 1.2 | 0.843 | 마법 스킬을 사용하거나 버프를 받을 때 발생하는 반짝이는 느낌의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5bd82e92a40d4c2aa55da388e2b2793e) |
| ☐ | `11ae7cfdd5e847d2b5118574d91e3e28` | audioclip-2895 | 2.5 | 0.842 | 반짝이는 느낌의 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=11ae7cfdd5e847d2b5118574d91e3e28) |
| ☐ | `2edf672e2c774e23a0b98084ddb86e94` | audioclip-62051 | 0.5 | 0.842 | 마법적인 분위기의 반짝이는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2edf672e2c774e23a0b98084ddb86e94) |
| ☐ | `22a564506a0e4b65a77c6f02f1675e2b` | audioclip-5571 | 2.9 | 0.842 | 신비롭고 반짝이는 느낌의 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=22a564506a0e4b65a77c6f02f1675e2b) |
| ☐ | `76ab1aed568d499ab1904221c5ae39f5` | audioclip-18571 | 4 | 0.842 | 신비롭고 반짝이는 느낌의 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=76ab1aed568d499ab1904221c5ae39f5) |


## 은신

### 은신 진입/해제  <sub>(effect, 검색어: 모습을 감추는 은신 사라짐 효과음 투명)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `a6ddb23645f9475487c817f5c7738927` | audioclip-26142 | 0.4 | 0.764 | 무언가 사라지거나 나타날 때 들리는 가벼운 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a6ddb23645f9475487c817f5c7738927) |
| ☐ | `e2ed5d07eed1493c954ceb8273a72111` | audioclip-35663 | 3.7 | 0.749 | 순간이동이나 짧은 마법 스킬을 사용할 때 발생하는 빠르고 날카로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e2ed5d07eed1493c954ceb8273a72111) |
| ☐ | `b7bff81d06cb4debac41e81423113946` | audioclip-28819 | 3.9 | 0.741 | 신비로운 느낌의 마법 에너지가 방출되거나 순간이동하는 듯한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b7bff81d06cb4debac41e81423113946) |
| ☐ | `5bfb525dc4574cf2bc80dcf7b0378823` | audioclip-14504 | 5.7 | 0.741 | 공간을 이동하거나 포탈을 탈 때 발생하는 신비로운 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5bfb525dc4574cf2bc80dcf7b0378823) |
| ☐ | `523128137cf24a30a3fadeabca948417` | audioclip-13004 | 3.7 | 0.74 | 빠르게 이동하거나 스킬을 사용할 때 발생하는 마법적인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=523128137cf24a30a3fadeabca948417) |
| ☐ | `69934328d6f04bf0b457ab6399b61954` | audioclip-41838 | 0.3 | 0.74 | 무언가 사라지거나 나타날 때 발생하는 짧은 마법 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=69934328d6f04bf0b457ab6399b61954) |
| ☐ | `bbc3ce30200d41e9baf6d35e71e46f82` | audioclip-29442 | 3.9 | 0.739 | 마법적인 기운이 모였다가 흩어지는 듯한 신비로운 텔레포트 또는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bbc3ce30200d41e9baf6d35e71e46f82) |
| ☐ | `3ee3a15c8fe94c25b1a8b549ec02702d` | audioclip-9953 | 2.4 | 0.739 | 몬스터가 공격을 받아 쓰러지며 소멸하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3ee3a15c8fe94c25b1a8b549ec02702d) |
| ☐ | `ed8e9dc52ac04f0998e4ee13bfc57196` | audioclip-37296 | 2.2 | 0.738 | 빠르게 이동하거나 마법을 시전할 때 발생하는 날카로운 에너지 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ed8e9dc52ac04f0998e4ee13bfc57196) |
| ☐ | `a13af269ae314269a436e313d7c61c21` | audioclip-60182 | 3.7 | 0.734 | 빠르게 이동하거나 순간이동할 때 발생하는 마법적이고 신비로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a13af269ae314269a436e313d7c61c21) |
| ☐ | `01423d14bbdb47ccadc47a63282cdf7c` | audioclip-297 | 3.9 | 0.734 | 신비로운 느낌의 마법 포탈이나 텔레포트 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=01423d14bbdb47ccadc47a63282cdf7c) |
| ☐ | `452beac8f22941a7b7f9d4bfe9632ade` | audioclip-10957 | 2.8 | 0.732 | 신비로운 느낌의 마법 효과음 또는 스킬 발동 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=452beac8f22941a7b7f9d4bfe9632ade) |
| ☐ | `b26985f471a44f9db6587fa67b7dcf0f` | audioclip-27986 | 3.9 | 0.731 | 마법적인 효과음과 함께 순간이동하거나 빠르게 이동하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b26985f471a44f9db6587fa67b7dcf0f) |
| ☐ | `4cf3c7a44b6047f78a82ac294d9205bd` | audioclip-12175 | 1.7 | 0.729 | 마법이 발동되거나 빛이 반짝이는 듯한 신비롭고 투명한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4cf3c7a44b6047f78a82ac294d9205bd) |
| ☐ | `5242b959203945bca72ba8b57ec2738f` | audioclip-13014 | 5.7 | 0.728 | 신비로운 분위기의 마법 포탈이나 텔레포트 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5242b959203945bca72ba8b57ec2738f) |
| ☐ | `05f8a95455b84a309f255177a5148309` | audioclip-1017 | 3 | 0.728 | 반짝이는 느낌의 고음역대 UI 알림음 또는 레벨업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=05f8a95455b84a309f255177a5148309) |
| ☐ | `051225b1dd3645cfbfbdee3421444b20` | audioclip-880 | 3.9 | 0.728 | 마법 에너지가 방출되거나 순간이동할 때 발생하는 신비로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=051225b1dd3645cfbfbdee3421444b20) |
| ☐ | `e12dbf736a654de8936a5e587ed0a778` | audioclip-35387 | 1.9 | 0.728 | 빠르게 에너지가 방출되거나 순간이동하는 듯한 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e12dbf736a654de8936a5e587ed0a778) |
| ☐ | `104dcae05de74e68a61cf4ca3568ddbe` | audioclip-2681 | 3.9 | 0.727 | 신비로운 마법 에너지가 방출되거나 순간이동할 때 발생하는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=104dcae05de74e68a61cf4ca3568ddbe) |
| ☐ | `e0d8a5d63e5742b5958cf938abe988f9` | audioclip-35338 | 3.7 | 0.725 | 빠르게 대시하거나 순간이동할 때 발생하는 날카로운 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e0d8a5d63e5742b5958cf938abe988f9) |


## 버프

### 버프 오라 적용  <sub>(effect, 검색어: 버프 적용 강화 반짝 효과음 오라)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `97b2e0b742d44672ab0221a92f1a01a7` | audioclip-23703 | 1.2 | 0.835 | 마법적인 기운이 퍼지며 버프가 적용되는 듯한 반짝이는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=97b2e0b742d44672ab0221a92f1a01a7) |
| ☐ | `918109d3c6294a0896588f9dc70a67f2` | audioclip-22770 | 2.9 | 0.828 | 스킬을 사용하거나 버프를 활성화할 때 발생하는 반짝이는 느낌의 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=918109d3c6294a0896588f9dc70a67f2) |
| ☐ | `338bebae4a614967a79b84744fb0e9ad` | audioclip-8179 | 1.2 | 0.824 | 마법적인 버프나 상태 이상이 적용될 때 발생하는 신비롭고 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=338bebae4a614967a79b84744fb0e9ad) |
| ☐ | `21a3c66b164d47c4a67c95c2980c0eff` | audioclip-5419 | 1.1 | 0.823 | 마법적인 기운이 퍼지거나 버프가 적용되는 듯한 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=21a3c66b164d47c4a67c95c2980c0eff) |
| ☐ | `72078506fcb54d688f126346a36eecdf` | audioclip-17869 | 4.1 | 0.823 | 마법 스킬을 사용하거나 버프가 적용될 때 발생하는 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=72078506fcb54d688f126346a36eecdf) |
| ☐ | `2d5171102eab4257b99a4fbcd7e7a732` | audioclip-61608 | 2.4 | 0.823 | 마법 스킬을 시전하거나 버프를 적용할 때 발생하는 반짝이는 느낌의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2d5171102eab4257b99a4fbcd7e7a732) |
| ☐ | `62b8655114534e2ca186e0d6b3d7491e` | audioclip-15523 | 2.5 | 0.822 | 마법 스킬을 사용하거나 버프를 받을 때 발생하는 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=62b8655114534e2ca186e0d6b3d7491e) |
| ☐ | `9badb55f477840a295a3550e7e550a94` | audioclip-24357 | 1.5 | 0.822 | 마법적인 기운이 퍼지며 버프가 적용되는 듯한 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9badb55f477840a295a3550e7e550a94) |
| ☐ | `03262a5816c54d5d9f472870eda1c9a0` | audioclip-599 | 0.8 | 0.819 | 마법적인 기운이 올라가며 버프를 부여하는 듯한 반짝이는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=03262a5816c54d5d9f472870eda1c9a0) |
| ☐ | `f2c89ea57c3d44e2b6d7321dfe541016` | audioclip-38172 | 2.7 | 0.819 | 마법 에너지가 방출되며 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f2c89ea57c3d44e2b6d7321dfe541016) |
| ☐ | `9bc47439a41149128244bdee77fe8a2b` | audioclip-24380 | 3.4 | 0.819 | 마법적인 에너지가 방출되거나 버프가 적용되는 듯한 반짝이는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9bc47439a41149128244bdee77fe8a2b) |
| ☐ | `efb3e0b05b9746e8a59068f41f66f226` | audioclip-37655 | 1.2 | 0.818 | 마법적인 느낌의 반짝이는 스킬 효과음 또는 버프 적용 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=efb3e0b05b9746e8a59068f41f66f226) |
| ☐ | `58d3a45fbc2b400bb34b0636a729b166` | audioclip-14030 | 1.2 | 0.818 | 마법적인 기운이 올라오며 버프를 부여하는 듯한 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58d3a45fbc2b400bb34b0636a729b166) |
| ☐ | `da3d9c40aa094ca69289607d14bc10a4` | audioclip-34328 | 11.8 | 0.818 | 마법적인 기운이 올라오며 버프를 부여하는 듯한 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=da3d9c40aa094ca69289607d14bc10a4) |
| ☐ | `b2342b8ec2a64661b4651cb8173b636f` | audioclip-27952 | 2.8 | 0.818 | 마법적인 기운이 퍼지며 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b2342b8ec2a64661b4651cb8173b636f) |
| ☐ | `e34ec589361f44828e5bb876cf7895e9` | audioclip-35722 | 3.1 | 0.818 | 마법적인 에너지가 방출되거나 버프가 적용되는 듯한 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e34ec589361f44828e5bb876cf7895e9) |
| ☐ | `5552f4a9f187496c9761faf56e9410af` | audioclip-13485 | 1.4 | 0.818 | 마법적인 효과음으로, 스킬 사용 시 발생하는 반짝이는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5552f4a9f187496c9761faf56e9410af) |
| ☐ | `db751ce6c9aa4e3fbd1ab43e5a00c87d` | audioclip-34509 | 0.7 | 0.818 | 마법적인 기운이 퍼지며 캐릭터에게 버프가 적용되는 듯한 신비로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=db751ce6c9aa4e3fbd1ab43e5a00c87d) |
| ☐ | `16597ef4d6fd47dfba5dda473f1e18a7` | audioclip-3657 | 0.8 | 0.817 | 마법적인 기운이 퍼지며 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=16597ef4d6fd47dfba5dda473f1e18a7) |
| ☐ | `3e5859abd81b4dd8a78d477b31e0a259` | audioclip-9867 | 1.3 | 0.817 | 마법이 발동되거나 버프가 적용될 때 들리는 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e5859abd81b4dd8a78d477b31e0a259) |


## 영웅 

### 영웅 등장(스폰)  <sub>(effect, 검색어: 영웅 등장 소환 웅장한 효과음 빛)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `1b321c10d75d41ae9e345823502fa7af` | audioclip-4416 | 5.4 | 0.783 | 강력한 마법 폭발이나 스킬 충격이 발생하는 웅장한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1b321c10d75d41ae9e345823502fa7af) |
| ☐ | `09ae59d83e554fadb47cc7310165405f` | audioclip-1611 | 2.8 | 0.773 | 강력한 마법 폭발이나 스킬 타격 시 발생하는 웅장한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=09ae59d83e554fadb47cc7310165405f) |
| ☐ | `1a0b41d7b3ad476eb20fd33219967661` | audioclip-4238 | 1.6 | 0.773 | 강력한 마법 폭발이나 타격 시 발생하는 웅장한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1a0b41d7b3ad476eb20fd33219967661) |
| ☐ | `fa4dc5658eec40af8d37c9940a0d061e` | audioclip-39314 | 3.1 | 0.772 | 강력한 마법 폭발이나 에너지 충격이 발생하는 웅장한 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fa4dc5658eec40af8d37c9940a0d061e) |
| ☐ | `2a7c01b2453041249b8cab9f379fde19` | audioclip-6816 | 2.9 | 0.77 | 강력한 마법 폭발이나 스킬 사용 시 발생하는 웅장한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a7c01b2453041249b8cab9f379fde19) |
| ☐ | `797dab563e014e30aba62ae6a9c03fbb` | audioclip-19025 | 3.8 | 0.77 | 강력한 마법 폭발이나 스킬 사용 시 발생하는 웅장한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=797dab563e014e30aba62ae6a9c03fbb) |
| ☐ | `e991980d1fd74664917ab09f82ec8bd6` | audioclip-36703 | 5.4 | 0.769 | 강력한 마법 폭발과 함께 에너지가 방출되는 웅장한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e991980d1fd74664917ab09f82ec8bd6) |
| ☐ | `700efbbe98a148d1b328bf61b1b025bf` | audioclip-17572 | 4.8 | 0.769 | 강력한 마법이나 기술이 폭발하며 발생하는 묵직하고 웅장한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=700efbbe98a148d1b328bf61b1b025bf) |
| ☐ | `9a7cd6f3677546feaad6a78fe1ccf5ce` | audioclip-24161 | 4.6 | 0.769 | 강력한 마법 폭발이나 에너지 스킬이 발동되는 웅장한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9a7cd6f3677546feaad6a78fe1ccf5ce) |
| ☐ | `42a8a009f913415aa7e0fb0927435b30` | audioclip-60694 | 3.8 | 0.769 | 강력한 마법 스킬이나 에너지가 방출되는 화려하고 웅장한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=42a8a009f913415aa7e0fb0927435b30) |
| ☐ | `fe52528fb8d343a7b58ad00f670c2696` | audioclip-39968 | 4.1 | 0.769 | 강력한 마법 폭발이나 스킬 타격 시 발생하는 웅장한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fe52528fb8d343a7b58ad00f670c2696) |
| ☐ | `068da1884c8e48f793d8109eb344d6d3` | audioclip-1115 | 2.3 | 0.768 | 강력한 마법 폭발이나 무거운 타격이 발생하는 웅장한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=068da1884c8e48f793d8109eb344d6d3) |
| ☐ | `2987cc64837841e0a05dfa0826df3b20` | audioclip-6677 | 2.4 | 0.768 | 강력한 마법 폭발이나 스킬 사용 시 발생하는 웅장한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2987cc64837841e0a05dfa0826df3b20) |
| ☐ | `45077ced32ce4cbf8c7f5f4755cdb57f` | audioclip-10943 | 2.1 | 0.768 | 강력한 마법 폭발이나 스킬 사용 시 발생하는 웅장한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=45077ced32ce4cbf8c7f5f4755cdb57f) |
| ☐ | `94cd3d6e4c814f6fb2ba1d740db33f6a` | audioclip-23246 | 3.7 | 0.768 | 강력한 마법 폭발이나 스킬 사용 시 발생하는 웅장한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=94cd3d6e4c814f6fb2ba1d740db33f6a) |
| ☐ | `2644701c785b4620890d04b5726b23cd` | audioclip-60384 | 5.5 | 0.767 | 강력한 기합 소리와 함께 거대한 마법 에너지가 폭발하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2644701c785b4620890d04b5726b23cd) |
| ☐ | `457da81cb8004308870964dea619f661` | audioclip-61004 | 3.6 | 0.766 | 강력한 마법 폭발이나 에너지 스킬이 방출되는 웅장한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=457da81cb8004308870964dea619f661) |
| ☐ | `d88f230ae39946338f0740d5fa2e6dbf` | audioclip-34059 | 6.8 | 0.766 | 강력한 마법 폭발이나 스킬 사용 시 발생하는 웅장한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d88f230ae39946338f0740d5fa2e6dbf) |
| ☐ | `f4d438d78a3d447992096b5a84ac94e2` | audioclip-60958 | 2.2 | 0.766 | 강력한 마법 폭발이나 스킬 타격 시 발생하는 웅장한 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f4d438d78a3d447992096b5a84ac94e2) |
| ☐ | `29f433e8a3294cf98f6444f9626ec2d1` | audioclip-6737 | 5.4 | 0.766 | 강력한 마법 폭발이나 스킬 사용 시 발생하는 웅장한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=29f433e8a3294cf98f6444f9626ec2d1) |

### 영웅 사망  <sub>(effect, 검색어: 영웅이 쓰러지는 극적인 사망 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `f10ce91969e2454a99186b594f9de6a8` | audioclip-61951 | 1.1 | 0.796 | 생명체가 타격을 입고 바닥으로 쓰러지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f10ce91969e2454a99186b594f9de6a8) |
| ☐ | `f3b0e31cae874a2a80eb54d52b581f2e` | audioclip-38327 | 2.2 | 0.778 | 검으로 무언가를 강하게 베거나 부딪히는 날카로운 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f3b0e31cae874a2a80eb54d52b581f2e) |
| ☐ | `5bb0ee1472294bdea0b5bd2b1f589b39` | audioclip-41703 | 1.5 | 0.777 | 거대 몬스터가 쓰러지며 내는 묵직한 사망 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5bb0ee1472294bdea0b5bd2b1f589b39) |
| ☐ | `3ee3a15c8fe94c25b1a8b549ec02702d` | audioclip-9953 | 2.4 | 0.776 | 몬스터가 공격을 받아 쓰러지며 소멸하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3ee3a15c8fe94c25b1a8b549ec02702d) |
| ☐ | `9c5f07d0b623496fa8babf05dee4b941` | audioclip-24469 | 3.1 | 0.775 | 게임 오버나 중요한 알림 상황에서 사용될 법한 웅장하고 극적인 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9c5f07d0b623496fa8babf05dee4b941) |
| ☐ | `259e61fceca1488aa88cb901ec833bc0` | audioclip-6066 | 2.5 | 0.774 | 남성의 비명 소리와 폭발음이 어우러진 캐릭터 또는 몬스터의 사망 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=259e61fceca1488aa88cb901ec833bc0) |
| ☐ | `71bca986da124d2f8a9447a92f4a3534` | audioclip-17809 | 2.2 | 0.773 | 검으로 무언가를 빠르게 베는 날카로운 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=71bca986da124d2f8a9447a92f4a3534) |
| ☐ | `6bfd441e7e114c1fac4917d1794d48f7` | audioclip-16951 | 2.2 | 0.772 | 검으로 무언가를 베거나 타격할 때 발생하는 날카로운 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6bfd441e7e114c1fac4917d1794d48f7) |
| ☐ | `954d0b5c41f140feba8bd4f97b11673d` | audioclip-23332 | 2.2 | 0.772 | 검으로 날카롭게 베는 듯한 빠르고 금속적인 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=954d0b5c41f140feba8bd4f97b11673d) |
| ☐ | `ba0338a3b0984eaf96ed796729d7d094` | audioclip-29166 | 3.3 | 0.77 | 거대한 괴물이 신음을 내뱉으며 바닥에 쓰러지는 묵직한 사망 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ba0338a3b0984eaf96ed796729d7d094) |
| ☐ | `612288dd78004daa996222fdcfb4f18f` | audioclip-15302 | 2.2 | 0.769 | 검을 휘두를 때 발생하는 날카롭고 빠른 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=612288dd78004daa996222fdcfb4f18f) |
| ☐ | `358e9f9bdc8c45e893c5a1f839bea8cf` | audioclip-8515 | 2.2 | 0.769 | 검을 휘둘러 날카롭게 베는 듯한 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=358e9f9bdc8c45e893c5a1f839bea8cf) |
| ☐ | `2248dfe05e57401fb238a3e940d59b2a` | audioclip-41091 | 1.3 | 0.769 | 거대한 몬스터가 쓰러지며 발생하는 묵직한 충격음과 잔해 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2248dfe05e57401fb238a3e940d59b2a) |
| ☐ | `f25e0a29d5fe4347b2763c0f21fe3a8d` | audioclip-38082 | 2.2 | 0.766 | 검으로 날카롭게 베는 듯한 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f25e0a29d5fe4347b2763c0f21fe3a8d) |
| ☐ | `566708693ee04fe095405d98728899b7` | audioclip-13650 | 2.2 | 0.765 | 검으로 공기를 가르거나 적을 베는 날카롭고 빠른 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=566708693ee04fe095405d98728899b7) |
| ☐ | `064b26e3d92c44768c16bf1371ccf703` | audioclip-1065 | 2.6 | 0.765 | 몬스터가 고통스러워하며 쓰러지는 듯한 묵직한 타격음과 괴성 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=064b26e3d92c44768c16bf1371ccf703) |
| ☐ | `12a795f139a9430f8b304691fb754c0e` | audioclip-3060 | 2 | 0.764 | 거대한 폭발과 함께 잔해가 무너져 내리는 듯한 웅장한 파괴음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=12a795f139a9430f8b304691fb754c0e) |
| ☐ | `a3c50ff73fda47c3a3d01f204b056801` | audioclip-25664 | 4.3 | 0.762 | 몬스터가 공격을 받아 비명을 지르며 쓰러지는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a3c50ff73fda47c3a3d01f204b056801) |
| ☐ | `69513e1adfb145a98e9243e274041919` | audioclip-16543 | 2.8 | 0.759 | 거대한 몬스터가 쓰러지거나 고통스러워하며 내는 무거운 괴성과 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=69513e1adfb145a98e9243e274041919) |
| ☐ | `7e17aaca1d584e96b2e34625ce70c39d` | audioclip-19833 | 2.2 | 0.757 | 검을 휘둘러 공기를 가르며 적을 베는 날카로운 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7e17aaca1d584e96b2e34625ce70c39d) |

### 영웅 부활  <sub>(effect, 검색어: 부활 되살아남 성스러운 빛 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `9b6dfd4394c643d4ae9b0c982f3a20a6` | audioclip-24310 | 1.1 | 0.765 | 신비롭고 반짝이는 느낌의 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9b6dfd4394c643d4ae9b0c982f3a20a6) |
| ☐ | `fda4b4350ef14f07b2de294974efe1aa` | audioclip-39859 | 4.7 | 0.747 | 밝고 경쾌한 멜로디의 UI 알림 또는 성취 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fda4b4350ef14f07b2de294974efe1aa) |
| ☐ | `bfb3f7c0dab44a028df1ccf24412da27` | audioclip-30024 | 0.4 | 0.746 | 마법 스킬이 활성화되면서 빛나는 듯한 신비로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bfb3f7c0dab44a028df1ccf24412da27) |
| ☐ | `bc1458bfa6164ef1b4257f14f5dd78de` | audioclip-29480 | 1.7 | 0.745 | 스킬 사용 시 발생하는 신비롭고 반짝이는 느낌의 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bc1458bfa6164ef1b4257f14f5dd78de) |
| ☐ | `0f60050db0084fdb90fe1c0c30cd8148` | audioclip-2522 | 0.9 | 0.745 | 밝고 반짝이는 느낌의 마법 스킬 또는 버프 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0f60050db0084fdb90fe1c0c30cd8148) |
| ☐ | `11a23310ff6341c08fb1d379be6d61de` | audioclip-2886 | 1.8 | 0.744 | 반짝이는 마법 효과음이 섞인 밝은 UI 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=11a23310ff6341c08fb1d379be6d61de) |
| ☐ | `4bd33daa4bf3438c906dbc0e8134ea90` | audioclip-11990 | 0.7 | 0.744 | 마법 스킬을 사용하거나 버프를 받을 때 발생하는 반짝이는 느낌의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4bd33daa4bf3438c906dbc0e8134ea90) |
| ☐ | `5552f4a9f187496c9761faf56e9410af` | audioclip-13485 | 1.4 | 0.744 | 마법적인 효과음으로, 스킬 사용 시 발생하는 반짝이는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5552f4a9f187496c9761faf56e9410af) |
| ☐ | `0710fb16f1fb4e368bf3bd7d2808850a` | audioclip-1199 | 0.6 | 0.743 | 마법 스킬을 사용하거나 버프를 받을 때 발생하는 반짝이는 느낌의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0710fb16f1fb4e368bf3bd7d2808850a) |
| ☐ | `e739e3b135204f3b83189cdcc133480d` | audioclip-36351 | 1 | 0.742 | 신비롭고 반짝이는 느낌의 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e739e3b135204f3b83189cdcc133480d) |
| ☐ | `918109d3c6294a0896588f9dc70a67f2` | audioclip-22770 | 2.9 | 0.741 | 스킬을 사용하거나 버프를 활성화할 때 발생하는 반짝이는 느낌의 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=918109d3c6294a0896588f9dc70a67f2) |
| ☐ | `184848beff0846749f6a5a792787f6b3` | audioclip-40992 | 2.7 | 0.74 | 신비롭고 밝은 느낌의 마법 스킬 또는 버프 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=184848beff0846749f6a5a792787f6b3) |
| ☐ | `f007cd8dd7f54bceb0e223b47a6487be` | audioclip-43254 | 1.1 | 0.739 | 마법적인 에너지가 공명하며 반짝이는 느낌의 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f007cd8dd7f54bceb0e223b47a6487be) |
| ☐ | `b2c63c2d3b98477688c69ac603f656d8` | audioclip-28046 | 1.7 | 0.738 | 밝고 신비로운 분위기의 마법 스킬 발동 또는 버프 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b2c63c2d3b98477688c69ac603f656d8) |
| ☐ | `a6cab00fb969404eb00a1a2d1b7dcef9` | audioclip-26130 | 0.9 | 0.737 | 마법적인 에너지가 발산되거나 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a6cab00fb969404eb00a1a2d1b7dcef9) |
| ☐ | `58d0aa1e9dd64a3f82b27313220adf11` | audioclip-14021 | 4.1 | 0.737 | 밝고 신비로운 느낌의 마법적인 효과음 또는 UI 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58d0aa1e9dd64a3f82b27313220adf11) |
| ☐ | `f4b9d3c00e654a72af9e99629fc27430` | audioclip-38491 | 2.1 | 0.735 | 반짝이는 느낌의 마법적인 효과가 포함된 밝은 UI 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f4b9d3c00e654a72af9e99629fc27430) |
| ☐ | `f2c89ea57c3d44e2b6d7321dfe541016` | audioclip-38172 | 2.7 | 0.735 | 마법 에너지가 방출되며 반짝이는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f2c89ea57c3d44e2b6d7321dfe541016) |
| ☐ | `b52f0fc710d244bdbee0b9eacddf81b1` | audioclip-28432 | 2.1 | 0.735 | 반짝이는 느낌의 마법 같은 UI 알림음 또는 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b52f0fc710d244bdbee0b9eacddf81b1) |
| ☐ | `efb3e0b05b9746e8a59068f41f66f226` | audioclip-37655 | 1.2 | 0.734 | 마법적인 느낌의 반짝이는 스킬 효과음 또는 버프 적용 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=efb3e0b05b9746e8a59068f41f66f226) |

### 영웅 레벨업  <sub>(effect, 검색어: 레벨업 효과음 성장 축하)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `c6813615a6fc4850b907302a698ffae5` | audioclip-31146 | 1.6 | 0.867 | 캐릭터의 레벨이 올랐을 때 출력되는 밝고 화려한 축하 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c6813615a6fc4850b907302a698ffae5) |
| ☐ | `27d1c68e69384b19b7fa24783ab315f8` | audioclip-6392 | 0.6 | 0.864 | 캐릭터의 레벨이 올랐을 때 출력되는 밝고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=27d1c68e69384b19b7fa24783ab315f8) |
| ☐ | `51c0090fe47b4331ab9b936dbce94fbd` | audioclip-12928 | 3.4 | 0.853 | 캐릭터가 레벨 업을 했을 때 출력되는 밝고 화려한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=51c0090fe47b4331ab9b936dbce94fbd) |
| ☐ | `df1afe444939490b815fcb4121e46ceb` | audioclip-35055 | 1.5 | 0.846 | 캐릭터의 레벨이 오르거나 목표를 달성했을 때 재생되는 밝고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=df1afe444939490b815fcb4121e46ceb) |
| ☐ | `e66e923782af411ea859fa4fc4dbd3f8` | audioclip-36223 | 0.2 | 0.839 | 레벨 업이나 퀘스트 완료 시 발생하는 축하하는 느낌의 밝은 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e66e923782af411ea859fa4fc4dbd3f8) |
| ☐ | `e8a0a470bd224d10936ba13cd3ef180a` | audioclip-43176 | 0.4 | 0.839 | 캐릭터가 레벨 업을 했을 때 발생하는 밝고 경쾌한 느낌의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e8a0a470bd224d10936ba13cd3ef180a) |
| ☐ | `f9bf291f9b9b4e9bbcac28f1ad071f25` | audioclip-39228 | 0.5 | 0.838 | 캐릭터가 레벨업을 하거나 퀘스트를 완료했을 때 발생하는 밝고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f9bf291f9b9b4e9bbcac28f1ad071f25) |
| ☐ | `305bf83a6e4f4b988451b4e0d156bf07` | audioclip-41239 | 4.3 | 0.836 | 캐릭터의 레벨업이나 퀘스트 완료 시 발생하는 밝고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=305bf83a6e4f4b988451b4e0d156bf07) |
| ☐ | `8e5e5a515ca84352bb8ed8dbaa817042` | audioclip-22297 | 3.3 | 0.83 | 캐릭터의 레벨이 오르거나 업적을 달성했을 때 출력되는 밝고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8e5e5a515ca84352bb8ed8dbaa817042) |
| ☐ | `58d88326af20492aa35a84fd7e40696d` | audioclip-14033 | 1.9 | 0.83 | 레벨 업이나 성공을 나타내는 밝고 마법 같은 느낌의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58d88326af20492aa35a84fd7e40696d) |
| ☐ | `00fafaac075243ed9983de6f6059d7e8` | audioclip-247 | 1.5 | 0.828 | 밝고 경쾌한 느낌의 레벨 업 또는 성공 알림 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=00fafaac075243ed9983de6f6059d7e8) |
| ☐ | `e5234aabf8af4973ae15fb663341e4b0` | audioclip-36009 | 0.5 | 0.826 | 캐릭터의 레벨이 오르거나 퀘스트를 완료했을 때 재생되는 밝고 경쾌한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e5234aabf8af4973ae15fb663341e4b0) |
| ☐ | `f29471e390864149be9839db61c03c0d` | audioclip-38122 | 5.1 | 0.826 | 레벨 업이나 퀘스트 완료 시 들리는 밝고 웅장한 축하 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f29471e390864149be9839db61c03c0d) |
| ☐ | `83b5ce53be4f4f7a87755e105f5a30c6` | audioclip-20689 | 0.5 | 0.824 | 레벨 업이나 퀘스트 완료 시 발생하는 밝고 경쾌한 마법적인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=83b5ce53be4f4f7a87755e105f5a30c6) |
| ☐ | `fca7384e61cd4972816bd3ce28601dee` | audioclip-43375 | 1.5 | 0.824 | 밝고 경쾌한 느낌의 마법 효과음 또는 레벨업 성공 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fca7384e61cd4972816bd3ce28601dee) |
| ☐ | `a95fafcab2634b6f8be44f5833456440` | audioclip-26553 | 9.8 | 0.823 | 레벨 업이나 업적 달성 시 재생되는 밝고 경쾌한 축하 팡파르 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a95fafcab2634b6f8be44f5833456440) |
| ☐ | `3a35b5e62017486c8f3e11d6ca491c82` | audioclip-9251 | 9.1 | 0.823 | 아이의 환호성과 마법적인 반짝임이 어우러진 성공 또는 레벨 업 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3a35b5e62017486c8f3e11d6ca491c82) |
| ☐ | `401ca227c0c844569422a53bd21ab647` | audioclip-10161 | 3.2 | 0.822 | 무언가 성공하거나 레벨업했을 때 들리는 밝고 경쾌한 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=401ca227c0c844569422a53bd21ab647) |
| ☐ | `30e5d4c6aadc4afc843289fa8f72f7c5` | audioclip-7802 | 0.4 | 0.822 | 레벨 업이나 퀘스트 완료 시 들리는 밝고 웅장한 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=30e5d4c6aadc4afc843289fa8f72f7c5) |
| ☐ | `069b5c9c0a204dd0b99bb267a74a9d4e` | audioclip-1123 | 1.3 | 0.822 | 레벨 업이나 성공을 나타내는 밝고 반짝이는 상승 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=069b5c9c0a204dd0b99bb267a74a9d4e) |


## 알림

### 알림-본진/건물 피격  <sub>(effect, 검색어: 경보 사이렌 기지가 공격받음 경고 알림)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `98e9c05088db4dbc853dfb4e56734220` | audioclip-23888 | 1.9 | 0.815 | 경고나 비상 상황을 알리는 날카롭고 반복적인 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=98e9c05088db4dbc853dfb4e56734220) |
| ☐ | `5d704b3c83504094b96febc1c936239f` | audioclip-14711 | 1.9 | 0.809 | 비상 상황이나 경고를 알리는 날카로운 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5d704b3c83504094b96febc1c936239f) |
| ☐ | `e5397d34e85e4a3caf593748afbf030f` | audioclip-36024 | 4.8 | 0.802 | 비상 상황이나 시스템 경고를 알리는 날카로운 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e5397d34e85e4a3caf593748afbf030f) |
| ☐ | `762421119c1148f18d592554cfde4d9c` | audioclip-18502 | 3.1 | 0.801 | 높은 톤으로 반복해서 울리는 전자식 경고음 또는 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=762421119c1148f18d592554cfde4d9c) |
| ☐ | `a74d1652120942c9a5ca3afcdaedf33e` | audioclip-26214 | 1.9 | 0.801 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a74d1652120942c9a5ca3afcdaedf33e) |
| ☐ | `540ef7865b7943128cbca004ec5c10ae` | audioclip-13281 | 3.1 | 0.795 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=540ef7865b7943128cbca004ec5c10ae) |
| ☐ | `bed718715fc145ceb2dc1a14d28e0ad0` | audioclip-29891 | 2.9 | 0.793 | 긴급 상황을 알리는 고음의 사이렌 경보음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bed718715fc145ceb2dc1a14d28e0ad0) |
| ☐ | `8003d139e3dd4c99958becbcbe6ff097` | audioclip-20123 | 2.9 | 0.792 | 긴급 상황을 알리는 날카롭고 반복적인 사이렌 경보음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8003d139e3dd4c99958becbcbe6ff097) |
| ☐ | `7adc4731e2d04522a411012f77351d6a` | audioclip-60047 | 12.1 | 0.776 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 알람 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7adc4731e2d04522a411012f77351d6a) |
| ☐ | `1bee698506af44c4a1f84b01be7373a2` | audioclip-41034 | 1 | 0.771 | 경고나 알림을 나타내는 날카롭고 반복적인 전자 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1bee698506af44c4a1f84b01be7373a2) |
| ☐ | `1a8f9420dc0c4b2c9a14519285c31f44` | audioclip-4325 | 1.9 | 0.765 | 경찰차나 구급차에서 발생하는 긴박한 사이렌 경보음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1a8f9420dc0c4b2c9a14519285c31f44) |
| ☐ | `7dacf4c7fe5345eea51112a2286691ee` | audioclip-19762 | 1.9 | 0.763 | 경찰차나 비상 상황에서 들리는 높고 반복적인 사이렌 경보음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7dacf4c7fe5345eea51112a2286691ee) |
| ☐ | `ccad465c54194302a5db36f178e4329f` | audioclip-32126 | 1 | 0.763 | 높은 톤으로 반복해서 울리는 전자식 경보음 또는 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ccad465c54194302a5db36f178e4329f) |
| ☐ | `e325749ac6684a67beef864a0241ee1c` | audioclip-35691 | 1.9 | 0.76 | 경찰차나 긴급 차량에서 울리는 날카로운 사이렌 경고음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e325749ac6684a67beef864a0241ee1c) |
| ☐ | `1a692dadaa104230a812ab59e01db31f` | audioclip-4306 | 1.9 | 0.759 | 경찰차나 비상 상황에서 들리는 높고 반복적인 사이렌 경보음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1a692dadaa104230a812ab59e01db31f) |
| ☐ | `d54077cf43a144c2aa6ad0a17a2789a0` | audioclip-33491 | 10.7 | 0.725 | 긴박한 상황이나 경고를 알리는 반복적인 고음의 디지털 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d54077cf43a144c2aa6ad0a17a2789a0) |
| ☐ | `652025e1107345aaa52a2e06681f284c` | audioclip-15911 | 4.1 | 0.721 | 전자적인 알람이나 경고를 나타내는 반복적인 고음의 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=652025e1107345aaa52a2e06681f284c) |
| ☐ | `81122a7025f84ffbb31b3989476ba080` | audioclip-20301 | 0.7 | 0.705 | 짧고 반복적인 전자음 형태의 UI 알림 또는 경고음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=81122a7025f84ffbb31b3989476ba080) |
| ☐ | `a77811423fc341408009f58438ee794e` | audioclip-42490 | 1 | 0.703 | 레이더나 스캐너에서 발생하는 반복적인 고음의 전자 신호음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a77811423fc341408009f58438ee794e) |
| ☐ | `5407688385eb42ac9d308f413c469bdd` | audioclip-13277 | 1.5 | 0.7 | 높은 음의 디지털 비프음이 연속적으로 발생하는 UI 알림 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5407688385eb42ac9d308f413c469bdd) |

### 알림-연구/업그레이드 완료  <sub>(effect, 검색어: 업그레이드 완료 알림 성공 띠링 연구)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `3f042fd9434845f5a5a1e465d4949876` | audioclip-9974 | 2.2 | 0.734 | 밝고 경쾌한 느낌의 알림음 또는 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3f042fd9434845f5a5a1e465d4949876) |
| ☐ | `1e46799f903f49ebae142a9831210d9b` | audioclip-4891 | 0.5 | 0.733 | UI 알림이나 성공을 나타내는 짧고 높은 톤의 금속성 벨소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1e46799f903f49ebae142a9831210d9b) |
| ☐ | `3e1802b362004017ba388b3d34071ca8` | audioclip-9835 | 1 | 0.733 | UI 알림이나 성공을 나타내는 짧고 높은 톤의 금속성 벨소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3e1802b362004017ba388b3d34071ca8) |
| ☐ | `a5427847c1ff40dc86c951d72ad2b16f` | audioclip-25895 | 2.7 | 0.732 | 성공이나 알림을 나타내는 맑고 높은 톤의 금속성 벨 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a5427847c1ff40dc86c951d72ad2b16f) |
| ☐ | `a33f450bf4b540099985d06531b71588` | audioclip-25593 | 2 | 0.732 | UI에서 무언가 완료되었거나 알림이 뜰 때 발생하는 맑고 높은 금속성 알림음. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a33f450bf4b540099985d06531b71588) |
| ☐ | `f35eac1d24224721b8e2205b71634eb1` | audioclip-38279 | 2.7 | 0.73 | UI에서 무언가 완료되거나 알림이 뜰 때 발생하는 맑고 높은 금속성 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f35eac1d24224721b8e2205b71634eb1) |
| ☐ | `b6f13753b2ad4c96a806846e1494b490` | audioclip-28703 | 1 | 0.729 | 밝고 긍정적인 느낌의 UI 알림음 또는 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b6f13753b2ad4c96a806846e1494b490) |
| ☐ | `21edf0cabbc8493ca77c5c707d199f27` | audioclip-5462 | 1.2 | 0.729 | 성공이나 레벨 업을 알리는 밝고 경쾌한 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=21edf0cabbc8493ca77c5c707d199f27) |
| ☐ | `718526843e9841ccb649cb4b45583c0a` | audioclip-17784 | 0.6 | 0.728 | 성공이나 확인을 나타내는 밝고 높은 톤의 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=718526843e9841ccb649cb4b45583c0a) |
| ☐ | `c7794642eab042a29ada24208d4eb096` | audioclip-31289 | 0.9 | 0.726 | 밝고 경쾌한 느낌의 UI 알림 또는 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c7794642eab042a29ada24208d4eb096) |
| ☐ | `7a90a5e6bdb14d89b29675bd8f8a019c` | audioclip-19216 | 3.2 | 0.726 | 레벨 업이나 성공을 나타내는 밝고 경쾌한 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7a90a5e6bdb14d89b29675bd8f8a019c) |
| ☐ | `271985ef8c3c4c7bb02e182ed455811f` | audioclip-6285 | 0.7 | 0.725 | UI에서 알림이나 성공을 나타낼 때 사용하는 높고 맑은 금속성 벨 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=271985ef8c3c4c7bb02e182ed455811f) |
| ☐ | `dbb38b4f04044499906bd7a2ca9c4d7c` | audioclip-83 | 2.4 | 0.725 | 레벨 업이나 성공을 알리는 밝고 경쾌한 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dbb38b4f04044499906bd7a2ca9c4d7c) |
| ☐ | `819d229ebc834eed97bba53cbc8e214e` | audioclip-20382 | 1.5 | 0.724 | 알림이나 성공을 나타내는 짧고 높은 톤의 금속성 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=819d229ebc834eed97bba53cbc8e214e) |
| ☐ | `d6c00457d9624073a9f30f2c0a4d4589` | audioclip-33740 | 1.4 | 0.724 | UI에서 알림이나 성공을 나타낼 때 사용하는 높고 맑은 딩 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d6c00457d9624073a9f30f2c0a4d4589) |
| ☐ | `563bf60e298a48a4924fc8d4d5ce1196` | audioclip-13630 | 1 | 0.724 | UI 알림이나 성공적인 동작을 나타내는 짧고 높은 톤의 금속성 벨 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=563bf60e298a48a4924fc8d4d5ce1196) |
| ☐ | `095f560658114eb697a10a7ffd19b54c` | audioclip-1553 | 0.7 | 0.724 | 밝고 높은 톤의 UI 알림음 또는 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=095f560658114eb697a10a7ffd19b54c) |
| ☐ | `c53de74514894b05ab91e65bd8ceccf9` | audioclip-30932 | 1.1 | 0.724 | 밝고 높은 톤의 UI 알림음 또는 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c53de74514894b05ab91e65bd8ceccf9) |
| ☐ | `f03bb9fb3d1c465fa28745745a5427a4` | audioclip-37733 | 0.6 | 0.724 | 밝고 높은 톤의 UI 알림음 또는 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f03bb9fb3d1c465fa28745745a5427a4) |
| ☐ | `13219495ce804c1eaa50e07d29edb233` | audioclip-3140 | 1.9 | 0.724 | 밝고 높은 톤의 UI 알림음 또는 성공 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=13219495ce804c1eaa50e07d29edb233) |

### 알림-적 영웅 발견  <sub>(effect, 검색어: 적 발견 경고 긴장감 짧은 알림)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `81122a7025f84ffbb31b3989476ba080` | audioclip-20301 | 0.7 | 0.779 | 짧고 반복적인 전자음 형태의 UI 알림 또는 경고음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=81122a7025f84ffbb31b3989476ba080) |
| ☐ | `a1ee58d11da14d74a18b63e31e1cfd25` | audioclip-25397 | 0.7 | 0.771 | UI에서 발생하는 짧고 경쾌한 디지털 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a1ee58d11da14d74a18b63e31e1cfd25) |
| ☐ | `e2ff9fc16355406c801dd053a4aee4ec` | audioclip-35676 | 2.1 | 0.758 | 짧고 높은 톤의 전자식 알림음 또는 UI 선택음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e2ff9fc16355406c801dd053a4aee4ec) |
| ☐ | `7adc4731e2d04522a411012f77351d6a` | audioclip-60047 | 12.1 | 0.754 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 알람 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7adc4731e2d04522a411012f77351d6a) |
| ☐ | `1bee698506af44c4a1f84b01be7373a2` | audioclip-41034 | 1 | 0.754 | 경고나 알림을 나타내는 날카롭고 반복적인 전자 비프음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1bee698506af44c4a1f84b01be7373a2) |
| ☐ | `ebd2f2040c034425bc5eaf52bdf63517` | audioclip-37030 | 3 | 0.753 | 짧고 높은 톤의 디지털 알림음 또는 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ebd2f2040c034425bc5eaf52bdf63517) |
| ☐ | `81e7b58deb7c4b0ba30818edd0161ff5` | audioclip-20419 | 1.1 | 0.75 | UI 메뉴를 선택하거나 알림이 뜰 때 발생하는 짧고 명확한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=81e7b58deb7c4b0ba30818edd0161ff5) |
| ☐ | `5d704b3c83504094b96febc1c936239f` | audioclip-14711 | 1.9 | 0.75 | 비상 상황이나 경고를 알리는 날카로운 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5d704b3c83504094b96febc1c936239f) |
| ☐ | `dedb87c18c644b7ba55d6d0f72fa69a1` | audioclip-35017 | 4.5 | 0.75 | 짧고 간결한 디지털 UI 알림음 또는 시스템 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=dedb87c18c644b7ba55d6d0f72fa69a1) |
| ☐ | `90dbb64402f04f40982ff665c254126e` | audioclip-22666 | 3.2 | 0.75 | 짧고 높은 톤의 디지털 알림음 또는 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=90dbb64402f04f40982ff665c254126e) |
| ☐ | `98e9c05088db4dbc853dfb4e56734220` | audioclip-23888 | 1.9 | 0.75 | 경고나 비상 상황을 알리는 날카롭고 반복적인 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=98e9c05088db4dbc853dfb4e56734220) |
| ☐ | `c15e945508d44dee8e805737d606e85e` | audioclip-30307 | 0.6 | 0.749 | UI에서 발생하는 짧고 높은 톤의 디지털 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c15e945508d44dee8e805737d606e85e) |
| ☐ | `f5ac1bd092c3450896286a56a7f6797f` | audioclip-38645 | 2 | 0.749 | 메뉴 선택이나 알림 시 발생하는 짧고 명확한 UI 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f5ac1bd092c3450896286a56a7f6797f) |
| ☐ | `86f81259e7094a51844ceb9af3ae444e` | audioclip-21166 | 3 | 0.749 | 짧고 경쾌한 느낌의 디지털 UI 알림음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=86f81259e7094a51844ceb9af3ae444e) |
| ☐ | `8f3a422cb5f94a3c814040455a95c45f` | audioclip-22429 | 0.5 | 0.748 | 작고 날카로운 타격음 또는 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8f3a422cb5f94a3c814040455a95c45f) |
| ☐ | `e5397d34e85e4a3caf593748afbf030f` | audioclip-36024 | 4.8 | 0.748 | 비상 상황이나 시스템 경고를 알리는 날카로운 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e5397d34e85e4a3caf593748afbf030f) |
| ☐ | `805deb8f76034300917c44526a5a7500` | audioclip-42058 | 1.7 | 0.748 | 짧고 높은 톤의 디지털 알림음 또는 시스템 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=805deb8f76034300917c44526a5a7500) |
| ☐ | `540ef7865b7943128cbca004ec5c10ae` | audioclip-13281 | 3.1 | 0.747 | 경고나 비상 상황을 알리는 날카롭고 반복적인 전자 사이렌 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=540ef7865b7943128cbca004ec5c10ae) |
| ☐ | `174d501eccd04eadbd6c6411d4ade7e7` | audioclip-3801 | 0.9 | 0.747 | 짧고 날카로운 전자음으로, UI 오류나 경고 상황에 적합한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=174d501eccd04eadbd6c6411d4ade7e7) |
| ☐ | `fa39a393bf5c4bc9b48768204e8f1fc1` | audioclip-39299 | 1.9 | 0.747 | UI에서 알림이나 선택 시 발생하는 짧고 높은 톤의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fa39a393bf5c4bc9b48768204e8f1fc1) |


## VOICE

### VOICE 테스트-자원 부족  <sub>(voice, 검색어: 자원이 부족합니다 음성 안내)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `a861c2c5c6294dc48a853a28436ca7f6` | audioclip-26403 | 2.4 | 0.71 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a861c2c5c6294dc48a853a28436ca7f6) |
| ☐ | `8e024c39a1694ca490fc138b95917584` | audioclip-22243 | 1.7 | 0.7 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8e024c39a1694ca490fc138b95917584) |
| ☐ | `080f90188b58467c9e9b99e1060fe324` | audioclip-1357 | 1.7 | 0.7 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=080f90188b58467c9e9b99e1060fe324) |
| ☐ | `8f9dccc6000d413e853bde70bea78f1b` | audioclip-22492 | 6.3 | 0.7 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8f9dccc6000d413e853bde70bea78f1b) |
| ☐ | `7896b1d781454478bca6ca5013a84ac7` | audioclip-18888 | 1.7 | 0.698 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7896b1d781454478bca6ca5013a84ac7) |
| ☐ | `c873f57b376e4c76a78e50213123c54a` | audioclip-31450 | 2.2 | 0.698 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c873f57b376e4c76a78e50213123c54a) |
| ☐ | `ebcda45b5ea74c00ba6a06352291dc18` | audioclip-37028 | 4 | 0.698 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ebcda45b5ea74c00ba6a06352291dc18) |
| ☐ | `ea8319e413d94fe984e700d84079bb8f` | audioclip-36827 | 3.6 | 0.694 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ea8319e413d94fe984e700d84079bb8f) |
| ☐ | `2bc2be7322614792b4af69d5c439231f` | audioclip-7008 | 1.8 | 0.691 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2bc2be7322614792b4af69d5c439231f) |
| ☐ | `d36c71c40d1d4ce68dfede672a776396` | audioclip-42948 | 4.1 | 0.69 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d36c71c40d1d4ce68dfede672a776396) |
| ☐ | `9545a594e5a14075a14a152bb14b099f` | audioclip-23315 | 4.3 | 0.69 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9545a594e5a14075a14a152bb14b099f) |
| ☐ | `f7362cc7376143119283e61b6ed9b1d5` | audioclip-43320 | 1.2 | 0.687 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f7362cc7376143119283e61b6ed9b1d5) |
| ☐ | `c6bbd932b0cd4f439317d56f2a0d6fec` | audioclip-31183 | 2.1 | 0.684 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c6bbd932b0cd4f439317d56f2a0d6fec) |
| ☐ | `8d3f4c7d9d174cb68585c941d953731c` | audioclip-22140 | 1.5 | 0.683 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8d3f4c7d9d174cb68585c941d953731c) |
| ☐ | `9f25776546fe4f3481180c789bdf0fab` | audioclip-24916 | 2.2 | 0.683 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9f25776546fe4f3481180c789bdf0fab) |
| ☐ | `e9f64d5c683f44698ae0022a5314673c` | audioclip-36763 | 3.2 | 0.681 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e9f64d5c683f44698ae0022a5314673c) |
| ☐ | `36e770d5eff6496dae2152d32a1e67d5` | audioclip-8735 | 1.7 | 0.681 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=36e770d5eff6496dae2152d32a1e67d5) |
| ☐ | `aab5cc8dd3554858b1433a09dd3b05de` | audioclip-26758 | 5.7 | 0.679 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=aab5cc8dd3554858b1433a09dd3b05de) |
| ☐ | `d60ae96ca96147429c8e854d19f58e17` | audioclip-33624 | 2.3 | 0.679 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d60ae96ca96147429c8e854d19f58e17) |
| ☐ | `74c571868c274e8caab1df1df95ff20a` | audioclip-18286 | 3.1 | 0.679 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=74c571868c274e8caab1df1df95ff20a) |

### VOICE 테스트-공격받음  <sub>(voice, 검색어: 공격받고 있습니다 음성 경고)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `098f054f734f4eeeb481dadb6404080f` | audioclip-1587 | 2.9 | 0.821 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=098f054f734f4eeeb481dadb6404080f) |
| ☐ | `5c53443ee27a4e01b9c9a5bee2dd709f` | audioclip-14549 | 1.5 | 0.813 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5c53443ee27a4e01b9c9a5bee2dd709f) |
| ☐ | `8ba973ef63b4448db11913febc5f71ba` | audioclip-21891 | 2.5 | 0.771 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8ba973ef63b4448db11913febc5f71ba) |
| ☐ | `f0b95558e93f4ad2b773978db6b2a265` | audioclip-37817 | 4.2 | 0.759 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f0b95558e93f4ad2b773978db6b2a265) |
| ☐ | `25ddbb8ebf184cceb0aed08f2e4e8b45` | audioclip-6105 | 2.4 | 0.759 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=25ddbb8ebf184cceb0aed08f2e4e8b45) |
| ☐ | `0f5eefdbcbda4389966e13a540476e38` | audioclip-2521 | 1.9 | 0.747 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0f5eefdbcbda4389966e13a540476e38) |
| ☐ | `b828a696a95e493b810bc3ce8531fb6d` | audioclip-28882 | 2 | 0.745 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b828a696a95e493b810bc3ce8531fb6d) |
| ☐ | `a8e3af831ae7408a849ff20288faa169` | audioclip-26486 | 2.1 | 0.739 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a8e3af831ae7408a849ff20288faa169) |
| ☐ | `419235973c164d07b2559b7cbfdc3ce2` | audioclip-10393 | 2.6 | 0.739 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=419235973c164d07b2559b7cbfdc3ce2) |
| ☐ | `a0b2181f19c54b75ab90f641dcbc1a7a` | audioclip-42431 | 2.5 | 0.737 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a0b2181f19c54b75ab90f641dcbc1a7a) |
| ☐ | `bbf295afaee1447d8586b099569f0f86` | audioclip-29470 | 3.3 | 0.737 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bbf295afaee1447d8586b099569f0f86) |
| ☐ | `e09aee50edde4fba808e16cae6c49a4f` | audioclip-43083 | 1.6 | 0.736 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e09aee50edde4fba808e16cae6c49a4f) |
| ☐ | `981789a377d240f49ef92891e5d38e43` | audioclip-23769 | 2 | 0.733 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=981789a377d240f49ef92891e5d38e43) |
| ☐ | `099587caf93e41df9248f508d078d9c4` | audioclip-1593 | 2 | 0.733 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=099587caf93e41df9248f508d078d9c4) |
| ☐ | `a4755e4ec2c0405abe50c961bb3d00d2` | audioclip-25778 | 2.2 | 0.733 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a4755e4ec2c0405abe50c961bb3d00d2) |
| ☐ | `3c9ecbd03d344f498fd06d97affad437` | audioclip-9608 | 3.2 | 0.733 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3c9ecbd03d344f498fd06d97affad437) |
| ☐ | `976cbb76514d480a922f74eb04762d09` | audioclip-23655 | 2.6 | 0.733 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=976cbb76514d480a922f74eb04762d09) |
| ☐ | `b5eedf76fa514c8abd2c5522fcfd889c` | audioclip-28542 | 2 | 0.731 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b5eedf76fa514c8abd2c5522fcfd889c) |
| ☐ | `0764ea6a817d4d5d92e3d7a63aaf75a0` | audioclip-1242 | 2.2 | 0.728 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0764ea6a817d4d5d92e3d7a63aaf75a0) |
| ☐ | `bb820c65b2e049cf82649ab45ec0d900` | audioclip-29401 | 1.4 | 0.728 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bb820c65b2e049cf82649ab45ec0d900) |

### VOICE 테스트-유닛 대답  <sub>(voice, 검색어: 명령 수락 유닛 음성 대답 알겠습니다)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `ee8796b5bcb14bbaac73495fc488609d` | audioclip-43237 | 1.3 | 0.804 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ee8796b5bcb14bbaac73495fc488609d) |
| ☐ | `247c8b1eefc244f29bc1108bd64fed3b` | audioclip-5878 | 1 | 0.803 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=247c8b1eefc244f29bc1108bd64fed3b) |
| ☐ | `50a3fed8c38e464cb7d63f7c04ca19f8` | audioclip-12765 | 1 | 0.802 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=50a3fed8c38e464cb7d63f7c04ca19f8) |
| ☐ | `081e569e9ac14417b50186a9620b5409` | audioclip-1366 | 1 | 0.801 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=081e569e9ac14417b50186a9620b5409) |
| ☐ | `f1ec40fd65f34cb0bab32eb7c86ee486` | audioclip-43265 | 1.3 | 0.801 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f1ec40fd65f34cb0bab32eb7c86ee486) |
| ☐ | `33ac8cd7d0e948fba29c66db40bc828f` | audioclip-8197 | 1 | 0.798 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=33ac8cd7d0e948fba29c66db40bc828f) |
| ☐ | `70ce174c05b54cd9b6fb5f942dc68302` | audioclip-17687 | 4.4 | 0.798 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=70ce174c05b54cd9b6fb5f942dc68302) |
| ☐ | `0ec6191347ba4b3889f2d79c94e57567` | audioclip-2429 | 4.4 | 0.798 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0ec6191347ba4b3889f2d79c94e57567) |
| ☐ | `b013c2b8001e4bb8a9f230d1af2848b0` | audioclip-27625 | 1.4 | 0.795 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b013c2b8001e4bb8a9f230d1af2848b0) |
| ☐ | `16da9fbd0a6346719f72ad5d1158cf8c` | audioclip-40971 | 1.4 | 0.794 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=16da9fbd0a6346719f72ad5d1158cf8c) |
| ☐ | `6d85407ac5924f249dc315132ae35c5b` | audioclip-41879 | 1 | 0.79 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6d85407ac5924f249dc315132ae35c5b) |
| ☐ | `b9a64cad20234009993dbe11f1e7d01a` | audioclip-29101 | 1.3 | 0.782 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b9a64cad20234009993dbe11f1e7d01a) |
| ☐ | `92d9633addad4b1cb4c78dfedd9c4964` | audioclip-22960 | 1.3 | 0.781 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=92d9633addad4b1cb4c78dfedd9c4964) |
| ☐ | `272fa58289604c41bf9cb4da2027c37c` | audioclip-6294 | 1.8 | 0.78 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=272fa58289604c41bf9cb4da2027c37c) |
| ☐ | `0ce60081cec44ac492f27c732240b8f2` | audioclip-2107 | 1.1 | 0.776 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0ce60081cec44ac492f27c732240b8f2) |
| ☐ | `684d68adec3b4ad4aab69e50d615ee50` | audioclip-16400 | 1.3 | 0.775 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=684d68adec3b4ad4aab69e50d615ee50) |
| ☐ | `42c283b3741547dbb28ae6f4e675c1be` | audioclip-10580 | 2.6 | 0.77 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=42c283b3741547dbb28ae6f4e675c1be) |
| ☐ | `f3c14064b21841ca91a016efa5e86dd1` | audioclip-38336 | 2.7 | 0.769 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f3c14064b21841ca91a016efa5e86dd1) |
| ☐ | `bdfc635ff85b456082ab5e5fb6140564` | audioclip-42728 | 1.8 | 0.767 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bdfc635ff85b456082ab5e5fb6140564) |
| ☐ | `ac62bad204f9450d9d1eb6400137f4ed` | audioclip-27025 | 1.6 | 0.762 |  | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ac62bad204f9450d9d1eb6400137f4ed) |


## 영웅스킬

### 영웅스킬-배틀메이지  <sub>(effect, 검색어: 배틀메이지 스킬 어둠 마법 체인 사신 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `01f8b72895ee46e190ad4fc66ae346d9` | audioclip-415 | 1.9 | 0.784 | 빠르고 날카롭게 휘두르는 듯한 스킬 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=01f8b72895ee46e190ad4fc66ae346d9) |
| ☐ | `2d0d80d2732547258dbe2e215ca621d3` | audioclip-7196 | 7.4 | 0.783 | 강력한 포효와 함께 에너지가 연쇄적으로 폭발하는 마법 공격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2d0d80d2732547258dbe2e215ca621d3) |
| ☐ | `54dc385f33cd4006aba1e2d636a65eb9` | audioclip-13414 | 5.3 | 0.782 | 어둠의 마법 에너지가 폭발하며 여러 번 타격하는 강력한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=54dc385f33cd4006aba1e2d636a65eb9) |
| ☐ | `f79cd8baed714394a46076bdaaee430e` | audioclip-38914 | 3.5 | 0.772 | 강력한 마법 에너지가 폭발하며 퍼지는 묵직한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f79cd8baed714394a46076bdaaee430e) |
| ☐ | `89fa051abb37429e9857d549d50f791d` | audioclip-62886 | 7 | 0.77 | 강력한 마법 폭발이나 에너지 파동이 연속적으로 발생하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=89fa051abb37429e9857d549d50f791d) |
| ☐ | `af57512e009f499f9f15cf2d29af95d1` | audioclip-27513 | 4.5 | 0.767 | 강력한 폭발음과 함께 묵직한 타격감을 주는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=af57512e009f499f9f15cf2d29af95d1) |
| ☐ | `5b32d6ca97d8427ba4b77796c0620703` | audioclip-14370 | 2.7 | 0.763 | 강력한 마법 폭발이나 무거운 타격이 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5b32d6ca97d8427ba4b77796c0620703) |
| ☐ | `f9585f0794bc4e8ea762e6885b2c2326` | audioclip-39166 | 5.2 | 0.761 | 강력한 마법이나 기술이 폭발하며 발생하는 무겁고 웅장한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f9585f0794bc4e8ea762e6885b2c2326) |
| ☐ | `59814cd050bd4f2ba9f6e8c6c0fd3460` | audioclip-60675 | 4.3 | 0.756 | 강력한 마법 에너지가 폭발하며 발생하는 웅장하고 파괴적인 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=59814cd050bd4f2ba9f6e8c6c0fd3460) |
| ☐ | `8ddb655837a941edaedb2641b4f02f5f` | audioclip-22227 | 3.1 | 0.756 | 강력하고 어두운 마법 에너지가 폭발하며 발생하는 무거운 타격음. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8ddb655837a941edaedb2641b4f02f5f) |
| ☐ | `bdb2a84f86444d41850b9bc314fd9bfa` | audioclip-29723 | 1.8 | 0.755 | 빠르고 날카로운 금속성 소리가 연속적으로 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bdb2a84f86444d41850b9bc314fd9bfa) |
| ☐ | `fd65f221624948b18fdb934cf377dbe7` | audioclip-39816 | 2.1 | 0.752 | 검을 휘두를 때 발생하는 날카롭고 빠른 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fd65f221624948b18fdb934cf377dbe7) |
| ☐ | `17478d88bc5d4fee8f021876c244609d` | audioclip-3797 | 5.6 | 0.751 | 남성 캐릭터의 강한 기합과 함께 어두운 마법 기운이 소용돌이치는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=17478d88bc5d4fee8f021876c244609d) |
| ☐ | `4f0afcb9c14849aca31890c67bd1e091` | audioclip-12499 | 4.9 | 0.75 | 사슬이나 기계 장치가 빠르게 움직이며 발생하는 날카로운 금속성 타격음과 회전음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4f0afcb9c14849aca31890c67bd1e091) |
| ☐ | `ed3974c916914848a25dd08d29b68563` | audioclip-37237 | 1.8 | 0.749 | 날카로운 금속음이 섞인 빠른 검기 또는 스킬 공격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ed3974c916914848a25dd08d29b68563) |
| ☐ | `b9e214a159604a2c864b42f9dbb018b6` | audioclip-29149 | 3.2 | 0.747 | 강력한 타격감과 함께 폭발하는 듯한 묵직한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b9e214a159604a2c864b42f9dbb018b6) |
| ☐ | `0223f2a706a247fab325daff23d477c3` | audioclip-451 | 6 | 0.743 | 강력하고 신비로운 마법 폭발 또는 스킬 발동 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0223f2a706a247fab325daff23d477c3) |
| ☐ | `bbec8c990c284026af92b8956b7f2704` | audioclip-29466 | 3.6 | 0.743 | 강력한 마법 에너지가 방출되어 폭발하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=bbec8c990c284026af92b8956b7f2704) |
| ☐ | `d372d9b3c0364ad7aabf9deef1788ffb` | audioclip-33180 | 2.9 | 0.741 | 빠르게 휘두르거나 에너지를 방출하는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d372d9b3c0364ad7aabf9deef1788ffb) |
| ☐ | `14af7fd9cbc04e63877cd44dd8774713` | audioclip-3389 | 2.8 | 0.74 | 강력한 폭발이나 타격이 발생하는 묵직한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=14af7fd9cbc04e63877cd44dd8774713) |

### 영웅스킬-블래스터  <sub>(effect, 검색어: 블래스터 건틀릿 펀치 폭발 스킬 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `58d3173eb897475a89607bfb231af507` | audioclip-14028 | 3 | 0.864 | 강력한 폭발음과 함께 묵직한 타격감을 주는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58d3173eb897475a89607bfb231af507) |
| ☐ | `2a8b3d7ba8cd410baa4562e5584a8ea2` | audioclip-6801 | 2.8 | 0.857 | 강력한 폭발과 함께 발생하는 묵직한 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a8b3d7ba8cd410baa4562e5584a8ea2) |
| ☐ | `8f977f93876c462697966bbbe36d4dd2` | audioclip-22486 | 5.4 | 0.847 | 강력한 폭발음이 여러 번 이어지는 타격감 있는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8f977f93876c462697966bbbe36d4dd2) |
| ☐ | `0f356585558f4b8288e6b65c1c893937` | audioclip-2496 | 3.2 | 0.844 | 강력한 폭발음과 함께 마법적인 타격감이 느껴지는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0f356585558f4b8288e6b65c1c893937) |
| ☐ | `00190eb2d6aa42a7a3afa188d8730bb2` | audioclip-95 | 3 | 0.842 | 강력한 타격감과 함께 터지는 마법적인 폭발 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=00190eb2d6aa42a7a3afa188d8730bb2) |
| ☐ | `b576039f6473459386be5604678fd84e` | audioclip-60131 | 4.2 | 0.841 | 강력한 폭발음과 함께 에너지가 방출되는 웅장한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b576039f6473459386be5604678fd84e) |
| ☐ | `49f9f1b005954eeb9ec93d25d121bebf` | audioclip-11714 | 3 | 0.841 | 강력한 타격음과 함께 폭발하는 듯한 화려한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=49f9f1b005954eeb9ec93d25d121bebf) |
| ☐ | `0944837045dd430c9b0bfd05ec32983c` | audioclip-1542 | 2.8 | 0.84 | 강력한 폭발음과 함께 마법 에너지가 터지는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0944837045dd430c9b0bfd05ec32983c) |
| ☐ | `1d82753a6c164ffe8e53e46b4284fd19` | audioclip-4790 | 4.2 | 0.839 | 강력한 폭발이나 타격이 발생하는 묵직한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1d82753a6c164ffe8e53e46b4284fd19) |
| ☐ | `12364612c4164c2b9cf6c2965788e93c` | audioclip-2974 | 5.6 | 0.839 | 강력한 폭발음과 함께 발생하는 묵직한 타격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=12364612c4164c2b9cf6c2965788e93c) |
| ☐ | `40ed30c135b64cc6b8d5843965088dae` | audioclip-10272 | 3.1 | 0.839 | 강력한 폭발과 함께 에너지가 방출되는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=40ed30c135b64cc6b8d5843965088dae) |
| ☐ | `588246a819d240538026cf599718f0cc` | audioclip-13981 | 2.6 | 0.838 | 강력한 힘이 폭발하며 발생하는 웅장하고 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=588246a819d240538026cf599718f0cc) |
| ☐ | `291d8ebb03c747c6ae00e25e59ada2ca` | audioclip-6608 | 3.4 | 0.838 | 강력한 폭발이나 충격을 동반한 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=291d8ebb03c747c6ae00e25e59ada2ca) |
| ☐ | `c44b0463ce314b72b25bb02342237052` | audioclip-30750 | 6 | 0.837 | 강력한 마법 에너지가 폭발하며 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c44b0463ce314b72b25bb02342237052) |
| ☐ | `d8bbb2664f9d4a44934c6759d0ae31b1` | audioclip-34088 | 3.3 | 0.836 | 강력한 폭발이나 묵직한 타격이 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d8bbb2664f9d4a44934c6759d0ae31b1) |
| ☐ | `6b1d598534fe4e12833e7898d5f32d85` | audioclip-16802 | 2.2 | 0.836 | 강력한 폭발음과 함께 묵직한 타격감을 주는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6b1d598534fe4e12833e7898d5f32d85) |
| ☐ | `226eea76456d47ec86fb78bac8f3b604` | audioclip-5555 | 4.1 | 0.836 | 강력한 마법 에너지가 폭발하며 발생하는 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=226eea76456d47ec86fb78bac8f3b604) |
| ☐ | `6814936a18a74e7ab93b22d00147bf7a` | audioclip-62917 | 3.4 | 0.836 | 강력한 마법 에너지가 폭발하며 발생하는 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6814936a18a74e7ab93b22d00147bf7a) |
| ☐ | `caedde013b644fbbb76fb4462476df68` | audioclip-31846 | 1.7 | 0.835 | 강력한 폭발음과 함께 에너지가 방출되는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=caedde013b644fbbb76fb4462476df68) |
| ☐ | `6f2ccda1da43456689fb048f14eeb410` | audioclip-60985 | 2.6 | 0.834 | 강력한 폭발음과 함께 마법적인 타격감이 느껴지는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6f2ccda1da43456689fb048f14eeb410) |

### 영웅스킬-캡틴  <sub>(effect, 검색어: 캡틴 권총 사격 연사 스킬 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `017e5313a3d344acbb7d0498853fbae0` | audioclip-61790 | 1.5 | 0.79 | 권총을 세 번 연속으로 발사하는 날카로운 총성 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=017e5313a3d344acbb7d0498853fbae0) |
| ☐ | `70040a0555744508bbd7b640e557192d` | audioclip-17557 | 5.1 | 0.779 | 개틀링 건이나 기계 장치가 빠르게 연속으로 발사되는 날카로운 금속성 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=70040a0555744508bbd7b640e557192d) |
| ☐ | `13f039c3fbd64502aa2ced8c86406cf1` | audioclip-3271 | 6.3 | 0.777 | 빠르게 연속으로 발사되는 에너지 탄환 또는 마법 투사체 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=13f039c3fbd64502aa2ced8c86406cf1) |
| ☐ | `e40e199784a94aaea4a7d24e1fcad384` | audioclip-60128 | 2.3 | 0.772 | 권총을 발사한 후 탄피가 떨어지는 소리가 포함된 날카로운 총기 격발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e40e199784a94aaea4a7d24e1fcad384) |
| ☐ | `c359649e15de431ba7d9f9b14f082358` | audioclip-30615 | 6.3 | 0.772 | 빠르게 연속으로 발사되는 레이저 또는 에너지 탄환의 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c359649e15de431ba7d9f9b14f082358) |
| ☐ | `ace9ad8a86b4474e8fdb34e96dbd0d24` | audioclip-27116 | 3.7 | 0.771 | 기계적인 연사음 뒤에 강력한 폭발음이 이어지는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ace9ad8a86b4474e8fdb34e96dbd0d24) |
| ☐ | `171bf69facdd4d5abe6c7a37ba235fcf` | audioclip-3776 | 3 | 0.763 | 기계적인 소리와 함께 빠르게 연사되는 타격음과 묵직한 마지막 타격음. | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=171bf69facdd4d5abe6c7a37ba235fcf) |
| ☐ | `c2aa2ab77dc44d89b93e0f87a268e0c2` | audioclip-30511 | 3 | 0.762 | 기계적인 느낌의 무거운 금속 타격음이 연속적으로 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c2aa2ab77dc44d89b93e0f87a268e0c2) |
| ☐ | `e88a1a9411e046c9980298517e622f3e` | audioclip-40343 | 0.9 | 0.761 | 검을 휘두를 때 발생하는 날카롭고 빠른 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e88a1a9411e046c9980298517e622f3e) |
| ☐ | `41edbde25d7c4bc0b61dd0db7c42a168` | audioclip-10451 | 6.3 | 0.758 | 빠르게 연속적으로 발사되는 디지털 느낌의 레이저 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=41edbde25d7c4bc0b61dd0db7c42a168) |
| ☐ | `02677ec632ca4c49b784f3c0dfb1481a` | audioclip-492 | 6.3 | 0.756 | 빠르게 연속으로 발사되는 마법 투사체 또는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=02677ec632ca4c49b784f3c0dfb1481a) |
| ☐ | `0ace1649024a4559ab27530fca723535` | audioclip-1771 | 6.3 | 0.75 | 빠르게 에너지를 발사한 후 기합 소리와 함께 마무리하는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0ace1649024a4559ab27530fca723535) |
| ☐ | `1930cb081aa94525a2b645715765bc9d` | audioclip-4107 | 6.3 | 0.749 | 에너지나 레이저를 빠르게 여러 번 발사하는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1930cb081aa94525a2b645715765bc9d) |
| ☐ | `376335f87e064d6d809aa2e463162d2e` | audioclip-8806 | 5.4 | 0.745 | 기계 장치가 빠르게 연사되는 듯한 묵직하고 날카로운 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=376335f87e064d6d809aa2e463162d2e) |
| ☐ | `80f6f8431543458f8813a58c6c277f46` | audioclip-20280 | 5.7 | 0.742 | 중기관총이나 연사 스킬처럼 빠르고 묵직하게 터지는 연속 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=80f6f8431543458f8813a58c6c277f46) |
| ☐ | `5e8b433297e34667994f1cf9e9809103` | audioclip-14896 | 4.7 | 0.74 | 강력한 폭발과 금속성 타격음이 섞인 연속적인 스킬 공격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5e8b433297e34667994f1cf9e9809103) |
| ☐ | `d7404e6c7d4a40bda37b8573469a0b92` | audioclip-61231 | 1.7 | 0.738 | 연속적으로 발생하는 고음의 디지털 마법 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d7404e6c7d4a40bda37b8573469a0b92) |
| ☐ | `24160248c29640da902e0ece668dd75b` | audioclip-5813 | 5.5 | 0.738 | 여러 번 빠르게 타격하는 기계적인 느낌의 연속 공격 스킬 사운드 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=24160248c29640da902e0ece668dd75b) |
| ☐ | `4b84f87643e8444bbe2e6c0d85771f8b` | audioclip-11947 | 4.8 | 0.737 | 강력한 폭발과 금속성 타격음이 섞인 연속적인 스킬 공격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4b84f87643e8444bbe2e6c0d85771f8b) |
| ☐ | `462bab718e984714933f0c8027959965` | audioclip-11112 | 4 | 0.737 | 강력한 에너지 레이저가 발사되는 기계적인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=462bab718e984714933f0c8027959965) |

### 영웅스킬-플레임위자드  <sub>(effect, 검색어: 플레임위자드 화염 마법 불꽃 스킬 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `cecc2c8817e0434bb210acec299e2731` | audioclip-32463 | 4 | 0.881 | 불꽃이 폭발하며 타오르는 듯한 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cecc2c8817e0434bb210acec299e2731) |
| ☐ | `a0cda3bb612a454bb115f3fa1f7c8ecb` | audioclip-25158 | 3 | 0.875 | 강력한 불길이 뿜어져 나오며 타오르는 마법 공격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a0cda3bb612a454bb115f3fa1f7c8ecb) |
| ☐ | `7b1ff8f8c6f345eaa9fbd1d9ae56bcec` | audioclip-42000 | 1.5 | 0.869 | 강력한 불꽃이 폭발하듯 뿜어져 나오는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7b1ff8f8c6f345eaa9fbd1d9ae56bcec) |
| ☐ | `4fb384a2bcfa456f87e96a1d2a7e002d` | audioclip-12606 | 16.3 | 0.866 | 강력한 화염 마법이 폭발하며 지속적으로 타오르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4fb384a2bcfa456f87e96a1d2a7e002d) |
| ☐ | `56446062a2cb481aa77252884629f70a` | audioclip-13637 | 4.6 | 0.858 | 강력한 화염 폭발과 함께 타오르는 소리가 담긴 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=56446062a2cb481aa77252884629f70a) |
| ☐ | `6034c63dc99b4e349e6335174a1b735b` | audioclip-15163 | 3.4 | 0.855 | 강력한 폭발과 함께 불길이 타오르는 화염 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6034c63dc99b4e349e6335174a1b735b) |
| ☐ | `0b253c5fcf224ac09916b223579aa536` | audioclip-1825 | 3.6 | 0.855 | 강력한 화염 마법이 여러 번 폭발하며 적을 타격하는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0b253c5fcf224ac09916b223579aa536) |
| ☐ | `2a43df614a0f41409adaf86a8e5f2dfd` | audioclip-6774 | 3 | 0.85 | 강력한 마법 폭발이나 스킬 사용 시 발생하는 화염 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2a43df614a0f41409adaf86a8e5f2dfd) |
| ☐ | `c9d42aff9aca42169c8f3dddc9569b49` | audioclip-31670 | 3.4 | 0.846 | 강력한 화염 마법이나 폭발이 일어나는 화려한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c9d42aff9aca42169c8f3dddc9569b49) |
| ☐ | `431e60421b0847568e3f9ac314ec28dd` | audioclip-10635 | 2.8 | 0.845 | 강력한 마법 에너지가 방출되며 빠르게 휘감기는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=431e60421b0847568e3f9ac314ec28dd) |
| ☐ | `d8ec056693214a0a8e3f1ee372d45193` | audioclip-34125 | 5 | 0.845 | 강력한 폭발과 함께 불길이 치솟는 듯한 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d8ec056693214a0a8e3f1ee372d45193) |
| ☐ | `97c8ba01250944cf851e4186459f76bc` | audioclip-23726 | 3.8 | 0.844 | 강렬하게 타오르는 불꽃이나 화염 마법의 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=97c8ba01250944cf851e4186459f76bc) |
| ☐ | `031f57412ea945b6aadcea1fe953e435` | audioclip-592 | 3.2 | 0.844 | 강력한 화염 마법 폭발이나 스킬 사용 시 발생하는 에너지 방출음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=031f57412ea945b6aadcea1fe953e435) |
| ☐ | `73fa9fbd48594ea7a95a198349449eb7` | audioclip-18169 | 2 | 0.844 | 강력한 화염 마법이나 폭발 스킬의 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=73fa9fbd48594ea7a95a198349449eb7) |
| ☐ | `f3499946e86c4a1ca6f92000ab641d5f` | audioclip-38262 | 3.4 | 0.843 | 강력한 화염이 폭발하며 거세게 타오르는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f3499946e86c4a1ca6f92000ab641d5f) |
| ☐ | `4d844c472db743ab8ab8987b27956b04` | audioclip-12266 | 3.1 | 0.842 | 강력한 화염이나 에너지가 폭발하며 퍼지는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4d844c472db743ab8ab8987b27956b04) |
| ☐ | `524b08c78e0b497aa5627b95ec219382` | audioclip-13024 | 3.4 | 0.841 | 강력한 화염 마법이 폭발하며 타오르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=524b08c78e0b497aa5627b95ec219382) |
| ☐ | `86db52415d0949c9bce3381d836ad476` | audioclip-21155 | 3.8 | 0.841 | 강력한 마법 에너지가 폭발하며 발생하는 화염 속성의 스킬 공격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=86db52415d0949c9bce3381d836ad476) |
| ☐ | `63987f9ab5b14efa8dd4e123b7ecf337` | audioclip-15654 | 2.3 | 0.841 | 강력한 폭발음과 함께 불꽃이 터지는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=63987f9ab5b14efa8dd4e123b7ecf337) |
| ☐ | `9cf09802f13d4d838e284e2f1214acea` | audioclip-24549 | 2.2 | 0.84 | 강력한 화염 마법이나 폭발이 일어나는 웅장한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9cf09802f13d4d838e284e2f1214acea) |

### 영웅스킬-메카닉  <sub>(effect, 검색어: 메카닉 로봇 미사일 런처 스킬 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `462bab718e984714933f0c8027959965` | audioclip-11112 | 4 | 0.813 | 강력한 에너지 레이저가 발사되는 기계적인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=462bab718e984714933f0c8027959965) |
| ☐ | `f91f37239ee3447486cbb9c40da4fc82` | audioclip-39136 | 4.9 | 0.81 | 강력한 에너지 레이저를 발사하는 기계적인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f91f37239ee3447486cbb9c40da4fc82) |
| ☐ | `c00b25e55f2840c8bb4f13396e3d465b` | audioclip-30087 | 2.1 | 0.808 | 날카롭고 빠른 금속성의 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c00b25e55f2840c8bb4f13396e3d465b) |
| ☐ | `f226c3147988401ead5865cc6f24586e` | audioclip-38048 | 7.9 | 0.797 | 강력한 에너지 포격이나 기계적인 폭발음이 동반된 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f226c3147988401ead5865cc6f24586e) |
| ☐ | `6582e56c9eb545d780180d4969382cff` | audioclip-15964 | 5.4 | 0.796 | 강력한 폭발음과 기계적인 금속음이 섞인 중량감 있는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6582e56c9eb545d780180d4969382cff) |
| ☐ | `ace9ad8a86b4474e8fdb34e96dbd0d24` | audioclip-27116 | 3.7 | 0.796 | 기계적인 연사음 뒤에 강력한 폭발음이 이어지는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ace9ad8a86b4474e8fdb34e96dbd0d24) |
| ☐ | `f0d413ba8085447798e96e7e40b30e58` | audioclip-62897 | 3.4 | 0.793 | 강력한 기계 장치나 에너지 무기가 발사되어 폭발하는 웅장한 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f0d413ba8085447798e96e7e40b30e58) |
| ☐ | `b9153096b4104c139239d1873b7c28d2` | audioclip-29019 | 6.6 | 0.793 | 강력한 에너지를 충전하여 발사하는 공상과학 스타일의 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b9153096b4104c139239d1873b7c28d2) |
| ☐ | `b995a94403e64fd78e0caf33c57e4af0` | audioclip-61065 | 2.6 | 0.793 | 강력하고 묵직한 기계적 또는 금속성 타격음이 포함된 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b995a94403e64fd78e0caf33c57e4af0) |
| ☐ | `e6dd58448f5f48108da2103102e2354a` | audioclip-36301 | 4.1 | 0.793 | 기계적인 소리와 에너지 방출음이 섞인 연속적인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e6dd58448f5f48108da2103102e2354a) |
| ☐ | `ab1104b2e99c4725b79c4b29e3072347` | audioclip-26810 | 3.7 | 0.79 | 강력한 폭발과 함께 금속적인 울림이 느껴지는 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ab1104b2e99c4725b79c4b29e3072347) |
| ☐ | `4122b76fef50470cb2a6431904daa09c` | audioclip-61614 | 1.4 | 0.79 | 강력한 폭발음과 기계적인 타격음이 연속되는 화려한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4122b76fef50470cb2a6431904daa09c) |
| ☐ | `30f31595b7bf484283b4dd5caed6372f` | audioclip-60362 | 7.1 | 0.789 | 기계적인 타격음과 함께 발생하는 묵직한 에너지 폭발 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=30f31595b7bf484283b4dd5caed6372f) |
| ☐ | `00270f545feb469cb22241efc386812a` | audioclip-97 | 4.2 | 0.789 | 강력한 에너지 포격이나 기계적인 폭발이 일어나는 화려한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=00270f545feb469cb22241efc386812a) |
| ☐ | `1999c487b6a0419d948579000e836310` | audioclip-4169 | 3.7 | 0.788 | 기계적인 느낌의 연속적인 폭발과 파편이 튀는 소리가 포함된 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1999c487b6a0419d948579000e836310) |
| ☐ | `c2aa2ab77dc44d89b93e0f87a268e0c2` | audioclip-30511 | 3 | 0.787 | 기계적인 느낌의 무거운 금속 타격음이 연속적으로 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c2aa2ab77dc44d89b93e0f87a268e0c2) |
| ☐ | `c6684c5b2cf94adf98bc996efe4653fa` | audioclip-31124 | 2.8 | 0.786 | 강력한 폭발과 함께 금속적인 충격음이 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c6684c5b2cf94adf98bc996efe4653fa) |
| ☐ | `856f6740c93b4e5280bd90a0eec329d6` | audioclip-20951 | 5.7 | 0.786 | 기계적인 느낌의 빠른 연타 공격과 마지막 타격음이 포함된 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=856f6740c93b4e5280bd90a0eec329d6) |
| ☐ | `8a22289cc83848bbadee4c1f603ba321` | audioclip-60437 | 6.6 | 0.785 | 기계적인 충전음과 함께 여러 번의 날카로운 금속성 타격이 이어지는 강력한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8a22289cc83848bbadee4c1f603ba321) |
| ☐ | `70040a0555744508bbd7b640e557192d` | audioclip-17557 | 5.1 | 0.785 | 개틀링 건이나 기계 장치가 빠르게 연속으로 발사되는 날카로운 금속성 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=70040a0555744508bbd7b640e557192d) |

### 영웅스킬-나이트로드  <sub>(effect, 검색어: 나이트로드 표창 던지기 스킬 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `6dcf25bc078c4814b47adb6b374afe63` | audioclip-17218 | 1.5 | 0.815 | 무언가를 빠르게 던지거나 발사하는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6dcf25bc078c4814b47adb6b374afe63) |
| ☐ | `ca4c49b20de341d4bb9dea4c1c9c68fc` | audioclip-75 | 0.5 | 0.812 | 금속 무기가 부딪히거나 단단한 물체에 타격되는 날카로운 금속음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ca4c49b20de341d4bb9dea4c1c9c68fc) |
| ☐ | `d241be0f5d4d429ba2ce750b3d02eab9` | audioclip-33000 | 3.5 | 0.775 | 날카로운 물체가 공기를 가르며 빠르게 날아가는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d241be0f5d4d429ba2ce750b3d02eab9) |
| ☐ | `722bf79413164973869325e94364168d` | audioclip-17887 | 3.3 | 0.774 | 마법 에너지가 발사되어 타격하는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=722bf79413164973869325e94364168d) |
| ☐ | `6bc961c36ca94d609eefa68714636ab3` | audioclip-16920 | 2 | 0.773 | 마법 에너지가 빠르게 날아가며 발생하는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6bc961c36ca94d609eefa68714636ab3) |
| ☐ | `58778cf5b5de43fb831b90c1677ead4d` | audioclip-62334 | 1.8 | 0.769 | 무언가를 빠르게 던지거나 발사할 때 발생하는 마법적인 투사체 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=58778cf5b5de43fb831b90c1677ead4d) |
| ☐ | `a4c452b41ae8405aa3e959a2509970b1` | audioclip-25820 | 3.7 | 0.767 | 에너지가 담긴 투사체가 빠르게 날아가는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a4c452b41ae8405aa3e959a2509970b1) |
| ☐ | `5b6b777f0e564b84aa09fe68c9115535` | audioclip-14407 | 1.1 | 0.766 | 검으로 무언가를 날카롭게 베거나 타격하는 금속성 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5b6b777f0e564b84aa09fe68c9115535) |
| ☐ | `ce1226a418db495e919a0aaec492cd4c` | audioclip-32340 | 3.2 | 0.766 | 빠르고 날카롭게 공기를 가르며 날아가는 투사체 또는 베기 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ce1226a418db495e919a0aaec492cd4c) |
| ☐ | `3234da689f2946a1a83e70a9ecf4ddd0` | audioclip-7996 | 3 | 0.765 | 바람이 휘감기며 마법 투사체가 날아가는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3234da689f2946a1a83e70a9ecf4ddd0) |
| ☐ | `9706c7e7cd5448679ed4eaa521bf1258` | audioclip-23594 | 1.3 | 0.765 | 빠르게 휘둘러 타격하는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9706c7e7cd5448679ed4eaa521bf1258) |
| ☐ | `c464e3f280b64ef48852d42de9b4cd82` | audioclip-30778 | 4 | 0.764 | 마법 에너지가 빠르게 발사되거나 휘둘러지는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c464e3f280b64ef48852d42de9b4cd82) |
| ☐ | `a85f7e677b95478bbe54cd8702090e2f` | audioclip-26398 | 3.1 | 0.764 | 빠르고 날카롭게 휘두르며 타격하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a85f7e677b95478bbe54cd8702090e2f) |
| ☐ | `41a8b196ad864ae1844abdcdbbdd69fa` | audioclip-10405 | 1.1 | 0.763 | 마법 투사체가 날아가서 가볍게 부딪히는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=41a8b196ad864ae1844abdcdbbdd69fa) |
| ☐ | `6dacc95a41db492fbbaca1fa68ecabf4` | audioclip-17191 | 1.3 | 0.763 | 빠르고 날카롭게 베는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6dacc95a41db492fbbaca1fa68ecabf4) |
| ☐ | `7ea93158e1b64a48847591ede4fcb637` | audioclip-19905 | 2.5 | 0.762 | 강력한 물리적 타격음과 함께 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7ea93158e1b64a48847591ede4fcb637) |
| ☐ | `5909635da36a4f40a4ecdaee66cce1b7` | audioclip-14063 | 2.4 | 0.762 | 바람이 휘감기며 마법 투사체가 날아가는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5909635da36a4f40a4ecdaee66cce1b7) |
| ☐ | `66c54ce7c4cf40d48b22c4cd942a01c9` | audioclip-16157 | 2.7 | 0.761 | 무언가를 빠르게 던지거나 발사할 때 발생하는 바람을 가르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=66c54ce7c4cf40d48b22c4cd942a01c9) |
| ☐ | `4ed43ad722164bb4b32cb028a8bd5496` | audioclip-12470 | 0.6 | 0.761 | 빠르고 날카롭게 휘두르는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4ed43ad722164bb4b32cb028a8bd5496) |
| ☐ | `fa83bfb724964467910feda763f4bf36` | audioclip-39342 | 2.3 | 0.76 | 여러 번 빠르게 휘두르는 듯한 마법 공격 또는 에너지 스킬 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fa83bfb724964467910feda763f4bf36) |

### 영웅스킬-나이트워커  <sub>(effect, 검색어: 나이트워커 표창 어둠 박쥐 스킬 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `83529166c98f420092183aa310b2d660` | audioclip-48 | 1.7 | 0.765 | 검을 휘두를 때 발생하는 날카롭고 빠른 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=83529166c98f420092183aa310b2d660) |
| ☐ | `54dc385f33cd4006aba1e2d636a65eb9` | audioclip-13414 | 5.3 | 0.756 | 어둠의 마법 에너지가 폭발하며 여러 번 타격하는 강력한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=54dc385f33cd4006aba1e2d636a65eb9) |
| ☐ | `01f8b72895ee46e190ad4fc66ae346d9` | audioclip-415 | 1.9 | 0.755 | 빠르고 날카롭게 휘두르는 듯한 스킬 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=01f8b72895ee46e190ad4fc66ae346d9) |
| ☐ | `6dcf25bc078c4814b47adb6b374afe63` | audioclip-17218 | 1.5 | 0.753 | 무언가를 빠르게 던지거나 발사하는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6dcf25bc078c4814b47adb6b374afe63) |
| ☐ | `a85f7e677b95478bbe54cd8702090e2f` | audioclip-26398 | 3.1 | 0.751 | 빠르고 날카롭게 휘두르며 타격하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a85f7e677b95478bbe54cd8702090e2f) |
| ☐ | `38230b0dec8e4e3eb903c513bb0fb031` | audioclip-8927 | 1.9 | 0.75 | 빠르게 휘두르는 듯한 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=38230b0dec8e4e3eb903c513bb0fb031) |
| ☐ | `ed3974c916914848a25dd08d29b68563` | audioclip-37237 | 1.8 | 0.748 | 날카로운 금속음이 섞인 빠른 검기 또는 스킬 공격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ed3974c916914848a25dd08d29b68563) |
| ☐ | `4ed43ad722164bb4b32cb028a8bd5496` | audioclip-12470 | 0.6 | 0.748 | 빠르고 날카롭게 휘두르는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4ed43ad722164bb4b32cb028a8bd5496) |
| ☐ | `6df14d0bb5474cd9b65f22cbbffd0441` | audioclip-17244 | 2.2 | 0.747 | 빠르고 날카롭게 휘두르는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6df14d0bb5474cd9b65f22cbbffd0441) |
| ☐ | `297cf5dea2584d01a682cad6a21d757b` | audioclip-41178 | 1.3 | 0.747 | 빠르고 날카롭게 무언가를 휘두르는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=297cf5dea2584d01a682cad6a21d757b) |
| ☐ | `722bf79413164973869325e94364168d` | audioclip-17887 | 3.3 | 0.746 | 마법 에너지가 발사되어 타격하는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=722bf79413164973869325e94364168d) |
| ☐ | `af57512e009f499f9f15cf2d29af95d1` | audioclip-27513 | 4.5 | 0.746 | 강력한 폭발음과 함께 묵직한 타격감을 주는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=af57512e009f499f9f15cf2d29af95d1) |
| ☐ | `9706c7e7cd5448679ed4eaa521bf1258` | audioclip-23594 | 1.3 | 0.746 | 빠르게 휘둘러 타격하는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9706c7e7cd5448679ed4eaa521bf1258) |
| ☐ | `17478d88bc5d4fee8f021876c244609d` | audioclip-3797 | 5.6 | 0.745 | 남성 캐릭터의 강한 기합과 함께 어두운 마법 기운이 소용돌이치는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=17478d88bc5d4fee8f021876c244609d) |
| ☐ | `fee926821a3a473b85553477d37992a1` | audioclip-40071 | 2.7 | 0.745 | 날카롭고 빠르게 휘두르는 스킬 공격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=fee926821a3a473b85553477d37992a1) |
| ☐ | `2b1d181e6cd745639f98661855ff4e14` | audioclip-61036 | 1.3 | 0.743 | 빠르고 날카롭게 베는 듯한 느낌의 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2b1d181e6cd745639f98661855ff4e14) |
| ☐ | `78b90b93017545b59160c19439723f19` | audioclip-18913 | 1.1 | 0.743 | 빠르고 날카로운 휘두르는 소리와 타격음이 섞인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=78b90b93017545b59160c19439723f19) |
| ☐ | `35457971c2804664bce095f0c9d979a3` | audioclip-8464 | 1.4 | 0.742 | 빠르게 휘두르거나 타격하는 듯한 짧고 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=35457971c2804664bce095f0c9d979a3) |
| ☐ | `b7a169f6ddb34345842f6ddd44399cb2` | audioclip-61042 | 1.3 | 0.742 | 빠르고 날카롭게 휘두르거나 이동하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b7a169f6ddb34345842f6ddd44399cb2) |
| ☐ | `31a5c54994814109887734f485650f9a` | audioclip-7896 | 1.9 | 0.742 | 빠르고 날카롭게 휘두르는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=31a5c54994814109887734f485650f9a) |

### 영웅스킬-소울마스터  <sub>(effect, 검색어: 소울마스터 검 빛 베기 스킬 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `39a723b838dc462f90b50f9f9b1601ab` | audioclip-9168 | 2.3 | 0.834 | 날카로운 검으로 공기를 가르며 공격하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=39a723b838dc462f90b50f9f9b1601ab) |
| ☐ | `8199e457f9ac4748a194646d6090cc8a` | audioclip-42073 | 1.5 | 0.832 | 날카로운 금속성 베기 소리와 함께 에너지가 방출되는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=8199e457f9ac4748a194646d6090cc8a) |
| ☐ | `534d1712ed4541838aa5ba3c28ebccdf` | audioclip-13160 | 3.2 | 0.83 | 날카로운 검으로 공기를 가르며 베는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=534d1712ed4541838aa5ba3c28ebccdf) |
| ☐ | `865dcf021cda44d3b2dfae129a7899d2` | audioclip-61246 | 3 | 0.827 | 검을 휘둘러 에너지를 방출하며 적을 베는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=865dcf021cda44d3b2dfae129a7899d2) |
| ☐ | `6cd3aff31d544ed7b08de8ea0174ee78` | audioclip-17077 | 3.7 | 0.827 | 날카로운 금속성 검격 소리와 함께 에너지가 방출되는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6cd3aff31d544ed7b08de8ea0174ee78) |
| ☐ | `1e8e6f797296474593a0ed0bc6f39517` | audioclip-4936 | 2.6 | 0.825 | 검으로 베는 듯한 날카로운 금속성 타격음과 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1e8e6f797296474593a0ed0bc6f39517) |
| ☐ | `6f7bd1e5aaf74c26b82730a2547a2426` | audioclip-17471 | 2.7 | 0.824 | 검이나 날카로운 무기로 빠르게 베는 듯한 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6f7bd1e5aaf74c26b82730a2547a2426) |
| ☐ | `7ae14d247e6b4fb6a6d4629140528ea1` | audioclip-19255 | 2.1 | 0.823 | 검으로 적을 빠르게 베는 날카로운 금속성 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7ae14d247e6b4fb6a6d4629140528ea1) |
| ☐ | `93c761dd06694c61b0173d14e6011aac` | audioclip-23113 | 3 | 0.823 | 날카로운 금속성 검격 소리와 함께 에너지가 방출되는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=93c761dd06694c61b0173d14e6011aac) |
| ☐ | `38e513a4e41845bfa51b4bc4ebeeb9e6` | audioclip-9054 | 2.6 | 0.823 | 검으로 빠르게 베는 날카롭고 강력한 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=38e513a4e41845bfa51b4bc4ebeeb9e6) |
| ☐ | `54a79c6270ca42bd826fb9db4afb547c` | audioclip-13387 | 2.5 | 0.822 | 검으로 베는 듯한 날카로운 금속음과 마법적인 에너지가 섞인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=54a79c6270ca42bd826fb9db4afb547c) |
| ☐ | `b777f9ce019d46069bab433053fa7dbc` | audioclip-28779 | 2.1 | 0.822 | 검을 휘둘러 적을 베는 날카롭고 강력한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b777f9ce019d46069bab433053fa7dbc) |
| ☐ | `97268e73402f4d50833f5b717a4c2ce0` | audioclip-23616 | 2.3 | 0.822 | 검으로 베는 날카로운 소리와 함께 마법적인 공명이 느껴지는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=97268e73402f4d50833f5b717a4c2ce0) |
| ☐ | `c9cb71cb94f34690bff6963316441222` | audioclip-31663 | 3.1 | 0.821 | 에너지가 실린 날카로운 검기 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c9cb71cb94f34690bff6963316441222) |
| ☐ | `96f61f9db3034684a12495f404bcc2a2` | audioclip-23586 | 2.2 | 0.821 | 검으로 날카롭게 베는 듯한 금속성 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=96f61f9db3034684a12495f404bcc2a2) |
| ☐ | `75f4ae44ceee4144b498867649b78ff4` | audioclip-18487 | 2 | 0.82 | 날카로운 금속성의 베기 소리와 에너지가 느껴지는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=75f4ae44ceee4144b498867649b78ff4) |
| ☐ | `f042965f01aa41a9aee032e887456f84` | audioclip-37738 | 4 | 0.82 | 빠르고 날카로운 마법 에너지 베기 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f042965f01aa41a9aee032e887456f84) |
| ☐ | `56c013bcaeba4999b09817f3a7fd2530` | audioclip-13701 | 1.5 | 0.819 | 날카로운 금속음과 마법 에너지가 섞인 검술 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=56c013bcaeba4999b09817f3a7fd2530) |
| ☐ | `583d7850d53a40f9830db7ac1df7224d` | audioclip-13945 | 7.8 | 0.819 | 빠르고 날카로운 검 휘두르는 소리와 짧은 효과음이 섞인 스킬 사운드 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=583d7850d53a40f9830db7ac1df7224d) |
| ☐ | `7b3e06140588497691143d11625960fb` | audioclip-19324 | 2.8 | 0.818 | 검으로 빠르게 베는 듯한 날카롭고 금속성 있는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7b3e06140588497691143d11625960fb) |

### 영웅스킬-스트라이커  <sub>(effect, 검색어: 스트라이커 번개 파도 주먹 스킬 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `9208c952ff1245a5b870c157ab350104` | audioclip-22838 | 3.7 | 0.81 | 강력한 전격 에너지가 방출되며 여러 번 타격하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9208c952ff1245a5b870c157ab350104) |
| ☐ | `1095ddded6f34de0bd1ccff79976de49` | audioclip-2727 | 2.8 | 0.795 | 전기 에너지가 방출되며 발생하는 강력한 마법 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1095ddded6f34de0bd1ccff79976de49) |
| ☐ | `0c3c2c364d134be687f953b9ad1da064` | audioclip-2001 | 7.8 | 0.793 | 강력한 마법 에너지가 폭발하며 발생하는 전기적인 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0c3c2c364d134be687f953b9ad1da064) |
| ☐ | `cb5c013813874394a90babf9d06ff872` | audioclip-31906 | 6.9 | 0.789 | 강력한 번개 마법과 함께 발생하는 묵직한 타격음과 폭발음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cb5c013813874394a90babf9d06ff872) |
| ☐ | `51024f6e1d5042c2ba00cf755c708fb0` | audioclip-12827 | 3.5 | 0.785 | 강력한 에너지가 실린 타격음 또는 스킬 발동 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=51024f6e1d5042c2ba00cf755c708fb0) |
| ☐ | `d4ae52672ede4440b64958521863c340` | audioclip-33398 | 2.8 | 0.784 | 전기 에너지가 방출되며 지지직거리는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d4ae52672ede4440b64958521863c340) |
| ☐ | `49f9f1b005954eeb9ec93d25d121bebf` | audioclip-11714 | 3 | 0.779 | 강력한 타격음과 함께 폭발하는 듯한 화려한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=49f9f1b005954eeb9ec93d25d121bebf) |
| ☐ | `6b7376652cc7475982387fa118218102` | audioclip-16862 | 3.7 | 0.779 | 강력한 물리적 타격감이 느껴지는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6b7376652cc7475982387fa118218102) |
| ☐ | `a0bb0074ad85432fb6ff7ad2df93767b` | audioclip-25150 | 2.9 | 0.778 | 강력한 타격감과 폭발음이 섞인 묵직한 스킬 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a0bb0074ad85432fb6ff7ad2df93767b) |
| ☐ | `cb7edad25cab48a88a89337b59ca0b40` | audioclip-31931 | 7.8 | 0.778 | 강력한 마법 에너지가 방출되며 폭발하는 화려한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=cb7edad25cab48a88a89337b59ca0b40) |
| ☐ | `37df16ca512c43f5982e314374b84172` | audioclip-8876 | 3.9 | 0.777 | 강력하고 날카로운 타격음이 포함된 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=37df16ca512c43f5982e314374b84172) |
| ☐ | `291d8ebb03c747c6ae00e25e59ada2ca` | audioclip-6608 | 3.4 | 0.776 | 강력한 폭발이나 충격을 동반한 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=291d8ebb03c747c6ae00e25e59ada2ca) |
| ☐ | `c20bf9ec3f53498c8c750819478eca2f` | audioclip-30417 | 3.7 | 0.775 | 남성 캐릭터의 기합 소리와 함께 전기 속성이 부여된 날카로운 검격 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c20bf9ec3f53498c8c750819478eca2f) |
| ☐ | `981f5e61e36a42869a5eccfded4d0b38` | audioclip-23775 | 5.9 | 0.775 | 강력한 마법 에너지가 폭발하며 발생하는 웅장하고 날카로운 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=981f5e61e36a42869a5eccfded4d0b38) |
| ☐ | `1c3214108cf340ee9ee90f2e81c87a83` | audioclip-4585 | 3.5 | 0.774 | 강력한 에너지가 방출되며 적을 타격하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1c3214108cf340ee9ee90f2e81c87a83) |
| ☐ | `d8bbb2664f9d4a44934c6759d0ae31b1` | audioclip-34088 | 3.3 | 0.774 | 강력한 폭발이나 묵직한 타격이 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d8bbb2664f9d4a44934c6759d0ae31b1) |
| ☐ | `ad336409438a4ba3a399c2941895af23` | audioclip-27171 | 3.7 | 0.774 | 천둥 주문을 외치는 목소리와 함께 강력한 번개가 떨어지는 마법 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ad336409438a4ba3a399c2941895af23) |
| ☐ | `9231a36aa8f540d692f2dda29641cfb1` | audioclip-22866 | 6.9 | 0.774 | 강력한 폭발과 천둥 소리가 섞인 웅장하고 파괴적인 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9231a36aa8f540d692f2dda29641cfb1) |
| ☐ | `900c56c10596403a8c85e18b270eefe4` | audioclip-60850 | 2.5 | 0.773 | 강력한 타격감과 함께 폭발하는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=900c56c10596403a8c85e18b270eefe4) |
| ☐ | `98ca7e60c8f84a68a97fcdc820073731` | audioclip-23872 | 2.2 | 0.773 | 강력한 에너지가 빠르게 이동하며 타격하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=98ca7e60c8f84a68a97fcdc820073731) |

### 영웅스킬-와일드헌터  <sub>(effect, 검색어: 와일드헌터 석궁 재규어 스킬 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `634a359221f744888b435bb9c200cd2b` | audioclip-15598 | 0.7 | 0.788 | 검을 휘두를 때 발생하는 날카롭고 빠른 금속성 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=634a359221f744888b435bb9c200cd2b) |
| ☐ | `c6150f95af38425183444660a956001b` | audioclip-31075 | 1.3 | 0.776 | 빠르고 날카롭게 휘두르는 듯한 물리적 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=c6150f95af38425183444660a956001b) |
| ☐ | `310fc1bd43744f2cb3da1610d41d9343` | audioclip-7818 | 3.3 | 0.767 | 강력한 에너지 폭발이나 마법 기술이 적중했을 때 발생하는 묵직한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=310fc1bd43744f2cb3da1610d41d9343) |
| ☐ | `a9ccec5d32b0474fa0a4626abeb042f5` | audioclip-26625 | 1.3 | 0.747 | 빠르고 날카롭게 휘두르는 물리적인 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a9ccec5d32b0474fa0a4626abeb042f5) |
| ☐ | `d9850331d24c4d13bb2c1125dca807e1` | audioclip-34217 | 2.4 | 0.743 | 마법적인 폭발이나 스킬 사용 시 발생하는 강력한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=d9850331d24c4d13bb2c1125dca807e1) |
| ☐ | `82b4aaf5eea040dd83b49107dbe3f9a0` | audioclip-20558 | 1.5 | 0.741 | 검으로 날카롭게 베는 듯한 금속성 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=82b4aaf5eea040dd83b49107dbe3f9a0) |
| ☐ | `7ea93158e1b64a48847591ede4fcb637` | audioclip-19905 | 2.5 | 0.741 | 강력한 물리적 타격음과 함께 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=7ea93158e1b64a48847591ede4fcb637) |
| ☐ | `559148fb4e984dabaa2620876e8286d8` | audioclip-13529 | 1.5 | 0.74 | 금속 무기로 적을 타격할 때 발생하는 날카롭고 강한 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=559148fb4e984dabaa2620876e8286d8) |
| ☐ | `722bf79413164973869325e94364168d` | audioclip-17887 | 3.3 | 0.74 | 마법 에너지가 발사되어 타격하는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=722bf79413164973869325e94364168d) |
| ☐ | `a85f7e677b95478bbe54cd8702090e2f` | audioclip-26398 | 3.1 | 0.739 | 빠르고 날카롭게 휘두르며 타격하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=a85f7e677b95478bbe54cd8702090e2f) |
| ☐ | `9706c7e7cd5448679ed4eaa521bf1258` | audioclip-23594 | 1.3 | 0.738 | 빠르게 휘둘러 타격하는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9706c7e7cd5448679ed4eaa521bf1258) |
| ☐ | `37df16ca512c43f5982e314374b84172` | audioclip-8876 | 3.9 | 0.735 | 강력하고 날카로운 타격음이 포함된 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=37df16ca512c43f5982e314374b84172) |
| ☐ | `3234da689f2946a1a83e70a9ecf4ddd0` | audioclip-7996 | 3 | 0.733 | 바람이 휘감기며 마법 투사체가 날아가는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3234da689f2946a1a83e70a9ecf4ddd0) |
| ☐ | `954ba561e48d451eb3f726b9f1ec78de` | audioclip-23320 | 3.9 | 0.733 | 몬스터가 위협적으로 으르렁거리는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=954ba561e48d451eb3f726b9f1ec78de) |
| ☐ | `5f940dd247db4147bbd896481f87e6b4` | audioclip-61162 | 1.5 | 0.732 | 빠르게 휘두르거나 이동하며 발생하는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5f940dd247db4147bbd896481f87e6b4) |
| ☐ | `35457971c2804664bce095f0c9d979a3` | audioclip-8464 | 1.4 | 0.731 | 빠르게 휘두르거나 타격하는 듯한 짧고 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=35457971c2804664bce095f0c9d979a3) |
| ☐ | `478594d9c36e4cc9bdb523abd9f6d97d` | audioclip-11325 | 1.3 | 0.731 | 빠르게 휘두르며 타격하는 물리적인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=478594d9c36e4cc9bdb523abd9f6d97d) |
| ☐ | `872f82bbaa3d45c489a49e29718e64f5` | audioclip-21204 | 1.5 | 0.731 | 무기를 휘둘러 공기를 가르거나 적을 베는 듯한 날카롭고 빠른 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=872f82bbaa3d45c489a49e29718e64f5) |
| ☐ | `78b90b93017545b59160c19439723f19` | audioclip-18913 | 1.1 | 0.73 | 빠르고 날카로운 휘두르는 소리와 타격음이 섞인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=78b90b93017545b59160c19439723f19) |
| ☐ | `6687c58a60dd4e86b2b707b1a422f585` | audioclip-16123 | 2.1 | 0.73 | 빠르고 날카롭게 휘두르거나 타격하는 물리적인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6687c58a60dd4e86b2b707b1a422f585) |

### 영웅스킬-윈드브레이커  <sub>(effect, 검색어: 윈드브레이커 바람 활 회오리 스킬 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `da33cdec988242ad8f2dd9711d3ecf8d` | audioclip-34318 | 2.5 | 0.854 | 강한 바람이나 마법 에너지가 휘몰아치며 공격하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=da33cdec988242ad8f2dd9711d3ecf8d) |
| ☐ | `18041e155b3f45eb8fda6b09a2b0fd58` | audioclip-3918 | 5.2 | 0.848 | 강력한 바람이나 마법 에너지가 휘몰아치는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=18041e155b3f45eb8fda6b09a2b0fd58) |
| ☐ | `f87c005599234a3dbfb60974529d2572` | audioclip-39035 | 6.6 | 0.844 | 강력한 바람을 일으키며 여러 번 빠르게 공격하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f87c005599234a3dbfb60974529d2572) |
| ☐ | `5909635da36a4f40a4ecdaee66cce1b7` | audioclip-14063 | 2.4 | 0.839 | 바람이 휘감기며 마법 투사체가 날아가는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5909635da36a4f40a4ecdaee66cce1b7) |
| ☐ | `da1ccc4c66964fafb29ec5d6f4e9d58f` | audioclip-61788 | 2.6 | 0.837 | 바람이나 마법 에너지가 빠르게 방출되는 듯한 스킬 공격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=da1ccc4c66964fafb29ec5d6f4e9d58f) |
| ☐ | `5f5bf221903b49dd8198400f59d5190a` | audioclip-15033 | 3 | 0.835 | 바람이 휘몰아치는 듯한 빠르고 날카로운 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=5f5bf221903b49dd8198400f59d5190a) |
| ☐ | `ac090a410cab4a7ebd9cec50f6a7e767` | audioclip-26955 | 3.1 | 0.831 | 강력한 바람이 휘몰아치는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ac090a410cab4a7ebd9cec50f6a7e767) |
| ☐ | `f0f6721a07b440a5bb232bcfaafedf86` | audioclip-37860 | 3.5 | 0.83 | 강력한 바람이나 마법 에너지가 방출되는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f0f6721a07b440a5bb232bcfaafedf86) |
| ☐ | `86681ee1d59f4b5e9fa632b4bafff93a` | audioclip-61382 | 2.2 | 0.83 | 빠르게 공기를 가르는 듯한 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=86681ee1d59f4b5e9fa632b4bafff93a) |
| ☐ | `0ca6db9c34384b49aab60394509d7799` | audioclip-2061 | 3.3 | 0.829 | 바람이나 마법 에너지를 빠르게 발사하는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0ca6db9c34384b49aab60394509d7799) |
| ☐ | `3707586a2ca44fbd8b65175bc2779776` | audioclip-61294 | 1.8 | 0.829 | 바람을 가르며 빠르게 움직이거나 스킬을 시전할 때 발생하는 날카로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3707586a2ca44fbd8b65175bc2779776) |
| ☐ | `3b07c9fca01f41a1aef803694b204c63` | audioclip-9374 | 3 | 0.828 | 바람이나 마법 에너지가 빠르게 휘몰아치는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3b07c9fca01f41a1aef803694b204c63) |
| ☐ | `3234da689f2946a1a83e70a9ecf4ddd0` | audioclip-7996 | 3 | 0.828 | 바람이 휘감기며 마법 투사체가 날아가는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=3234da689f2946a1a83e70a9ecf4ddd0) |
| ☐ | `6bc961c36ca94d609eefa68714636ab3` | audioclip-16920 | 2 | 0.827 | 마법 에너지가 빠르게 날아가며 발생하는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6bc961c36ca94d609eefa68714636ab3) |
| ☐ | `1835c8fe4e204ece83c48856f8ea3504` | audioclip-3949 | 2.4 | 0.826 | 빠르고 날카롭게 휘두르는 듯한 바람 소리와 함께 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1835c8fe4e204ece83c48856f8ea3504) |
| ☐ | `e0645f18498d46349a65d0b4500aea7c` | audioclip-60546 | 2.3 | 0.825 | 빠르고 강력하게 휘두르는 바람 소리와 함께 발생하는 스킬 공격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e0645f18498d46349a65d0b4500aea7c) |
| ☐ | `ff3de44c240a44319bb1a24e6ffd9d09` | audioclip-40121 | 2.8 | 0.825 | 빠르게 이동하거나 스킬을 시전할 때 발생하는 바람 가르는 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=ff3de44c240a44319bb1a24e6ffd9d09) |
| ☐ | `f51b9f6221d640e48402786f1e4e3eb0` | audioclip-38554 | 2.2 | 0.824 | 강한 바람이 휘몰아치는 듯한 마법 또는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f51b9f6221d640e48402786f1e4e3eb0) |
| ☐ | `34067d50f32143349e7566310244bebf` | audioclip-60868 | 4.4 | 0.824 | 강력한 바람이 휘몰아치는 마법 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=34067d50f32143349e7566310244bebf) |
| ☐ | `2c2e844fd94040e18819123d60c986e8` | audioclip-7071 | 2.5 | 0.823 | 빠르고 날카롭게 휘두르는 바람 소리와 함께 발생하는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=2c2e844fd94040e18819123d60c986e8) |

### 영웅스킬-제논  <sub>(effect, 검색어: 제논 에너지 레이저 기계 스킬 효과음)</sub>

| 채택 | RUID | 이름 | 길이 | 점수 | 설명 | 미리듣기 |
|---|---|---|---:|---:|---|---|
| ☐ | `f91f37239ee3447486cbb9c40da4fc82` | audioclip-39136 | 4.9 | 0.852 | 강력한 에너지 레이저를 발사하는 기계적인 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f91f37239ee3447486cbb9c40da4fc82) |
| ☐ | `462bab718e984714933f0c8027959965` | audioclip-11112 | 4 | 0.842 | 강력한 에너지 레이저가 발사되는 기계적인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=462bab718e984714933f0c8027959965) |
| ☐ | `581cf8e65fc9488c9730b694debee137` | audioclip-13920 | 7.1 | 0.834 | 강력한 에너지 충전 후 발사되는 기계적인 레이저 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=581cf8e65fc9488c9730b694debee137) |
| ☐ | `54f603c95c9e4d1085a8e3174b3c156d` | audioclip-13455 | 5 | 0.822 | 미래적인 레이저 충전 소리에 이어지는 강력한 금속성 폭발 및 타격 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=54f603c95c9e4d1085a8e3174b3c156d) |
| ☐ | `f226c3147988401ead5865cc6f24586e` | audioclip-38048 | 7.9 | 0.82 | 강력한 에너지 포격이나 기계적인 폭발음이 동반된 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f226c3147988401ead5865cc6f24586e) |
| ☐ | `e6386d6de1c841c4a92df8b1b91af3fb` | audioclip-36181 | 4.1 | 0.811 | 미래지향적인 레이저나 에너지 빔이 발사되는 날카로운 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e6386d6de1c841c4a92df8b1b91af3fb) |
| ☐ | `06e9cf6f050f4bda88f1c51f3fc22760` | audioclip-1193 | 2.2 | 0.81 | 날카로운 금속음과 함께 에너지가 방출되는 듯한 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=06e9cf6f050f4bda88f1c51f3fc22760) |
| ☐ | `0ab31646b1594dc3874642849dae0d56` | audioclip-1761 | 4.9 | 0.806 | 강력한 에너지 빔이 발사되어 폭발하는 공상과학 스타일의 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=0ab31646b1594dc3874642849dae0d56) |
| ☐ | `b9153096b4104c139239d1873b7c28d2` | audioclip-29019 | 6.6 | 0.806 | 강력한 에너지를 충전하여 발사하는 공상과학 스타일의 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b9153096b4104c139239d1873b7c28d2) |
| ☐ | `56b3ff8e53b5460e8b162c7d56df6857` | audioclip-13702 | 10.8 | 0.804 | 강력한 에너지 빔이 발사되어 폭발하는 미래적인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=56b3ff8e53b5460e8b162c7d56df6857) |
| ☐ | `4086ce8af5dc47669cda7aeab3c65bf1` | audioclip-41431 | 7 | 0.802 | 에너지를 충전한 뒤 강력한 레이저 빔을 발사하는 공상과학 스타일의 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4086ce8af5dc47669cda7aeab3c65bf1) |
| ☐ | `f6305472467f4da387e3a611387b49a2` | audioclip-38705 | 2.2 | 0.802 | 날카로운 금속음과 에너지가 섞인 강력한 스킬 타격음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=f6305472467f4da387e3a611387b49a2) |
| ☐ | `30f31595b7bf484283b4dd5caed6372f` | audioclip-60362 | 7.1 | 0.799 | 기계적인 타격음과 함께 발생하는 묵직한 에너지 폭발 소리 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=30f31595b7bf484283b4dd5caed6372f) |
| ☐ | `4c995234c6b9425381bc89641c00d78e` | audioclip-12114 | 2.6 | 0.799 | 강력한 에너지가 모인 뒤 날카롭게 베고 폭발하는 듯한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=4c995234c6b9425381bc89641c00d78e) |
| ☐ | `1930cb081aa94525a2b645715765bc9d` | audioclip-4107 | 6.3 | 0.799 | 에너지나 레이저를 빠르게 여러 번 발사하는 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=1930cb081aa94525a2b645715765bc9d) |
| ☐ | `e6dd58448f5f48108da2103102e2354a` | audioclip-36301 | 4.1 | 0.796 | 기계적인 소리와 에너지 방출음이 섞인 연속적인 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e6dd58448f5f48108da2103102e2354a) |
| ☐ | `9bf851bfa45d4e82aef3ad34111280a6` | audioclip-24401 | 3.4 | 0.796 | 강력한 에너지가 방출되며 발생하는 묵직하고 날카로운 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=9bf851bfa45d4e82aef3ad34111280a6) |
| ☐ | `e890e6b1e8834d7594b597e1f55dfc95` | audioclip-36562 | 2.9 | 0.794 | 강력한 마법 에너지나 레이저 빔을 발사하는 화려한 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=e890e6b1e8834d7594b597e1f55dfc95) |
| ☐ | `b17bffdb98f4461cad7fc5dae3c72971` | audioclip-27829 | 5.1 | 0.793 | 강력한 기계적 에너지 충전과 폭발적인 타격음이 포함된 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=b17bffdb98f4461cad7fc5dae3c72971) |
| ☐ | `6cd3aff31d544ed7b08de8ea0174ee78` | audioclip-17077 | 3.7 | 0.793 | 날카로운 금속성 검격 소리와 함께 에너지가 방출되는 스킬 효과음 | [열기](https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=6cd3aff31d544ed7b08de8ea0174ee78) |


## 기존 영웅 데이터의 사운드 보유 현황 (HeroData BuildVfx 기준)

| 영웅 | Q | W | E | R | T | 기타 키 |
|---|---|---|---|---|---|---|
| BattleMage | -/- | -/- | -/- | -/- | -/- |  |
| Bishop | sound/- | -/- | sound/- | sound/- | sound/- |  |
| Blaster | -/- | -/- | -/- | -/- | -/- |  |
| Bowmaster | sound/impact | -/- | sound/impact | sound/impact | -/- |  |
| Captain | -/- | -/- | -/- | -/- | -/- |  |
| DarkKnight | sound/impact | sound/impact | sound/impact | sound/impact | sound/impact |  |
| FlameWizard | -/- | -/- | -/- | -/- | -/- |  |
| Mechanic | -/- | -/- | -/- | -/- | -/- |  |
| NightLord | -/- | -/- | -/- | -/- | -/- |  |
| NightWalker | -/- | -/- | -/- | -/- | -/- |  |
| SoulMaster | -/- | - | - | - | -/- | WB:-/-, WC:-/-, EB:-/-, EC:-/-, RB:-/-, RC:-/- |
| Striker | - | -/- | - | - | -/- | QB:-/-, QC:-/-, EB:-/-, EC:-/-, RB:-/-, RC:-/- |
| WildHunter | -/- | -/- | -/- | -/- | -/- |  |
| WindBreaker | -/- | -/- | -/- | -/- | -/- |  |
| Xenon | -/- | -/- | -/- | -/- | -/- |  |

`sound/impact` = 시전음/명중음 둘 다 있음, `sound/-` = 시전음만, `-` = 없음(또는 그 키의 vfx 항목 없음).

점검 결과: **다크나이트**만 Q~T 시전음+명중음 완비. **보우마스터**는 W·T 시전음과 전 키 명중음 일부 없음(Q/E/R만 완비). **비숍**은 W(홀리 파운틴) 시전음 없음, 명중음은 전 키 없음. 나머지 12명은 전부 없음. 소울마스터·스트라이커는 연계 키(WB/WC…)도 전부 비어 있다.

VOICE 결과는 리소스에 설명이 없어 표가 비어 있다 — 링크를 열어 직접 들어 봐야 한국어 멘트인지 알 수 있다.

## 다음 단계
1. 이 목록에서 ✅ 고른 뒤 알려 주면 `UIResources`처럼 `SoundResources` @Logic에 슬롯별 RUID 상수를 만들고, 버튼/토스트/생산/건설/전투/영웅 각 호출 지점에 `_SoundService:PlaySound(ruid, volume)`를 연결한다.
2. BGM은 맵별 `_SoundService:PlayBGM` 류 API 확인 후 로비/인게임/승패 전환을 `SceneController`·`LobbyController`에 연결한다.
3. 음성(voice) 리소스에 한국어 안내 멘트가 있는지는 아래 VOICE 테스트 항목 결과로 판단한다.

## 모험가 메인 BGM 확정 후보 (기준곡 유사도 검색, 2026-10-05)

기준곡: `a8d9d161381c4f7bab3b95f8871662eb` sound-375 (205.8초) — "신비롭고 긴장감 있는 분위기에서 점차 웅장하고 모험적인 느낌으로 변화하는 오케스트라". 아래는 사이트의 유사 리소스 API(topK 40) 결과를 용도별로 추린 것.

| 용도 | 채택 | RUID | 이름 | 길이 | 유사도 | 설명 |
|---|---|---|---|---:|---:|---|
| 순환 A (기준곡과 같은 결) | ☐ | `e755890f739d4e92901ab4104df8b04c` | sound-549 | 152.0 | 0.898 | 긴박하고 웅장한 오케스트라, 전투·추격 |
| 순환 A | ☐ | `e5c1aa0cec0b46518f48d55b7a311c73` | sound-545 | 177.1 | 0.872 | 긴장감 넘치는 오케스트라, 모험·전투의 긴박함 |
| 순환 A | ☐ | `7a8f657721f7432fa0804dfbf2b8aadc` | sound-255 | 260.3 | 0.863 | 긴장감+신비, 리드미컬한 던전/전투 |
| 순환 A | ☐ | `be5fb97e993e48b29e23b55ca2029610` | sound-437 | 200.5 | 0.859 | 신비롭고 긴장감, 탐험·조사 리듬 |
| 순환 A | ☐ | `d9884ccae86d44a1aa9a91a8b2fd84ca` | sound-513 | 154.5 | 0.856 | 웅장·긴장, 모험/전투의 서막 |
| 순환 B (밝은 모험가 변주) | ☐ | `022d0be8aacf4cb19851c11eeebccb96` | sound-7 | 157.0 | 0.850 | 신비롭고 모험적, 마을·필드 탐험 |
| 순환 B | ☐ | `4fc7d1d6121d48f4b4051e98fff30a86` | sound-160 | 216.9 | 0.850 | 플루트·현악, 밝고 희망찬 모험 테마 |
| 순환 B | ☐ | `ea14202614c74967a9461c4521aab7e3` | sound-554 | 151.1 | 0.841 | 피아노·현악·플루트 판타지 모험 |
| 순환 B | ☐ | `c5b4f2b9b4ea48c8b2c105d8c52bce20` | sound-458 | 145.5 | 0.820 | 신비로운 플루트 → 경쾌한 모험 오케스트라 |
| 순환 B | ☐ | `7272cf2a358e483bbe8ca83080ce3894` | sound-234 | 125.8 | 0.833 | 경쾌한 리듬, 피아노·목관 모험 |
| 교전 전환(선택) | ☐ | `ac30e4669c3e445783a0ded36cfa52e2` | sound-383 | 145.9 | 0.840 | 빠른 전자음+오케스트라 전투 |
| 교전 전환(선택) | ☐ | `d835d42a9a054229a8c98f9ff2df850a` | sound-507 | 134.7 | 0.835 | 긴장감 리드미컬 던전/전투 |
| 교전 전환(선택) | ☐ | `6a51add7c2214e0baf78033a4847b56a` | sound-213 | 136.5 | 0.819 | 긴장감 리듬+웅장 오케스트라 전투 |

보스전 성격이 강한 sound-125(`3826f700…`, 0.893)는 메인 순환보다 교전 전환에 더 맞아 위에서 뺐다. 추천 구성: 기준곡 + 순환 A 1곡 + 순환 B 1곡(3곡 순환, 합 8~10분). 미리듣기: `https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=<RUID>`


### 모험가 메인 BGM — 2차 후보 (sound-255 확정 후 추가 추출, 2026-10-05)

확정: `7a8f657721f7432fa0804dfbf2b8aadc` sound-255 ✅. 아래는 sound-255의 유사곡(topK 60) + 의미 검색 4회에서 1차 표와 겹치지 않는 것만. 보스전 전용·사이버펑크·8비트·산업 계열은 뺐다.

| 결 | 채택 | RUID | 이름 | 길이 | 유사도 | 설명 |
|---|---|---|---|---:|---:|---|
| 긴장 리듬(255와 같은 결) | ☐ | `c1ac907e0ca644b5943c47c8801cc1f1` | sound-447 | 126.5 | 0.852 | 웅장·긴장, 던전 탐험·전투 |
| 긴장 리듬 | ☐ | `183b609d03ed43bdb3abb419bd9df933` | sound-49 | 129.9 | 0.841 | 던전/미션 비트감, 오케+신스 |
| 긴장 리듬 | ☐ | `eabdc2ee5dfc4c238104ab9607c3bb11` | sound-556 | 149.4 | 0.826 | 신비롭고 리드미컬, 전자+오케 모험 |
| 긴장 리듬 | ☐ | `11d73722121249679de8bf8e4478341d` | sound-33 | 125.8 | 0.840 | 웅장·긴박, 현악+타악 모험/전투 |
| 긴장 리듬 | ☐ | `b1682186f26d409089b001feaa0a88b9` | sound-396 | 135.1 | 0.836 | 웅장·긴박 오케, 전투·모험 |
| 신비 도입 → 고조(기준곡 375와 같은 결) | ☐ | `e708d95c152245e8be3f8a5eb447b308` | sound-547 | 173.6 | 0.842 | 현악·피아노 신비·긴장, 점차 고조 시네마틱 |
| 신비 도입 → 고조 | ☐ | `7671a665727041598c4a358060aeae40` | sound-244 | 156.6 | 0.833 | 신비 도입 → 웅장·박진 모험 |
| 신비 도입 → 고조 | ☐ | `8fda117d789c4d4a8c123a3b5f8773a8` | sound-314 | 172.6 | 0.779 | 신비 도입 → 강렬 클라이맥스 모험 |
| 신비 도입 → 고조 | ☐ | `80a18b7f3e87412e8e8c487cdb8a065b` | sound-268 | 153.6 | 0.793 | 신비·기묘, 오케+전자, 긴장과 호기심 |
| 이국적 타악 모험 | ☐ | `ebcd7440e61c46f28d9b3dfa52b113ff` | sound-560 | 237.1 | 0.823 | 강렬 타악 + 이국 플루트, 모험심·긴장 |
| 이국적 타악 모험 | ☐ | `86c104bf5ff84f8693a471ef40105975` | sound-283 | 135.2 | 0.791 | 웅장 오케 + 이국 타악, 모험·탐험 |
| 던전·마법 탐험(짧음) | ☐ | `b83dc196364f4f1087b03b3e4e132fc4` | sound-414 | 115.3 | 0.805 | 신비·긴장, 마법 탐험·던전 |
| 밝은 변주(순환 B) | ☐ | `f5bb92d91e134c699e7bb2cf1aaca8e6` | sound-575 | 117.1 | 0.824 | 웅장 브라스 + 경쾌 현악, 활기찬 모험 |
| 밝은 변주 | ☐ | `e08a91d5292e423ebbc511ff14df482c` | sound-537 | 146.9 | 0.819 | 경쾌 피아노 + 오케, 밝은 모험 마을 |
| 밝은 변주 | ☐ | `80be8e7600c041bd8032fc6e950ca7e9` | sound-269 | 138.2 | 0.819 | 밝고 경쾌한 RPG 모험, 피아노+오케 |


## 시그너스 메인 BGM 후보 (기준곡 유사도 검색, 2026-10-05)

기준곡: `063f1dddbf8b4a1bb9067b0c7a196922` sound-14 (189.6초) — "신비롭고 서정적인 오케스트라, 피아노와 현악기, 평화로운 느낌". 유사곡 topK 50 + 의미 검색 3회(성가·고귀함·성스러움)에서 추림. 60초 미만 짧은 곡, 기괴·국악·보스전 전용은 뺐다.

| 결 | 채택 | RUID | 이름 | 길이 | 유사도 | 설명 |
|---|---|---|---|---:|---:|---|
| 서정·신비(기준곡과 같은 결) | ☐ | `ba8ce178a584420d98e6e9c9db792881` | sound-422 | 149.5 | 0.833 | 몽환적 피아노·현악, 평화로운 탐험 |
| 서정·신비 | ☐ | `e277da825c0f4ce5805d04617cab5cd3` | sound-540 | 130.1 | 0.813 | 피아노·현악, 서정적이고 감동적 |
| 서정·신비 | ☐ | `bcc73825742745089f771fbb23c881e9` | sound-432 | 129.1 | 0.811 | 평화롭고 신비로운 서정 |
| 서정·신비 | ☐ | `8e366297ce4d469bb6b211e1945a4141` | sound-310 | 141.5 | 0.808 | 판타지 세계의 서사, 피아노·현악 |
| 서정·신비 | ☐ | `a4139e0733154eb1a2f1d785caf78c1e` | sound-364 | 149.9 | 0.807 | 피아노 중심, 차분하고 신비 |
| 서정·신비 | ☐ | `61c0bb4a75454e21aaf00a09a0138bea` | sound-199 | 138.1 | 0.798 | 우아하고 서정적, 피아노·바이올린 |
| 서정·신비 | ☐ | `190ac389eaf547e1b817baaca733a5d0` | sound-50 | 166.6 | 0.779 | 잔잔한 피아노·현악, 몽환 |
| 서정 → 확장(순환에 기복) | ☐ | `9642ef6c4a4a4e83984665eedc2840a9` | sound-333 | 140.7 | 0.781 | 서정적 피아노 → 풍성한 오케스트라로 확장 |
| 서정 → 확장 | ☐ | `fcd18880cff0408e881dac4aa3e4169b` | sound-590 | 136.3 | 0.798 | 잔잔한 피아노·현악에 긴장감 |
| 우아·왈츠(기사단 궁정 느낌) | ☐ | `4c7aea4348314c8abc94341d42f0b2be` | sound-154 | 92.8 | 0.803 | 우아하고 신비로운 왈츠풍 |
| 우아·왈츠 | ☐ | `93147bcf77494841b8d4478791ed9282` | sound-324 | 101.7 | 0.796 | 우아하고 평화로운 왈츠 |
| 신비·마법(신수의 숲) | ☐ | `d51e7664c4724ea1a66d8ad4b46f34cc` | sound-502 | 128.8 | 0.791 | 피치카토 현악·플루트, 마법 숲 탐험 |
| 신비·마법 | ☐ | `dbe429e5dc69406ab0c80c4b1e99766b` | sound-524 | 125.6 | 0.780 | 하프·목관, 몽환적 판타지 |
| 신비·마법 | ☐ | `25205ef769434c69ae032d6b264604c1` | sound-76 | 126.0 | 0.786 | 환상적, 모험의 시작·마법 공간 |
| 비장·성가(대비용 1곡) | ☐ | `c386a7d316bd46b6a27098e7dc37b8ea` | sound-454 | 89.5 | 0.708 | 웅장한 합창+현악, 신비·긴장 시네마틱 |
| 비장·성가 | ☐ | `7f12be7facb84f47b5a4bdbd79858d4a` | sound-266 | 113.7 | 0.682 | 신비 도입 → 비장하고 감동적 |
| 비장·성가 | ☐ | `7f73d3afe48a4d618dcda18f741731b5` | sound-646 | 150.8 | 0.804 | 웅장한 오케스트라, 설렘과 긴장 |

메모: 기준곡이 차분한 쪽이라 세 곡 모두 서정곡이면 전투 중 긴장감이 안 산다. 추천은 기준곡(14) + 서정→확장 1곡(333 또는 590) + 비장·성가 1곡(646 또는 454). 합창이 들어간 보스전 트랙(sound-648/649/231/439)은 교전 전환용 후보로만 남겨 둔다.


### 시그너스 — 긴박한 결 추가 후보 (2026-10-05)

의미 검색 5회(신비+긴박 리듬 / 성스러움+고조 합창 / 기사단 전투 현악·금관 / 서정 도입→전투 / 현악 트레몰로+합창). 일렉 기타·전자음·어둠/공포 계열은 뺐다.

| 결 | 채택 | RUID | 이름 | 길이 | 유사도 | 설명 |
|---|---|---|---|---:|---:|---|
| 신비 + 긴장 리듬(기준곡 색 유지) | ☐ | `eee2a1be2908456cb09fae3921b04e94` | sound-564 | 93.6 | 0.756 | 리드미컬한 현악·목관, 신비·긴장 |
| 신비 + 긴장 리듬 | ☐ | `b0ab2d0776484a1ba79998d4bdeaded1` | sound-393 | 124.0 | 0.752 | 현악·목관, 긴장감과 동화 같은 느낌 |
| 신비 + 긴장 리듬 | ☐ | `8a81d1865d1f4152b4cbf800efed62af` | sound-296 | 125.6 | 0.751 | 웅장 오케 + 긴장 퍼커션, 판타지 모험 |
| 신비 + 긴장 리듬 | ☐ | `d9884ccae86d44a1aa9a91a8b2fd84ca` | sound-513 | 154.5 | 0.756 | 웅장·긴장, 모험/전투의 서막 |
| 신비 도입 → 클라이맥스 | ☐ | `8fda117d789c4d4a8c123a3b5f8773a8` | sound-314 | 172.6 | 0.749 | 서사적, 신비 도입에서 강렬한 절정 |
| 신비 도입 → 클라이맥스 | ☐ | `52205023afeb4904821d764670f3c517` | sound-161 | 87.8 | 0.757 | 웅장·신비, 긴장감 있는 시네마틱 |
| 합창 + 긴박(성가 결) | ☐ | `bf12afd2632644b19e8f6075339907d9` | sound-439 | 128.5 | 0.697 | 웅장 오케 + 긴장 합창 |
| 합창 + 긴박 | ☐ | `c78591fac73847b5be4dfc0143cc1241` | sound-461 | 95.8 | 0.735 | 웅장 합창 + 오케, 긴장·박진 |
| 합창 + 긴박 | ☐ | `a3e1d64b93824ddd809a9b81a2ded673` | sound-363 | 102.4 | 0.689 | 합창 + 오케, 긴박·강렬 |
| 합창 + 긴박 | ☐ | `e81c438b3fec4bf68a932323a4876975` | sound-649 | 95.1 | 0.749 | 긴박한 합창, 드라마틱 |
| 기사단 전투(현악·금관) | ☐ | `8a7aabed91c14684b0ff2214838762e1` | sound-295 | 127.1 | 0.768 | 빠른 현악 + 웅장 금관 전투 |
| 기사단 전투 | ☐ | `fb897b414ed44f2cb3a54dbefeac77c4` | sound-587 | 91.6 | 0.765 | 긴박한 현악 리듬 + 금관 |
| 기사단 전투 | ☐ | `9bdbcb7de15c4c9e8493fb8e7ad9db40` | sound-347 | 144.6 | 0.723 | 긴박·웅장, 보스전/긴장 모험 |
| 기사단 전투 | ☐ | `7d681eceb71d44f88a36b32422180d8c` | sound-262 | 134.5 | 0.780 | 긴박·웅장 전투/보스전 |
| 기사단 전투 | ☐ | `4cb9a18f1ed540ada6f40e7cd1612a65` | sound-155 | 123.8 | 0.732 | 타악 + 금관, 전투 긴장감 |

추천 조합(긴박 포함): 기준곡 14(서정) → 296 또는 393(신비+긴장 리듬) → 439 또는 295(합창/기사단 전투). 세 곡이 "평화 → 경계 → 결전"으로 이어지고, 신비로운 색은 세 곡 모두에 남는다.

## 에델슈타인 메인 BGM 후보 (기준곡 유사도 검색, 2026-10-05)

기준곡: `bf1f1c64293943baa5ce66a2b6c8ce76` sound-440 (178.9초) — "미스테리하고 산업적인 분위기의 전자 음악, 연구소나 미래적인 공간". 유사곡 topK 25 + 의미 검색 3회(기계·산업·공장 / 어두운 산업·연구소·긴장 / 전자 록·반란군)에서 추림. 스프라이트·60초 미만 짧은 곡, 다른 진영 확정곡, 순수 오케스트라(모험가·시그너스와 겹치는 결), 국악·마을곡은 뺐다.

| 결 | 채택 | RUID | 이름 | 길이 | 유사도 | 설명 |
|---|---|---|---|---:|---:|---|
| 산업·기계(기준곡과 같은 결) | ☐ | `bfa8c3e2a33f4e8d871e03df2737c304` | sound-442 | 327.4 | 0.794 | 금속성 타악기 + 신시사이저, 기계적·긴장 (5분 27초, 가장 긴 곡) |
| 산업·기계 | ☐ | `732c8aeac0624d21bdcfc89bc6244105` | sound-237 | 144.1 | 0.758 | 어두운 금속성 타격음 + 낮은 신스, 보스전 도입부 |
| 신스·미스터리(기준곡과 같은 결) | ☐ | `8dc48bc172d947ea987c12412f91e34c` | sound-308 | 119.1 | 0.833 | 전자음 + 현악, 리드미컬, 묘한 긴장감 (유사도 1위) |
| 신스·미스터리 | ☐ | `af3acec8784a4f80a0a354479b2132ff` | sound-388 | 165.0 | 0.797 | 레트로 신스, 신비·긴장, 리듬감 |
| 신스·미스터리 | ☐ | `80a18b7f3e87412e8e8c487cdb8a065b` | sound-268 | 153.6 | 0.731 | 오케스트라 + 전자음, 기묘한 긴장과 호기심 |
| 도시·사이버펑크(세련된 비트) | ☐ | `f555b438ab2a41b0a714ccc6dbe720df` | sound-574 | 191.0 | 0.764 | 세련된 비트 + 신스, 도시적 긴장감 |
| 도시·사이버펑크 | ☐ | `f2677ea116ba4474bd80277b32545758` | sound-571 | 141.9 | 0.763 | 빠른 비트 신스, 사이버펑크 |
| 도시·사이버펑크 | ☐ | `2f6c3b7579d04d1297ff1f913a4788b9` | sound-103 | 112.5 | 0.779 | 세련된 비트 + 몽환 신스, 도시 |
| 도시·사이버펑크 | ☐ | `2de176cd6a9f496caf8c2bd06e961838` | sound-99 | 113.7 | 0.769 | 그루비 비트, 일렉트로닉, 도시/던전 탐험 |
| 긴박·전자 전투(대비용) | ☐ | `82a6606e1a074934be368b8e4a642b45` | sound-275 | 130.5 | 0.803 | 빠르고 강렬한 비트 + 신시사이저, 긴박 전투 |
| 긴박·전자 전투 | ☐ | `60a1438e4c4f4c7caea02100a86578a9` | sound-198 | 129.0 | 0.735 | 강렬한 신시사이저 + 빠른 비트 |
| 긴박·전자 전투 | ☐ | `78e27b35f81c431ca80ef11c14a74ffc` | sound-251 | 124.2 | 0.747 | 강렬한 비트 + 긴박한 신스 멜로디 |
| 긴박·전자 전투 | ☐ | `71e5aa17038648e6a9daac7c5b762b5b` | sound-230 | 143.0 | 0.734 | 레트로풍 신스, 빠르고 긴박 |
| 긴박·록(레지스탕스 반란군 결) | ☐ | `8aeeed0861e242a7b1e17867cd560bb8` | sound-298 | 130.1 | 0.812 | 일렉 기타 리프 + 비트, 매우 빠르고 파워풀 |
| 긴박·록 | ☐ | `4a48bbd4b74142a6a997d478e78ed870` | sound-150 | 207.0 | 0.686 | 오케스트라 서곡 → 일렉 기타 + 빠른 비트 |
| 긴박·록 | ☐ | `bb0761e13692453792ac00bb08a99dd3` | sound-424 | 140.0 | 0.700 | 일렉 기타 + 빠른 드럼, 에너지 |

메모: 기준곡 440이 "어둡고 느린 산업 전자" 쪽이라, 모험가·시그너스처럼 3곡 중 1곡은 긴박곡을 두는 게 좋다. 추천 조합 두 가지.
- A(산업 일관): 440 → 442(산업·기계) → 275(긴박·전자). 합 약 10.6분. 전 곡이 전자음이라 진영색이 가장 선명하다.
- B(록 대비): 440 → 308 또는 388(신스·미스터리) → 298(일렉 기타). 합 약 7.2~8분. 레지스탕스의 "반란군·기계" 두 얼굴이 다 드러난다.
미리듣기: `https://maplestoryworlds-resourcesearch-new.nexon.com/search?tab=audio&selected=<RUID>`

### 에델슈타인 — 긴박곡 1곡 추가 후보 (2026-10-05) — 보류: 3곡으로 확정

확정 3곡(440 산업 전자 / 388 레트로 신스 / 237 금속·낮은 신스)이 모두 "어둡고 느린 전자" 결이라, 네 번째는 같은 신스 색을 유지하면서 템포만 올린 곡으로 골랐다. 388·237의 유사곡(topK 20) + 의미 검색 2회에서 "긴박·빠른·강렬" 설명이 있는 60초 이상 곡만 남기고, 오케스트라·합창 보스전(모험가·시그너스와 겹침)과 8비트 칩튠(가벼움)은 뺐다.

| 순위 | 채택 | RUID | 이름 | 길이 | 유사도 | 설명 |
|---|---|---|---|---:|---:|---|
| 1 (추천) | ☐ | `304c754c743341549676338f92fdeb5d` | sound-104 | 178.0 | 0.842(↔388) | 강렬한 신스 베이스 + 긴장감 비트, 순수 전자. 확정 3곡과 색이 같고 길이도 비슷 |
| 2 | ☐ | `82a6606e1a074934be368b8e4a642b45` | sound-275 | 130.5 | 0.806 | 빠르고 강렬한 비트 + 신시사이저, 긴박 전투. 템포가 가장 빠름 |
| 3 | ☐ | `ac30e4669c3e445783a0ded36cfa52e2` | sound-383 | 146.0 | 0.751 | 긴박한 빠른 전자음 + 오케스트라 요소. 전자 색 유지하며 스케일 큼 |
| 4 | ☐ | `78e27b35f81c431ca80ef11c14a74ffc` | sound-251 | 124.2 | 0.817(↔388) | 강렬한 비트 + 긴박한 신스 멜로디 |
| 5 | ☐ | `60a1438e4c4f4c7caea02100a86578a9` | sound-198 | 129.0 | 0.749 | 강렬한 신시사이저 + 빠른 비트 |
| 록 대안 | ☐ | `8aeeed0861e242a7b1e17867cd560bb8` | sound-298 | 130.1 | 0.825 | 일렉 기타 리프, 매우 빠르고 파워풀. 전자 색에서 벗어나지만 "반란군" 느낌 |

추천 순환: 440(미스터리) → 388(리듬 신스) → **104(긴박)** → 237(어두운 금속) → 반복. 긴박곡이 중간에 들어가면 "잠입 → 가동 → 교전 → 여파"처럼 흐른다. 4곡 합 약 11분.
