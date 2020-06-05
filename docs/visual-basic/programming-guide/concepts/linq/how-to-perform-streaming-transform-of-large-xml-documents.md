---
title: '방법: 큰 XML 문서의 스트리밍 변환 수행'
ms.date: 07/20/2015
ms.assetid: 3d954cc9-4b3c-4b47-8132-ff7541cff53b
ms.openlocfilehash: f648371581ed2854c107ebed920068e2abec4239
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397988"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-visual-basic"></a><span data-ttu-id="9c9e6-102">방법: 대량 XML 문서의 스트리밍 변환 수행 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c9e6-102">How to: Perform Streaming Transform of Large XML Documents (Visual Basic)</span></span>
<span data-ttu-id="9c9e6-103">큰 XML 파일을 변환하고 애플리케이션의 메모리 사용 공간이 예상 가능하도록 애플리케이션을 작성해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="9c9e6-104">XML 트리를 매우 큰 XML 파일로 채우려는 경우 메모리 사용은 파일 크기에 비례하므로 지나치게 증가하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="9c9e6-105">따라서 스트리밍 기법을 대신 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="9c9e6-106">스트리밍 기법은 소스 문서를 한 번만 처리해야 하고 문서 순서의 요소를 처리할 수 있는 경우에 가장 효과적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="9c9e6-107"><xref:System.Linq.Enumerable.OrderBy%2A>와 같은 특정 표준 쿼리 연산자는 자신의 소스를 반복하고 모든 데이터를 수집하여 정렬한 다음 시퀀스의 첫 번째 항목을 최종적으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="9c9e6-108">첫 번째 항목을 반환하기 전에 소스를 유형화하는 쿼리 연산자를 사용하는 경우 애플리케이션에 대한 작은 메모리 사용 공간이 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="9c9e6-109">[방법: 헤더 정보에 액세스 하 여 Xml 조각 스트리밍 (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md)에 설명 된 기법을 사용 하는 경우에도 변환 된 문서를 포함 하는 xml 트리를 조합 하려고 하면 메모리 사용이 너무 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="9c9e6-110">두 가지 주요 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-110">There are two main approaches.</span></span> <span data-ttu-id="9c9e6-111">그 중 하나는 <xref:System.Xml.Linq.XStreamingElement>의 지연된 처리 특성을 사용하는 것이고,</span><span class="sxs-lookup"><span data-stu-id="9c9e6-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="9c9e6-112">다른 하나는 <xref:System.Xml.XmlWriter>를 만들고 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]의 기능을 사용하여 요소를 <xref:System.Xml.XmlWriter>에 쓰는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="9c9e6-113">이 항목에서는 두 방법을 모두 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c9e6-114">예제</span><span class="sxs-lookup"><span data-stu-id="9c9e6-114">Example</span></span>  
 <span data-ttu-id="9c9e6-115">다음 예제는 [방법: 헤더 정보에 액세스 하 여 XML 조각 스트리밍 (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md)의 예제를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="9c9e6-116">이 예제에서는 <xref:System.Xml.Linq.XStreamingElement>의 지연된 실행 기능을 사용하여 출력을 스트림합니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="9c9e6-117">이 예제에서는 작은 메모리 사용 공간을 유지하면서도 매우 큰 문서를 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="9c9e6-118">사용자 지정 축(`StreamCustomerItem`)은 문서에 `Customer`, `Name` 및 `Item` 요소가 있고 이러한 요소가 다음 Source.xml 문서의 경우와 마찬가지로 정렬되어 있다고 가정하고 작성된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="9c9e6-119">그러나 더욱 강력한 구현은 잘못된 문서의 구문을 분석할 준비가 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="9c9e6-120">다음은 소스 문서인 Source.xml입니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-120">The following is the source document, Source.xml:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
```vb  
Module Module1  
    Sub Main()  
        Dim root = New XStreamingElement("Root",  
            From el In New StreamCustomerItem("Source.xml")  
            Select <Item>  
                       <Customer><%= el.Parent.<Name>.Value %></Customer>  
                       <%= el.<Key> %>  
                   </Item>  
            )  
        root.Save("Test.xml")  
        Console.WriteLine(My.Computer.FileSystem.ReadAllText("Test.xml"))  
    End Sub  
End Module  
  
Public Class StreamCustomerItem  
    Implements IEnumerable(Of XElement)  
  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamCustomerItemEnumerator(_uri)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamCustomerItemEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _customerName As String  
    Private _reader As Xml.XmlReader  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        Dim item As XElement  
        Dim name As XElement  
  
        ' Parse the file, save header information when encountered, and return the  
        ' current Item XElement.  
  
        ' loop through Customer elements  
        While _reader.Read()  
            If _reader.NodeType = Xml.XmlNodeType.Element Then  
                Select Case _reader.Name  
                    Case "Customer"  
                        ' move to Name element  
                        While _reader.Read()  
  
                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso  
                                _reader.Name = "Name" Then  
  
                                name = TryCast(XElement.ReadFrom(_reader), XElement)  
                                _customerName = If(name IsNot Nothing, name.Value, "")  
                                Exit While  
                            End If  
  
                        End While  
                    Case "Item"  
                        item = TryCast(XElement.ReadFrom(_reader), XElement)  
                        Dim tempRoot = <Root>  
                                           <Name><%= _customerName %></Name>  
                                           <%= item %>  
                                       </Root>  
                        _current = item  
                        Return True  
                End Select  
            End If  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 <span data-ttu-id="9c9e6-121">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-121">This code produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="9c9e6-122">예제</span><span class="sxs-lookup"><span data-stu-id="9c9e6-122">Example</span></span>  
 <span data-ttu-id="9c9e6-123">다음 예제는 [방법: 헤더 정보에 액세스 하 여 XML 조각 스트리밍 (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md)의 예제를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="9c9e6-124">이 예제에서는 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]의 기능을 사용하여 요소를 <xref:System.Xml.XmlWriter>에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="9c9e6-125">이 예제에서는 작은 메모리 사용 공간을 유지하면서도 매우 큰 문서를 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="9c9e6-126">사용자 지정 축(`StreamCustomerItem`)은 문서에 `Customer`, `Name` 및 `Item` 요소가 있고 이러한 요소가 다음 Source.xml 문서의 경우와 마찬가지로 정렬되어 있다고 가정하고 작성된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="9c9e6-127">그러나 더욱 강력한 구현은 XSD를 사용하여 소스 문서의 유효성을 검사하거나, 잘못된 문서의 구문을 분석할 준비가 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="9c9e6-128">이 예제에서는 이 항목의 이전 예제와 동일한 소스 문서인 Source.xml을 사용하고</span><span class="sxs-lookup"><span data-stu-id="9c9e6-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="9c9e6-129">똑같은 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="9c9e6-130"><xref:System.Xml.Linq.XStreamingElement>를 사용하여 출력 XML을 스트림하는 것이 <xref:System.Xml.XmlWriter>에 쓰는 것보다 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim srcTree =  
            From el In New StreamCustomerItem("Source.xml")  
            Select <Item>  
                       <Customer><%= el.Parent.<Name>.Value %></Customer>  
                       <%= el.<Key> %>  
                   </Item>  
  
        Dim xws = New Xml.XmlWriterSettings()  
        xws.OmitXmlDeclaration = True  
        xws.Indent = True  
        Using xw = Xml.XmlWriter.Create("Output.xml", xws)  
            xw.WriteStartElement("Root")  
            For Each el In srcTree  
                el.WriteTo(xw)  
            Next  
            xw.WriteEndElement()  
        End Using  
  
        Dim s = My.Computer.FileSystem.ReadAllText("Output.xml")  
        Console.WriteLine(s)  
    End Sub  
End Module  
  
Public Class StreamCustomerItem  
    Implements IEnumerable(Of XElement)  
  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamCustomerItemEnumerator(_uri)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamCustomerItemEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _customerName As String  
    Private _reader As Xml.XmlReader  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        Dim item As XElement  
        Dim name As XElement  
  
        ' Parse the file, save header information when encountered, and return the  
        ' current Item XElement.  
  
        ' loop through Customer elements  
        While _reader.Read()  
            If _reader.NodeType = Xml.XmlNodeType.Element Then  
                Select Case _reader.Name  
                    Case "Customer"  
                        ' move to Name element  
                        While _reader.Read()  
  
                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso  
                                _reader.Name = "Name" Then  
  
                                name = TryCast(XElement.ReadFrom(_reader), XElement)  
                                _customerName = If(name IsNot Nothing, name.Value, "")  
                                Exit While  
                            End If  
  
                        End While  
                    Case "Item"  
                        item = TryCast(XElement.ReadFrom(_reader), XElement)  
                        Dim tempRoot = <Root>  
                                           <Name><%= _customerName %></Name>  
                                           <%= item %>  
                                       </Root>  
                        _current = item  
                        Return True  
                End Select  
            End If  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 <span data-ttu-id="9c9e6-131">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-131">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c9e6-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c9e6-132">See also</span></span>

- [<span data-ttu-id="9c9e6-133">Visual Basic (Advanced LINQ to XML 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="9c9e6-133">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
