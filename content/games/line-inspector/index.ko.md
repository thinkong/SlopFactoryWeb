---
title: "Line Inspector"
slug: "line-inspector"
date: 2026-10-14T06:30:00Z
summary: "장난감 공장 라인 끝에서 일하는 검수원이 되어 보세요. 근무마다 바뀌는 규정집에 맞춰 장난감을 통과시키거나 불량 처리하세요. 3번 틀리면 라인에서 빠져요."
cover: "line-inspector-devlog06-title-best-tablet.png"
version: "1.1.0"
status: "출시 완료"
platforms: ["PC 브라우저", "휴대폰 브라우저", "태블릿 브라우저"]
controls: "오른쪽으로 스와이프하거나 → 또는 D 키로 통과. 왼쪽으로 스와이프하거나 ← 또는 A 키로 불량. 버튼을 눌러도 돼요."
play: "play/"
---

태엽 로봇, 통통 동물, 포켓 로켓이 라인을 따라 하나씩 굴러 와요. 장난감마다 할 일은 한 가지, **통과**시킬지 **불량** 처리할지 정하는 거예요. 무엇이 불량인지는 **검수 규정집**에 적혀 있고, 규정집은 근무마다 바뀌어요. 5분 전까지 멀쩡했던 장난감이 지금은 불량일 수도 있어요.

근무가 바뀔 때마다 규정이 늘거나 바뀌고, 장난감 하나당 주어지는 시간은 조금씩 줄어요. 잘못 판정하거나 놓치면 경고 1회이고, 놓친 규정에 불이 들어와서 이유를 알 수 있어요. 경고 3번이면 끝이에요. 게임 오버 카드에는 경고를 받은 장난감과 어긴 규정이 모두 나와요.

![태블릿의 Line Inspector 타이틀 화면: 노란 LINE 간판 아래 INSPECTOR 도장, 컨베이어 벨트 위의 초록 물방울무늬 동물과 눈이 세 개인 빨간 로봇, 최고 점수 1640, START SHIFT, HOW TO PLAY, CREDITS 버튼](line-inspector-devlog06-title-best-tablet.png)

## 구성품

- 규정이 계속 바뀌는 근무 9번, 그 뒤로 버티는 만큼 이어지는 무한 야근
- 불량 장난감은 규정을 딱 하나만 어겨요. 그래서 경고를 받을 때마다 뭘 놓쳤는지 알 수 있어요
- 연속 기록, 저장되는 최고 기록, 친구에게 공유할 수 있는 한 줄 결과
- 색약 친화 도색 무늬, 그리고 소리, 음악, 화면 흔들림, 진동 설정
- 그래픽, 음악, 효과음을 전부 코드로 만들었어요. 게임 전체가 약 86KB예요
- PC, 휴대폰, 태블릿 브라우저에서 플레이할 수 있어요. 휴대폰을 세워서 하는 게 제일 좋아요

![휴대폰의 SHIFT OVER 카드: 경고 3번과 각 장난감 그림, 검수한 제품 47개, NEW BEST! 도장이 찍힌 점수 2000, 최고 연속 36, 공유 문구, 큼직한 TRY AGAIN 버튼](line-inspector-devlog05-game-over-phone.png)

## 크레딧

제작: Slop Factory. 모든 그래픽, 음악, 효과음은 직접 만든 것이며 실행 중에 코드로 생성돼요. 제목 서체는 Matt McInerney / The League of Moveable Type의 [Orbitron](https://github.com/theleagueof/orbitron)이고, SIL Open Font License 1.1에 따라 사용해요.
