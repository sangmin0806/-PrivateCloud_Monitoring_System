# 빅데이터를 활용한 Private Cloud 및 모니터링 시스템 구축

## 1. 프로젝트 배경

![](https://velog.velcdn.com/images/show7441/post/c3218b54-d685-4549-9e5c-6f6370bc4c48/image.png)

Private Cloud 환경을 구축하고 Monitoring을 할 수 있도록 하는 Project 입니다.
Monitoring Server에서는 Private Cloud에 존재하는 Resource를 확인할 수 있으며, 해당 자원을 사용자에게 보여주는 동작등을 할 수 있습니다.

## 2. 프로젝트 설명

### 모니터링 웹 서버 동작 화면

![](https://user-images.githubusercontent.com/121588874/244625515-fd98078a-9753-49f8-9b21-049a8ac0fed7.gif)

### 가상화 환경

Private Cloud와 같은 환경을 구성하기 위해 VMWare SoftWare를 사용했습니다.
단일한 물리 HardWare System을 ESXi Hypervisor를 통해 Virtual Machine으로 분할하여 환경을 구성했습니다.

![](https://velog.velcdn.com/images/show7441/post/0cdd9031-b545-4807-85f6-8fe63a1fd3f0/image.png)

### vCenter REST API & vRealize Operations REST API 활용

![](https://velog.velcdn.com/images/show7441/post/0c0cfe16-bbbc-45c7-9b56-c19e20b3fb74/image.png)

vSphere 가상화 플랫폼을 활용하여, ESXi HyperVisor를 통해 VirtualMachine을 생성하였습니다.
Monitoring을 위해 vCenter API와 vRealize API를 사용하여 데이터를 통신하였습니다.
가상머신의 기본 설정정보등 정적정보는 vCenter API를 통해 데이터를 가져왔고,
Realtime Information은 vRealize Operations Solution을 사용한, vRealize API를 통해 데이터를 가져왔습니다.

## 3. 프로젝트 기능

1. Hypervisor Type 2 Host Environment

    - vCenter에 등록된 Host 구성 정보
    - Host에 Power State와 Name 확인

2. ESXi Host 위에 존재하는 VM List 확인

    - VM Power State, Name 확인
    - VM Create
    - VM Power ON/OFF

3. VM Create

    - Name, Guest OS, Memory, CPU Core 등 정보 입력을 통해 VM 생성

4. VM Static Information

    - Host, CPU Core, Memory, Disk File, Free Disk Resources, Network Name, Network State, GuestOS 등 Table 형태로 정보 확인
    - VM Edit(CPU Core, Memory)
    - VM Delete

5. VM Realtime CPU/Memory Usage

    - Hourly utilization rate
    - Average Usage

6. Send Mail
    - 송신: Server `.env` 등록된 E-Mail
    - 수신: Monitoring Web Server 가입 시 등록한 E-Mail
    - 사용 예시(CPU 사용량에 따른 부하/위험 정보)
