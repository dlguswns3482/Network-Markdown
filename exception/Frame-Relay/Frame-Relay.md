## Frame-Relay란 ?


* `Datalink 계층`에서 사용하는 WAN 전용 Protocol로써, 전용선에 비해서 구조가 간단하고 복잡하지도 않아서 구성이 쉽다. 

* 또한 전용선에 비해 높은 유연성과 보안성을 나타낸다.

* `Frmae-Relay`를 사용하면 가상 회선을 사용해서 여러 물리 포트 여러개를 하나의 회선만으로 대체해서 사용 가능하다. 

## Frmae-Relay 용어 정리

    (1) DLCI (Data-Link Connect Identifier)
    
    1-1. DLCI는 Frame-Relay에서 사용하는 연결주소이다. 하나의 식별명이라고 생각하면 된다.

    1-2. DLCI는 하나의 링크마다 각각 하나씩 주어진다. 따라서 하나의 인터페이스에는 여러개의 DLCI가 있을 수 있다. 왜냐하면 하나의 인터페이스 안에는 여러개의 논리적 링크를 구현할 수 있기 때문이다. 

    (2) LMI (Local Management Interface)

    2-1. DLCI와 함께 설정된 PVC의 정보를 알려줌으로써 인터페이스의 다양한 정보와 특정 상태들을 인접한 라우터에 알려주는 기능을 한다.

    2-2. Frame-Relay 네트워크에서 가상 회선의 상태를 쉽게 알 수 있게 해주는 기능을 제공한다.

    2-3. 이떄, LMI를 라우터와 동일하게 설정해줘야 한다.

## Frame-Relay 구성방식

    1. Encapsulation 방식

    Encapsulation 방식은 F-R망을 통과할떄 마치 캡슐로 덮어씌우는 것으로 Encapsulation 설정은 Interface에 해줘야 한다.

    명령 방식은  IETF와 CISCO 방식이 있다.

    #IETF

    router(config-if)#encapsulation frame-relay ietf

    #CISCO

    router(config-if)#encapsulation frame-relay


    2. LMI 방식

    F-R을 구성할때 원할한 설정을 위해서 서비스 공급자(ISP)한테 정확한 LMI값을 줘야한다. 하지만 요즘은 자동으로 LMI값을 인식하기 때문에 따로 명령어를 입력해줄 필요는 없다.


## Frame-Relay DLCI 연결

    # Inverse ARP
    
    DLCI는 F-R 환경에서 LMI와 Encapsulation만 맞으면 자동으로 연결이 되지만 명령어를 통해 수동으로 연결할 수 있다!!

    (1) Multi-to-Multi F-R

    router(config-subif)# framerelay map [protocol] [상대편 주소] [DLCI NUM] broadcast

    Inverse ARP 사용한다면 이 명령어를 절대 사용하면 안된다. 

    Inverse ARP 수동 설정이나 실제 존재하는 서브 인터페이스에서 구성할떄 이 명령어가 사용된다

    (2) POINT-To-POINT F-R

    router(config-subif)# framerelay interface-dlci [DLCI-NUM]

    Multi-to-Multi F-R 환경에서는 같은 망이였다고 하면 P-T-P 에서는 다른 네트워크를 연결해주는 F-R 설정이다.


