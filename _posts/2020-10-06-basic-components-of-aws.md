---
layout: post
title: Basic Concepts and Terminologies for AWS
subtitle: Intro to AWS
categories: [AWS, cloud]
tags: [AWS, cloud]
---

 <img src="https://docs.amazonaws.cn/en_us/vpc/latest/userguide/images/subnets-diagram.png" alt="VPC with multiple Availability Zones" style="zoom: 80%;" />



### VPC(Virtual Private Cloud)

- 네트워크 계층
- EC2 인스턴스를 비롯한 여러 AWS 서비스의 리소스를 담을 수 있는 가상 네트워크
- 한 AWS region 안에서만 존대할 수 있고, 한 region에 만든 VPC는 다른 region에서 보이지 않음
- 연속적인 IP 주소 범위로 구성 --> CIDR 블록으로 표시
  - 10.0.0.0/8 --> 10.0.0.0 ~ 10.255.255.255
  - 172.16.0.0/12 -> 172.16.0.0 ~ 172.31.255.255
  - 192.168.0.0/16 --> 192.168.255.255



### Subnet

- VPC  내 논리 컨테이너
- EC2 인스턴스를 배치하는 장소 (인스턴스는 서브넷 안에 위치)
  - Once an instance in created in a subnet, it can't be relocated to another subnet
  - After shutting off an instance, a new instance can be created in another subnet
- 인스턴스를 서로 격리하고, 인스턴스 간의 트래픽 흐름을 제어하고 인스턴스를 기능별로 묶을 수 있음
- Subnet CIDR Block
  - Subset of VPC, it has to be **unique** within a VPC
- Subnet can only exist in one region



### ENI (Elastic Network Interface)

- Serves the function of a network interface in the physical server



### Internet Gateway(IGW)

- Public IP address를 할당받은 인스턴스가 인터넷과 연결돼서 요청을 수신할 수 있도록 기능을 제공
- 처음 VPC를 만들면 인터넷 게이트웨이가 연결되어 있지 않으므로, 직접 인터넷 게이트웨이를 만들고 VPC와 연결해야함
- 하나의 VPC는 하나의 인터넷 게이트웨이만 연결할 수 있음



### Routing

- VPC는 소프트웨어 함수로 IP routing을 구현
- Routing Table: consisted of one or more routing and one or more subnet
- Default Routing: routing that points to the internet gateway
  - 대상 주소: 0.0.0.0/0 - 인터넷 상의 모든 호스트 IP를 기반
  - 대상: igw-xxxxxxxxx - 인터넷 게이트웨이
- Public Subnet: 기본 라우팅이 포함된 라우팅 테이블과 연결된 서브넷
- Private Subnet: 기본 라우팅이 포함된 라우팅 테이블과 연결되지 않은 서브넷

**Example**

| 대상 주소     | 대상          |
| ------------- | ------------- |
| 172.31.0.0/16 | LOCAL         |
| 0.0.0.0/0     | igw-xxxxxxxxx |

**Scenario 1**: Sending a packet to 198.51.100.50

- 라우팅할 위치와 가장 근접하게 일치하는 항목을 기반으로 라우팅을 함; 인터넷 게이트웨이로 라우팅됨

- 라우팅 테이블의 항목들간의 순서는 중요하지 않음
- 0.0.0.0/0으로 패킷이 보내짐



### 보안 그룹 (Security Group)

- Works like a firewall
- Instance의 ENI에서 송수신하는 트래픽을 허가해서 트래픽을 제어
- 모든 ENI는 최소 한개 이상의 보안 그룹과 연결되야 하고, 보안 그룹은 여러 ENI와 연결될 수 있음
- 생성할 때 보안 그룹 이름, 설명, 포함될 VPC를 지정하고, 생성 후에 인바운드, 아웃바운드 규칙을 지정 --> 트래픽을 허용
- 상태 저장 방화벽 역할 --> 보안 그룹이트래픽을 한 방향으로 전달되도록 허용할 때 반대 방향의 응답 트래픽을 지능적으로 허용 (ex. 웹 클라이언트에서 https로 요청을 허용했다면 요청에 대한 응답도 허용)



### NACL(Network Access Control List)

- 보안 그룹과 유사

  - 원본 또는 대상 주소 CIDR, 프로토콜, 포트를 기반으로 트래픽을 인바운드, 아웃바운드 규칙으로 제어 --> 방화벽과 같은 역할
  - VPC에 삭제할 수 없는 기본 NACL이 있음

- 서브넷에 연결되어 해당 서브넷과 송수신되는 트래픽을 제어

- 상태 비저장

  - NACL을 통과한 연결 상태를 추적하지 않는다
  - 모든 인바운드와 아웃바운드 트래픽을 허용 규칙을 별도로 작성해야 함

- 규칙을 적용할 때 번호의 오름차순으로 정리

  