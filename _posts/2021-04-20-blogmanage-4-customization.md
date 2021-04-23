---
title:  "[Blog 관리] 4. Github 블로그 커스터마이징 A-Z 정리 (Plugins)"
excerpt: "Github 블로그를 커스터마이징 기법"

# categories:
#   - Blog
# tags:
#   - Blog
#   - MathJax
#   - Jekyll
#   - LaTeX

toc: true
toc_sticky: true
toc_icon : fas fa-file-code
use_math: true
 
date: 2021-04-20
last_modified_at: 2021-04-20
---

사이트를 한 눈에 잘 보이도록 사이트에 네비게이션 기능과, 메뉴는 꼭 필요하다. 아래는 내 사이트의 현재 상태이다.  

{% include figure image_path="/assets/image/blogmanage-4/blogmain_no_menu.jpg" alt="기본 상태" caption="기본 상태" %}  

위와 같은 상태로 유지하면서 블로그를 키워나가면 나중에는 더 이상 정리가 어려워지게 된다. 아래와 같이 나누어 하나씩 커스터마이징 할 수 있는 방법을 살펴보며 사이트를 업그레이드 시켜보도록 하겠다.  

{% include figure image_path="/assets/image/blogmanage-4/BlogStructure.png" alt="구역 별 이름" caption="구역 별 이름" %}  

---

## [**Liquid**](https://shopify.github.io/liquid/)
{: .text-center}  

앞에서 따로 언급은 안 했지만, Jekyll 은 kramdown과 더불어 Liquid를 병행하여 사용할 수 있도록 디자인되었다. Liquid는 Ruby로 작성된 오픈소스 템플릿 언어로 단조로운 kramdown에 프로그래밍적 요소를 가미한다. 이 부분에 대해서는 추후 자세히 정리할 예정이다. 혹시나 Liquid를 위해 헛걸음했을 수 있는 방문자들을 위해 Liquid에 대해 잘 설명되어 있는 블로그 포스트를 안내한다. ( [**링크**](https://ansohxxn.github.io/blog/liquid/) ) 

---

## **Plugin (플러그인)**
{: .text-center}  

Jekyll은 여러가지 플러그인을 설치할 수 있도록 되어 있다. 먼저, 사용가능한 플러그인 리스트는 아래 링크를 따라가면 확인할 수 있다.  

- [공식사이트 Jekyll 플러그인 목록](https://jekyllrb.com/docs/plugins/your-first-plugin/)  
- [인기있는 Jekyll 플러그인 TOP 33](https://planetjekyll.github.io/plugins/top)

Jekyll은 Generators, Converters, Commands, Tags, Filters, Hooks 총 6개 타입의 플러그인을 지원한다.  

> Generators    : Markdown을 변환하여 Static Site를 생성  
> Converters    : Markup언어를 변환하여 State Site에 포함  
> Commands      : Jekyll Exe의 기능을 확장  
> Tags          : Liquid Tag 생성  
> Filters       : Liquid Filter 생성  
> Hooks         : Jekyll 블로그 사용성 증가  

플러그인 추가방식은 아래와 같다. 먼저, 루트폴더에 있는 Gemfile을 편집한다. [**Gemfile**](https://bundler.io/man/gemfile.5.html)은 Ruby 프로그램에서 사용되는 라이브러리에 대한 정보를 나타내는 파일로 매니페스트 파일이라고 생각하면 될 것 같다.
```ruby
source "https://rubygems.org"
...
gem "jekyll-archives" # 추가
...
gemspec
```
이후에, _config.yml에도 플러그인을 추가해주어야 한다.
```yml
...
# Plugins (previously gems:)
plugins:
  - ...
  - jekyll-archives # 추가

# mimic GitHub Pages with --safe
whitelist:
  - ...
  - jekyll-archives # 추가
...
```
여기까지 작업한 내용을 저장하고, "Start Command Propmt With Ruby" 를 실행하여 cd 명령어를 통해 루트폴더로 cmd를 이동시킨 뒤, bundle 명령어를 입력하여 실행해주면 자동으로 누락된 Ruby 라이브러리가 다운로드가 된다. (만약 Ruby가 설치되어 있지 않다면 이 [**링크**](https://rubyinstaller.org/downloads/)로 들어가서, 컴퓨터의 운영체제(x86/x64)에 맞는 Ruby(with Devkit)을 설치하면 된다.)

라이브러리 추가 문구(Gemfile, _config.yml)가 정확하지 않으면 git push를 해도 사이트에 업데이트 되지 않는 에러가 발생할 수 있다. 물론, 잘못된 내용을 수정하고 다시 git push를 하면 정상적으로 사이트가 생성된다.  
하지만 일단 에러가 발생하면 디버깅에 어려움이 발생할 수 있으므로, 라이브러리를 추가하기 전에는 글을 먼저 올리고 정상적으로 사이트가 생성되는 것을 확인한 뒤에 라이브러리 추가하는 작업을 하는 식으로 작업을 나눠서 진행하는 것을 추천한다. 

---
이제, Jekyll에 적용시킬 수 있는 플러그인을 차근차근 살펴보려 한다. 

### `Generators - Jekyll Feed`  

Front Matter, Profile, Site 이름을 표시한다.




