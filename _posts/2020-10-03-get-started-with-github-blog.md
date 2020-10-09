---
layout: post
title: 깃허브로 나만의 블로그 만들기 (Get Started with the Github Blog)
categories: [githubblog, korean]
tags: [jekyll, ruby, github]
---

### Github Blog에 대해서

개발을 처음 배우기 시작하고 나서부터 꼭 해보고 싶었던 것이 나만의 포트폴리오 / 블로그를 만드는 것이었다. Wordpress, wix 같은 좋은 서비스들도 많이 있지만 직접 내손으로 코딩해서 나만의 개성과 개발 과정을 담을 수 있는 공간을 꼭 만들고 싶었다.

그러던 중 찾게된것이 Github Pages를 이용한 Github Blog! 개인적으로 개발자의 멋과 간지라고 생각하는 깃허브를 사용해서 블로그도 만들 수 있다는 것이 매력적이었다. 그리고 좀 더 리서치를 해본 결과 깃허브로 블로그를 만들기로 결심했다.

깃헙 블로그의 장점을 간단히 정리하자면:

- Github url을 통한 블로그 페이지 **무료 호스팅**
- **Static website** 제공 (DB랑 연동되있지 않기 때문에 로딩속도가 빠름)
- 이미 오픈소스로 배포된 **Jekyll template**이 많아서 단기간에 쉽고 빠르게 웹사이트 구축 가능
- 코드를 직접 수정할 수 있기 때문에 쉽게 디테일한 부분도 **customize** 할 수 있음
- **.md 파일**로 쉽게 포스트를 작성할 수 있음 (노트 필기의 끝판왕인 md 파일!)





### Github Blog 만들기

<h4>1. 마음에 드는 Jekyll 템플릿 찾기</h4>

<a href="https://github.com/topics/jekyll-theme">Github</a> 나 구글에 검색해보면 수백까지 다양한 Jekyll 테마들이 있어 고르는데만 한참 걸렸다ㅠㅠ Minimal 하고 깔끔한 디자인이 많아 블로그 형식으로 쓰기에 좋은 테마들이 많이 있었다.

그 중 내가 고른 테마는 <a href="https://github.com/jeffreytse/jekyll-theme-yat">jekyll-theme-yat</a> 이라는 테마 -- 테마 선택 후 소스 코드가 있는 Github 페이지를 찾아 오면 된다.

<h4>2. Repository Fork 하기</h4>

Github에는 Fork 라는 기능이 있는데 다른 사람이 만든 repository의 복제본을 따와서 내 repository로 만들어 쓸 수 있는 기능이다. 아래 이미지에서 맨 오른쪽 fork 버튼을 눌러 내 저장소로 fork 한다.

![Image Alt Text](/assets/images/fork.png)



#### **3. Repository Publish 하기**

방금 fork 해온 repository의 setting에 들어가서 repository의 이름을 `<my_username>.github.io` 로 바꾼다.

이 세팅을 변경해야지만 블로그의 주소가 https://my_username.github.io 형태로 바뀐다.

![Image Alt Text](/assets/images/github-settings.png)



이름을 바꾼 후 밑으로 스크롤 해 Github Pages 섹션에서 source를 선택하고 (repository를 fork 했을때 따로 브랜치를 생성하지 않았다면 master 브랜치에 /root가 source일 가능성이 높다) save 버튼을 누르면 사이트가 publish 됐다는 문구가 뜬다. (몇분 정도 소요 될 수도 있음!)

![Image Alt Text](/assets/images/publish.png)



#### **4. _config.yml 파일 수정하기**

Url이 정상 작동 할 수 있도록 소스코드의 baseurl과 url을 지정해준다. Baseurl은 서브페이지들이 있는 경우 /blog같은 형식으로 더해주지만, 나같은 경우 블로그 메인페이지 하나기 때문에 baseurl을 따로 지정해주지 않았다.

theme은 내가 사용한 jekyll-theme-yat으로 입력! (이 부분은 Github page에 있는 documentation을 참고해서 입력했다.)

Config 파일은 템플릿에 따라 수정해야 될 부분이 다를 수 있으니 템플릿을 찾았던 Github page에 있는 official documentation을 참고해서 하나하나 수정해보면 좋다.

```yaml
baseurl: "" # the subpath of your site, e.g. /blog
url: "https://<user_name>.github.io" # the base hostname & protocol for your site, e.g. http://example.com
favicon: "" # the favicon for your site
theme: jekyll-theme-yat
```



#### **5. 웹사이트 확인**

여기까지 했으면 기본적인 웹사이트 템플릿을 이용한 세팅은 끝! 

아까 publish 했을때 봤던 url로 접속해서 웹사이트가 제대로 publish 되었는지 확인해보면 된다.

![Image Alt Text](/assets/images/blog-home.png)