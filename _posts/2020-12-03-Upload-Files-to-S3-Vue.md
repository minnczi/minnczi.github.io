---
layout: post
title: AWS Amplify로 안드로이드에서 Cognito 추가하기
subtitle: Integrating AWS Amplify with Android Application
categories: [AWS, 융복합프로젝트]
tags: [AWS, cloud, 융복합프로젝트]


---



## AWS Amplify CLI를 통해 Cognito 추가



```bash
amplify add auth

? Do you want to use the default authentication and security configuration? Select Default configuration with Social Provider and press enter
? How do you want users to be able to sign in? Select the default Username and press enter
? Do you want to configure advanced settings? Select the default No, I am done and press enter
? What domain name prefix do you want to use? Select the default and press enter
Enter your redirect signin URI: type gettingstarted:// and press enter
? Do you want to add another redirect signin URI? Select the default N and press enter
Enter your redirect signout URI: type gettingstarted:// and press enter
? Do you want to add another redirect signout URI? Select the default N and press enter
Select the social providers you want to configure for your user pool: Google
```



이후에 Google OAuth Client ID랑 Secret을 묻는 항목이 나오는데, Google Developer Console에서 Credential을 만들어서 휙득할 수 있다

https://console.developers.google.com/apis/credentials

1. 위쪽에 CREATE CREDENTIALS 버튼 클릭
2. 절차에 따라 Credential을 만듬
3. Credentials --> OAuth 2.0 Client IDs 밑에 알맞는 Client ID를 클릭하면 ID랑 Secret을 둘다 볼수 있다



이 설정을 다 완료했으면

```bash
amplify push
```



그러면 amplifyconfiguration.json / awsconfiguration.json에 자동으로 CredentialsProvifder, CognitoUserPool, Auth가 생성된걸 볼 수 있다.





