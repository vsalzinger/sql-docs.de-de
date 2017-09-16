---
title: NEWSEQUENTIALID (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/08/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NEWSEQUENTIALID
- NEWSEQUENTIALID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- NEWSEQUENTIALID function
- GUIDs [SQL Server]
ms.assetid: e06d2cab-f1ff-42f1-8550-6aaec57be36f
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2a453b99d7ab0512e57275b5ad1805f5a66522ba
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="newsequentialid-transact-sql"></a>NEWSEQUENTIALID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Erstellt einen GUID, der größer ist als alle GUIDs, die seit dem Start von Windows bisher von dieser Funktion auf einem angegebenen Computer generiert wurden. Nach dem Neustart von Windows kann der GUID wieder in einem niedrigeren Bereich beginnen, ist aber immer noch global eindeutig. Wenn eine GUID-Spalte als Zeilenbezeichner verwendet wird, kann die Verwendung von NEWSEQUENTIALID schneller zu Ergebnissen führen als die Verwendung der NEWID-Funktion. Dies ist darauf zurückzuführen, dass die NEWID-Funktion zufällige Aktivität erzeugt und weniger zwischengespeicherte Datenseiten verwendet. Die Verwendung von NEWSEQUENTIALID hilft auch beim vollständigen Ausfüllen der Daten- und Indexseiten.  
  
> [!IMPORTANT]  
>  Falls Datenschutz eine wichtige Überlegung ist, sollten Sie diese Funktion nicht verwenden. Der Wert der als Nächstes erstellten GUID ist vorhersagbar, daher ist auch der Zugriff auf Daten möglich, die mit dieser GUID verknüpft sind.  
  
 NEWSEQUENTIALID ist ein Wrapper über die Windows [UuidCreateSequential](http://go.microsoft.com/fwlink/?LinkId=164027) Funktion.  
  
> [!WARNING]  
>  Die UuidCreateSequential-Funktion muss es sich um Hardware Abhängigkeiten. Auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Clustern mit sequenziellen Werten können entstehen, wenn Datenbanken (z. B. eigenständige Datenbanken) auf andere Computer verschoben werden. Verwendung von Always On und auf [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)], Clustern mit sequenziellen Werten können entstehen, wenn die Datenbank auf einen anderen Computer Failover.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
NEWSEQUENTIALID ( )  
```  
  
## <a name="return-type"></a>Rückgabetyp  
 **uniqueidentifier**  
  
## <a name="remarks"></a>Hinweise  
 NEWSEQUENTIALID() kann nur verwendet werden, mit DEFAULT-Einschränkungen für Tabellenspalten vom Typ **"uniqueidentifier"**. Beispiel:  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT NEWSEQUENTIALID());   
```  
  
 Wenn NEWSEQUENTIALID() in DEFAULT-Ausdrücken verwendet wird, ist eine Kombination mit anderen Skalaroperatoren nicht möglich. Sie können z. B. folgende Aktionen nicht ausführen:  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT dbo.myfunction(NEWSEQUENTIALID()));  
```  
  
 Im vorherigen Beispiel ist `myfunction()` eine benutzerdefinierte Skalarfunktion, die einen `uniqueidentifier`-Wert annimmt und zurückgibt.  
  
 Auf NEWSEQUENTIALID() kann in Abfragen nicht verwiesen werden.  
  
 Sie können NEWSEQUENTIALID() zum Generieren von GUIDs verwenden, um Seitenteilungen und zufällige E/A auf Blattebene von Indizes zu reduzieren.  
  
 Jede mit NEWSEQUENTIALID() generierte GUID ist auf diesem Computer eindeutig. Die mit NEWSEQUENTIALID() generierten GUIDs sind nur über mehrere Computer hinweg eindeutig, wenn der Quellcomputer über eine Netzwerkkarte verfügt.  
  
## <a name="see-also"></a>Siehe auch  
 [NEWID &#40; Transact-SQL &#41;](../../t-sql/functions/newid-transact-sql.md)   
 [Vergleichsoperatoren &#40; Transact-SQL &#41;](../../t-sql/language-elements/comparison-operators-transact-sql.md)  
  
  
