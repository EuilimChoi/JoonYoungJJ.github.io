---
title:  "Blog 관리 4 - Github 블로그 커스터마이징 A-Z 정리 (Plugins)"
excerpt: "Github 블로그를 커스터마이징 기법"

categories:
  - Blog
tags:
  - Blog Management

toc: true
toc_sticky: true
toc_icon : fas fa-file-code
use_math: true
 
date: 2021-04-20
last_modified_at: 2021-04-20


gallery:
  - url: /assets/image/blogmanage-4/jekyll-archives-tags_Index.jpg
    image_path: /assets/image/blogmanage-4/jekyll-archives-tags_Index.jpg
    alt: "Index of Tags"
    title: "Index of Tags"
  - url: /assets/image/blogmanage-4/jekyll-archives-categories_Index.jpg
    image_path: /assets/image/blogmanage-4/jekyll-archives-categories_Index.jpg
    alt: "Index of Categories"
    title: "Index of Categories"
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

> Generators    : Github Pages의 파일들을 변환하여 Static Site를 생성  
> Converters    : Markup언어를 변환하여 HTML로 변환  
> Commands      : Jekyll Exe의 기능을 확장 (모든 포스트에 반복되는 Front Matter 고정 등..)  
> Tags          : Liquid Tag 생성  
> Filters       : Liquid Filter 생성  
> Hooks         : Jekyll 블로그 사용성 증가  

플러그인 추가방식은 아래와 같다. `jekyll-archives`를 설치하는 방법이다. 먼저, 루트폴더에 있는 Gemfile을 편집한다. [**Gemfile**](https://bundler.io/man/gemfile.5.html)은 Ruby 프로그램에서 사용되는 라이브러리에 대한 정보를 나타내는 파일로 매니페스트 파일이라고 생각하면 될 것 같다.
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

### `Generators > jekyll-feed`  
Front Matter, Profile, Site 에 대한 내용을 Html로 변환한다. Front Matter는 이전에 작성해 둔 [블로그 관리 1](https://joonyoungjj.github.io/blogmanage-1-front_matter)을 참고하면 된다.  

### `Generators > jekyll-archives`  
날짜, 태그, 카테고리를 생성한다. Github 블로그에 포스트를 작성할 때에는 전문(Front Matter)에 필요에 따라서 Tag, Category, Date를 작성할 수 있다. 이 태그들은 jekyll-archives 플러그인을 통해 자동으로 메뉴를 만들기 위한 키워드다.  

태그와 카테고리는 아래와 같이 포스트의 마지막에 나타난다.  
![태그와 카테고리](/assets/image/blogmanage-4/jekyll-archives-tags.jpg)
{: .text-center}  

그리고 이를 각각 클릭해보면 Tag 인덱싱 테이블, Category 인덱싱 테이블이 각각 자동으로 만들어져있음을 확인할 수 있다.

{% include gallery caption="Index" layout="half" %}  

- [**Tags/Categories 설명**](https://jekyllrb.com/docs/posts/#including-images-and-resources)

하지만, 위와 같은 디자인으로 메뉴를 내비두기에는 디자인이 너무 심플하다. 다행히 이 메뉴를 커스텀할 수 있는 방법이 존재한다. 먼저 알아둬야 하는 것이 jekyll-archives 플러그인을 설치하고 활성화시킨 후, 포스트 Front Matter에 Tag(Tags), Category(Categories)를 입력해두고 Jekyll을 실행시키면 `루트폴더/_site/tags`와 `루트폴더/_site/categories` 에 사이트 내에 모든 Tag와 Category가 폴더별로 저장된다는 것이다.  
Liquid 명령어에서는 site 오브젝트를 통해 포스트 제목 등에 접근이 가능하다. 아래 코드를 보면 이해가 쉽다. 아래 내용을 수정해서 각 포스트의 상단에 관련글 목록을 나열하는 것이 가능할 것 같다. 해당 코드에 대한 정보는 이 [링크](https://wiki.archlinux.org/index.php/Jekyll)를 참조하면 확인할 수 있다.  

### `Generators > jekyll-sitemap`  
[사이트 맵](https://developers.google.com/search/docs/advanced/sitemaps/overview?hl=ko)을 자동으로 생성한다.  

{% include video id="JlamLfyFjTA" provider="youtube" %}
{: .text-center}  

### `Converters > jekyll-textile-converter`  
Markup언어의 종류는 상당히 다양하지만, jekyll은 markdown과 textile만 지원한다. 사실, textile로 Github 블로그를 작성한다는 글을 많이 접하지 않아 몰랐지만, 이 플러그인을 설치하면 markdown 대신 textile로 포스트를 작성할 수 있다고 한다.  

- [textile](https://textile-lang.com/)

### `Converters > jekyll-coffeescript`  
웹 사이트를 보기좋게 꾸미는 데 있어서 자바스크립트는 꼭 필요한 존재이다. CoffeeScript는 이 플러그인으로 인해 JavaScript로 컴파일된다. CoffeeScript를 사용하면 기존 JS 코드에 비해 훨씬 간결하게 원하는 작업을 수행할 수 있는 장점이 있다.  

- [CoffeeScript](https://coffeescript.org/)  

### `Converters > jekyll-opal`  
jekyll-coffescript 와 마찬가지로 JavaScript 코드를 생성해내지만, 이 때 사용되는 언어는 Ruby 이다.  

### `Commands > jekyll-compose`  
이 플러그인을 사용하면 포스트를 등록할 때 여러  




