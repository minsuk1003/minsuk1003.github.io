---
layout: post
title: 'Hydejack에서 수식 렌더링 문제 해결하기'
date: 2024-05-28T00:00:00.000Z
categories: 
  - debugging
description: >
  Hydejack, MathJax, 수식 렌더링

---
부푼 기대감을 안고 Github 블로그를 운영하기 시작했으나.. 선택한 Hydejack 테마에서 수식 렌더링 문제가 발생했다 ㅠㅠ

이 문제를 해결한 과정을 기록한 블로그도 없어서 문제 해결이 매우 쉽지 않았다..

기술 블로그에서 수식을 포기하는 건 있을 수 없고, 다른 테마로 교체할 까도 수만번 고민했으나.. 

결국 2주일 만에 수식 렌더링 문제를 해결하였다!

Hydejack에서 수식 렌더링 문제가 발생하고 있는 분들이 이 포스팅으로 문제를 쉽게 해결하셨으면 한다.

---
### 목차
- [Hydejack의 수식 렌더링 방식](#hydejack의-수식-렌더링-방식)
- [MathJax](#mathjax)
- [마지막 단계](#마지막-단계)
- [참조](#참조)

---
## Hydejack의 수식 렌더링 방식

먼저, Hydejack에는 2가지의 렌더링 방식이 존재한다.

- katex : 가볍지만, 적은 기능
- MathJax : 무겁지만, 많은 기능

Hydejack은 기본적으로 katex에 맞춰져 있지만, 현 시점에서 업데이트가 제대로 되어 있지 않아 수식 렌더링이 제대로 되지 못하는 문제가 발생하고 있다.

[Hydejack의 공식 홈페이지](https://hydejack.com/docs/config/#enabling-math-blocks)에 katex를 사용하는 방법을 다음과 같이 자세하게 알려주고 있지만..

```yml
## _config.yml
kramdown:
  math_engine:         katex
  math_engine_opts:    {}
```

```python
## Gemfile
gem "kramdown-math-katex"
```

> 뭔 짓을 해도 안된다..

결국 katex를 포기하고, MathJax를 사용하여 겨우 문제를 해결할 수 있었다.

---
## MathJax

물론, MathJax를 사용해도 문제가 바로 해결되지는 않았다. config 파일 내 math_engine에 MathJax를 넣어도 렌더링이 되지 않았다..

결국, GPT의 힘을 빌려 다음의 자바스크립트 코드를 post.html에 삽입했다.

```html
<!-- _includes > post.html -->
<script type="text/javascript">
  if (typeof MathJax === "undefined") {
    window.MathJax = {
      tex2jax: {
        inlineMath: [['$', '$'], ['\\(', '\\)']],
        displayMath: [['$$', '$$'], ['\\[', '\\]']],
        processEscapes: true,
        processEnvironments: true
      },
      "HTML-CSS": { availableFonts: ["TeX"] }
    };

    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src = "https://cdn.jsdelivr.net/npm/mathjax@2.7.7/MathJax.js?config=TeX-MML-AM_CHTML";
    script.onload = function() {
      MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
    };
    document.getElementsByTagName("head")[0].appendChild(script);
  } else {
    MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
  }
</script>
```

> 드디어 수식 렌더링이 적용되었다!

그런데.. 여기서 수식이 중복되는 문제가 발생하였다. 웃긴 건 새로고침을 할 때마다 중복이 될 때도 있고 안될 때도 있었다..😂 

HTML 코드를 살펴본 결과, katex와 MathJax가 모두 적용된 문제로 수식이 중복되는 것으로 확인되었다.

본인은 katex와 관련된 모든 파일을 하나하나 뜯어 모두 주석 처리하였다.

여기서 파일들을 모두 언급하기는 어렵지만.. 본인은 katex가 적용되지 않도록 VS Code에서 katex를 검색해 관련된 코드를 모두 주석 처리해 주었다.

이 작업은 안정적인 블로그 관리를 위해 직접 로컬에서 테스트하면서 실행하길 권한다.

---
## 마지막 단계

이와 같은 수작업 끝에 앞선 중복 문제는 해결되었다..

그러나, 페이지에 처음 접속하면 수식 렌더링이 되지 않았고, 이상하게도 새로고침 후 수식이 제대로 표현되었다.

앞서 GPT가 주었던 MathJax를 렌더링하는 코드를 post.html에 삽입했다.

본인은 블로그 내의 모든 페이지에서 수식 렌더링이 적용될 수 있도록 MathJax 자바스크립트 코드를 head.html에도 삽입하였다.

![image](https://github.com/minsuk1003/minsuk1003.github.io/assets/63490319/8ea94f3c-cf38-41a0-8d98-2de9ec208f09)

> 마침내 수식 렌더링 문제를 해결하는 데 성공했다.

---
## 참조

[02-Hydejack에서 TeXt로 넘어오기까지](https://junhyoung-chung.github.io/2023/01/27/githubpages-02.html)
- Hydejack에서 수식 렌더링 문제를 다룬 거의 유일한 블로그이다. 위 블로거는 결국 다른 테마를 선택했지만, 문제를 해결하는 데 큰 도움을 주어 감사함을 표한다.

