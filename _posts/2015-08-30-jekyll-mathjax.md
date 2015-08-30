---
layout: post
title: "Jekyll + MathJax"
date:   2015-08-30 23:47:00
categoreis:
tags:
---

### 설정

우선 MathJax 스크립트를 모든 페이지에서 쓸 수 있게 만든다. `_includes/head.html`에 다음을 추가한다.

```html
<script type="text/javascript"
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

```

markdown 프로세서도 충돌하지 않도록 설정해야 한다. redcarpet이라면 다음과 같은
설정은 괜찮다. superscript를 켜면 수식을 markdown 프로세서가 바꿔버리기 때문에
MathJax가 제대로 처리하지 못한다.

```
markdown: redcarpet
redcarpet:
  extensions: ["no_intra_emphasis", "fenced_code_blocks", "autolink", "strkethrough", "with_toc_data", "tables"]
```

### 사용

인라인 수식을 \\(a + b\\)처럼 쓰려면 다음과 같이 입력해야 한다.

```
\\(a + b\\)
```

디스플레이 수식은 다음과 같이 입력하거나 `$$`로 둘러싸서 입력해야 한다.

```
\\[
S = \sum_{i=1}^n (Y_i - (\beta_0 + \beta_1 X_i))^2
\\]
```
\\[
S = \sum_{i=1}^n (Y_i - (\beta_0 + \beta_1 X_i))^2
\\]

align 같은 수식 환경도 사용할 수 있다. 줄바꿈에서 `\\\\`라고 입력해야 한다.

```
\begin{align}
\frac{\partial S}{\partial \beta_0} &= -2 \sum_{i=1}^2 (Y_i - (\beta_0 + \beta_1 X_i)) = 0\\\\
\frac{\partial S}{\partial \beta_1} &= -2 \sum_{i=1}^2 X_i(Y_i - (\beta_0 + \beta_1 X_i)) = 0\\\\
\end{align}
```

\begin{align}
\frac{\partial S}{\partial \beta_0} &= -2 \sum_{i=1}^2 (Y_i - (\beta_0 + \beta_1 X_i)) = 0\\\\
\frac{\partial S}{\partial \beta_1} &= -2 \sum_{i=1}^2 X_i(Y_i - (\beta_0 + \beta_1 X_i)) = 0\\\\
\end{align}


