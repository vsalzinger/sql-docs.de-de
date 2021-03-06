---
title: SQL Server-Meldungsergebnisse | Microsoft Docs
description: SQL Server-Meldungsergebnisse
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d9ab76565bac6a1fbf41dd5f8372776ea8625975
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-message-results"></a>SQL Server-Meldungsergebnisse
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen generieren keine OLE DB-Treiber für SQL Server-Rowsets oder Anzahl der betroffenen Zeilen zurück, wenn ausgeführt:  
  
-   PRINT  
  
-   RAISERROR mit einem Schweregrad von 10 oder niedriger  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Diese Anweisungen geben entweder eine oder mehrere Informationsmeldungen zurück oder veranlassen, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Informationsmeldungen anstelle von Rowset- oder Anzahlergebnissen zurückgibt. Bei einer erfolgreichen Ausführung der OLE DB-Treiber für SQL Server gibt S_OK zurück, und die Nachrichten für den OLE DB-Treiber für SQL Server-Consumer verfügbar sind.  
  
 Der OLE DB-Treiber für SQL Server gibt S_OK zurück und hat eine oder mehrere informationsmeldungen jeweils nach der Ausführung zahlreicher [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen oder die Ausführung Consumer einen OLE DB-Treiber für SQL Server-Memberfunktion.  
  
 Der OLE DB-Treiber für SQL Server-Consumer ermöglicht die dynamische Angabe von Abfragetext prüfen Schnittstellen für Error nach jeder Ausführung der Elementfunktion unabhängig vom Wert des den Rückgabecode, Anwesenheit oder Abwesenheit eines zurückgegebenen **IRowset** oder **IMultipleResults** -Schnittstellenverweises oder die Anzahl der betroffenen Zeilen.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler](../../oledb/ole-db-errors/errors.md)  
  
  
