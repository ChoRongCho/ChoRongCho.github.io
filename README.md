# Changmin Planning Notes

AI Planning과 Robotics를 공부하며 정리한 개인 홈페이지입니다. 연구 소개, 프로젝트, 논문 목록과 함께 Classical AI Planning, domain-independent planner, Task and Motion Planning(TAMP), uncertainty에 관한 학습 노트를 제공합니다.

- Website: [ChoRongCho.github.io](https://chorongcho.github.io/)
- Author: Changmin Park
- Affiliation: AIROBOTICS Lab, Sogang University
- Research interests: AI Planning, Robotics, TAMP, long-horizon robotic tasks

## Study 구성

| Chapter | 주제 | 현재 구성 |
| --- | --- | --- |
| 1 | Introduction to AI | Agent, Propositional Logic, First-Order Logic |
| 2 | Classical AI Planning | Overview, Problem Formalisms, PDDL, Causal Graph, Domain Transition Graph |
| 3 | Domain-Independent Planner | Planner Overview, FF, Fast Downward, OPTIC |
| 4 | Task and Motion Planning | Overview 및 관련 논문 정리 |
| 5 | Uncertainty | Overview 및 관련 논문 정리 |

전체 목차는 [`study/index.html`](study/index.html)에서 확인할 수 있습니다.

## Classical AI Planning

이 프로젝트에서 우선적으로 정리하는 영역입니다. 유한하고 완전 관측 가능하며 결정론적인 환경에서, 초기 상태로부터 목표 상태에 도달하는 액션 시퀀스를 찾는 문제를 다룹니다.

### 학습 흐름

1. **Planning Overview** — Planning의 필요성, PlanEx와 PlanOpt, domain-independent planning
2. **Problem Formalisms** — Transition System, STRIPS, FDR(Finite Domain Representation)
3. **PDDL** — Domain/Problem 파일, predicate, action, precondition, effect
4. **Causal Graph** — FDR 변수 사이의 의존성과 문제 구조 분석
5. **Domain Transition Graph** — 개별 변수의 값과 가능한 전이 분석

### 페이지별 현황

| 페이지 | 상태 | 보완할 내용 |
| --- | --- | --- |
| [`2-0. Planning Overview`](study/2-classical-ai/2-0-overview.html) | 초안 작성 | 오탈자 교정, 고전적 계획의 가정과 PlanEx/PlanOpt 설명 보강 |
| [`2-1. Problem Formalisms`](study/2-classical-ai/2-1-problem-formulation.html) | 작성 중 | FDR complete assignment 예시와 상태 전이 정의 완성, 기호 통일 |
| [`2-2. PDDL`](study/2-classical-ai/2-2-pddl.html) | 초안 작성 | PDDL 버전별 기능 검증, requirements와 실행 가능한 예제 추가 |
| [`2-3. Causal Graph`](study/2-classical-ai/2-3-causal-graph.html) | 작성 중 | 수학적 edge 정의, arc 유형, 구체적인 FDR 예시와 그래프 추가 |
| [`2-4. Domain Transition Graph`](study/2-classical-ai/2-4-domain-transition-graph.html) | 골격 작성 | 정식 정의, transition label, 예시 그래프, 활용 방법 추가 |

### Classical AI 우선 작업 목록

- [ ] 모든 장에서 planning task 표기를 `\(\Pi\)`, transition system 표기를 `\(\Theta\)`로 통일하기
- [ ] STRIPS와 FDR의 cost, initial state, goal 정의에서 잘못 사용된 기호 수정하기
- [ ] FDR의 complete variable assignment 예시와 상태 전이식을 완성하기
- [ ] 하나의 공통 예제(예: Logistics 또는 Blocks World)를 다섯 페이지에 걸쳐 일관되게 사용하기
- [ ] Causal Graph의 두 edge 조건(precondition–effect, effect–effect)을 수식으로 정의하기
- [ ] Causal Graph 예제 그림과 해석 추가하기
- [ ] Domain Transition Graph의 node, edge, condition label을 정의하기
- [ ] 같은 planning task로 Causal Graph와 Domain Transition Graph의 차이를 비교하기
- [ ] 각 장에 참고 문헌과 출처 추가하기
- [ ] 이전/다음 페이지 링크의 순서와 대상을 점검하기

## 프로젝트 구조

```text
.
├── _config.yml              # Jekyll 설정
├── _layouts/default.html    # 공통 HTML 레이아웃과 MathJax 설정
├── _includes/sidebar.html   # 페이지별 사이드바 내비게이션
├── assets/css/site.css      # 사이트 스타일
├── index.html               # 홈
├── about.html               # 소개
├── publication.html         # 논문 목록
├── projects/                # 프로젝트 페이지
└── study/                   # AI Planning 학습 노트
    ├── 1-introduction-to-ai/
    ├── 2-classical-ai/
    ├── 3-planner/
    ├── 4-tamp/
    └── 5-uncertainty/
```

## 로컬 실행

이 사이트는 GitHub Pages에서 제공하는 Jekyll 구조를 사용합니다. Ruby와 Bundler가 설치되어 있다면 다음 명령으로 로컬 서버를 실행할 수 있습니다.

```bash
bundle exec jekyll serve
```

현재 저장소에 `Gemfile`이 없다면 먼저 GitHub Pages용 개발 환경을 준비하거나 Jekyll을 설치해야 합니다. 서버 실행 후 `http://localhost:4000`에서 페이지를 확인합니다.

## Study 페이지 작성 규칙

각 학습 페이지는 YAML front matter와 공통 레이아웃을 사용합니다.

```html
---
layout: default
title: "2-x. Topic"
---

<div class="breadcrumb">...</div>
<h1>2-x. Topic</h1>
<p class="meta">마지막 업데이트: YYYY-MM-DD</p>
```

- URL과 파일명은 기존 번호 체계(`2-0`, `2-1`, ...)를 따릅니다.
- 수식은 MathJax의 `\(...\)` 또는 `\[...\]` 문법을 사용합니다.
- 새 페이지를 만들면 해당 chapter의 `index.html`, `study/index.html`, `_includes/sidebar.html`을 함께 갱신합니다.
- 본문 끝에는 이전/다음 페이지 링크를 추가합니다.
- 정의, 예시, 해석, 참고 자료의 순서로 작성해 개념과 활용을 함께 설명합니다.

## 배포

`main` 브랜치에 반영된 정적 페이지는 GitHub Pages를 통해 배포됩니다. 배포 전에는 내부 링크, 수식 렌더링, 모바일 레이아웃을 확인합니다.
