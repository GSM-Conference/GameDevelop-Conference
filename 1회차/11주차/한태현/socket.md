# C# 소켓 프로그래밍
멀티플레이 게임에서 클라이언트와 서버는 소켓으로 구현되고 있다.

## 소켓
네트워크에서 데이터를 송수신 할 수 있게 하는 창구같은 역할을 하는 규격이다. 주로 전송계층(TCP, UDP)에서 동작하는 소켓을 주로 사용하게 된다. 소켓의 근본은 파일이기 때문에 읽기/쓰기 작업을 할 때 동작이 비슷하다.

## 소켓 프로그램 실행 흐름
- 클라이언트
    1. 소켓 생성
    2. connect - 서버와 연결한다. UDP도 가능
    3. send, receive
    4. 소켓 닫기
- 서버
    1. 소켓 생성
    2. 주소 bind - 소켓에 IP주소와 포트 번호를 등록
    3. listen - 연결대기 상태. UDP에서 사용 안함
    4. accept - 클라이언트 연결대기. UDP에서 사용 안함
    5. send, receive
    6. 소켓 닫기

## 간단한 통신

### 클라이언트
```CSharp
public static void Main(string[] args)
{
    Socket sock = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);
    IPEndPoint ep = new IPEndPoint(IPAddress.Loopback, 8888); // 주소 : 나 자신, 포트 : 임의로 정한 수

    sock.Connect(ep); // 서버 주소로 연결
    Console.WriteLine("Connected to server.");

    byte[] buffer = new byte[1024];
    sock.Receive(buffer); // 수신 대기

    Console.WriteLine(buffer); // 받은 문자열 출력하기
}
```
### 서버
```CSharp
public static void Main(string[] args)
{
    Socket listenSock = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);
    IPEndPoint ep = new IPEndPoint(IPAddress.Loopback, 8888); // 주소 : 나 자신, 포트 : 임의로 정한 수
    listenSock.Bind(ep); // 소켓에 주소 등록
    listenSock.Listen(64); // 접속 대기열의 길이

    string sendData = "Hello, World!"; // 접속한 클라이언트에게 보낼 문자열
    while (true)
    {
        Socket clientSock = listenSock.Accept(); // 연결 대기
        Console.WriteLine("Client Connected");

        clientSock.Send(Encoding.UTF8.GetBytes(sendData));
    }
}
```