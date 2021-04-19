---
title:  "[Blog 관리] 2. Jekyll - markdown + css (kramdown)"
excerpt: "kramdown 에 대한 이해"

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

이처럼 GitHub 블로그의 자유도가 높은 이유는 Jekyll에서 사용되는 Markdown 문법에는 css 클래스 지정 문법을 지원하기 때문이다. 일반적으로 Markdown 에서는 css가 사용되지 않는다. 하지만 Jekyll 덕분에, Markdown에서 css로 정의된 스타일을 사용할 수 있게 되었다. Jekyll 에 적용되는 Markdown은 [**kramdown**]("https://kramdown.gettalong.org/index.html")으로 불려진다. 기존의 Markdown 문법을 지원하면서 kramdown 만의 문법이 더해진 것이 특징이다.  

- [**Markdown 기본 문법**]("https://www.markdownguide.org/basic-syntax/")
- [**kramdown 기본 문법**]("https://kramdown.gettalong.org/syntax.html#kramdown-syntax")

## **kramdown syntax**
{: .text-center}  

jekyll 의 markdown 렌더링 엔진으로 kramdown이 사용된다고 했지만, jekyll 공식 사이트에서는 kramdown의 기능 중 2가지는 지원이 되지 않는다고 명시해두고 있다. ([ **링크** ]("https://jekyllrb.com/docs/configuration/markdown/")) CommonMark, Cusotm Markdown Proceessors 두 기능을 제외한 나머지 기능은 모두 지원이 된다.

그 중에서 눈 여겨 봐야할 것 같은 기능들을 아래에 정리한다.

- CSS Class 지정

kramdown에서 CSS 의 class를 지정하는 문법은 아래와 같다.  
```markdown
Left aligned text
{: .text-left}
```
블록의 맨 마지막에 { **:** `class_name` }과 같은 형태로 미리 지정된 클래스를 입력하면, css 에 정의된 대로 스타일이 변경된다. 이 기능을 통해, 글자 색 변경, 음영 넣기 등이 가능해진다.  

- Escape Character (\\)

> 문자열 처리와 관련된 프로그래밍을 많이 하던 사람들에게는 Escape 문자는 굉장히 익숙한 기능 중 하나이다. 기존 Markdown에서도 Escape 문자를 지원하지만 kramdown에서는 몇몇 문자에 대해 추가적인 Escape 기능을 지원한다.


