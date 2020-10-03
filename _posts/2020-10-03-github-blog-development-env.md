---
layout: post
title: 깃허브 블로그 개발환경 세팅하기 (Setting up Development Environment for Github Blog)
categories: [githubblog, korean]
tags: [jekyll, ruby, github]
---

### Local 개발환경 세팅이 필요한 이유

만약 저번 포스팅에서 publish한 웹사이트에서 디자인을 전혀 수정하지 않고 md 파일만 추가할거라면 이 과정이 필요 없겠지만, 개인적으로 디자인도 이것저것 바꿔보고 코드도 더 쉽게 작성하기 위해 local 환경에 개발환경을 세팅하기로 했다.

Local에 개발환경을 세팅하면:

- 코드를 쉽게 수정할 수 있고
- Publish된 웹사이트에 내용이 반영될때까지 1-2분 기다리지 않고 바로바로 내용을 추가하고 반영 사항을 테스트 해볼 수 있고
- Publish하기 전에 local 환경에서 어떻게 페이지가 나오는지 확인해 볼 수 있다



### 개발환경 세팅하기

그럼 본격적으로 개발환경 세팅하기!

이 부분도 역시 official documentation을 많이 참고해가면서 했다 - 아무래도 세팅하는 방법이 조금씩 다를 수 있으니 각 템플릿에 나와있는 방법대로 하는것이 젤 쉽고 정확하겠지만 기본적인 원리는 다 비슷한거 같았당

#### 1. Gemfile 수정하기

jekyll이 사용하는 Ruby Framework에서 패키지 / 라이브러리 설치를 담당해주는게 바로 Gem. Gemfile안에 어떤 라이브러리를 설치해야될지 명시해놓기 때문에 official documentation에 나와있는대로 Gemfile을 수정해주었다.

```ruby
# frozen_string_literal: true

source "https://rubygems.org"
gem "jekyll-theme-yat"
```

`gem jekyll-theme-yat` 부분에 이 템플릿에 필요한 패키지들이 내포되어있다.



#### 2. Jekyll과 bundler 설치하기

패키지 설치를 할때 bundle이라는 명령어를 사용해서 설치를 하는데, 이 명령어를 사용하려면 jekyll과 bundler가 설치되어 있어야 한다. 설치 명령어는 working directory 안 터미널 창에서:

`gem install jekyll bundler`

이 부분에서 참고했던 <a href="https://jekyllrb.com/docs/">웹사이트</a>



#### 3. Bundle을 사용해서 필요한 패키지 설치하기

앞에 바꿔놓았던 gemfile을 바탕으로 bundle 명령어를 이용해서 필요한 패키지를 설치해준다. 설치 명령어는 터미널에서:

`bundle install`

이 부분에서 처음에 권한 문제로 오류가 났는데 그럴경우 설치 경로를 정확히 지정해주면 된다!  <a href="https://bundler.io/bundle_install.html">참고 soruce</a>

`bundle install --path vendor/bundle`



이 부분이 처음에 뭔지 좀 헷갈렸는데 장고로 웹개발을 먼저 배워서인지 장고에 비교해서 생각해보니 엄청 쉬운 개념이었다. 장고의 `pip install -r requirements.txt`와 비슷한 기능을 하는 코드다. Gemfile에 명시되있는 패키지들과 dependency를 찾아서 install 해주는 기능이다.



#### 4. 패키지 설치 확인하기

여기서 부터 엄청난 오류가 났다ㅠㅠㅠ 자세한 오류설명은 다음포스팅에서 이어서 하겠지만 만약 설치가 제대로 되었는지 보고싶다면 루비를 확인해 보면된다.

루비 버전 확인하기: `ruby -v`

여기에서 최신 루비버전이 잘 설치된것이 나온다면 (현재 가장 최신버전은 2.7) 1차적으로는 설치가 잘 된 것!



#### 5. 로컬 환경에서 실행하기

여기까지 성공적으로 따라왔다면 `bundle exec jekyll serve` 코드를 터미널창에 입력하면 http://localhost:4000 주소로 로컬환경에서 접속이 가능하다. (장고의 `python manage.py runserver` 와 비슷한 코드)

Local에서 접속할 경우 코드를 git에 commit / push 하지 않아도 local repository에서 저장만 하면 새로고침 했을때 변한점을 테스트 해 볼 수 있다. (다만 config파일의 환경변수를 수정했을때는 포트를 끄고 다시 재접속 해야됨!) 

Git에 commit / push를 하기 전까지 변경사항이 반영되진 않지만 그 전에 local에서 빨리빨리 확인해 볼 수 있다!



이상 모든게 해결됐으면 30분만에 끝났겠지만 사실 반나절이 걸린 로컬 개발환경 세팅 메뉴얼이었다..