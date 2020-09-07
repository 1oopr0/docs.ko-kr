---
ms.openlocfilehash: ccba3cf98a1ca9e199d9a48f00e254bf34b93f72
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496549"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a>BinaryFormatter가 LoadFrom 컨텍스트에서 형식을 찾지 못함

#### <a name="details"></a>설명

.NET Framework 4.5부터 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>의 여러 가지 변경으로 인해 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName>을 사용하여 LoadFrom 컨텍스트에서 로드된 형식을 역직렬화할 때 역직렬화의 차이가 발생할 수 있습니다. 이러한 변경 내용은 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName>이 나중에 해당 형식으로 역직렬화를 시도할 때 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>이 다른 동작을 유발하는 형식을 로드하는 새로운 방법 때문입니다. 기본 직렬화 바인더는 XmlSerializer의 이전 동작에 따라 일부 상황에서 작동했을지라도 LoadFrom 컨텍스트를 자동으로 검색하지 않습니다. 변경 내용으로 인해 다른 컨텍스트에서 로드된 어셈블리에서 형식을 로드할 때 <xref:System.IO.FileNotFoundException?displayProperty=fullName>이 throw될 수 있습니다.

#### <a name="suggestion"></a>제안 해결 방법

이 예외가 표시되면 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName>의 <code>Binder</code> 속성을 올바른 형식을 찾을 수 있는 사용자 지정 바인더로 설정할 수 있습니다.<pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre>그런 다음, 사용자 지정 바인더:<pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>

| 이름    | 값       |
|:--------|:------------|
| Scope   |Microsoft Edge|
|버전|4.5|
|형식|런타임|

#### <a name="affected-apis"></a>영향을 받는 API

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)`

-->
