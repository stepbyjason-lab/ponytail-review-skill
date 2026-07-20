# _SOURCE — 이 스킬의 출처와 재동기화

## 업스트림

- 레포: <https://github.com/DietrichGebert/ponytail>
- 가져온 파일: `skills/ponytail-review/SKILL.md`
- 기준 커밋: `16f29800fd2681bdf24f3eb4ccffe38be3baec6b` (2026-07-15)
- 라이선스: MIT (© 2026 DietrichGebert) — `LICENSE` 원본 그대로 유지

## 왜 서브트리가 아니라 최소 포크인가

업스트림 레포는 루트에 `SKILL.md`가 없고 `skills/ponytail-review/SKILL.md`로 두 단계 안쪽에 있다.
`~/.claude`(dotclaude)의 서브모듈 관례는 **`skills/<이름>` → 그 레포 루트에 `SKILL.md`**라,
업스트림을 그대로 서브모듈하면 경로 깊이가 어긋나 스킬로 인식되지 않는다.
그래서 해당 파일만 루트에 두는 최소 포크로 만들었다.

## 왜 이 스킬만 가져왔나

업스트림은 6개 스킬(`ponytail`·`-review`·`-audit`·`-debt`·`-gain`·`-help`)과
Node.js 라이프사이클 훅을 함께 배포한다. 그중 `ponytail-review`만 가져온 이유:

- **필요한 건 diff 단위 과설계 렌즈 하나**다. 나머지는 지금 쓸 자리가 없다
  (ponytail 자신의 rung 1 "정말 필요한가?"를 채택 결정에 적용한 결과).
- **훅은 의도적으로 제외**했다. 훅을 설치하면 모든 세션에 "lazy senior dev" 모드가
  상시 주입되는데, 이는 렌즈 하나 추가가 아니라 전 세션 행동 변경이라 별개 결정이다.
  (훅 코드 자체는 검토 결과 안전하다 — `fs`·`path`·`os`만 쓰고
  `child_process`·네트워크·`exec` 호출이 없으며, 설정/상태 파일 읽기·쓰기만 한다.)

## 이 스킬을 쓰는 이유 (madi 맥락)

madi §2의 리뷰 패널 렌즈는 전부 **"빠진 것 없나"**를 본다
(`devils-advocate`·`architect`·`product-identity`·`safety-continuity`·`implementation-readiness`).
**"너무 많이 들어있지 않나"를 보는 역할이 없다.** 이 스킬이 그 자리를 채운다.

채택 결정적 요인 — **읽기 전용**이다("Does not apply the fixes, only lists them").
설치된 `review` 스킬은 fix-first라 §2의 역할 분리(Reviewer=read-only finding만)를 깨는데,
이 스킬은 그렇지 않아 게이트 렌즈로 바로 쓸 수 있다.

## 재동기화 방법

```bash
git clone --depth 1 https://github.com/DietrichGebert/ponytail.git /tmp/pt
diff /tmp/pt/skills/ponytail-review/SKILL.md ./SKILL.md
```

차이가 있으면 검토 후 반영하고, 이 파일의 「기준 커밋」을 갱신한다.

## 로컬 수정 이력

없음 — 현재 `SKILL.md`는 업스트림 원본과 동일하다.
madi용으로 손을 대면 여기에 무엇을 왜 바꿨는지 적는다.
