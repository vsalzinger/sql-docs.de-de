---
title: IsClosed-Methode (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.isClosed
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3560ab18-4350-4d02-9716-439f0c2f7142
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 94028c26ce5f2a7d43db72f9874e37dc68ec6877
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="isclosed-method-sqlserverconnection"></a>IsClosed-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob dies [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) Objekt geschlossen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** ist die Verbindung schließen, **"false"** wird jedoch nicht.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Hinweise  
 Diese IsClosed-Methode wird von der IsClosed-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Überprüft den Status des aufgerufenen SQLServerConnection-Objekts. Eine Verbindung wird geschlossen, wenn die [schließen](../../../connect/jdbc/reference/close-method-sqlserverconnection.md) Methode, die davon aufgerufen wurde oder bestimmte schwerwiegende Fehler aufgetreten sind. Von dieser Methode zurückgegeben **"true"** nur wenn sie aufgerufen wird, nachdem der close-Methode aufgerufen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
