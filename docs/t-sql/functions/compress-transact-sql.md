---
title: KOMPRIMIEREN (Transact-SQL) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COMPRESS
- COMPRESS_TSQL
helpviewer_keywords:
- COMPRESS function
ms.assetid: c2bfe9b8-57a4-48b4-b028-e1a3ed5ece88
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c30cb5f351d9a84beec608483380edb94b8c7844
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="compress-transact-sql"></a>KOMPRIMIEREN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Den eingegebenen Ausdruck mithilfe des GZIP-Algorithmus komprimiert werden. Das Ergebnis der Komprimierung ist Byte-Array des Typs **varbinary(max)**.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
COMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Argumente  
*expression*  
Ist eine **Nvarchar (***n***)**, **nvarchar(max)**, **Varchar (**  *n*  **)**, **varchar(max)**, **Varbinary (**  *n*  **)**, **varbinary(max)**, **Char (***n***)**, **Nchar ()**   *n*  **)**, oder **binäre (***n***)** Ausdruck. Weitere Informationen finden Sie unter [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="return-types"></a>Rückgabetypen
Gibt den Datentyp der **varbinary(max)** , die am komprimierten Inhalt der Eingabe darstellt.
  
## <a name="remarks"></a>Hinweise  
Komprimierte Daten können nicht indiziert werden.
  
Die Funktion COMPRESS komprimiert die Daten als der eingegebene Ausdruck bereitgestellt und für jeden Bereich, der die zu komprimierenden Daten aufgerufen werden muss. Automatische Komprimierung auf der Zeilen- oder Seitenebene während der Speicher, finden Sie unter [Datenkomprimierung](../../relational-databases/data-compression/data-compression.md).
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-compress-data-during-the-table-insert"></a>A. Daten komprimieren, während die Tabelle einfügen  
Im folgende Beispiel wird gezeigt, wie beim Komprimieren von Daten in die Tabelle eingefügt wird:
  
```sql
INSERT INTO player (name, surname, info )  
VALUES (N'Ovidiu', N'Cracium',   
        COMPRESS(N'{"sport":"Tennis","age": 28,"rank":1,"points":15258, turn":17}'));  
  
INSERT INTO player (name, surname, info )  
VALUES (N'Michael', N'Raheem', compress(@info));  
```  
  
### <a name="b-archive-compressed-version-of-deleted-rows"></a>B. Archivieren Sie komprimierte Version der gelöschten Zeilen  
Die folgende Anweisung löscht alte Player-Datensätze aus der `player` Tabelle und speichert die Datensätze in der `inactivePlayer` Tabelle in einem komprimierten Format, um Platz zu sparen.
  
```sql
DELETE player  
WHERE datemodified < @startOfYear  
OUTPUT id, name, surname datemodifier, COMPRESS(info)   
INTO dbo.inactivePlayers ;  
```  
  
## <a name="see-also"></a>Siehe auch
[Zeichenfolgenfunktionen &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
[DEKOMPRIMIEREN &#40; Transact-SQL &#41;](../../t-sql/functions/decompress-transact-sql.md)
  
  
