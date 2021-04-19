---
title:  "[Blog 관리] 1. Jekyll Front Matter"
excerpt: "블로그 관리를 위한 Jekyll 문법"

# categories:
#   - Blog
# tags:
#   - [Blog, jekyll, Github, Git]

# toc: true
# toc_sticky: true
# toc_icon : fas fa-heading
 
date: 2021-04-19
last_modified_at: 2021-04-19
---

_아래 작성되는 애드인은 이 블로그의 테마이자 가장 흔히 쓰이고 있는 Jekyll 테마인 Miminal Mistakes를 기준으로 작성되었습니다. 다른 GH Blog 테마에서는 검증되지 않았습니다._
{: .notice--primary}  

GitHub 블로그를 운영하기 위해서는 Markdown에 대한 이해도 중요하지만 Jekyll 에서 제공하는 키워드도 정확히 알고 있어야 한다. 아래는 향후 블로그 관리에 필요한 키워드들만 뽑아내어 정리하고 있다. 자세한 내용은 [**Minimal Mistakes**](https://mmistakes.github.io/minimal-mistakes/) / [**Jekyll**](https://jekyllrb.com/) 사이트에 접속하게 되면 볼 수 있다.

> 아무래도 이쯤에서 GitHub 블로그가 자신의 감성과 맞지 않는다고 느껴진다면 다른 블로그를 알아보는 게 좋을 것 같다는 생각이 들었다. 다행히도 나는 GitHub 방식이 덜 지루하고 흥미롭다.

GitHub 블로그는 Jekyll 이라는 Static Site Generator를 사용하고 있는데, markdown 문법을 사용하여 간단하게 웹사이트를 구축할 수 있도록 해주고 있다. 이 내용과 관련하여 간단하게 설명된 블로그 글이 있어 링크를 남긴다. ( [**GitHub Pages 블로그 소개 - SW developer**](https://devinlife.com/howto%20github%20pages/github-blog-intro/) )

위 블로그의 글에 덧붙여 설명하자면, Jekyll은 GitHub 공동창시자인 Tom Preston-Werner에 의해 Ruby 로 작성되었으며, 따라서 Jekyll 사용을 위해서는 Ruby 설치가 필수적이다. 각 GitHub 테마에는 기본적으로 설치가 되어야 하는 내용이 \*.gemspec 에 기재되어 있으며, 추가적으로 플러그인 설치가 필요한 경우에는 Gemfile 에 문법에 맞추어서 필요한 Ruby 라이브러리 (\*.gem)를 기재한 후, Ruby Command Propmpt 창을 통해 설치를 진행하면 된다.

## **Front Matter (전문)**
{: .text-center}  

전문은 포스트의 레이아웃, 제목, 짧은 설명 등 포스트 설정과 관련된 부분이다. 여기에 적은 제목과 설명문 등이 모두 블로그에 그대로 드러나게 되므로 신경써서 작성이 필요하다. 제목과 짧은 설명은 [**GitHub 블로그 첫글쓰기 - SW developer**](https://devinlife.com/howto%20github%20pages/github-blog-intro/) 를 참고하면, 블로그에 포스트가 어떠한 형식으로 게시가 되는 것인지 확인할 수 있다.

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

---

↓ Contents ...
```