---
title: Row-Eigenschaft (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::PutRow
- ADORecordConstruction::GetRow
- ADORecordConstruction::get_Row
- ADORecordConstruction::Row
- ADORecordConstruction::put_Row
helpviewer_keywords:
- Row property [ADO]
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65ef451a62023eea3139098370bd3b65f6352811
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="row-property-ado"></a>Row-Eigenschaft (ADO)
Ruft ab oder legt einen OLE DB- **Zeile** Objekt aus, oder auf eine [ADORecordConstruction Schnittstelle](../../../ado/reference/ado-api/adorecordconstruction-interface.md) Objekt. Bei Verwendung von **Put_Row** festzulegende eine **Zeile** -Objekt, eine Zeile in einer ADO umgewandelt ist **Datensatz** Objekt.  
  
## <a name="readwritesyntax"></a>Lese-/Schreibzugriff. Syntax  
  
```  
HRESULT get_Row([out, retval] IUnknown** ppRow);  
HRESULT put_Row([in] IUnknown* pRow);  
```  
  
## <a name="parameters"></a>Parameter  
 *ppRow*  
 Zeiger auf einen OLE DB- **Zeile** Objekt.  
  
 *PRow*  
 OLE DB- **Zeile** Objekt.  
  
## <a name="return-values"></a>Rückgabewerte  
 Diese Eigenschaftsmethode gibt die standardmäßige HRESULT-Werte, einschließlich S_OK und E_FAIL zurück.  
  
## <a name="applies-to"></a>Gilt für  
 [ADORecordConstruction-Schnittstelle](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
