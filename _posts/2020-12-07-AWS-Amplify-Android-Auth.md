---
layout: post
title: Amplify를 이용해 안드로이드 앱에서 Auth 추가하기
subtitle: Adding Authentication on Android using Amplify
categories: [AWS, 융복합프로젝트]
tags: [AWS, cloud, 융복합프로젝트]

---

## Authentication 추가하기

1. Google에서 새로운 프로젝트를 만들고 새로운 Credential을 만든다

참고 링크: https://docs.amplify.aws/lib/auth/social_signin_web_ui/q/platform/android#amazon-cognito-user-pool-setup

2. Project 루트 폴더에서 터미널을 켜서 Authorization을 추가해 준다

```bash
amplify add auth

Do you want to use the default authentication and security configuration? Default configuration with Social Provider (Federation)
 
? How do you want users to be able to sign in? Username
? Do you want to configure advanced settings? No, I am done.
? What domain name prefix do you want to use? js1342
 Enter your redirect signin URI: <app_name>://callback/
? Do you want to add another redirect signin URI No
 Enter your redirect signout URI: <app_name>://signout/
? Do you want to add another redirect signout URI No
 Select the social providers you want to configure for your user pool: Google
 
 Enter your Google Web Client ID for your OAuth flow: <O_Auth Client ID>
 Enter your Google Web Client Secret for your OAuth flow: <O_Auth Client Secret>


```



3. 추가가 완료됐으면 Amplify 에 Push해서 추가 사항을 반영해준다

```
amplify push
```





