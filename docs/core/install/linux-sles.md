---
title: SLES에 .NET 설치 - .NET
description: SLES에 .NET SDK 및 .NET 런타임을 설치하는 다양한 방법을 보여 줍니다.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 558574116aac2a3c755481069641e81a435a2a43
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506889"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-sles"></a>SLES에 .NET SDK 또는 .NET 런타임 설치

.NET은 SLES에서 지원됩니다. 이 문서에서는 SLES에 .NET을 설치하는 방법을 설명합니다.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a>지원되는 배포

다음 표는 SLES 12 SP2와 SLES 15에서 현재 지원되는 .NET 릴리스의 목록입니다. 이러한 버전은 [.NET 버전이 지원 종료에 도달](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)하거나 SLES 버전이 더 이상 지원되지 않을 때까지 계속 지원됩니다.

- ✔️는 SLES 또는 .NET 버전이 계속 지원됨을 나타냅니다.
- ❌는 SLES 또는 .NET 버전이 해당 SLES 릴리스에서 지원되지 않음을 나타냅니다.
- SLES 버전과 .NET 버전 모두에 ✔가 있으면 해당 OS와 .NET 조합은 지원됩니다.

| SLES                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](#sles-15-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [12 SP2](#sles-12-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |

다음 .NET Core 버전은 더 이상 지원되지 않습니다. 이러한 버전의 다운로드는 여전히 게시된 상태로 유지됩니다.

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>다른 버전을 설치하는 방법

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a>SLES 15 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

현재 SLES 15 Microsoft 리포지토리 설치 패키지는 *microsoft-prod.repo* 파일을 잘못된 디렉터리에 설치하므로 zypper가 .NET 패키지를 찾을 수 없습니다. 이 문제를 해결하려면 올바른 디렉터리에 symlink를 만듭니다.

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="sles-12-"></a>SLES 12 ✔️

.NET에는 SLES 12 제품군에 대한 최소 요건으로 SP2가 필요합니다.

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a>패키지 관리자 문제 해결

이 섹션에서는 패키지 관리자를 사용하여 .NET을 설치할 때 발생할 수 있는 일반적인 오류에 대한 정보를 제공합니다.

### <a name="failed-to-fetch"></a>가져오지 못함

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a>종속성

패키지 관리자를 설치할 때 이러한 라이브러리가 설치됩니다. 그러나 .NET을 수동으로 설치하거나 자체 포함 앱을 게시할 경우 이러한 라이브러리가 설치되어 있는지 확인해야 합니다.

- krb5
- libicu
- libopenssl1_1

대상 런타임 환경의 OpenSSL 버전이 1.1 이상인 경우, **compat-openssl10** 을 설치해야 합니다.

종속성에 대한 자세한 내용은 [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)(자체 포함 Linux 앱)를 참조하세요.

*System.Drawing.Common* 어셈블리를 사용하는 .NET 앱의 경우 다음과 같은 종속성도 필요합니다.

- [libgdiplus(버전 6.0.1 이상)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > 시스템에 Mono 리포지토리를 추가하여 최신 버전의 *libgdiplus* 를 설치할 수 있습니다. 자세한 내용은 <https://www.mono-project.com/download/stable/>를 참조하세요.

## <a name="scripted-install"></a>스크립팅된 설치

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>수동 설치

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>다음 단계

- [자습서: Visual Studio Code를 사용하여 .NET SDK에서 콘솔 애플리케이션 만들기](../tutorials/with-visual-studio-code.md)
