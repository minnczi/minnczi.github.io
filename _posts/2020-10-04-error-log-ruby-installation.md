---
layout: post
title: Ruby Gem FilePermissionError 해결
subtitle: Error Log
categories: [errorlog, githubblog]
tags: [jekyll, ruby, github]

---

### 에러 설명 

처음 gem을 설치했을때는 문제 없이 실행이 되었었다. 하지만 중간에 theme을 바꾸기로 결정했고, source code에 있는 Gemfile, config파일등을 수정하는 과정에서 불필요한 gem들이 생기기 시작했다.

불필요한 gem을 삭제하고 bundler를 재설치 하는 과정에서 이런 에러가 발생했다.

```bash
$ gem install bundler
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.6.0 directory.
```



### 해결방법

#### Method 1: Gem 삭제 및 재설치

이 방법은 결론적으로 불필요한 gem을 정리해주긴 했지만 문제를 해결하지는 못했다.

1. 모든 gem 삭제: `gem uninstall --all`
2. vendor/bundler 디렉토리 삭제:  `rm -rf vendor`
   - 이 방법은 권장하는 방법은 아니다. 모든 패키지를 vendor 라는 새로운 PATH에 깔았기 때문에 system 디렉토리가 아니었고, 그래서 디렉토리를 깔끔하게 삭제하는 방법을 택했다.
3. Working directory에서 bundler 재설치: `gem install bundler`



#### Method 2: rbenv를 이용한 루비 재설치

맥에서는 기본적으로 사용되는 system Ruby가 있는데 이 Ruby에 대한 실행권한이 없을경우 위와 같은 에러가 생길 수 있다.

이런 경우에는 system Ruby를 변경하는 것 보다 이 프로젝트에서 사용할 수 있는 ruby environment를 설치, 지정해주는 것이 훨씬 더 효율적이고 보안상으로도 안전한 방법이라고 한다.

1. Working directory에서 루비 재설치: `brew install ruby`
2. Default로 사용되는 루비 환경변수 지정: `echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.bash_profile`
3. 사용되는 ruby version과 경로 확인하기: 확인할 수 있는 방법이 여러가지 있다
   - `ruby -v` or `rbenv versions` -- ruby 버전이 새로운 기능을 서포트 할 수 있는 정도의 최신버젼인지 확인
   - 경로 확인: `which ruby` -- 만약 경로가 /usr/bin/ruby 가 아니라면 성공!
4. Bundler 재설치: `gem install bundler`