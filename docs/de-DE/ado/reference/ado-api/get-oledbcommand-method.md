---
title: Get_OLEDBCommand Methode | Microsoft Docs
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
helpviewer_keywords:
- get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 849ec1b0ffe714a8f8894649c4873ed0911b2cc1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="getoledbcommand-method"></a>Get_OLEDBCommand-Methode
Gibt den zugrunde liegenden OLE DB-Befehl, weitergeben zuerst alle Parameterinformationen für den ADO-Befehl an den OLE DB-Befehl festgelegt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 *ppOLEDBCommand*  
 [out] Ein Zeiger auf einen Zeiger Speicherort, in dem der IUnknown-Zeiger für den zugrunde liegenden OLE DB-Befehl geschrieben wird.  
  
## <a name="applies-to"></a>Gilt für  
 [IADOCommandConstruction](http://msdn.microsoft.com/en-us/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)
