---
title: FilterGroupEnum | Microsoft Docs
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 424bb4b32915c774778cfd32dab18c42c5e573a8
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="filtergroupenum"></a>FilterGroupEnum
Gibt die Gruppe von Datensätzen aus gefiltert werden sollen eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|Filter für die Anzeige von nur Datensätze, die von der letzten betroffenen [löschen](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), oder [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) aufrufen.|  
|**vorliegt**|5|Filter für die Anzeige der Datensätze, die die letzte Batchaktualisierung fehlgeschlagen ist.|  
|**adFilterFetchedRecords**|3|Filter für die Anzeige der Datensätze im aktuellen Cache – d. h. die Ergebnisse der dem letzten Aufruf von Datensätzen aus der Datenbank abzurufen.|  
|**adFilterNone**|0|Entfernt den aktuellen Filter und alle Datensätze für die Anzeige wiederhergestellt.|  
|**adFilterPendingRecords**|1|Filter für die Anzeige von Datensätzen, die geändert wurden, aber noch nicht an den Server gesendet wurden. Gilt nur für Batch-Updatemodus.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.FilterGroup.AFFECTEDRECORDS|  
|AdoEnums.FilterGroup.CONFLICTINGRECORDS|  
|AdoEnums.FilterGroup.FETCHEDRECORDS|  
|AdoEnums.FilterGroup.NONE|  
|AdoEnums.FilterGroup.PENDINGRECORDS|  
  
## <a name="applies-to"></a>Gilt für  
 [Filter-Eigenschaft](../../../ado/reference/ado-api/filter-property.md)