---
title: DBCC USEROPTIONS (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DBCC USEROPTIONS
- DBCC_USEROPTIONS_TSQL
- USEROPTIONS_TSQL
- USEROPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC USEROPTIONS statement
- active SET options
- SET statement, active SET options
ms.assetid: 565ab112-7af1-4c18-a579-07cdb332f539
caps.latest.revision: 41
author: uc-msft
ms.author: umajay
manager: craigg
ms.openlocfilehash: bd94360f42130c2ab60e58b6d7608c82b236077e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="dbcc-useroptions-transact-sql"></a>DBCC USEROPTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt die aktiven (also die festgelegten) SET-Optionen für die aktuelle Sitzung zurück.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
DBCC USEROPTIONS  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argumente  
NO_INFOMSGS  
Unterdrückt alle Informationsmeldungen mit einem Schweregrad von 0 bis 10.
  
## <a name="result-sets"></a>Resultsets  
DBCC USEROPTIONS gibt je eine Spalte für den Namen der SET-Option und für den Wert der Option zurück (Werte und Einträge können variieren):

```sql

Set Option                   Value`  
---------------------------- ---------------------------`  
textsize                     64512 
language                     us_english 
dateformat                   mdy  
datefirst                    7 
lock_timeout                 -1 
quoted_identifier            SET 
arithabort                   SET 
ansi_null_dflt_on            SET 
ansi_warnings                SET 
ansi_padding                 SET 
ansi_nulls                   SET 
concat_null_yields_null      SET 
isolation level              read committed  
(13 row(s) affected) 
DBCC execution completed. If DBCC printed error messages, contact your system administrator.
 ```  
  
## <a name="remarks"></a>Hinweise  
DBCC USEROPTIONS meldet die Isolationsstufe 'read committed snapshot', wenn die Datenbankoption READ_COMMITTED_SNAPSHOT auf ON festgelegt ist und die Isolationsstufe der Transaktion auf 'read commited' festgelegt ist. Die eigentliche Isolationsstufe ist 'read commited'.
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die Mitgliedschaft in der **public** -Rolle.
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel werden die aktiven SET-Optionen für die aktuelle Sitzung zurückgegeben.
  
```sql  
DBCC USEROPTIONS;  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[SET-Anweisungen &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
[SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)
  
  
