---
title:  "Github Blog 3 - Github 블로그 웹마스터 작업, 방문자 분석, 댓글 추가 (minimal-mistakes)"
excerpt: "Github 블로그 메뉴얼 작업 리스트"

categories:
  - blog
tags:
  - comments
  - google-analytics
  - webmatser-tool

toc: true
toc_sticky: true
toc_icon : fas fa-file-code
use_math: true
 
date: 2021-04-20
last_modified_at: 2021-04-24
---

Github 블로그는 타 블로그와는 달라서, 웹 사이트 노출, 댓글기능, 웹 사이트 방문자 분석 등 기본적으로 제공되어야 할 법한 기능들을 모두 직접 등록하여 사용하여야 한다. 다행히도 대부분의 기업들이 무료로 이러한 서비스를 제공하고 있어서 제대로된 가이드만 있다면 따라하는 데 있어서 어려움은 없을 것 같다.  

---

## **웹 사이트 노출**
{: .text-center}  

타 블로그 전문 사이트에서 블로그를 개설하는 것과 달리 Github 블로그는 노출을 원하는 각 검색엔진마다 내 블로그를 등록해야 한다. 이 블로그의 경우에는 Google, Naver, Daum, Bing에 각각 등록을 마쳤다. 이 내용의 경우에는 Github 블로그에서 상당히 흔한 주제로 검색을 하면 여러 블로그에 이에 대해 상세하게 다루고 있기 때문에 나까지 이 것을 상세하게 다룰 필요는 없을 듯 하다. 따라서 자세한 설명을 위해서는 구글에 "github 블로그 검색엔진 등록" 와 같이 검색한 다음, 이 블로그를 제외한 다른 블로그에 들어가면 된다.  

사실 내 생각에는 간단하게만 설명해도 대부분의 사람들이 이해하고 따라하는데 어려움이 없을 것이라 생각한다. 각 사이트마다 웹마스터(도구)가 존재한다. 네이버를 예로 들면, 네이버 웹마스터도구라고 검색을 하게되면 해당 사이트가 존재한다. 이 사이트에 들어가서, 자신의 github 주소를 입력하면 된다. 내 블로그를 기준으로는 `joonyoungjj.github.io`가 되겠다. 이후, 등록절차를 진행하면 되는데 다음을 제외하고 나머지 검색엔진은 루트폴더에 인증을 위한 xml, html 파일을 설치하라고 요구한다. _config.yml 이 존재하고 있는 위치가 루트 폴더이고, 다운로드 받으라고 하는 파일을 루트 폴더에 다운받아 두고, github desktop (또는 cmd) 로 commit/push 이후에 github 서버에 해당 파일이 업로드가 완료되면 인증이 정상적으로 이루어진다. 이 때, 꼭 정상적으로 등록이 완료되었다는 문구를 확인해야 한다.  
그 이후, 사이트맵 (Sitemap.xml)을 웹마스터 도구에 등록을 하게되면 검색을 할 수 있는 준비가 끝난다. 다음과 Zum은 별도의 사이트맵 등록이 불필요하다고 한다.  
- [**Naver 사이트맵 등록**](http://blog.naver.com/PostView.nhn?blogId=pswkiller&logNo=221343368118&categoryNo=0&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView)
- [**Google 사이트맵 등록**](https://imweb.me/faq?mode=view&category=29&category2=35&idx=15573)
- [**Bing 사이트맵 등록**](https://nicksstory.tistory.com/405)  

Google 의 경우에는 위 방법을 따라 사이트맵을 등록하더라도 정상적으로 사이트맵이 적용되지 않는 경우가 있다. 사이트맵을 등록했을 때 정상적으로 등록이 되지 않고 **`가져올 수 없음 (could not be read)`** 에러가 발생하는 경우가 흔히 알려진 현상인데, 이 에러를 해결하기 위해서는 웹 마스터 도구 메뉴 중 `URL 검사`를 눌러 직접 Github 블로그 URL 을 입력한 뒤 검사하여 나오는 결과 화면에서 "색인 생성 요청" 을 클릭하면 된다. (나의 경우에는 이 URL 검사 결과 화면에 **`URL이 Google에 등록되어 있지 않음`** 이라는 에러문구가 떠 있었다.)  

---

## **댓글 기능**
{: .text-center}  

어느 사이트를 가더라도 흔히 있는 댓글 기능이 Github 블로그에서는 플러그인으로 별도 설치를 해야 적용이 된다. 거기에 더불어 _config.yml도 일부 손을 봐야한다.  
댓글 플러그인은 크게 두 가지가 있다.  
- [**utterance**](https://github.com/apps/utterances)  
  Github 아이디를 사용하여 댓글을 달고, Issues에서 댓글들을 모두 모아서 볼 수 있음 ( [참고 블로그](https://ansohxxn.github.io/blog/utterances/) )  
- [**disqus**](https://disqus.com/)  
  소셜 미디어 아이디를 사용하여 댓글을 달 수 있다. ( [참고 블로그](https://devinlife.com/howto%20github%20pages/blog-disqus/) )

_(이 블로그에는 utterance가 적용되어 있다. Issues에서 댓글을 모아볼 수 있다면 댓글을 놓치게 되는 경우가 적을 것 같기도 했고 이 블로그는 프로그래밍에 관심이 있는 사람들을 위한 블로그이므로 Github 사용자를 중심으로 생각하는 것이 맞다고 생각했다.)_

## **방문자 분석**
{: .text-center}  

방문자 분석의 경우에도 구글의 힘을 빌려야 한다. 구글에서는 웹 사이트의 방문자 분석을 위해 애널리틱스 서비스를 운영하고 있다. 이 [**블로그 글**](https://devinlife.com/howto%20github%20pages/google-search-console-and-analytics/)을 참고하면 어렵지 않게 애널리틱스에 내 사이트를 등록하여 방문자 분석을 해볼 수 있다. 위 블로그 글 참고시에 추적 ID의 형태가 "UA-XXX..." 에서 "G-XXX..."로 변경되었다는 점을 유념하고 보아야 한다.  
그리고, 아래와 같이 _config.xml을 변경해줘야 정상적으로 동작한다. 
```markdown
# Analytics
analytics:
  provider               : "google-gtag" # false (default), "google", "google-universal", "google-gtag", "custom"
  google:
    tracking_id          : "G-??????????"
    anonymize_ip         : false # true, false (default)
```