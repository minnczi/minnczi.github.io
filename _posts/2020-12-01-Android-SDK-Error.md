---
layout: post
title: Android SDK 에러 해결
subtitle: Error Log
categories: [AWS, 융복합프로젝트, errorlog]
tags: [AWS, cloud, 융복합프로젝트]
---



## “Failed to install the following Android SDK packages as some licences have not been accepted” error

이 에러는 새로운 파일을 받아와서 처음 build를 진행할때 생겼던 에러이다.

새로운 파일을 받을때 라이센스에 동의를 해야되는데 그걸 하지 않아서 생기는 에러이다.

다음 코드들을 실행하면 쉽게 해결된다.



Mac:

```bash
export JAVA_HOME=/Applications/Android\ Studio.app/Contents/jre/jdk/Contents/Home
yes | ~/Library/Android/sdk/tools/bin/sdkmanager --licenses
```



Windows:

```bash
%ANDROID_HOME%/tools/bin/sdkmanager --licenses
```



참고 출처: https://stackoverflow.com/questions/54273412/failed-to-install-the-following-android-sdk-packages-as-some-licences-have-not



## [Android] please select android sdk 에러

이 에러는 빌드 완료 이후 실행하는 과정에서 났던 에러이다.

실행을 눌렀을때 설정이 잘 안됐다는 경고가 뜨고 SDK를 선택하라는 팝업창이 뜨는데 그걸 무시하고 run anyways를 눌렀을때 이런 에러가 발생한다.

이럴경우 file --> sync project with gradle files를 누르면 쉽게 해결된다.

참고 출처: https://medium.com/@sket8993/android-please-select-android-sdk-186085c3b946