---
title:  "Github Blog 5 - 메뉴 생성 (minimal-mistakes)"
excerpt: "Github Blog 메뉴 - 사이드 바, 네비게이션"

categories:
  - Blog
tags:
  - Blog Management

toc: true
toc_sticky: true
toc_icon : fas fa-file-code
use_math: true

sidebar:
  nav : "sidemenu"
 
date: 2021-04-25
last_modified_at: 2021-04-25
---

## **사이드 바 메뉴**

minimal-mistakes 테마에 사이드 바 메뉴 생성을 위해서는 `_data/navigation.yml` 파일을 수정해야 한다. 자세한 내용은 이 [**링크**](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#custom-sidebar-navigation-menu) 를 참조하면 자세히 알아볼 수 있다.  
간단히 요약하면, navigation에 메뉴 오브젝트를 생성한 다음, 포스트의 전문에 sidebar, nav 키워드를 사용하여 오브젝트를 지정하는 형식이다.  

아래는 예제 코드로 아래와 같이 navatigation.yml 에 yaml 오브젝트를 생성한 뒤, 전문에 해당 yaml 을 지정만 하면 된다.

```yml
sidemenu:
  - title : 블로그 관리 
    children :
      - title : "일지"
        url : /blog/2021/04/20/blogmanage-4-customization/
```  

`_data/navigation.yml`
{: .text-center}  


```Markdown
---
...
sidebar:
  nav : "sidemenu"
...
---
```  

`_config.yml`
{: .text-center}  


## **네비게이션 메뉴**  
`_data/navigation.yml` 의 main 오브젝트를 수정하면 된다.
