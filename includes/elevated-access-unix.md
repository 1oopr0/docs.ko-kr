---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67540114"
---
### <a name="install-the-global-tool"></a><span data-ttu-id="7c813-101">글로벌 도구 설치</span><span class="sxs-lookup"><span data-stu-id="7c813-101">Install the global tool</span></span>

<span data-ttu-id="7c813-102">패키지 자산은 `--tool-path` 옵션을 사용하여 보호된 위치에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c813-102">Package assets should be installed in a protected location using the `--tool-path` option.</span></span> <span data-ttu-id="7c813-103">이러한 분리는 제한된 사용자 환경을 높은 환경과 공유하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c813-103">This separation avoids sharing a restricted user environment with an elevated environment.</span></span>

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="7c813-104">`/usr/local/share/dotnet-tools`는 `drwxr-xr-x` 사용 권한으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c813-104">`/usr/local/share/dotnet-tools` will be created with permission `drwxr-xr-x`.</span></span> <span data-ttu-id="7c813-105">디렉터리가 이미 존재하는 경우 `ls -l` 명령을 사용하여 제한된 사용자에게 디렉터리 편집 권한이 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7c813-105">If the directory already exists, use the `ls -l` command to verify the restricted user doesn't have permission to edit the directory.</span></span> <span data-ttu-id="7c813-106">그렇다면 `sudo chmod o-w -R /usr/share/dotnet-tools` 명령을 사용하여 액세스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7c813-106">If so, use the `sudo chmod o-w -R /usr/share/dotnet-tools` command to remove the access.</span></span>

### <a name="run-the-global-tool"></a><span data-ttu-id="7c813-107">글로벌 도구 실행</span><span class="sxs-lookup"><span data-stu-id="7c813-107">Run the global tool</span></span>

<span data-ttu-id="7c813-108">**옵션 1** sudo로 함께 전체 경로를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7c813-108">**Option 1** Use the full path with sudo:</span></span>

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

<span data-ttu-id="7c813-109">**옵션 2** 도구당 한 번씩 도구의 기호 링크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7c813-109">**Option 2** Add the symbol link of the tool, once per tool:</span></span>

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

<span data-ttu-id="7c813-110">다음 항목으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7c813-110">And run with:</span></span>

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="7c813-111">글로벌 도구 제거</span><span class="sxs-lookup"><span data-stu-id="7c813-111">Uninstall the global tool</span></span>

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="7c813-112">기호 링크를 만든 경우 기호 링크도 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c813-112">If you made a symbol link, you also need to remove it:</span></span>

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```