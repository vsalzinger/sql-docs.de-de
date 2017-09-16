---
title: 'Senden die Updates: UpdateBatch-Methode | Microsoft Docs'
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87123797-831f-48e0-94b5-f669f9ca194a
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6cad1bfd63ffafd32d0621f6142717cd7175ccd0
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="sending-the-updates-updatebatch-method"></a>Senden die Updates: UpdateBatch-Methode
Im folgende Code wird ein Recordset im Batchmodus durch Festlegen der LockType-Eigenschaft AdLockBatchOptimistic und CursorLocation auf AdUseClient geöffnet. Es fügt zwei neue Datensätze und ändert den Wert eines Felds in einem vorhandenen Datensatz, und speichern die ursprünglichen Werte, und ruft dann UpdateBatch um, dass die Änderungen werden wieder an die Datenquelle zu senden.  
  
## <a name="remarks"></a>Hinweise  
  
```  
'BeginBatchUpdate  
    strConn = "Provider=SQLOLEDB;Initial Catalog=Northwind;" & _  
              "Data Source=MySQLServer;Integrated Security=SSPI;"  
  
    strSQL = "SELECT ShipperId, CompanyName, Phone FROM Shippers"  
  
    Set objRs1 = New ADODB.Recordset  
    objRs1.CursorLocation = adUseClient  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
  
    ' Change value of Phone field for first record in Recordset, saving value  
    ' for later restoration.  
    intId = objRs1("ShipperId")  
    sPhone = objRs1("Phone")  
  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Add two new records  
    For i = 0 To 1  
        objRs1.AddNew  
        objRs1(1) = "New Shipper #" & CStr((i + 1))  
        objRs1(2) = "(nnn) 555-" & i & i & i & i  
    Next i  
  
    ' Send the updates  
    objRs1.UpdateBatch  
'EndBatchUpdate  
```  
  
 Wenn Sie den aktuellen Datensatz bearbeiten oder einen neuen Datensatz hinzufügen, wenn Sie die UpdateBatch-Methode aufrufen, wird die Update-Methode, um alle ausstehenden Änderungen in den aktuellen Datensatz zu speichern, vor dem Übertragen der zusammengefasste Änderungen an den Anbieter automatisch von ADO aufrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Batchmodus](../../../ado/guide/data/batch-mode.md)