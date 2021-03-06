---
title: "Entwicklungsumgebung für Docker-Apps"
description: Lebenszyklus von Docker-Containeranwendungen mit der Microsoft-Plattform und Tools
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ad1a6e4cb0974ebb067cf1a7be987d696e8bc82a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/23/2017
---
# <a name="development-environment-for-docker-apps"></a>Entwicklungsumgebung für Docker-Apps

## <a name="development-tools-choices-ide-or-editor"></a>Optionen für Entwicklungstools: IDE oder -Editor

Unabhängig davon Wunsch eine vollständige und leistungsfähige IDE oder eine einfache und agile-Editor, hat Microsoft Sie beim Entwickeln von Docker-Anwendungen behandelt.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio-Code und Docker-Befehlszeilenschnittstelle (plattformübergreifenden Tools für Windows, Mac und Linux)

Wenn Sie einen einfachen, plattformübergreifende-Editor unterstützt Entwicklungssprache bevorzugen, können Sie Visual Studio-Code und Docker-Befehlszeilenschnittstelle verwenden. Diese Produkte bieten eine einfache, aber robuste erzielen Sie, die für die Optimierung von des Developer-Workflows entscheidender Bedeutung ist. Installieren Sie "Docker für Mac" oder "Docker für Windows" (Development Environment), können Docker-Entwickler eine einzelne Docker-Befehlszeilenschnittstelle Sie um apps für Windows oder Linux (Common Language Runtime Environment) zu erstellen. Darüber hinaus Visual Studio Code unterstützt Erweiterungen für Docker mit IntelliSense für dockerfile-Dateien und Verknüpfung Aufgaben zum Docker-Befehle aus dem Editor ausführen.

> [!NOTE]
> Um Visual Studio Code herunterzuladen, wechseln Sie zu <https://code.visualstudio.com/download>.

Um Docker für Macintosh- und Windows herunterzuladen, wechseln Sie zu <http://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools"></a>Visual Studio mit Docker-Tools

Wenn Sie Visual Studio 2015 verwenden, können Sie das Add-on-Tools "Docker-Tools für Visual Studio." installieren Für Visual Studio 2017 stammen Docker-Tools bereits integrierten. In beiden Fällen können Sie entwickeln, ausführen und überprüfen Ihre Anwendungen direkt in der ausgewählten Docker-Umgebung. F5 Ihrer Anwendung (einzelne Container oder mehrere Container) direkt in ein Docker hosten beim Debuggen oder drücken Sie STRG + F5, bearbeiten und aktualisieren Sie die app ohne den Container neu erstellt wird. Dies ist die einfachste und leistungsfähiger Wahl für Windows-Entwickler, die Docker-Container für Linux- oder Windows erstellen.

> [!NOTE]
> Um Docker-Tools für Visual Studio herunterzuladen, wechseln Sie zu <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.

## <a name="language-and-framework-choices"></a>Sprache und Framework-Optionen

Sie können die Docker-Anwendungen und Microsoft-Tools für die meisten modernen Sprachen entwickeln. Im folgenden finden eine anfängliche Liste, aber Sie sind nicht darauf beschränkt:

-   .NET Core und ASP.NET Core

-   Node.js

-   Golang

-   Java

-   Ruby

-   Python

Grundsätzlich können Sie eine moderne Sprache, die von Docker unter Linux oder Windows unterstützt.


>[!div class="step-by-step"]
[Vorherigen] (orchestrieren-High-Skalierbarkeit-availability.md) [weiter] (Docker-apps-Inner-Schleife-workflow.md)
