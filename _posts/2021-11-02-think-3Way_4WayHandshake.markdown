---  
layout: post  
title: "3Way-Handshake, 4Way-Handshake"  
subtitle: "TCP통신의 시작과 끝에 필요한 기술"  
categories: think
tags: 
comments: true  
header-img:
---

## 3-Way, 4-Way Handshake
### 3-Way Handshake	
- TCP(Transmission Control Protocol) 통신을 이용해 연결을 설정(Connection Establishment) 함으로서 정확한 전송을 보장 할 수 있도록 하는 방법이다.
- TCP연결을 초기화 할 때 사용한다.
- Client와 Server의 상태를 표로 나타내면 아래와 같다.
	- SYN : SYnchronize Sequence Number
	- ACK : ACKnowledgements
	- TCB : Transmission Control Block
		- TCP 연결 처리에 필요한 정보가 담겨저 있다.
			- Connection state(LISTEN, ESTABLISHED, TIME-WAIT등)
			- Receive window, Congestion Window, Sequence number, 재전송 타이머 등

|Client State|Client|Server|Sever State|
|----|----|----|----|
|CLOSED|Wait For Server|Passive Open: Create TCB|CLOSED -> LISTEN|
|CLOSED -> SYN-SENT|Active Open: Create TCB, Send SYN|Wait For Client|LISTEN -> SYN-RECEIVED|
|SYN-SENT -> ESTABLISHED|Wait For ACK to SYN|Receive SYN, Send SYN+ACK|SYN-RECEIVED|
|ESTABLISHED|Receive SYN+ACK, Send ACK|Wait For ACK to SYN|SYN-RECEIVED -> ESTABLISHED|
|||Receive ACK|ESTABLISHED|

### 4-Way Handshake
- TCP의 연결을 해제할 때(Connection Termination) 사용한다.

|Client State|Client|Sever|Sever State|
|----|----|----|----|
|ESTABLISHED -> FIN-WAIT-1|Receive Close Signal From App, Send FIN|Normal Operation|ESTABLISHED|
|FIN-WAIT-1|Wait for ACK and FIN From Server|Receive FIN, Send ACK, Tell App To Close|ESTABLISHED -> CLOSE-WAIT|
|FIN-WAIT-1 -> FIN-WAIT-2|Receive ACK|(Wait for App)|CLOSE-WAIT -> LAST-ACK|
|FIN-WAIT-2|Wait for Server FIN|App is Ready To Close, Send FIN|LAST-ACK|
|FIN-WAIT-2 -> TIME-WAIT|Receive FIN, Send ACK|Wait for ACK to FIN|LAST-ACK -> CLOSED|
|TIME-WAIT|Wait For Double Maximum Segment Life(MSL) Time|Receive ACK|CLOSED|
|CLOSED|||CLOSED|
- Server측에서 Client에게 전송한 패킷이 FIN 패킷보다 늦게 도착해 데이터가 유실 될 상황을 대비해 Sever측은 일정 시간(Default : 240 sec)동안 잉여 패킷을 기다리는 과정을 가진다. 이를 **TIME-WAIT**이라 한다. 