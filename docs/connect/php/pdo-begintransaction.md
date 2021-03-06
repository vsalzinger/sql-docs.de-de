---
title: 'PDO:: BeginTransaction | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4d5db438-9df7-4d22-9907-3ddc63bd2220
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e4ad9df1db56719e683a3047f19a9f1842df9f3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="pdobegintransaction"></a>PDO::beginTransaction
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Schaltet den Autocommit-Modus aus und beginnt eine Transaktion.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
bool PDO::beginTransaction();  
```  
  
## <a name="return-value"></a>Rückgabewert  
„true“, bei erfolgreichem Aufruf der Methode; andernfalls „false“.  
  
## <a name="remarks"></a>Hinweise  
Die Transaktion, die mit PDO:: BeginTransaction gestartet wurde beendet, wenn [PDO:: Commit](../../connect/php/pdo-commit.md) oder [PDO:: Rollback](../../connect/php/pdo-rollback.md) aufgerufen wird.  
  
PDO::beginTransaction ist nicht betroffen von dem (und hat keinen Einfluss auf den) Wert von PDO::ATTR_AUTOCOMMIT.  
  
Sie dürfen PDO::beginTransaction nicht aufrufen, solange die vorherige PDO::beginTransaction noch nicht mit PDO::rollback oder PDO::commit beendet wurde.  
  
Wenn diese Methode fehlschlägt, werden die Verbindung zum Autocommit-Modus zurückgegeben.  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
Im folgenden Beispiel wird eine Datenbank namens „Test“ und eine Tabelle namens „Tabelle1“ verwendet. Es startet eine Transaktion und gibt die Befehle aus, um zwei Zeilen hinzuzufügen und dann eine Zeile zu löschen. Diese Befehle werden an die Datenbank geschickt und die Transaktion wird explizit mit `PDO::commit`beendet.  
  
```  
<?php  
   $conn = new PDO( "sqlsrv:server=(local); Database = Test", "", "");  
   $conn->beginTransaction();  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'b') ");  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'c') ");  
   $ret = $conn->exec("delete from Table1 where col1 = 'a' and col2 = 'b'");  
   $conn->commit();  
   // $conn->rollback();  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>Siehe auch  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
