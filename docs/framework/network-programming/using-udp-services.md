---
title: UDP 서비스 사용
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- protocols, UDP
- network resources, UDP
- requesting data from Internet, UDP
- UDP
- receiving data, UDP
- Internet, UDP
- broadcasting messages to multiple addresses
- data requests, UDP
- UdpClient class, about UdpClient class
- sending data, UDP
- application protocols, UDP
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
ms.openlocfilehash: 5ff40e8759b1732d4ad228b1414f96f9c37e5ac5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209775"
---
# <a name="use-udp-services"></a><span data-ttu-id="eb282-102">UDP 서비스 사용</span><span class="sxs-lookup"><span data-stu-id="eb282-102">Use UDP services</span></span>

<span data-ttu-id="eb282-103"><xref:System.Net.Sockets.UdpClient> 클래스는 UDP를 사용하여 네트워크 서비스와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-103">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="eb282-104"><xref:System.Net.Sockets.UdpClient> 클래스의 속성 및 메서드는 UDP를 사용하여 데이터를 요청 및 수신하는 <xref:System.Net.Sockets.Socket>을 만들기 위한 세부 정보를 추상화합니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-104">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>

<span data-ttu-id="eb282-105">UDP(User Datagram Protocol)는 원격 호스트에 데이터를 전달하기 위해 최상의 노력을 하는 간단한 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-105">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="eb282-106">그러나 UDP 프로토콜은 연결 없는 프로토콜이기 때문에 원격 엔드포인트에 전송된 UDP 데이터그램은 도착한다고 보장되지 않으며 전송된 동일한 순서로 도착한다고 보장되지도 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-106">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="eb282-107">UDP를 사용하는 애플리케이션은 누락, 중복 및 순서가 잘못된 데이터그램을 처리하도록 준비해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-107">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>

<span data-ttu-id="eb282-108">UDP를 사용하여 데이터그램을 보내려면 필요한 서비스를 호스트하는 네트워크 디바이스의 네트워크 주소와 서비스가 통신에 사용하는 UDP 포트 번호를 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-108">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="eb282-109">IANA(Internet Assigned Numbers Authority)는 공통 서비스의 포트 번호를 정의합니다([서비스 이름 및 전송 프로토콜 포트 번호 레지스트리](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml) 참조).</span><span class="sxs-lookup"><span data-stu-id="eb282-109">The Internet Assigned Numbers Authority (IANA) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="eb282-110">IANA 목록에 없는 서비스에는 1,024~65,535 범위의 포트 번호를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-110">Services not on the IANA list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="eb282-111">특수 네트워크 주소는 IP 기반 네트워크에서 UDP 브로드캐스트 메시지를 지원하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-111">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="eb282-112">예를 들어 다음 설명에서는 인터넷에서 사용되는 IP 버전 4 주소 패밀리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-112">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>

<span data-ttu-id="eb282-113">IP 버전 4 주소는 32비트를 사용하여 네트워크 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-113">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="eb282-114">네트워크 마스크 255.255.255.0을 사용하는 클래스 C 주소의 경우 이러한 비트가 4개의 8진수로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-114">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="eb282-115">10진수로 표현된 경우 4개의 8진수는 192.168.100.2 같은 친숙한 점 표기법을 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-115">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="eb282-116">처음 두 개의 8진수(이 예제의 192.168)는 네트워크 번호를 형성하고, 세 번째 8진수(100)는 서브넷을 정의하고, 최종 8진수(2)는 호스트 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-116">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>

<span data-ttu-id="eb282-117">IP 주소의 모든 비트를 1 또는 255.255.255.255로 설정하면 제한된 브로드캐스트 주소가 형성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-117">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="eb282-118">이 주소에 UDP 데이터그램을 보내면 로컬 네트워크 세그먼트의 모든 호스트에 메시지가 배달됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-118">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="eb282-119">라우터는 이 주소로 전송된 메시지를 전달하지 않으므로 네트워크 세그먼트의 호스트만 브로드캐스트 메시지를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-119">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>

<span data-ttu-id="eb282-120">호스트 식별자의 모든 비트를 설정하여 브로드캐스트를 네트워크의 특정 부분으로 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-120">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="eb282-121">예를 들어 192.168.1로 시작하는 IP 주소로 식별되는 네트워크의 모든 호스트에 브로드캐스트를 보내려면 192.168.1.255 주소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-121">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>

<span data-ttu-id="eb282-122">다음 코드 예제에서는 <xref:System.Net.Sockets.UdpClient>를 사용하여 포트 11,000에서 UDP 데이터 그램을 수신 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-122">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams on port 11,000.</span></span> <span data-ttu-id="eb282-123">클라이언트는 메시지 문자열을 수신하고 메시지를 콘솔에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-123">The client receives a message string and writes the message to the console.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class UDPListener
   Private Const listenPort As Integer = 11000

   Private Shared Sub StartListener()
      Dim listener As New UdpClient(listenPort)
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)
      Try
         While True
            Console.WriteLine("Waiting for broadcast")
            Dim bytes As Byte() = listener.Receive(groupEP)
            Console.WriteLine("Received broadcast from {0} :", groupEP)
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytes.Length))
         End While
      Catch e As SocketException
         Console.WriteLine(e)
      Finally
         listener.Close()
      End Try
   End Sub 'StartListener

   Public Shared Sub Main()
      StartListener()
   End Sub 'Main
End Class 'UDPListener
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

public class UDPListener
{
    private const int listenPort = 11000;

    private static void StartListener()
    {
        UdpClient listener = new UdpClient(listenPort);
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any, listenPort);

        try
        {
            while (true)
            {
                Console.WriteLine("Waiting for broadcast");
                byte[] bytes = listener.Receive(ref groupEP);

                Console.WriteLine($"Received broadcast from {groupEP} :");
                Console.WriteLine($" {Encoding.ASCII.GetString(bytes, 0, bytes.Length)}");
            }
        }
        catch (SocketException e)
        {
            Console.WriteLine(e);
        }
        finally
        {
            listener.Close();
        }
    }

    public static void Main()
    {
        StartListener();
    }
}
```

<span data-ttu-id="eb282-124">다음 코드 예제에서는 <xref:System.Net.Sockets.Socket>를 사용하여 포트 11,000을 통해 리디렉션된 브로드캐스트 주소 192.168.1.255로 UDP 데이터그램을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-124">The following code example uses a <xref:System.Net.Sockets.Socket> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="eb282-125">클라이언트는 명령줄에 지정된 메시지 문자열을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="eb282-125">The client sends the message string specified on the command line.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class Program
    Public Shared Sub Main(args() As [String])
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp)
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))
      Dim ep As New IPEndPoint(broadcast, 11000)
      s.SendTo(sendbuf, ep)
      Console.WriteLine("Message sent to the broadcast address")
   End Sub 'Main
End Class
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

class Program
{
    static void Main(string[] args)
    {
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp);

        IPAddress broadcast = IPAddress.Parse("192.168.1.255");

        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);

        s.SendTo(sendbuf, ep);

        Console.WriteLine("Message sent to the broadcast address");
    }
}
```

## <a name="see-also"></a><span data-ttu-id="eb282-126">참조</span><span class="sxs-lookup"><span data-stu-id="eb282-126">See also</span></span>

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
