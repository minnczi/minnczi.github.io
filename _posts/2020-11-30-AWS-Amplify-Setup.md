---
layout: post
title: 안드로이드 앱에서 Amplify CLI 설치하고 구성하기
subtitle: Integrating AWS Amplify with Android Application
categories: [AWS, 융복합프로젝트]
tags: [AWS, cloud, 융복합프로젝트]

---

## AWS CLI 설치 및 계정 연결

AWS CLI가 설치되어 있는지 확인하기 안되있다면 <a href="https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html">이 링크</a> 에서 설치 가능

AWS 설치 후 터미널 껐다 켠 후 터미널 창에서 설치 되었는지 체크한다.

```bash
aws --version
```



AWS CLI가 설치 되었다면 프로젝트 계정을 연결한다

```bash
aws --configure
? AWS Access Key ID: <Access Key ID 입력>
? AWS Secret Access Key: <Secret Access Key 입력>
? Default region name: us-east-1
? Default output format: 엔터친다 (json으로 default 설정)
```



## 안드로이드와 AWS Amplify 연동하기

#### Amplify CLI 설치

터미널에서 설치 명령어를 입력:

```javascript
npm install -g @aws-amplify/cli

// 만약 이 명령어가 안될경우 권한 문제일 가능성이 있으므로
sudo npm install -g @aws-amplify/cli
```



CLI가 설치되었는지 체크한다

```javascript
amplify --version
```



Amplify 설정을 로컬에서 바꾼 이후에는 다음 명령어를 이용해 배포할 수 있다

```javascript
amplify push
```



Cloud에 반영되어있는 최신 업데이트를 반영하려면:

```javascript
amplify pull
```



#### Amplify 백엔드 초기설정

터미널에서 프로젝트 루트 디렉토리로 이동:

```javascript
cd ~/AndroidStudioProject/<project 이름>
```



다음 링크의 Amplify 백엔드 초기화부터 시작해서 초기 설정 완료하면 된다!

https://aws.amazon.com/ko/getting-started/hands-on/build-android-app-amplify/module-two/

