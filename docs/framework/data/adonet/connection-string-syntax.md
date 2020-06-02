---
title: 연결 문자열 구문
description: ADO.NET의 연결 문자열 구문에 대해 알아봅니다. 각 공급자에 대 한 구문은 ConnectionString 속성에 설명 되어 있습니다.
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: bb29365a4729e731ddeffc7cfa61e379c3144a46
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287053"
---
# <a name="connection-string-syntax"></a><span data-ttu-id="ce0db-104">연결 문자열 구문</span><span class="sxs-lookup"><span data-stu-id="ce0db-104">Connection String Syntax</span></span>
<span data-ttu-id="ce0db-105">각 .NET Framework 데이터 공급자에는 `Connection`뿐 아니라 공급자별 <xref:System.Data.Common.DbConnection> 속성에서 상속되는 <xref:System.Data.Common.DbConnection.ConnectionString%2A> 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-105">Each .NET Framework data provider has a `Connection` object that inherits from <xref:System.Data.Common.DbConnection> as well as a provider-specific <xref:System.Data.Common.DbConnection.ConnectionString%2A> property.</span></span> <span data-ttu-id="ce0db-106">각 공급자의 특정 연결 문자열 구문은 해당 `ConnectionString` 속성에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-106">The specific connection string syntax for each provider is documented in its `ConnectionString` property.</span></span> <span data-ttu-id="ce0db-107">다음 표에서는 .NET Framework에 포함되어 있는 네 개의 데이터 공급자를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-107">The following table lists the four data providers that are included in the .NET Framework.</span></span>  
  
|<span data-ttu-id="ce0db-108">.NET Framework 데이터 공급자(.NET Framework data provider)</span><span class="sxs-lookup"><span data-stu-id="ce0db-108">.NET Framework data provider</span></span>|<span data-ttu-id="ce0db-109">Description</span><span class="sxs-lookup"><span data-stu-id="ce0db-109">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|<span data-ttu-id="ce0db-110">Microsoft SQL Server에 대한 데이터 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-110">Provides data access for Microsoft SQL Server.</span></span> <span data-ttu-id="ce0db-111">연결 문자열 구문에 대한 자세한 내용은 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0db-111">For more information on connection string syntax, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.OleDb>|<span data-ttu-id="ce0db-112">OLE DB를 사용하여 노출되는 데이터 소스에 대한 데이터 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-112">Provides data access for data sources exposed using OLE DB.</span></span> <span data-ttu-id="ce0db-113">연결 문자열 구문에 대한 자세한 내용은 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0db-113">For more information on connection string syntax, see <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.Odbc>|<span data-ttu-id="ce0db-114">ODBC를 사용하여 노출되는 데이터 소스에 대한 데이터 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-114">Provides data access for data sources exposed using ODBC.</span></span> <span data-ttu-id="ce0db-115">연결 문자열 구문에 대한 자세한 내용은 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0db-115">For more information on connection string syntax, see <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.OracleClient>|<span data-ttu-id="ce0db-116">Oracle 버전 8.1.7 이상에 대한 데이터 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-116">Provides data access for Oracle version 8.1.7 or later.</span></span> <span data-ttu-id="ce0db-117">연결 문자열 구문에 대한 자세한 내용은 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0db-117">For more information on connection string syntax, see <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.</span></span>|  
  
## <a name="connection-string-builders"></a><span data-ttu-id="ce0db-118">연결 문자열 작성기</span><span class="sxs-lookup"><span data-stu-id="ce0db-118">Connection String Builders</span></span>  
 <span data-ttu-id="ce0db-119">ADO.NET 2.0에는 .NET Framework 데이터 공급자에 사용할 수 있는 다음과 같은 연결 문자열 작성기가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-119">ADO.NET 2.0 introduced the following connection string builders for the .NET Framework data providers.</span></span>  
  
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
- <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
- <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
- <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 <span data-ttu-id="ce0db-120">연결 문자열 작성기를 사용하면 구문이 올바른 연결 문자열을 런타임에 작성할 수 있기 때문에 코드에 연결 문자열 값을 직접 연결하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-120">The connection string builders allow you to construct syntactically valid connection strings at run time, so you do not have to manually concatenate connection string values in your code.</span></span> <span data-ttu-id="ce0db-121">자세한 내용은 [연결 문자열 작성기](connection-string-builders.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0db-121">For more information, see [Connection String Builders](connection-string-builders.md).</span></span>  

## <a name="windows-authentication"></a><span data-ttu-id="ce0db-122">Windows 인증</span><span class="sxs-lookup"><span data-stu-id="ce0db-122">Windows Authentication</span></span>  
 <span data-ttu-id="ce0db-123">Windows 인증 ( *통합 보안*이 라고도 함)을 사용 하 여이를 지 원하는 데이터 원본에 연결 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-123">We recommend using Windows Authentication (sometimes referred to as *integrated security*) to connect to data sources that support it.</span></span> <span data-ttu-id="ce0db-124">연결 문자열에 사용되는 구문은 공급자별로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-124">The syntax employed in the connection string varies by provider.</span></span> <span data-ttu-id="ce0db-125">다음 표에서는 .NET Framework 데이터 공급자에서 사용되는 Windows 인증 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-125">The following table shows the Windows Authentication syntax used with the .NET Framework data providers.</span></span>  
  
|<span data-ttu-id="ce0db-126">공급자</span><span class="sxs-lookup"><span data-stu-id="ce0db-126">Provider</span></span>|<span data-ttu-id="ce0db-127">구문</span><span class="sxs-lookup"><span data-stu-id="ce0db-127">Syntax</span></span>|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
> <span data-ttu-id="ce0db-128">`Integrated Security=true` 공급자와 함께 사용하는 경우 `OleDb`이면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-128">`Integrated Security=true` throws an exception when used with the `OleDb` provider.</span></span>  
  
## <a name="sqlclient-connection-strings"></a><span data-ttu-id="ce0db-129">SqlClient 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="ce0db-129">SqlClient Connection Strings</span></span>  
<span data-ttu-id="ce0db-130"><xref:System.Data.SqlClient.SqlConnection> 연결 문자열의 구문은 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 속성에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-130">The syntax for a <xref:System.Data.SqlClient.SqlConnection> connection string is documented in the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ce0db-131"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 속성을 사용하면 SQL Server 데이터베이스에 대한 연결 문자열을 가져오거나 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-131">You can use the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property to get or set a connection string for a SQL Server database.</span></span> <span data-ttu-id="ce0db-132">이전 버전의 SQL Server에 연결해야 하는 경우에는 .NET Framework Data Provider for OleDb(<xref:System.Data.OleDb>)를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-132">If you need to connect to an earlier version of SQL Server, you must use the .NET Framework Data Provider for OleDb (<xref:System.Data.OleDb>).</span></span> <span data-ttu-id="ce0db-133">대부분의 연결 문자열 키워드는 또한 <xref:System.Data.SqlClient.SqlConnectionStringBuilder>의 속성에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-133">Most connection string keywords also map to properties in the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="ce0db-134">키워드의 기본 설정은 `Persist Security Info` `false` 입니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-134">The default setting for the `Persist Security Info` keyword is `false`.</span></span> <span data-ttu-id="ce0db-135">이 키워드를 `true` 또는 `yes`로 설정하면 연결이 열린 다음 연결에서 사용자 ID 및 암호와 같은 보안 관련 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-135">Setting it to `true` or `yes` allows security-sensitive information, including the user ID and password, to be obtained from the connection after the connection has been opened.</span></span> <span data-ttu-id="ce0db-136">`Persist Security Info`을로 설정 하 여 `false` 신뢰할 수 없는 소스가 중요 한 연결 문자열 정보에 액세스할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-136">Keep `Persist Security Info` set to `false` to ensure that an untrusted source does not have access to sensitive connection string information.</span></span>  

### <a name="windows-authentication-with-sqlclient"></a><span data-ttu-id="ce0db-137">SqlClient를 사용 하는 Windows 인증</span><span class="sxs-lookup"><span data-stu-id="ce0db-137">Windows authentication with SqlClient</span></span>
 <span data-ttu-id="ce0db-138">다음의 각 구문은 Windows 인증을 사용 하 여 로컬 서버의 **AdventureWorks** 데이터베이스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-138">Each of the following forms of syntax uses Windows Authentication to connect to the **AdventureWorks** database on a local server.</span></span>  
  
```csharp  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a><span data-ttu-id="ce0db-139">SqlClient를 사용 하 여 SQL Server 인증</span><span class="sxs-lookup"><span data-stu-id="ce0db-139">SQL Server authentication with SqlClient</span></span>
 <span data-ttu-id="ce0db-140">SQL Server에 연결하기 위해 기본적으로 Windows 인증이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-140">Windows Authentication is preferred for connecting to SQL Server.</span></span> <span data-ttu-id="ce0db-141">그러나 SQL Server 인증이 필요한 경우 다음 구문을 사용하여 사용자 이름과 암호를 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0db-141">However, if SQL Server Authentication is required, use the following syntax to specify a user name and password.</span></span> <span data-ttu-id="ce0db-142">이 예제에서 유효한 사용자 이름과 암호를 나타내기 위해 별표를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-142">In this example, asterisks are used to represent a valid user name and password.</span></span>  
  
```csharp  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

<span data-ttu-id="ce0db-143">Azure SQL Database 또는 Azure SQL Data Warehouse에 연결 하 고 형식으로 로그인을 제공 하는 경우 `user@servername` `servername` 로그인의 값이에 제공 된 값과 일치 하는지 확인 합니다 `Server=` .</span><span class="sxs-lookup"><span data-stu-id="ce0db-143">When you connect to Azure SQL Database or to Azure SQL Data Warehouse and provide a login in the format `user@servername`, make sure that the `servername` value in the login matches the value provided for `Server=`.</span></span>

> [!NOTE]
> <span data-ttu-id="ce0db-144">Windows 인증은 SQL Server 로그인에 우선적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-144">Windows authentication takes precedence over SQL Server logins.</span></span> <span data-ttu-id="ce0db-145">Integrated Security=true와 사용자 이름 및 암호를 모두 지정하는 경우 사용자 이름과 암호는 무시되고 Windows 인증이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-145">If you specify both Integrated Security=true as well as a user name and password, the user name and password will be ignored and Windows authentication will be used.</span></span>  

### <a name="connect-to-a-named-instance-of-sql-server"></a><span data-ttu-id="ce0db-146">SQL Server의 명명 된 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="ce0db-146">Connect to a named instance of SQL Server</span></span>
<span data-ttu-id="ce0db-147">SQL Server의 명명 된 인스턴스에 연결 하려면 *Server name\instance name* 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-147">To connect to a named instance of SQL Server, use the *server name\instance name* syntax.</span></span>  
  
```csharp  
"Data Source=MySqlServer\MSSQL1;"  
```  

<span data-ttu-id="ce0db-148">연결 문자열을 작성할 때 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>의 `SqlConnectionStringBuilder` 속성을 인스턴스 이름으로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-148">You can also set the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> property of the `SqlConnectionStringBuilder` to the instance name when building a connection string.</span></span> <span data-ttu-id="ce0db-149"><xref:System.Data.SqlClient.SqlConnection.DataSource%2A> 개체의 <xref:System.Data.SqlClient.SqlConnection> 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-149">The <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> property of a <xref:System.Data.SqlClient.SqlConnection> object is read-only.</span></span>  
  
### <a name="type-system-version-changes"></a><span data-ttu-id="ce0db-150">Type System Version 변경 내용</span><span class="sxs-lookup"><span data-stu-id="ce0db-150">Type System Version Changes</span></span>  
 <span data-ttu-id="ce0db-151">`Type System Version`의 키워드는 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> SQL Server 형식의 클라이언트 쪽 표현을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-151">The `Type System Version` keyword in a <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> specifies the client-side representation of SQL Server types.</span></span> <span data-ttu-id="ce0db-152"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 키워드에 대한 자세한 내용은 `Type System Version`을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0db-152">See <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> for more information about the `Type System Version` keyword.</span></span>  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a><span data-ttu-id="ce0db-153">SQL Server Express 사용자 인스턴스에 연결 및 추가</span><span class="sxs-lookup"><span data-stu-id="ce0db-153">Connecting and Attaching to SQL Server Express User Instances</span></span>  
 <span data-ttu-id="ce0db-154">사용자 인스턴스는 SQL Server Express의 한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-154">User instances are a feature in SQL Server Express.</span></span> <span data-ttu-id="ce0db-155">최소 권한의 로컬 Windows 계정에서 실행 중인 사용자가 관리자 권한 없이 SQL Server 데이터베이스에 연결하여 SQL Server 데이터베이스를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-155">They allow a user running on a least-privileged local Windows account to attach and run a SQL Server database without requiring administrative privileges.</span></span> <span data-ttu-id="ce0db-156">사용자 인스턴스는 서비스가 아닌 사용자의 Windows 자격 증명을 사용하여 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-156">A user instance executes with the user's Windows credentials, not as a service.</span></span>  
  
 <span data-ttu-id="ce0db-157">사용자 인스턴스 사용에 대 한 자세한 내용은 [SQL Server Express 사용자 인스턴스](./sql/sql-server-express-user-instances.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0db-157">For more information on working with user instances, see [SQL Server Express User Instances](./sql/sql-server-express-user-instances.md).</span></span>  
  
## <a name="using-trustservercertificate"></a><span data-ttu-id="ce0db-158">TrustServerCertificate 사용</span><span class="sxs-lookup"><span data-stu-id="ce0db-158">Using TrustServerCertificate</span></span>  
 <span data-ttu-id="ce0db-159">`TrustServerCertificate`키워드는 유효한 인증서를 사용 하 여 SQL Server 인스턴스에 연결 하는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-159">The `TrustServerCertificate` keyword is valid only when connecting to a SQL Server instance with a valid certificate.</span></span> <span data-ttu-id="ce0db-160">`TrustServerCertificate`이 `true`로 설정된 경우 전송 계층에서는 SSL을 사용하여 채널을 암호화하고 인증서 체인을 무시하여 신뢰의 유효성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-160">When `TrustServerCertificate` is set to `true`, the transport layer will use SSL to encrypt the channel and bypass walking the certificate chain to validate trust.</span></span>  
  
```csharp  
"TrustServerCertificate=true;"
```  
  
> [!NOTE]
> <span data-ttu-id="ce0db-161">`TrustServerCertificate`이 `true`로 설정되고 암호화가 설정되면 연결 문자열에서 `Encrypt`가 `false`로 설정된 경우에도 서버에 지정된 암호화 수준이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-161">If `TrustServerCertificate` is set to `true` and encryption is turned on, the encryption level specified on the server will be used even if `Encrypt` is set to `false` in the connection string.</span></span> <span data-ttu-id="ce0db-162">그렇지 않으면 연결 문자열이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-162">The connection will fail otherwise.</span></span>  
  
### <a name="enabling-encryption"></a><span data-ttu-id="ce0db-163">암호화 설정</span><span class="sxs-lookup"><span data-stu-id="ce0db-163">Enabling Encryption</span></span>  
 <span data-ttu-id="ce0db-164">인증서가 서버에서 프로 비전 되지 않은 경우 암호화를 사용 하도록 설정 하려면 SQL Server 구성 관리자에서 **프로토콜 암호화 강제** 사용 및 **서버 인증서 신뢰** 옵션을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-164">To enable encryption when a certificate has not been provisioned on the server, the **Force Protocol Encryption** and the **Trust Server Certificate** options must be set in SQL Server Configuration Manager.</span></span> <span data-ttu-id="ce0db-165">이 경우 확인할 수 있는 인증서가 서버에 제공되지 않으면 유효성 검사 없이 자체 서명된 서버 인증서가 암호화에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-165">In this case, encryption will use a self-signed server certificate without validation if no verifiable certificate has been provisioned on the server.</span></span>  
  
 <span data-ttu-id="ce0db-166">애플리케이션 설정에서 SQL Server에 구성된 보안 수준을 낮출 수는 없지만 선택적으로 높일 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-166">Application settings cannot reduce the level of security configured in SQL Server, but can optionally strengthen it.</span></span> <span data-ttu-id="ce0db-167">응용 프로그램은 및 키워드를로 설정 하 여 암호화를 요청할 수 있으므로 `TrustServerCertificate` `Encrypt` `true` 서버 인증서가 프로 비전 되지 않은 경우에도 암호화가 적용 되 고 클라이언트에 대해 **프로토콜 암호화** 가 구성 되지 않은 경우에도 암호화가 수행 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-167">An application can request encryption by setting the `TrustServerCertificate` and `Encrypt` keywords to `true`, guaranteeing that encryption takes place even when a server certificate has not been provisioned and **Force Protocol Encryption** has not been configured for the client.</span></span> <span data-ttu-id="ce0db-168">그러나 `TrustServerCertificate`이 클라이언트 구성에서 설정되지 않은 경우 서버 인증서를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-168">However, if `TrustServerCertificate` is not enabled in the client configuration, a provisioned server certificate is still required.</span></span>  
  
 <span data-ttu-id="ce0db-169">다음 표에는 가능한 모든 경우가 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-169">The following table describes all cases.</span></span>  
  
|<span data-ttu-id="ce0db-170">프로토콜 암호화 강제 사용 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="ce0db-170">Force Protocol Encryption client setting</span></span>|<span data-ttu-id="ce0db-171">서버 인증서 신뢰 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="ce0db-171">Trust Server Certificate client setting</span></span>|<span data-ttu-id="ce0db-172">데이터 연결 문자열/특성에 대해 암호화 및 암호화 사용</span><span class="sxs-lookup"><span data-stu-id="ce0db-172">Encrypt/Use Encryption for Data connection string/attribute</span></span>|<span data-ttu-id="ce0db-173">서버 인증서 신뢰 연결 문자열/특성</span><span class="sxs-lookup"><span data-stu-id="ce0db-173">Trust Server Certificate connection string/attribute</span></span>|<span data-ttu-id="ce0db-174">결과</span><span class="sxs-lookup"><span data-stu-id="ce0db-174">Result</span></span>|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|<span data-ttu-id="ce0db-175">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-175">No</span></span>|<span data-ttu-id="ce0db-176">해당 없음</span><span class="sxs-lookup"><span data-stu-id="ce0db-176">N/A</span></span>|<span data-ttu-id="ce0db-177">아니요(기본값)</span><span class="sxs-lookup"><span data-stu-id="ce0db-177">No (default)</span></span>|<span data-ttu-id="ce0db-178">무시됨</span><span class="sxs-lookup"><span data-stu-id="ce0db-178">Ignored</span></span>|<span data-ttu-id="ce0db-179">암호화가 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-179">No encryption occurs.</span></span>|  
|<span data-ttu-id="ce0db-180">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-180">No</span></span>|<span data-ttu-id="ce0db-181">해당 없음</span><span class="sxs-lookup"><span data-stu-id="ce0db-181">N/A</span></span>|<span data-ttu-id="ce0db-182">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-182">Yes</span></span>|<span data-ttu-id="ce0db-183">아니요(기본값)</span><span class="sxs-lookup"><span data-stu-id="ce0db-183">No (default)</span></span>|<span data-ttu-id="ce0db-184">확인할 수 있는 서버 인증서가 있는 경우에만 암호화가 수행되고 그렇지 않으면 연결 시도가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-184">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="ce0db-185">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-185">No</span></span>|<span data-ttu-id="ce0db-186">해당 없음</span><span class="sxs-lookup"><span data-stu-id="ce0db-186">N/A</span></span>|<span data-ttu-id="ce0db-187">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-187">Yes</span></span>|<span data-ttu-id="ce0db-188">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-188">Yes</span></span>|<span data-ttu-id="ce0db-189">항상 암호화가 수행되지만 자체 서명된 서버 인증서가 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-189">Encryption always occurs, but may use a self-signed server certificate.</span></span>|  
|<span data-ttu-id="ce0db-190">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-190">Yes</span></span>|<span data-ttu-id="ce0db-191">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-191">No</span></span>|<span data-ttu-id="ce0db-192">무시됨</span><span class="sxs-lookup"><span data-stu-id="ce0db-192">Ignored</span></span>|<span data-ttu-id="ce0db-193">무시됨</span><span class="sxs-lookup"><span data-stu-id="ce0db-193">Ignored</span></span>|<span data-ttu-id="ce0db-194">검증 가능한 서버 인증서가 있는 경우에만 암호화가 발생 합니다. 그렇지 않으면 연결 시도가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-194">Encryption occurs only if there is a verifiable server certificate; otherwise, the connection attempt fails.</span></span>|  
|<span data-ttu-id="ce0db-195">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-195">Yes</span></span>|<span data-ttu-id="ce0db-196">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-196">Yes</span></span>|<span data-ttu-id="ce0db-197">아니요(기본값)</span><span class="sxs-lookup"><span data-stu-id="ce0db-197">No (default)</span></span>|<span data-ttu-id="ce0db-198">무시됨</span><span class="sxs-lookup"><span data-stu-id="ce0db-198">Ignored</span></span>|<span data-ttu-id="ce0db-199">항상 암호화가 수행되지만 자체 서명된 서버 인증서가 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-199">Encryption always occurs, but may use a self-signed server certificate.</span></span>|  
|<span data-ttu-id="ce0db-200">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-200">Yes</span></span>|<span data-ttu-id="ce0db-201">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-201">Yes</span></span>|<span data-ttu-id="ce0db-202">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-202">Yes</span></span>|<span data-ttu-id="ce0db-203">아니요(기본값)</span><span class="sxs-lookup"><span data-stu-id="ce0db-203">No (default)</span></span>|<span data-ttu-id="ce0db-204">검증 가능한 서버 인증서가 있는 경우에만 암호화가 발생 합니다. 그렇지 않으면 연결 시도가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-204">Encryption occurs only if there is a verifiable server certificate; otherwise, the connection attempt fails.</span></span>|  
|<span data-ttu-id="ce0db-205">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-205">Yes</span></span>|<span data-ttu-id="ce0db-206">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-206">Yes</span></span>|<span data-ttu-id="ce0db-207">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-207">Yes</span></span>|<span data-ttu-id="ce0db-208">예</span><span class="sxs-lookup"><span data-stu-id="ce0db-208">Yes</span></span>|<span data-ttu-id="ce0db-209">항상 암호화가 수행되지만 자체 서명된 서버 인증서가 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-209">Encryption always occurs, but may use a self-signed server certificate.</span></span>|  
  
 <span data-ttu-id="ce0db-210">자세한 내용은 [유효성 검사 없이 암호화 사용](/sql/relational-databases/native-client/features/using-encryption-without-validation)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0db-210">For more information, see [Using Encryption Without Validation](/sql/relational-databases/native-client/features/using-encryption-without-validation).</span></span>
  
## <a name="oledb-connection-strings"></a><span data-ttu-id="ce0db-211">OleDb 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="ce0db-211">OleDb Connection Strings</span></span>  
 <span data-ttu-id="ce0db-212"><xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>의 <xref:System.Data.OleDb.OleDbConnection> 속성을 사용하면 Microsoft Access와 같은 OLE DB 데이터 소스에 대한 연결 문자열을 가져오거나 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-212">The <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> property of a <xref:System.Data.OleDb.OleDbConnection> allows you to get or set a connection string for an OLE DB data source, such as Microsoft Access.</span></span> <span data-ttu-id="ce0db-213">`OleDb` 클래스를 사용하여 런타임에 <xref:System.Data.OleDb.OleDbConnectionStringBuilder> 연결 문자열을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-213">You can also create an `OleDb` connection string at run time by using the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> class.</span></span>  
  
### <a name="oledb-connection-string-syntax"></a><span data-ttu-id="ce0db-214">OleDb 연결 문자열 구문</span><span class="sxs-lookup"><span data-stu-id="ce0db-214">OleDb Connection String Syntax</span></span>  
 <span data-ttu-id="ce0db-215"><xref:System.Data.OleDb.OleDbConnection> 연결 문자열의 공급자 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-215">You must specify a provider name for an <xref:System.Data.OleDb.OleDbConnection> connection string.</span></span> <span data-ttu-id="ce0db-216">다음 연결 문자열은 Jet 공급자를 사용하여 Microsoft Access 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-216">The following connection string connects to a Microsoft Access database using the Jet provider.</span></span> <span data-ttu-id="ce0db-217">데이터베이스가 보호되지 않는 경우(기본값) `User ID`와 `Password` 키워드를 선택적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-217">Note that the `User ID` and `Password` keywords are optional if the database is unsecured (the default).</span></span>  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;
```  
  
 <span data-ttu-id="ce0db-218">사용자 수준의 보안을 사용하여 Jet 데이터베이스를 보호하는 경우에는 작업 그룹 정보 파일(.mdw)의 위치를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-218">If the Jet database is secured using user-level security, you must provide the location of the workgroup information file (.mdw).</span></span> <span data-ttu-id="ce0db-219">작업 그룹 정보 파일은 연결 문자열에 포함된 자격 증명의 유효성을 검사하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-219">The workgroup information file is used to validate the credentials presented in the connection string.</span></span>  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="ce0db-220">UDL (Universal Data Link) 파일에 **OleDbConnection** 에 대 한 연결 정보를 제공할 수 있습니다. 그러나 이렇게 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-220">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="ce0db-221">UDL 파일은 암호화되지 않으므로 연결 문자열 정보를 일반 텍스트로 노출시킵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-221">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="ce0db-222">UDL 파일은 애플리케이션에 대해 외부 파일 기반 리소스이므로 .NET Framework를 사용하여 보호할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-222">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span> <span data-ttu-id="ce0db-223">**SqlClient**의 경우 UDL 파일이 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-223">UDL files are not supported for **SqlClient**.</span></span>  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a><span data-ttu-id="ce0db-224">Access/Jet          DataDirectory</span><span class="sxs-lookup"><span data-stu-id="ce0db-224">Using DataDirectory to Connect to Access/Jet</span></span>  
 <span data-ttu-id="ce0db-225">`DataDirectory`는 `SqlClient`와 같이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-225">`DataDirectory` is not exclusive to `SqlClient`.</span></span> <span data-ttu-id="ce0db-226">또한 <xref:System.Data.OleDb> 및 <xref:System.Data.Odbc> .NET 데이터 공급자와도 같이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-226">It can also be used with the <xref:System.Data.OleDb> and <xref:System.Data.Odbc> .NET data providers.</span></span> <span data-ttu-id="ce0db-227">다음 샘플 <xref:System.Data.OleDb.OleDbConnection> 문자열에서는 애플리케이션의 app_data 폴더에 있는 Northwind.mdb에 연결하는 데 필요한 구문을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-227">The following sample <xref:System.Data.OleDb.OleDbConnection> string demonstrates the syntax required to connect to the Northwind.mdb located in the application's app_data folder.</span></span> <span data-ttu-id="ce0db-228">시스템 데이터베이스(System.mdw)도 같은 위치에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-228">The system database (System.mdw) is also stored in that location.</span></span>  
  
```csharp  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="ce0db-229">Access/Jet 데이터베이스가 안전하지 않은 경우 연결 문자열에 시스템 데이터베이스 위치를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-229">Specifying the location of the system database in the connection string is not required if the Access/Jet database is unsecured.</span></span> <span data-ttu-id="ce0db-230">기본적으로 보안이 해제되어 모든 사용자는 기본 제공 Admin 사용자 및 빈 암호로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-230">Security is off by default, with all users connecting as the built-in Admin user with a blank password.</span></span> <span data-ttu-id="ce0db-231">사용자 수준 보안이 제대로 구현된 경우에도 Jet 데이터베이스는 공격에 취약합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-231">Even when user-level security is correctly implemented, a Jet database remains vulnerable to attack.</span></span> <span data-ttu-id="ce0db-232">파일 기반 보안 스키마는 본래 보안에 취약하므로 Access/Jet 데이터베이스에 중요 정보를 저장하는 것은 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-232">Therefore, storing sensitive information in an Access/Jet database is not recommended because of the inherent weakness of its file-based security scheme.</span></span>  
  
### <a name="connecting-to-excel"></a><span data-ttu-id="ce0db-233">Excel에 연결</span><span class="sxs-lookup"><span data-stu-id="ce0db-233">Connecting to Excel</span></span>  
 <span data-ttu-id="ce0db-234">Microsoft Jet 공급자는 Excel 통합 문서에 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-234">The Microsoft Jet provider is used to connect to an Excel workbook.</span></span> <span data-ttu-id="ce0db-235">다음 연결 문자열에서 `Extended Properties` 키워드는 Excel 관련 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-235">In the following connection string, the `Extended Properties` keyword sets properties that are specific to Excel.</span></span> <span data-ttu-id="ce0db-236">"HDR=Yes;"는 첫 번째 행에 데이터가 아닌 열 이름이 있음을 나타내며 "IMEX=1;"은 "intermixed" 데이터 열을 항상 텍스트로 읽도록 드라이버에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-236">"HDR=Yes;" indicates that the first row contains column names, not data, and "IMEX=1;" tells the driver to always read "intermixed" data columns as text.</span></span>  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 <span data-ttu-id="ce0db-237">`Extended Properties`에 필요한 큰따옴표 문자는 큰따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-237">Note that the double quotation character required for the `Extended Properties` must also be enclosed in double quotation marks.</span></span>  
  
### <a name="data-shape-provider-connection-string-syntax"></a><span data-ttu-id="ce0db-238">Data Shape 공급자 연결 문자열 구문</span><span class="sxs-lookup"><span data-stu-id="ce0db-238">Data Shape Provider Connection String Syntax</span></span>  
 <span data-ttu-id="ce0db-239">Microsoft Data Shape 공급자를 사용하는 경우에는 `Provider`와 `Data Provider` 키워드를 모두 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0db-239">Use both the `Provider` and the `Data Provider` keywords when using the Microsoft Data Shape provider.</span></span> <span data-ttu-id="ce0db-240">다음 예제에서는 Data Shape 공급자를 사용하여 SQL Server의 로컬 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-240">The following example uses the Shape provider to connect to a local instance of SQL Server.</span></span>  
  
```csharp  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"
```  
  
## <a name="odbc-connection-strings"></a><span data-ttu-id="ce0db-241">Odbc 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="ce0db-241">Odbc Connection Strings</span></span>  
 <span data-ttu-id="ce0db-242"><xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>의 <xref:System.Data.Odbc.OdbcConnection> 속성을 사용하면 OLE DB 데이터 소스에 대한 연결 문자열을 가져오거나 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-242">The <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> property of a <xref:System.Data.Odbc.OdbcConnection> allows you to get or set a connection string for an OLE DB data source.</span></span> <span data-ttu-id="ce0db-243">Odbc 연결 문자열은 <xref:System.Data.Odbc.OdbcConnectionStringBuilder>에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-243">Odbc connection strings are also supported by the <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="ce0db-244">다음 연결 문자열에서는 Microsoft Text Driver를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-244">The following connection string uses the Microsoft Text Driver.</span></span>  
  
```csharp  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a><span data-ttu-id="ce0db-245">Visual FoxPro에 연결하기 위해 DataDirectory 사용</span><span class="sxs-lookup"><span data-stu-id="ce0db-245">Using DataDirectory to Connect to Visual FoxPro</span></span>  
 <span data-ttu-id="ce0db-246">다음 <xref:System.Data.Odbc.OdbcConnection> 연결 문자열 샘플에서는 `DataDirectory`를 사용하여 Microsoft Visual FoxPro 파일에 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-246">The following <xref:System.Data.Odbc.OdbcConnection> connection string sample demonstrates using `DataDirectory` to connect to a Microsoft Visual FoxPro file.</span></span>  
  
```csharp  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a><span data-ttu-id="ce0db-247">Oracle 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="ce0db-247">Oracle Connection Strings</span></span>  
 <span data-ttu-id="ce0db-248"><xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>의 <xref:System.Data.OracleClient.OracleConnection> 속성을 사용하면 OLE DB 데이터 소스에 대한 연결 문자열을 가져오거나 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-248">The <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> property of a <xref:System.Data.OracleClient.OracleConnection> allows you to get or set a connection string for an OLE DB data source.</span></span> <span data-ttu-id="ce0db-249">Oracle 연결 문자열은 <xref:System.Data.OracleClient.OracleConnectionStringBuilder>에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0db-249">Oracle connection strings are also supported by the <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .</span></span>  
  
```csharp
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 <span data-ttu-id="ce0db-250">ODBC 연결 문자열 구문에 대한 자세한 내용은 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0db-250">For more information on ODBC connection string syntax, see <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce0db-251">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce0db-251">See also</span></span>

- [<span data-ttu-id="ce0db-252">연결 문자열</span><span class="sxs-lookup"><span data-stu-id="ce0db-252">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="ce0db-253">데이터 소스에 연결</span><span class="sxs-lookup"><span data-stu-id="ce0db-253">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="ce0db-254">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="ce0db-254">ADO.NET Overview</span></span>](ado-net-overview.md)
