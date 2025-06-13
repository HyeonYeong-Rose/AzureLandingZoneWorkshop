![네트워크 구성도](https://github.com/HyeonYeong-Rose/AzureLandingZoneWorkshop/blob/7538415de77a46239ade0d6d41e5ff2cd64f0acd/images/NW%20setup.png)
## 리소스 그룹 생성

1. 리소스 그룹 메뉴로 이동합니다.
2. 왼쪽 상단 만들기 버튼을 클릭합니다.
3. 리소스 그룹 이름에 `azure-intermediate-worshop-rg` 를 입력하고 영역에 `(Asia Pacific) Korea Central`을 선택합니다.
4. 검토+만들기 버튼을 클릭 후, 만들기 버튼을 클릭합니다.

## 가상 WAN 생성

1. 가상 WAN 메뉴로 이동합니다.
2. 왼쪽 상단 만들기 버튼을 클릭합니다.
3. 다음과 같이 설정 후, 검토+만들기 버튼을 클릭하고 만들기 버튼을 클릭합니다.
    - 구독 : 생성한 구독 선택
    - 리소스 그룹 : azure-intermediate-worshop-rg
    - 지역 : Korea Central
    - 이름 : korea-virtual-wan
    - 유형 : 표준

### 허브 생성

1. 가상WAN 화면에서 생성한 `korea-virtual-wan`을 선택합니다.
2. 왼쪽 메뉴에서 허브를 선택하고 상단에 새 허브 버튼을 클릭합니다.
3. 다음과 같이 설정 후 검토 만들기 버튼을 클릭합니다.
    - 구독 : 생성한 구독 선택
    - 지역 : Korea Central
    - 이름 : vhub
    - 허브 프라이빗 주소 공간 : 10.0.0.0/16
    - 가상 허브 용량 : 2 라우팅 인프라 단위, 3 Gbps 라우터, 2000개 VM 지원
    - 허브 라우팅 기본 설정 : ExpressRoute
4. 만들기 버튼을 클릭합니다.

> 리소스가 생성되는 동안 화면을 이동하여도 리소스는 계속해서 배포됩니다.

## 가상 네트워크 생성

### 허브 네트워크 생성

1. 가상 네트워크 메뉴로 이동합니다.
2. 왼쪽 상단 만들기 버튼을 클릭합니다.
3. 다음과 같이 설정 후 다음 버튼을 2번 클릭합니다.
    - 구독 : 생성한 구독 선택
    - 리소스 그룹 : azure-intermediate-worshop-rg
    - 가상 네트워크 이름 : hub-vnet
    - 지역 : (Asia Pacific) Korea Central
4. IP 주소 탭에서 CIDR 공간을 지정합니다.
    - 가상 네트워크 CIDR : 10.1.0.0/16
    - default 서브넷의 연필 모양 아이콘을 클릭하여 서브넷을 수정합니다.
        - 서브넷 이름 : app-subnet
5. 검토+만들기 버튼을 클릭하고 만들기 버튼을 클릭합니다.

### 스포크 네트워크 생성

1. 다음과 같이 설정합니다.
    - 가상 네트워크 이름 : spoke-vnet
    - 가상 네트워크 CIDR : 10.2.0.0/16
    - 서브넷 이름 : app-subnet
2. 나머지는 위와 동일하게 가상 네트워크를 생성합니다.
