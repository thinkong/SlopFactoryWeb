# Korean style guide (ko-KR)

Owner: Translator. Applies to the Korean site at `/ko/`, every Korean devlog, and the Korean UI in every game. Terms come from the [glossary](ko-glossary.md); if this guide and the glossary disagree, fix one of them before shipping.

## 1. The one-line version

Write like a friendly, slightly tired factory worker who is proud of their cheap lunch: **해요체**, short sentences, dry jokes, and never stiff. Adapt, don't translate: if an English joke does not land in Korean, write a Korean joke that does the same job.

## 2. Register

| Where | Register | Example |
|---|---|---|
| Site copy (Home, About, game pages, cards, footer) | 해요체 | "작고, 이상하고, 무료인 브라우저 게임을 만들어요." |
| Devlogs | 해요체 | "봇이 먼저 플레이해 봤어요. 세 번 만에 망가졌어요." |
| Game instructions, hints, messages | 해요체 | "금색 호가 사라지기 전에 다시 도약하세요." |
| Buttons, tabs, HUD labels, headings | Noun or noun phrase, no verb ending | 플레이, 다시 하기, 설정, 근무 시작, 최고 기록 |
| Short shouts (results, events) | Noun + "!" | 신기록!, 우주 미아!, 소행성 충돌!, 통과! |
| Rule text in Line Inspector | Short rule style ending in 금지 / -해야 해요 | "초록 도색 금지.", "모자는 앞을 봐야 해요." |
| Legal / licence lines | 해요체, plain | "SIL Open Font License 1.1에 따라 사용해요." |

Rules:

- Do **not** use 합니다체 (-습니다) anywhere. It sounds like a bank notice and kills the jokes. The one exception is a quoted in-game character who should sound stiff on purpose (for example a robot announcer), and the glossary should note it.
- Do **not** use 반말 (-해, -야) in UI or site copy. Fine inside a quoted character line if the joke needs it.
- Do **not** address the player as 당신 or 여러분 in UI. Drop the subject; Korean does not need it. "You hopped the whole galaxy" → "은하 끝까지 건너뛰었어요."
- Commands to the player: use -세요 ("탭하세요", "다시 도약하세요"). For very short hints, "탭해서 시작" (no ending) is fine.
- Studio voice is "we": 저희 in polite sentences, but drop it when you can. Not 우리 in body copy, except fixed labels like the "우리 게임" heading.

## 3. Carrying the "slop" humour

The English site jokes by being honest about being cheap, small and machine-made, in a fond way. Keep that attitude; swap the references.

- **Keep the word 슬롭** as the studio's pet word. Korean tech readers know "AI 슬롭", so it carries the self-aware joke. Use it the way the English does: as something we are fond of, never as an insult to players.
- **Use Korean food and workplace references** instead of literal ones. They do the same job better:
  - cafeteria lunch → 급식 ("싸고, 따뜻하고, 의외로 든든한 급식 같은 게임")
  - overtime / endless shift → 야근
  - supervisor → 반장님
  - free-range → 방목 ("100% 방목 슬롭")
  - artisanal → 장인이 빚은 ("장인이 빚은 슬롭. 로봇이 손으로 젓고, 뜨끈하게 나가요.")
- **Footnote jokes stay footnote jokes.** "NEW DEVLOGS DAILY* / *NOT DAILY" → "개발 일지 매일 업데이트* / *매일은 아님". The punchline is the short, flat second line.
- **Deadpan beats exclamation.** One "!" per line at most. No ㅋㅋ, ㅎㅎ, emoji or 초성 in site copy, UI or devlogs.
- **Don't explain the joke.** If the Korean needs a footnote to be funny, rewrite it.
- **Puns that only work in English** (for example "No refunds (it's free)"): keep the logic, drop the wordplay. → "설치 없음. 계정 없음. 환불 없음(무료라서)."
- **Fake-corporate tone is part of the joke** ("certified", "spec sheet", "100%"). In Korean this is 인증, 제품 사양서, 품질 보증: use them deadpan. "CERTIFIED HUMAN-ADJACENT" → "사람 비스무리 인증 완료".
- The humour lives in site copy, devlog asides and game-over flavour lines. Instructions and settings must be plain and clear first.

Reference lines (use these as the tone benchmark):

| EN | KO |
|---|---|
| WE MAKE SLOP / YOU PLAY IT | 슬롭은 저희가 / 플레이는 여러분이 |
| Artisanal slop. Hand-churned by robots. Served hot. | 장인이 빚은 슬롭. 로봇이 손으로 젓고, 뜨끈하게 나가요. |
| This page fell into the slop vat. We are not going in after it. | 이 페이지는 슬롭 통에 빠졌어요. 건지러 들어가진 않을 거예요. |
| All slop reserved. … powered by vibes. | 모든 슬롭 보유. … 동력은 느낌적인 느낌. |
| No slop was harmed in the making of this website. | 이 웹사이트를 만드는 동안 다친 슬롭은 없어요. |
| Free. Slop is a human right. | 무료. 슬롭은 인권이니까요. |
| The supervisor would like a word. | 반장님이 잠깐 보재요. |

(Exception to "no 여러분 in UI": the hero headline is a slogan, not UI.)

## 4. Punctuation and typography

- **No ALL CAPS in Korean.** Hangul has no case, so English uppercase labels just become normal Korean. Get emphasis from the existing bold/colour styling, not from extra "!" marks.
- Full stop, comma, ?, ! are the ASCII ones, with no space before them. Short labels and buttons have no full stop.
- Quotes: “ ” and ‘ ’ in prose. Inside UI strings that are in code, straight quotes are fine.
- Ellipsis: "…" (one character), no space before.
- Middle dot " · " between UI items is kept as in the English (spaces on both sides).
- Tilde "~" for ranges only ("1~3번째 근무"), not as a cute ending.
- Spacing (띄어쓰기) follows standard rules, but keep fixed UI compounds together: 다시 하기, 다시 시작, 일시정지, 전체 화면, 효과음, 신기록.
- Brackets for glosses: "Orbit Hop(오빗 홉)", no space before the bracket.
- **Fonts:** Orbitron has no Hangul. Every Korean string needs a fallback Korean font (see §8). Do not draw Korean in the logo/title font; game titles stay in English for this reason.

## 5. Numbers, dates and units

| Thing | Format | Example |
|---|---|---|
| Numbers | Arabic digits, comma every 3 digits | 1,322 |
| Score / points | number + 점, no space | 577점, +25점 (HUD can drop 점: "+25") |
| Counting | number + counter, no space | 제품 86개, 3번째 시도, 경고 2, 5개 연속 |
| Combo / multiplier | × (U+00D7), no space | 콤보 ×5 |
| Seconds | 초, no space, one decimal like EN | 12.4초, 제품당 1.5초 |
| Percent | % | 40% |
| File size | KB / MB | 약 70KB |
| Long date (posts, game pages) | YYYY년 M월 D일 | 2026년 10월 14일 |
| Short date (cards, lists) | YYYY. M. D. | 2026. 10. 14. |
| Version | as in EN | v1.0.0 |
| Keys | Korean name for Space/Enter/arrows; letters stay Latin. In prose write 스페이스 키 (not 스페이스 바); short UI labels may use 스페이스 | 스페이스 키, 엔터, ← / A |

## 6. Strings with code placeholders (for engineers and translators)

- Translate the **whole sentence template**, not pieces. Korean word order differs: "`${toy}` approved, but it broke `${rule}`" must become one Korean template with both placeholders, for example "`${toy}` 통과 처리. 하지만 `${rule}` 위반이에요."
- **No particle right after a placeholder.** Rewrite so the placeholder ends a phrase, sits before a noun, or is followed by ":" ("점수: `${score}`", "규정 `${n}`번 위반").
- Counters go after numbers: "`${n}` IN A ROW!" → "`${n}`개 연속!", "SHIFT `${n}`" → "근무 `${n}`".
- No plural logic is needed in Korean; one string per message is enough.
- Share text (Line Inspector "COPY RESULT") is Korean but keeps the game name in English: "Line Inspector: 제품 86개 검수 / 점수 1,240".
- Flag to engineers: strings built by joining fragments (for example `${name} CLEAR`, `${d} ${m}`) need a single translatable template.

## 7. Length rules for a 360 px phone screen

Assume a 360 px wide screen with 16 px side margins, so **about 328 px of usable width**. A Hangul syllable is about 1 em wide (Latin capitals in Orbitron are about 0.7 em), so Korean is usually *narrower* than the English uppercase it replaces, but it does not wrap mid-word as nicely.

| Element | Typical size | Max Korean length (incl. spaces) | Target |
|---|---|---|---|
| Site nav item | 15–16 px | 4 | 게임, 블로그, 소개 |
| Primary button (game or site) | 18–20 px | 8 | 다시 하기, 근무 시작 |
| Small button / chip | 14 px | 6 | 결과 복사 |
| HUD label (score, shift, strike) | 12–14 px | 5 | 최고, 경고 2, 근무 3 |
| Big shout / result title | 28–34 px | 8 | 우주 미아!, 근무 끝 |
| Screen title (menu headings) | 22–26 px | 10 | 게임 방법, 설정 |
| One-line hint / subtitle | 15–16 px | 18 | 휴대폰을 세우면 더 크게 보여요 |
| Body text, how-to steps, rules | 15 px | Wraps: max 2 lines on a phone | |
| Ticker / marquee item | any | 16 | 100% 방목 슬롭 |
| Site card summary | 15 px | 60 (about 3 lines) | |

Rules:

- If a label is over the limit, shorten the Korean first (drop endings, use the noun form). Only ask engineers for more room when shortening would lose meaning.
- Never break a Korean line inside a word. On the web use `word-break: keep-all` for Korean text (flag for engineers).
- In canvas games, test Korean at the smallest scale the game uses. If a label overflows, list it in the localisation task with the string id and the Korean text so engineers can see it.
- Avoid line-final single syllables (one Hangul syllable alone on the last line); reword instead.

## 8. Things to flag to engineers (not translator decisions)

1. **Fonts:** Orbitron and the canvas fallbacks ("Trebuchet MS", "Segoe UI") have no Hangul. Korean needs an explicit fallback, for example `"Pretendard", "Apple SD Gothic Neo", "Malgun Gothic", "Noto Sans KR", sans-serif`. Check heavy weights (the games use 900) render with a real bold, not a faked one.
2. **`lang` attribute:** Korean pages need `<html lang="ko">` so screen readers and line breaking work.
3. **`word-break: keep-all`** on Korean text blocks.
4. **Templates:** some game strings are built by joining fragments (see §6). Those need single templates before they can be translated well.
5. **Dates:** the site formats dates with the English pattern "Jan 2, 2006"; Korean pages need "2006년 1월 2일".

## 9. Workflow

- New term → add to the glossary first, then use it.
- Every Korean devlog is adapted from the English post at the same time or soon after; titles are adapted too, but game names stay English.
- Screenshots and alt text: translate alt text; in-game text in screenshots stays as shot.
- Before shipping, read the Korean aloud once. If it sounds like a manual, rewrite it.
