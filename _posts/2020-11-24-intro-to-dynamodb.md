---
layout: post
title: Getting Started with AWS DynamoDB
subtitle: Creating and Setting up DynamoDB
categories: [AWS, cloud, DB]
tags: [AWS, cloud, DB]
---

## DynamoDB 기본 개념

이번 프로젝트때 NoSQL DB가 우리가 필요한 데이터를 저장하는데 더 적합하다고 생각했고 Amazon AWS에서 제공하는 DynamoDB를 써보기로 했다!



#### 참고자료

DynamoDB Tutorial Lab: https://aws.amazon.com/ko/getting-started/hands-on/create-manage-nonrelational-database-dynamodb/

DynamoDB Developer Guide (Dynamo DB 개념 설명이 잘 되어있음): https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html#HowItWorks.CoreComponents.TablesItemsAttributes

Boto3 DynamoDB Documentation (Boto3 사용한 명령어 설명이 잘 되어있음): https://boto3.amazonaws.com/v1/documentation/api/latest/guide/dynamodb.html

DynamoDB API Reference: https://docs.aws.amazon.com/ko_kr/amazondynamodb/latest/APIReference/Welcome.html



#### **DynamoDB (NoSQL) 기본 개념 정리**

**Table:** NoSQL에서 흔히 말하는 Collection의 개념 - RDS에서 한 Table과 비슷한 개념의 단위

**Item:** RDS에서 row 한개와 비슷한 개념

**Attribute:** RDS에서 column 한개와 비슷한 개념

- 속성을 테이블 작성시 지정하지 않아도 됨
- Int, Str같은 형대 이외에도 List, Dict와 같은 형태도 저장할 수 있음

**Primary Key:** RDS에서의 Primary Key와 거의 동일하며 테이블을 생성할 때 지정해야함. 단일 속성으로 이루어진 단일키나 (simple primary key) 2개 이상의 속성으로 이루어진 복합 기본키 (compound primary key)를 지정할 수 있다.

- **Partition Key (Hash Attribute)**: Simple primary key, 단일키를 사용할 경우 partition key 하나만 지정해서 primary key를 지정할수 있다
- **Sort Key (Range Attribute)**: 만약 compound primary를 사용할 경우 하나를 parition key, 하나를 sort key로 설정해서 두개를 합친 값이 unique하도록 설정할 수 있다



#### DynamoDB (NoSQL DB)의 특징

- 비 관계형 데이터베이스이므로 (Non-relationsional database), 테이블을 생성할 때 전체 스키마를 지정하지 않아도 됨
- 테이블에 대한 기본키 (고유 식별자)만 테이블을 생성할 때 지정
  

## 환경 설정

1. AWS 계정이 있는지 확인
2. <a href="https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html">AWS CLI가 설치</a>되어 있는지 확인
3. 연습을 위한 실습 파일 다운로드: `curl -sL https://s3.amazonaws.com/ddb-deep-dive/dynamodb.tar | tar -xv`
4. boto3 다운로드: `sudo pip install boto3`



## 테이블 생성

Sample Code:

```python
import boto3

# boto3 is the AWS SDK library for Python.
# We can use the low-level client to make API calls to DynamoDB.
client = boto3.client('dynamodb', region_name='us-east-1')

try:
    resp = client.create_table(
        TableName="Books",
        # Primary Key 설정
        KeySchema=[
            {
                "AttributeName": "Author",
                "KeyType": "HASH"
            },
            {
                "AttributeName": "Title",
                "KeyType": "RANGE"
            }
        ],
        # KeySchema나 Indexes에서 선언된 Primary Key의 속성을 지정
        AttributeDefinitions=[
            {
                "AttributeName": "Author",
                "AttributeType": "S"
            },
            {
                "AttributeName": "Title",
                "AttributeType": "S"
            }
        ],
        # ProvisionedThroughput controls the amount of data you can read or write to DynamoDB per second.
        # You can control read and write capacity independently.
        ProvisionedThroughput={
            "ReadCapacityUnits": 1,
            "WriteCapacityUnits": 1
        }
    )
    print("Table created successfully!")
except Exception as e:
    print("Error creating table:")
    print(e)
```

