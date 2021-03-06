---
title: ConnectionTimeout-Eigenschaft (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b60682fdc85cf7f24c21e5ac4a2f2efc9d3fb30
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="connectiontimeout-property-ado"></a>ConnectionTimeout-Eigenschaft (ADO)
Gibt an, wie lange gewartet wird, beim Herstellen einer Verbindung, bevor der Versuch beendet und ein Fehler generiert.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **lange** Wert an, in Sekunden an, wie lange um zu warten, bis die Verbindung zu öffnen. Standard ist 15.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie die **ConnectionTimeout** Eigenschaft auf einen [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt, wenn es Verzögerungen von Datenverkehr oder extremer die Verwendung des Server versucht, eine Verbindung zu verwerfen stellen. Wenn die Zeit aus der **ConnectionTimeout** Eigenschaft verstreicht, vor dem Öffnen der Verbindung, ein Fehler auftritt und ADO wird den Versuch abgebrochen. Wenn Sie die Eigenschaft auf 0 (null) festlegen, wartet ADO unbegrenzt, bis die Verbindung geöffnet wird. Stellen Sie sicher, dass der Anbieter, zu dem Sie Code schreiben, unterstützt die **ConnectionTimeout** Funktionalität.  
  
 Die **ConnectionTimeout** Eigenschaft ist Lese-/Schreibzugriff auf, wenn die Verbindung ist geschlossen und Read-only, wenn er geöffnet ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 ["ConnectionString" ConnectionTimeout und State-Eigenschaft (Beispiel) (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 ["ConnectionString" ConnectionTimeout und State-Eigenschaft (VC++-Beispiel)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [CommandTimeout-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)
