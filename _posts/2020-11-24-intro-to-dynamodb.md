---
layout: post
title: Getting Started with AWS DynamoDB
subtitle: Creating and Setting up DynamoDB
categories: [AWS, cloud, DB]
tags: [AWS, cloud, DB]
---

## DynamoDB 기본 개념

이번 프로젝트때 NoSQL DB가 우리가 필요한 데이터를 저장하는데 더 적합하다고 생각했고 Amazon AWS에서 제공하는 DynamoDB를 써보기로 했다!

참고 자료: https://aws.amazon.com/ko/getting-started/hands-on/create-manage-nonrelational-database-dynamodb/



#### **DynamoDB (NoSQL) 기본 개념 정리**

**Table:** NoSQL에서 흔히 말하는 Collection의 개념 - RDS에서 한 Table과 비슷한 개념의 단위

**Item:** RDS에서 row 한개와 비슷한 개념

**Attribute:** RDS에서 column 한개와 비슷한 개념

- 속성을 테이블 작성시 지정하지 않아도 됨
- Int, Str같은 형대 이외에도 List, Dict와 같은 형태도 저장할 수 있음

**Primary Key:** RDS에서의 Primary Key와 거의 동일하며 테이블을 생성할 때 지정해야함. 단일 속성으로 이루어진 단일키나 (simple primary key) 2개 이상의 속성으로 이루어진 복합 기본키 (compound primary key)를 지정할 수 있다.



#### DynamoDB (NoSQL DB)의 특징

- 비 관계형 데이터베이스이므로 (Non-relationsional database), 테이블을 생성할 때 전체 스키마를 지정하지 않아도 됨
- 테이블에 대한 기본키 (고유 식별자)만 테이블을 생성할 때 지정
  

## 환경 설정

1. AWS 계정이 있는지 확인
2. <a href="https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html">AWS CLI가 설치</a>되어 있는지 확인
3. 연습을 위한 실습 파일 다운로드: `curl -sL https://s3.amazonaws.com/ddb-deep-dive/dynamodb.tar | tar -xv`
4. boto3 다운로드: `sudo pip install boto3`

