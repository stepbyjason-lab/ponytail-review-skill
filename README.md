# ponytail-review (skill)

과설계만 잡는 코드리뷰 렌즈. diff를 읽고 **뭘 지울 수 있는지**만 한 줄씩 낸다.

- 태그 5종: `delete:` · `stdlib:` · `native:` · `yagni:` · `shrink:`
- 형식: `L<line>: <tag> <what>. <replacement>.`
- 끝에 `net: -<N> lines possible.` — 자를 게 없으면 `Lean already. Ship.`
- **읽기 전용** — 지적만 하고 고치지 않는다
- 정확성·보안·성능은 명시적으로 범위 밖이다. 그건 일반 리뷰 패스로 보낸다

## 설치 (서브모듈)

```bash
cd ~/.claude
git submodule add https://github.com/stepbyjason-lab/ponytail-review-skill.git skills/ponytail-review
```

## 출처

[DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail)의 `skills/ponytail-review`만
가져온 최소 포크다. 무엇을 왜 가져왔고 어떻게 재동기화하는지는 [`_SOURCE.md`](_SOURCE.md) 참조.

MIT © 2026 DietrichGebert
