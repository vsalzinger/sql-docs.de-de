---
title: CrossProduct-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 07e34958589bd9366cda6b42207c289bfda72453
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="crossproduct-element-xmla"></a>CrossProduct-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält ein Kreuzprodukt geordneten Mengen an Elementen aus jeder Hierarchie für eine [Achse](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) Element, das verwendet die [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) von zurückgegebener Datentyp der [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Axis>  
   ...  
   <CrossProduct Size="integer">  
      <Members>...</Members>  
   </CrossProduct>  
   ...  
</Axis>  
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
|Übergeordnete Elemente|[Achse](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
|Untergeordnete Elemente|[Element](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|Attribut|Description|  
|---------------|-----------------|  
|Größe|Erforderliche **Ganzzahl** Attribut. Gibt die Anzahl von Tupeln in das Kreuzprodukt, dargestellt durch die **CrossProduct** Element.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Clientanwendung legt die **AxisFormat** Eigenschaft, um *' Clusterformat '*, die Elemente auf jeder Achse in Cluster in der jeder Cluster ein Kreuzprodukt geordneten Mengen an darstellt unterteilt Elemente aus jeder Hierarchie. Jeder Cluster wird dargestellt, durch eine **CrossProduct** Element. Jede **CrossProduct** Element enthält eine **Elemente** -Element für jede Hierarchie auf der Achse. Ein **CrossProduct** Element kann Elemente aus einer einzelnen Hierarchie enthalten.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Struktur der **CrossProduct** -Element, wenn ein Client angibt, *' Clusterformat '* für die **AxisFormat** angegebene XMLA-Eigenschaft der folgende Elemente für die Achse:  
  
||||||  
|-|-|-|-|-|  
|**Time**-Hierarchie|1999|1999|2000|2001|  
|**Category**-Hierarchie|Tatsächlich|Budget|Budget|Budget|  
|Clusters|Cluster 1|Cluster 1|Cluster 1|Cluster 2|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size="4">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
      <CrossProduct Size="1">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[2001]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
