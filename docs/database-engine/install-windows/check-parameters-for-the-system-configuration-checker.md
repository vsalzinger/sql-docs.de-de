---
title: Überprüfen der Parameter für die Systemkonfigurationsprüfung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/05/2017
ms.prod: sql
ms.prod_service: install
ms.reviewer: ''
ms.suite: sql
ms.technology: install
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, system configuration checks
- failed system configuration checks [SQL Server]
- verifying configuration before installation
- SCC [SQL Server]
- system configuration checker
- scanning computer before installation [SQL Server]
- checking configuration before installation
- status information [SQL Server], system configuration checker
- parameters [SQL Server], system configuration checker
- configuration checkers [SQL Server]
- Setup [SQL Server], system configuration checker
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
caps.latest.revision: 46
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b92f343b3969e00931a81436e53f3dd7d1be6db7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="check-parameters-for-the-system-configuration-checker"></a>Überprüfen der Parameter für die Systemkonfigurationsprüfung

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Während des Setups von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durchsucht die Systemkonfigurationsprüfung (System Configuration Checker, SCC) den Computer, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert werden soll. Die SCC sucht nach Bedingungen, die eine erfolgreiche Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verhindern. Bevor Setup den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installations-Assistenten startet, ruft SCC den Status jedes Elements ab. SCC vergleicht dann das Ergebnis mit den erforderlichen Bedingungen und gibt Anweisungen zum Entfernen der Blockierungsprobleme.  
  
Die Systemkonfigurationsprüfung generiert einen Bericht, der eine kurze Beschreibung für jede ausgeführte Regel sowie den Ausführungsstatus enthält. Der Bericht der Systemkonfigurationsprüfung befindet sich unter %programfiles%\Microsoft SQL Server\140\Setup Bootstrap\Log\\\<JJJJMMTT_hhmm>\\\..    
  
Weitere Informationen finden Sie unter den folgenden Links:

- [Hardware- und Softwareanforderungen für die Installation von SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
- [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
- [Unterstützte Versions- und Editionsupgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
  
