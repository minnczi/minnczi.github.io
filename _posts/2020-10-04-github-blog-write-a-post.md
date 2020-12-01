---
layout: post
title: 깃허브로 나만의 블로그 만들기 3 (Getting Started with the Github Blog 3)
subtitle: 깃허브 블로그에서 게시물 작성하기 (Writing a blog post using Github blog)
categories: [githubblog]
tags: [jekyll, ruby, github]
---

### 기본 작성 방법

Jekyll로 만든 깃허브 블로그에서는 기본적으로 Markdown(.md) 파일을 사용해 새로운 포스트를 추가할 수 있다.

우선 source folder 안에 _posts라는 이름의 폴더가 없으면 하나 생성해준다.

이 폴더 안에서 Typora, vi editor, VS code 등등 취향에 맞는 에디터를 사용하여 markdown 파일을 작성하면 된다. 나같은 경우에는 평소 쓰던 Typora를 이용해서 markdown 파일을 사용해서 이 글을 작성했다.

또한 파일을 만들때는 파일이름을 `YYYY-MM-DD-post_title.md` 형식으로 지정해야 포스트로 인식을 하고 페이지에 추가가 된다.

글의 시작부분에는 템플릿에 지정되어있는 변수들을 사용해 정해진 포맷에 맞게 글을 등록해야 한다. 이 포스트의 경우 맨 위에 다음과 같은 변수들을 활용하여 템플릿을 적용시켜주었다.

```yaml
---
layout: post
title: 깃허브 블로그에서 게시물 작성하기
Subtitle: Writing a blog post using Github blog
categories: [githubblog, korean]
tags: [jekyll, ruby, github]
---
```



이 밑으로는 자유로운 형식으로 글을 작성해 주면 됩니다. 마크다운에서 쓰는 링크, heading을 활용한 스타일링 등등이 다 템플릿에 맞게 표시된다. 아래는 지금 이 포스트가 등록된 예제:

![Image Alt Text](/assets/images/blog-post-example.png)

이런식으로 작성을 해주면 된다!

### Yaml