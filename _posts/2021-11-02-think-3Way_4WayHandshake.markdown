---  
layout: post  
title: "3Way-Handshake, 4Way-Handshake"  
subtitle: "TCP����� ���۰� ���� �ʿ��� ���"  
categories: think
tags: 
comments: true  
header-img:
---

## 3-Way, 4-Way Handshake
### 3-Way Handshake	
- TCP(Transmission Control Protocol) ����� �̿��� ������ ����(Connection Establishment) �����μ� ��Ȯ�� ������ ���� �� �� �ֵ��� �ϴ� ����̴�.
- TCP������ �ʱ�ȭ �� �� ����Ѵ�.
- Client�� Server�� ���¸� ǥ�� ��Ÿ���� �Ʒ��� ����.
	- SYN : SYnchronize Sequence Number
	- ACK : ACKnowledgements
	- TCB : Transmission Control Block
		- TCP ���� ó���� �ʿ��� ������ ����� �ִ�.
			- Connection state(LISTEN, ESTABLISHED, TIME-WAIT��)
			- Receive window, Congestion Window, Sequence number, ������ Ÿ�̸� ��

|Client State|Client|Server|Sever State|
|----|----|----|----|
|CLOSED|Wait For Server|Passive Open: Create TCB|CLOSED -> LISTEN|
|CLOSED -> SYN-SENT|Active Open: Create TCB, Send SYN|Wait For Client|LISTEN -> SYN-RECEIVED|
|SYN-SENT -> ESTABLISHED|Wait For ACK to SYN|Receive SYN, Send SYN+ACK|SYN-RECEIVED|
|ESTABLISHED|Receive SYN+ACK, Send ACK|Wait For ACK to SYN|SYN-RECEIVED -> ESTABLISHED|
|||Receive ACK|ESTABLISHED|

### 4-Way Handshake
- TCP�� ������ ������ ��(Connection Termination) ����Ѵ�.

|Client State|Client|Sever|Sever State|
|----|----|----|----|
|ESTABLISHED -> FIN-WAIT-1|Receive Close Signal From App, Send FIN|Normal Operation|ESTABLISHED|
|FIN-WAIT-1|Wait for ACK and FIN From Server|Receive FIN, Send ACK, Tell App To Close|ESTABLISHED -> CLOSE-WAIT|
|FIN-WAIT-1 -> FIN-WAIT-2|Receive ACK|(Wait for App)|CLOSE-WAIT -> LAST-ACK|
|FIN-WAIT-2|Wait for Server FIN|App is Ready To Close, Send FIN|LAST-ACK|
|FIN-WAIT-2 -> TIME-WAIT|Receive FIN, Send ACK|Wait for ACK to FIN|LAST-ACK -> CLOSED|
|TIME-WAIT|Wait For Double Maximum Segment Life(MSL) Time|Receive ACK|CLOSED|
|CLOSED|||CLOSED|
- Server������ Client���� ������ ��Ŷ�� FIN ��Ŷ���� �ʰ� ������ �����Ͱ� ���� �� ��Ȳ�� ����� Sever���� ���� �ð�(Default : 240 sec)���� �׿� ��Ŷ�� ��ٸ��� ������ ������. �̸� **TIME-WAIT**�̶� �Ѵ�. 