## 소켓프로그래밍
- [x] 소켓은 IP + 포트를 합친 것
  
## UDP와 TCP  
- [x] UDP
  - 전체의 사서함(포트번호)을 마련한다. 순서가 상관없고 시간이 빠르다.
- [x] TCP
  - 개개인의 사서함(포트번호)을 마련한다. 그래서 공간이 필요하고 순서대로 배분을 하기 때문에 시간이 오래 걸린다.
  - 몇 개의 클라이언트가 요청할지 모르기 때문에 서버는 미리 사서함을 만들지 않는다.
  - 클라이언트가 없으면 서버는 Listen Socket(=Accept Socket = Server Socket)를 만들고 대기한다.
    - svrSock = new ServerSokcet(10000); 10000번의 포트를 만들고 대기한다.
  - 사서함을 만들고 편지 오기를 기다리는데 오자마자 낚아채야 한다.
    - svrSock.accept(); 
    
## 클라이언트와 서버 간 데이터 송수신하기
- [x] OutputStream, InputStream, PrintStream을 활용한다.