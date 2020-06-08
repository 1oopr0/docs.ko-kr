---
title: '방법: 네트워크 프로세스 간 통신에 명명된 파이프 사용'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- message-based communication [.NET Framework], named pipes
- named pipes [.NET Framework]
- pipes [.NET Framework]
- multiple connections via named pipes
- network communications [.NET Framework], named pipes
- impersonation [.NET Framework], named pipes
- full duplex communication [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
ms.openlocfilehash: bebfd136245fd7b577ffcd71954f46ca82bfc72d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291749"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a><span data-ttu-id="a1a59-102">방법: 네트워크 프로세스 간 통신에 명명된 파이프 사용</span><span class="sxs-lookup"><span data-stu-id="a1a59-102">How to: Use Named Pipes for Network Interprocess Communication</span></span>
<span data-ttu-id="a1a59-103">명명된 파이프는 파이프 서버와 하나 이상의 파이프 클라이언트 간의 프로세스 간 통신을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-103">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="a1a59-104">로컬 컴퓨터에서 프로세스 간 통신을 제공하는 익명 파이프보다 많은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-104">They offer more functionality than anonymous pipes, which provide interprocess communication on a local computer.</span></span> <span data-ttu-id="a1a59-105">명명된 파이프는 네트워크 및 다중 서버 인스턴스를 통한 양방향 통신, 메시지 기반 통신 및 연결 프로세스가 원격 서버에서 고유한 권한 집합을 사용할 수 있는 클라이언트 가장을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-105">Named pipes support full duplex communication over a network and multiple server instances, message-based communication, and client impersonation, which enables connecting processes to use their own set of permissions on remote servers.</span></span>  
  
 <span data-ttu-id="a1a59-106">명명된 파이프를 구현하려면, <xref:System.IO.Pipes.NamedPipeServerStream> 및 <xref:System.IO.Pipes.NamedPipeClientStream> 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-106">To implement name pipes, use the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1a59-107">예제</span><span class="sxs-lookup"><span data-stu-id="a1a59-107">Example</span></span>  
 <span data-ttu-id="a1a59-108">다음 예제는 <xref:System.IO.Pipes.NamedPipeServerStream> 클래스를 사용하여 명명된 파이프를 생성하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-108">The following example demonstrates how to create a named pipe by using the <xref:System.IO.Pipes.NamedPipeServerStream> class.</span></span> <span data-ttu-id="a1a59-109">이 예제에서 서버 프로세스는 네 개의 스레드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-109">In this example, the server process creates four threads.</span></span> <span data-ttu-id="a1a59-110">각 스레드는 클라이언트 연결을 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-110">Each thread can accept a client connection.</span></span> <span data-ttu-id="a1a59-111">연결된 클라이언트 프로세스는 서버에 파일 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-111">The connected client process then supplies the server with a file name.</span></span> <span data-ttu-id="a1a59-112">클라이언트에 충분한 권한이 있는 경우 서버 프로세스는 파일을 열고 콘텐츠를 클라이언트에 다시 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-112">If the client has sufficient permissions, the server process opens the file and sends its contents back to the client.</span></span>  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="a1a59-113">예제</span><span class="sxs-lookup"><span data-stu-id="a1a59-113">Example</span></span>  
 <span data-ttu-id="a1a59-114">다음 예제는 <xref:System.IO.Pipes.NamedPipeClientStream> 클래스를 사용하는 클라이언트 프로세스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-114">The following example shows the client process, which uses the <xref:System.IO.Pipes.NamedPipeClientStream> class.</span></span> <span data-ttu-id="a1a59-115">클라이언트는 서버 프로세스에 연결하여 서버에 파일 이름을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-115">The client connects to the server process and sends a file name to the server.</span></span> <span data-ttu-id="a1a59-116">이 예제에서는 가장을 사용하므로 클라이언트 애플리케이션을 실행하는 ID에는 파일에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-116">The example uses impersonation, so the identity that is running the client application must have permission to access the file.</span></span> <span data-ttu-id="a1a59-117">그런 다음, 서버는 파일의 내용을 클라이언트로 다시 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-117">The server then sends the contents of the file back to the client.</span></span> <span data-ttu-id="a1a59-118">그러면 파일의 내용이 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-118">The file contents are then displayed to the console.</span></span>  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a1a59-119">강력한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="a1a59-119">Robust Programming</span></span>  
 <span data-ttu-id="a1a59-120">이 예제의 클라이언트 및 서버 프로세스는 동일한 컴퓨터에서 실행되므로 <xref:System.IO.Pipes.NamedPipeClientStream> 개체에 제공된 서버 이름은 `"."`입니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-120">The client and server processes in this example are intended to run on the same computer, so the server name provided to the <xref:System.IO.Pipes.NamedPipeClientStream> object is `"."`.</span></span> <span data-ttu-id="a1a59-121">클라이언트 및 서버 프로세스가 별도의 컴퓨터에 있는 경우 `"."`는 서버 프로세스를 실행하는 컴퓨터의 네트워크 이름으로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1a59-121">If the client and server processes were on separate computers, `"."` would be replaced with the network name of the computer that runs the server process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1a59-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1a59-122">See also</span></span>

- <xref:System.Security.Principal.TokenImpersonationLevel>
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>
- [<span data-ttu-id="a1a59-123">파이프</span><span class="sxs-lookup"><span data-stu-id="a1a59-123">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="a1a59-124">방법: 로컬 프로세스 간 통신에 익명 파이프 사용</span><span class="sxs-lookup"><span data-stu-id="a1a59-124">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
