---
title: Command Events Data Columns | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ef4275eb57228ab31cac346a4dcbf6cfbdd39976
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="command-events-data-columns"></a>Datenspalten für Befehlsereignisse
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In der folgenden Tabelle sind die Datenspalten für jede Ereignisklasse in der **Befehlsereignisse** -Ereigniskategorie aufgeführt.  
  
 Die **Befehlsereignisse** -Ereigniskategorie weist folgende Ereignisklassen auf:  
  
-   [Command Begin-Klasse](#bkmk_1)  
  
-   [Command End-Klasse](#bkmk_2)  
  
 In den folgenden Tabellen sind die Datenspalten für jede dieser Ereignisklassen aufgeführt.  
  
##  <a name="bkmk_1"></a> Command Begin-Klasse – Datenspalten  
  
|Datenspalte|Description|  
|-----------------|-----------------|  
|ConnectionID|Enthält die eindeutige Verbindungs-ID, die dem Befehlsereignis zugeordnet ist.|  
|TextData|Enthält die eindeutigen Textdaten, die dem Befehlsereignis zugeordnet sind.|  
|ServerName|Enthält den Namen der Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , in der das Befehlsereignis aufgetreten ist.|  
|CurrentTime|Enthält die aktuelle Zeit des Befehlsereignisses.|  
|DatabaseName|Enthält den Namen der Datenbank, in der der Befehl ausgeführt wird.|  
|EventSubclass|Enthält die Ereignisklasse innerhalb des Befehlsereignisses. Diese Werte werden unterstützt:<br /><br /> 0: Create<br /><br /> 1: Alter<br /><br /> 2: Delete<br /><br /> 3: Process<br /><br /> 4: DesignAggregations<br /><br /> 5: WBInsert<br /><br /> 6: WBUpdate<br /><br /> 7: WBDelete<br /><br /> 8: Backup<br /><br /> 9: Restore<br /><br /> 10: MergePartitions<br /><br /> 11: Subscribe<br /><br /> 12: Batch<br /><br /> 13: BeginTransaction<br /><br /> 14: CommitTransaction<br /><br /> 15: RollbackTransaction<br /><br /> 16: GetTransactionState<br /><br /> 17: Cancel<br /><br /> 18: Synchronize<br /><br /> 19: Import80MiningModels<br /><br /> 20: Attach<br /><br /> 21: Detach<br /><br /> 22: SetAuthContext<br /><br /> 23: ImageLoad<br /><br /> 24: ImageSave<br /><br /> 10000: Other|  
|NTUserName|Enthält den Windows-Benutzernamen, der dem Befehlsereignis zugeordnet ist. Der Benutzername liegt im kanonischen Format vor. Beispiel: engineering.microsoft.com/software/user.|  
|RequestProperties|Enthält die XMLA-Anforderungseigenschaften (XML for Analysis), die dem Befehlsereignis zugeordnet sind.|  
|SPID|Enthält die Serverprozess-ID (SPID), mit der die Benutzersitzung eindeutig identifiziert wird, die dem Befehlsereignis zugeordnet ist. Die SPID entspricht direkt dem von XMLA verwendeten Sitzungs-GUID.|  
|StartTime|Enthält die Zeit, zu der das Befehlsereignis gestartet wurde, falls verfügbar.|  
|SessionType|Enthält die Entität, die den Vorgang verursacht hat.|  
|NTDomainName|Enthält das Windows-Domänenkonto, das dem Objektberechtigungsereignis zugeordnet ist.|  
|ClientProcessID|Enthält die eindeutige Clientprozess-ID, die dem Befehlsereignis zugeordnet ist.|  
  
##  <a name="bkmk_2"></a> Command End-Klasse – Datenspalten  
  
|Datenspalte|Description|  
|-----------------|-----------------|  
|ConnectionID|Enthält die eindeutige Verbindungs-ID, die dem Befehlsereignis zugeordnet ist.|  
|TextData|Enthält die eindeutigen Textdaten, die dem Befehlsereignis zugeordnet sind.|  
|ServerName|Enthält den Namen der Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , in der das Befehlsereignis aufgetreten ist.|  
|CurrentTime|Enthält die aktuelle Zeit des Befehlsereignisses. Für das Filtern stehen die Formate *JJJJ*-*MM*-*TT* und *JJJJ*-*MM*-*TT HH*:*MM*:*SS*zur Verfügung.|  
|DatabaseName|Enthält den Namen der Datenbank, in der der Befehl ausgeführt wird.|  
|Dauer|Enthält die ungefähre Dauer zwischen dem Command Begin- und dem Command End-Ereignis.|  
|EndTime|Enthält die Zeit, zu der das Befehlsereignis endete. Für das Filtern stehen die Formate *JJJJ*-*MM*-*TT* und *JJJJ*-*MM*-*TT HH*:*MM*:*SS*zur Verfügung.|  
|EventSubclass|Enthält die Ereignisklasse innerhalb des Befehlsereignisses. Diese Werte werden unterstützt:<br /><br /> 0: Create<br /><br /> 1: Alter<br /><br /> 2: Delete<br /><br /> 3: Process<br /><br /> 4: DesignAggregations<br /><br /> 5: WBInsert<br /><br /> 6: WBUpdate<br /><br /> 7: WBDelete<br /><br /> 8: Backup<br /><br /> 9: Restore<br /><br /> 10: MergePartitions<br /><br /> 11: Subscribe<br /><br /> 12: Batch<br /><br /> 13: BeginTransaction<br /><br /> 14: CommitTransaction<br /><br /> 15: RollbackTransaction<br /><br /> 16: GetTransactionState<br /><br /> 17: Cancel<br /><br /> 18: Synchronize<br /><br /> 19: Import80MiningModels<br /><br /> 20: Attach<br /><br /> 21: Detach<br /><br /> 22: SetAuthContext<br /><br /> 23: ImageLoad<br /><br /> 24: ImageSave<br /><br /> 10000: Other|  
|NTCanonicalUserName|Enthält den Windows-Benutzernamen, der dem Befehlsereignis zugeordnet ist. Der Benutzername liegt im kanonischen Format vor. Beispiel: engineering.microsoft.com/software/user.|  
|NTUserName|Enthält das Windows-Benutzerkonto, das dem Befehlsereignis zugeordnet ist.|  
|SPID|Enthält die Serverprozess-ID (SPID), mit der die Benutzersitzung eindeutig identifiziert wird, die dem Befehlsereignis zugeordnet ist. Die SPID entspricht direkt dem von XMLA verwendeten Sitzungs-GUID.|  
|StartTime|Enthält die Zeit, zu der das End-Befehlsereignis gestartet wurde, falls verfügbar.|  
|CPUTime|Enthält die CPU-Zeit (in Millisekunden), die vom Prozess zwischen dem Begin-Befehlsereignis und dem End-Befehlsereignis verwendet wurde.|  
|Fehler|Enthält die Fehlernummer jedes Fehlers, der dem Befehlsereignis zugeordnet ist.|  
|Severity|Enthält den Schweregrad einer Ausnahme, die dem Befehlsereignis zugeordnet ist. Die Werte sind:<br /><br /> 0 = Erfolg<br /><br /> 1 = Information<br /><br /> 2 = Warnung<br /><br /> 3 = Fehler|  
|Success|Enthält die Erfolgs- bzw. Fehlschlagsinformation des Befehlsereignisses. Die Werte sind:<br /><br /> 0 = Fehler<br /><br /> 1 = Erfolg|  
|SessionType|Enthält die Entität, die die Operation verursacht hat, die dem End-Befehlsereignis zugeordnet ist.|  
|NTDomainName|Enthält das Windows-Domänenkonto, das dem Befehlsereignis zugeordnet ist.|  
|ClientProcessID|Enthält die eindeutige Clientprozess-ID, die dem Befehlsereignis zugeordnet ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Befehlsereignisse (Ereigniskategorie)](../../analysis-services/trace-events/command-events-event-category.md)  
  
  
