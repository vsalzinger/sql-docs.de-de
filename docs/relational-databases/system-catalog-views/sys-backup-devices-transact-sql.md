---
title: Sys. backup_devices (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- backup_devices_TSQL
- backup_devices
- sys.backup_devices
- sys.backup_devices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], viewing information
- sys.backup_devices catalog view
ms.assetid: 457edaa4-aca1-4bd3-bf8d-734490b80fcd
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: be1c29322063c33797ff56451b55c619fd07db82
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="sysbackupdevices-transact-sql"></a>sys.backup_devices (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede registrierte mit Sicherungsmedium **Sp_addumpdevice** oder in erstellte [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Name des Sicherungsmediums. Ist im Sicherungssatz eindeutig.|  
|**type**|**tinyint**|Typ des Sicherungsmediums:<br /><br /> 2 = Datenträger<br /><br /> 3 = Diskette (veraltet)<br /><br /> 5 = Band<br /><br /> 6 = Pipe (veraltet)<br /><br /> 7 = Virtuelles Medium (für die optionale Verwendung von Drittsicherungsanbietern)<br /><br /> In der Regel werden nur Datenträger (2) und Band (5) verwendet.|  
|**type_desc**|**nvarchar(60)**|Beschreibung des Sicherungsmediumtyps:<br /><br /> DISK<br /><br /> DISKETTE (veraltet)<br /><br /> TAPE<br /><br /> PIPE (veraltet)<br /><br /> VIRTUAL_DEVICE (für die optionale Verwendung von Sicherungsdrittanbietern)<br /><br /> In der Regel werden nur DISK und TAPE verwendet.|  
|**physical_name**|**nvarchar(260)**|Physischer Dateiname oder Pfad des Sicherungsmediums.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Sicherungsmedien &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [Datenbanken und Dateikatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [Häufig gestellte Fragen zu Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
