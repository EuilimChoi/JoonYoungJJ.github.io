---
title:  "[Blog 관리] 2. Jekyll - markdown + css (kramdown)"
excerpt: "kramdown과 관련된 라이브러리에 대한 이해"

# categories:
#   - Blog
# tags:
#   - [Blog, jekyll, Github, Git]

toc: true
toc_sticky: true
toc_icon : fas fa-file-code
 
date: 2021-04-19
last_modified_at: 2021-04-19
---

GitHub 블로그가 다른 블로그에 비해서 자유도가 상당히 높은 편이다. 테마도 꽤 다양하고, 능력만 된다면 특정 테마를 시작으로 해서 자신이 원하는 대로 꾸미고 운영하는 것이 가능하다. 이런 점에서 GitHub 블로그는 블로그라는 명칭보다 웹사이트가 가깝다고 할 수 있을 듯하다.  

이처럼 GitHub 블로그의 자유도가 높은 이유는 Jekyll에서 사용되는 Markdown 문법에는 css 클래스 지정 문법을 지원하기 때문이다. 일반적으로 Markdown 에서는 css가 사용되지 않는다. 하지만 Jekyll 덕분에, Markdown에서 css로 정의된 스타일을 사용할 수 있게 되었다. Jekyll 에 적용되는 Markdown 렌더링 엔진은 [**kramdown**](https://kramdown.gettalong.org/index.html)으로 불려진다. 기존의 Markdown 문법에 몇 가지 유용한 기능들을 추가적으로 지원하는 것이 특징이다. 아래는 추가적인 설명을 위한 링크이다.  

- [**Markdown 기본 문법**](https://www.markdownguide.org/basic-syntax/)
- [**kramdown 기본 문법**](https://kramdown.gettalong.org/syntax.html#kramdown-syntax)  
- [**HTML 렌더링 엔진**](https://velog.io/@codenmh0822/%EB%A0%8C%EB%8D%94%EB%A7%81Rendering)

-------
-------

## **kramdown syntax**
{: .text-center}  

jekyll 의 markdown 렌더링 엔진 `(markdown ⇒ html)` 으로 kramdown이 사용되고 있지만, jekyll 공식 사이트에서는 kramdown의 기능 중 2가지는 제외된다고 명시해두고 있다. ([ **링크** ](https://jekyllrb.com/docs/configuration/markdown/)) CommonMark, Cusotm Markdown Proceessors 두 기능이 제외되는데, 나머지 기능은 모두 지원이 된다.  

Kramdown은 Markdown 뿐만 아니라, HTML도 지원을 하므로, 홈페이지 작성시에 Markdown, HTML을 병행하여 사용할 수 있다.

그 중에서 눈 여겨 봐야할 것 같은 기능들을 아래에 정리한다.

-------
- **Markdown Element에 CSS Class 지정**  
kramdown에서 CSS 의 class를 지정하는 문법은 아래와 같다. 아래 코드블록은 텍스트를 왼쪽으로 정렬하는 방법을 보여준다.  

    ```markdown
    Left aligned text
    {: .text-left}
    ```

    블록의 맨 마지막에 { **:** `class_name` }과 같은 형태로 미리 지정된 클래스를 입력하면, css 에 정의된 대로 스타일이 변경된다. 이 기능을 통해, 글자 색 변경, 음영 넣기 등이 가능해진다.  

    [Minimal-Mistakes 기본 제공 Class](https://mmistakes.github.io/minimal-mistakes/docs/utility-classes/)

-------
- **Escape Character - \\ or ￦**  
문자열 처리와 관련된 프로그래밍을 많이 하던 사람들에게는 Escape 문자는 굉장히 익숙한 기능 중 하나이다. 기존 Markdown에서도 Escape 문자를 지원하지만 kramdown에서는 몇몇 문자에 대해 추가적인 Escape 기능을 지원한다.

-------
- **Math Block** - [**MathJax**](http://docs.mathjax.org/en/latest/)  
Jekyll은 MathJax를 지원한다. MathJax는 브라우저에서 LaTeX를 사용할 수 있도록 해준다. MathJax는 오픈소스로 JavaScript를 기반으로 만들어진 렌더링 엔진이다. [**LaTeX**](https://www.latex-project.org/)는 기술/과학 문서의 제작을 위한 기능들을 포함하고 있는 시스템으로 흔히 논문 작성 등 전문적인 문서 작성에 사용되고 있다.  

    Latex를 사용하면 아래와 같이 수식을 GitHub 블로그에 넣는 것이 가능해진다.

    $$
    \begin{aligned}
    & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
    = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
    & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
        \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
        \vdots & \ddots & \vdots \\
        \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
        \end{array} \right)
    \left( \begin{array}{c}
        y_1 \\
        \vdots \\
        y_n
        \end{array} \right)
    \end{aligned}
    $$

    ```
    $$
    \begin{aligned}
    & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
    = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
    & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
        \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
        \vdots & \ddots & \vdots \\
        \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
        \end{array} \right)
    \left( \begin{array}{c}
        y_1 \\
        \vdots \\
        y_n
        \end{array} \right)
    \end{aligned}
    $$
    ```

-------
- HTML 블록 삽입  
위에서도 언급했지만, Markdown 중간중간에 HTML 태그를 넣는 것은 아무런 문제가 되지 않는다. kramdown이 HTML도 지원을 하기 때문이다. 예를 들면, 아래와 같다.

    ```
    This is a para.
    Something in here.
    Other para.  
    ```

    ```Markdown
    This is a para.
    <div>
    Something in here.
    </div>
    Other para.
    ```

-------
-------
## **Cusotm Class 만들기**
{: .text-center} 

이 부분이 GitHub 블로그를 예쁘게 꾸미고, 포스트를 눈에 띄게 잘 작성하는 중요한 포인트이다.


*[포인트]: It's called Markdown