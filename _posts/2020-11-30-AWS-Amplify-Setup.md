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



## AWS Amplify 초기설정 하기

AWS Amplify에 대해 배운것을 바탕으로 진행중인 안드로이드에 적용하는 방법이다.

1. amplify 초기 설정을 해준다

```bash
amplify init

? Enter a name for the environment
    `dev`
? Choose your default editor:
    `Visual Studio Code`
? Do you want to use an AWS profile?
    `Yes`
? Please choose the profile you want to use
    `default`

```

지시에 따라서 질문을 대답하면 프로젝트 폴더에 왼쪽과 같은 backend 폴더가 생긴다.

그리고  `~/app/res/raw` 에 amplifyconfiguration.json과 awsconfiguration.json 이렇게 두개 파일이 생긴다

amplifyconfiguration.json 에서 필요한 backend 자원들을 기술할수 있다.

다음 링크의 Amplify 백엔드 초기화부터 시작해서 초기 설정 완료하면 된다!

https://aws.amazon.com/ko/getting-started/hands-on/build-android-app-amplify/module-two/

2. Gradle Scripts의 build.grade(Project) 파일에서 buildscripts와 allprojects 아래에  `mavenCentral()`을 추가한다

3. Gradle Scripts의 build.grade(Module) 파일에서 buildscripts와 allprojects 아래에  `implementation 'com.amplifyframework:core:1.4.0'`을 추가한다

4. `~/app/java/com.example.project` 에 Backend.kt 파일을 만들어서 다음 ㅋh드를 복사한다

   ```kotlin
   package com.example.project1342
   
   import android.content.Context
   import android.util.Log
   import com.amplifyframework.AmplifyException
   import com.amplifyframework.core.Amplify
   
   object Backend {
   
       private const val TAG = "Backend"
   
       fun initialize(applicationContext: Context) : Backend {
           try {
               Amplify.configure(applicationContext)
               Log.i(TAG, "Initialized Amplify")
           } catch (e: AmplifyException) {
               Log.e(TAG, "Could not initialize Amplify", e)
           }
           return this
       }
   }
   ```

   

5. `~/app/java/com.example.project` 에 Application.kt 파일을 만들어서 다음 코드를 복사한다

```kotlin
package com.example.project1342

import android.app.Application

class AndroidGettingStartedApplication : Application() {

    override fun onCreate() {
        super.onCreate()

        // initialize Amplify when application is starting
        Backend.initialize(applicationContext)
    }
}
```



