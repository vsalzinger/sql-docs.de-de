---
title: Exception-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 91350ba6e82e070707d17b58c82bf305c1e87660
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="exception-element-xmla"></a>Exception-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Gibt an, dass eine Ausnahme zurückgegeben wurde, aus einer [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) oder [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) -Methodenaufruf.  
  
 **Namespace** `http://schemas.microsoft.com/analysisservices/2003/exception`  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<root>  
   ...  
   <Exception />  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Stamm](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Fehler auftritt, während der **Discover** -Methodenaufruf oder ein einzelner XMLA-Befehl in einem **Execute** -Methodenaufruf auftritt, der verhindert, dass die Methode oder der Befehl abgeschlossen werden kann, enthält das **root** -Element für diese Methode/diesen Befehl ein **Exception** - und ein **Messages** -Element. Das **Exception** -Element gibt an, dass ein Fehler aufgetreten ist, der verhindert, dass die Methode oder der Befehl erfolgreich ausgeführt wird, und das **Messages** -Element enthält die Liste der entsprechenden Fehler- oder Warnmeldungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Element Nachrichten &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)   
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
