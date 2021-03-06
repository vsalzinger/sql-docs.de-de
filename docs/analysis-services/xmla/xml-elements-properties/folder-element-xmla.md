---
title: Folder-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 184ae189e07a76eaf4fa3d68914c209927f48ff7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="folder-element-xmla"></a>Folder-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält einen Speicherort im Dateisystem aktualisiert werden muss eine [Speicherort](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) -Element während einer [wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) oder [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Folders>  
   ...  
   <Folder>  
      <Original>...</Original>  
      <New>...</New>  
   </Folder>  
   ...  
</Folders>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Ordner](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|Untergeordnete Elemente|[Neue](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md), [ursprünglichen](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das **Folder** -Element ändert, wenn es angegeben ist, die Speicherorte der Objekte, die entweder in der Sicherungsdatei ( **Restore** -Befehle) oder der Datenbank auf der Quellinstanz ( **Synchronize** -Befehle) enthalten sind und die den Wert des **Original** -Elements mit dem Wert des **New** -Elements abgleichen.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Objekten finden Sie unter [sichern, wiederherstellen, und Synchronisieren von Datenbanken & #40; XMLA & #41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [StorageLocation-Element & #40; ASSL & #41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
