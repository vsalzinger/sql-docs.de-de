---
title: Audit Database Scope GDR-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: event-classes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Audit Database Scope GDR event class
ms.assetid: 1641a38a-ef24-46ce-b2f4-bf732858c771
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5873f9a3c815a1e42d68d17e1b2bd537c5fcb9da
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="audit-database-scope-gdr-event-class"></a>Audit Database Scope GDR (Ereignisklasse)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die **Audit Database Scope GDR** -Ereignisklasse tritt immer auf, wenn Benutzer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für ausschließlich datenbankrelevante Vorgänge ein GRANT-, REVOKE- oder DENY für eine Anweisungsberechtigung ausgeben, beispielsweise das Gewähren von Berechtigungen für eine Datenbank.  
  
## <a name="audit-database-scope-gdr-event-class-data-columns"></a>Audit Database Scope GDR-Ereignisklasse (Datenspalten)  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|ja|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|ja|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|ja|  
|**DatabaseName**|**nvarchar**|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|ja|  
|**DBUserName**|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benutzername des Clients.|40|ja|  
|**EventClass**|**int**|Ereignistyp = 102.|27|nein|  
|**EventSequence**|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|**EventSubClass**|**int**|Der Typ der Ereignisunterklasse.<br /><br /> 1 = Erteilen<br /><br /> 2 = Aufheben<br /><br /> 3 = Verweigern|21|ja|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|ja|  
|**LoginName**|**nvarchar**|Anmeldename des Benutzers (Anmeldung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|ja|  
|**LoginSid**|**image**|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|ja|  
|**NTDomainName**|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|ja|  
|**NTUserName**|**nvarchar**|Windows-Benutzername.|6|ja|  
|**ObjectName**|**nvarchar**|Name des Objekts, auf das verwiesen wird|34|ja|  
|**ObjectType**|**int**|Der Wert, der den Typ des am Ereignis beteiligten Objekts darstellt. Dieser Wert entspricht der type-Spalte in der **sys.objects** -Katalogsicht. Weitere Werte finden Sie unter [ObjectType (Spalte für Ablaufverfolgungsereignisse)](../../relational-databases/event-classes/objecttype-trace-event-column.md).|28|ja|  
|**OwnerName**|**nvarchar**|Datenbank-Benutzername des Objektbesitzers.|37|ja|  
|**Berechtigungen**|**bigint**|Wert für ganze Zahl, der den Typ der überprüften Berechtigungen darstellt.<br /><br /> 1=CREATE DATABASE<br /><br /> 2 = CREATE TABLE<br /><br /> 4 = CREATE PROCEDURE<br /><br /> 8 = CREATE VIEW<br /><br /> 16 = CREATE RULE<br /><br /> 32 = CREATE DEFAULT<br /><br /> 64 = BACKUP DATABASE<br /><br /> 128 = BACKUP LOG<br /><br /> 256 = BACKUP TABLE<br /><br /> 512 = CREATE FUNCTION|19|ja|  
|**RequestID**|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|ja|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|**SessionLoginName**|**Nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|ja|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|ja|  
|**Success**|**int**|1 = Erfolg 0 = Fehler. Der Wert 1 deutet beispielsweise auf eine erfolgreiche Überprüfung der Berechtigungen hin, während die Überprüfung bei dem Wert 0 fehlgeschlagen ist.|23|ja|  
|**TargetLoginName**|**nvarchar**|Für Aktionen, die auf einen Anmeldenamen abzielen (z. B. das Hinzufügen eines neuen Anmeldenamens), der Anmeldename, auf den abgezielt wird.|42|ja|  
|**TargetLoginSid**|**image**|Für Aktionen, die auf einen Anmeldenamen abzielen (z. B. das Hinzufügen eines neuen Anmeldenamens), die Sicherheits-ID (SID), auf die abgezielt wird.|43|ja|  
|**TargetUserName**|**nvarchar**|Für Aktionen, die auf einen Datenbankbenutzer abzielen (z. B. das Erteilen von Berechtigungen für einen Benutzer), der Name des Benutzers.|39|ja|  
|**TextData**|**ntext**|SQL-Text der Gewähren-/Aufheben-/Verweigern-Anweisung.|1|ja|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|ja|  
|**XactSequence**|**bigint**|Token zur Beschreibung der aktuellen Transaktion.|50|ja|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)  
  
  
