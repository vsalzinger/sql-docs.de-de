---
title: Initialisieren eines Abonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
caps.latest.revision: 32
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 84bab2f62678b6a76389fe87fa06a9160f2342e6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="initialize-a-subscription"></a>Initialisieren eines Abonnements
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Abonnenten in einer Replikationstopologie müssen initialisiert werden, damit sie für jeden Artikel in der Veröffentlichung, die sie abonniert haben, eine Kopie des Schemas sowie alle erforderlichen Replikationsobjekte (gespeicherte Prozeduren, Trigger, Metadatentabellen usw.) erhalten. Darüber hinaus erhält der Abonnent typischerweise einen Anfangsdatensatz. Die Standardinitialisierungsmethode verwendet eine vollständige Momentaufnahme mit Schema, Replikationsobjekten und Daten. Veröffentlichungen können aber auch ohne eine vollständige Momentaufnahme initialisiert werden.  
  
 Weitere Informationen finden Sie unter [Initialize a Subscription with a Snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) und [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
  
