---
title:  "Github Blog 1 - Jekyll Front Matter"
excerpt: "블로그 관리를 위한 Jekyll 문법"

categories:
  - Blog
tags:
  - Blog Management
  - Front Matter

toc: true
toc_sticky: true
 
date: 2021-04-19
last_modified_at: 2021-04-19
---

_아래 작성되는 애드인은 이 블로그의 테마이자 가장 흔히 쓰이고 있는 Jekyll 테마인 Miminal Mistakes를 기준으로 작성되었습니다. 다른 GH Blog 테마에서는 검증되지 않았습니다._
{: .notice--primary}  

GitHub 블로그를 운영하기 위해서는 Markdown에 대한 이해도 중요하지만 Jekyll 에서 제공하는 키워드도 정확히 알고 있어야 한다. 아래는 향후 블로그 관리에 필요한 키워드들만 뽑아내어 정리하고 있다. 자세한 내용은 [**Minimal Mistakes**](https://mmistakes.github.io/minimal-mistakes/) / [**Jekyll**](https://jekyllrb.com/) 사이트에 접속하게 되면 볼 수 있다.  

GitHub 블로그는 Jekyll 이라는 Static Site Generator를 사용하고 있는데, markdown 문법을 사용하여 간단하게 웹사이트를 구축할 수 있도록 해주고 있다. 이 내용과 관련하여 간단하게 설명된 블로그 글이 있어 링크를 남긴다. ( [**GitHub Pages 블로그 소개 - SW developer**](https://devinlife.com/howto%20github%20pages/github-blog-intro/) )

위 블로그의 글에 덧붙여 설명하자면, Jekyll은 GitHub 공동창시자인 Tom Preston-Werner에 의해 Ruby 로 작성되었으며, 따라서 Jekyll 사용을 위해서는 Ruby 설치가 필수적이다. 각 GitHub 테마에는 기본적으로 설치가 되어야 하는 내용이 \*.gemspec 에 기재되어 있으며, 추가적으로 플러그인 설치가 필요한 경우에는 Gemfile 에 문법에 맞추어서 필요한 Ruby 라이브러리 (\*.gem)를 기재한 후, Ruby Command Propmpt 창을 통해 설치를 진행하면 된다.  

그리고, Static Site가 있다면 Dynamic Site가 있다. 그 둘의 차이와 각각을 이해해야 Static Site만의 장점이 무엇인지 더욱 정확하게 알 수 있을 것 같다. 아래 글이 영어로 적혀있기는 하지만, 간단하고 명쾌하게 Static Site와 Dynamic Site의 차이 및 각각의 정의를 풀어내었다.  

[**Static vs Dynamic Website: What Is the Difference?**](https://wpamelia.com/static-vs-dynamic-website/#:~:text=Static%20websites%20are%20ones%20that,databases%20in%20addition%20to%20HTML.)
{: .text-center}  

한마디로 말하면, Static 이란 상호작용 없이 일방적으로 내용만 보내주는 형태로 실시간으로 변동이 필요없는 페이지에 주로 사용된다. 좋은 예시로는 어느 회사의 회사소개 페이지, 뉴스 등이 있다. Dynamic 이란 상호작용이 필요하거나 실시간으로 데이터의 변경이 잦은 곳에 주로 사용된다. 예를 들어, 어느 영화관의 잔여 좌석 정보라든지, 온라인 쇼핑몰 등이 있다. Site Generator 라는 것은 HTML을 자동으로 생성해주는 것으로써, Markdown이 아니어도 여러가지 형태의 다른 방법으로 작성된 코드를 HTML로 빌드해서 방문자들에게 그 내용을 보여줄 수 있도록 하는 SW이다. 

{% include figure image_path="https://devopedia.org/images/article/78/1631.1525880749.png" alt="Static Site Generator" caption="Static Site Generator by. DEVOPEDIA" %}  

---

## **Front Matter (전문)**
{: .text-center}  

전문은 포스트의 레이아웃, 제목, 짧은 설명 등 포스트 설정과 관련된 부분이다. 여기에 적은 제목과 설명문 등이 모두 블로그에 그대로 드러나게 되므로 신경써서 작성이 필요하다. 제목과 짧은 설명은 [**GitHub 블로그 첫글쓰기 - SW developer**](https://devinlife.com/howto%20github%20pages/github-blog-intro/) 를 참고하면, 블로그에 포스트가 어떠한 형식으로 게시가 되는 것인지 확인할 수 있다.  

[MathJax](https://joonyoungjj.github.io/blogmanage-2-kramdown/) 는 다음 글을 참고하면 확인할 수 있다.

```markdown
---
layout : post
title : blog post title
excerpt : definition
published : true    # true (default) : show up post when git pushed  
                    # false : don't show up post when git pushed  

# toc (table of contents)
toc : true          # true : show toc 
                    # false (default) : don't show toc  
toc_sticky : true   # true : Stick table of contents to top of screen  
                    # false (default) : stationary  
toc_label : name    # optional. When toc_label is not defined here, 
                    # toc_label text in _config.yml shows up.
toc_icon : name  # optional. Font Awesome icon can be used.

# date
date : 2021-04-19   # yyyy-HH-dd hh:mm:ss +/-TTTT 
                    # (year, month, day is mendatory)

last_modified_at : 2021-04-19   # yyyy-HH-dd hh:mm:ss +/-TTTT 
                                # (year, month, day is mendatory)

# MathJax
use_math: true      # true  : use MathJax
                    # false (default) : don't use MathJax
---

↓ Contents ...
```