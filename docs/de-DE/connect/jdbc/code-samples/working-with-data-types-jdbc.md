---
title: Arbeiten mit Datentypen (JDBC) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49bc94f966bae9ae92e101789aa072f2ce398601
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-data-types-jdbc"></a>Arbeiten mit Datentypen (JDBC)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Die Hauptfunktion von der [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] besteht darin, Java-Entwicklern den Zugriff auf Daten ermöglichen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Datenbanken. Um dies zu erreichen, der JDBC-Treiber sorgt für die Konvertierung zwischen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] -Datentypen und Java-Typen und Objekte.  
  
> [!NOTE]  
>  Für eine ausführliche Erläuterung der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] und JDBC-treiberdatentypen, einschließlich deren Unterschiede und deren Konvertierung in Java-Datentypen, finden Sie unter [Grundlegendes zu den Datentypen des JDBC-Treiber](../../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
 Um mit SQL Server-Datentypen zu arbeiten, stellt der JDBC-Treiber Get\<Typ > und legen Sie\<Typ > Methoden für die [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) und [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) Klassen sowie Get\<Typ > und Aktualisieren von\<Typ > Methoden für die [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) Klasse. Die verwendete Methode hängt vom Datentyp ab, der verarbeitet wird, sowie davon, ob Resultsets oder Abfragen verwendet werden.  
  
 Die Themen in diesem Abschnitt wird beschrieben, wie die Datentypen des JDBC-Treiber verwenden, den Zugriff auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Daten in Ihren Java-Anwendungen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[Standarddatentypen – Beispiel](../../../connect/jdbc/basic-data-types-sample.md)|Beschreibt, wie Abrufmethoden Ergebnis abgerufen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] -Datentyp, Werte und zum Ergebnis Set-Methoden verwenden, um diese Werte zu aktualisieren.|  
|[Beispiel für den SQLXML-Datentyp](../../../connect/jdbc/sqlxml-data-type-sample.md)|Beschreibt, wie ein XML-Daten in einer relationalen Datenbank gespeichert, wie XML-Daten aus einer Datenbank abgerufen und das Analysieren von XML-Daten mit den **SQLXML** Java-Datentyp.|  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiele für JDBC-Treiberanwendungen](../../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
